This is a Spark/Cassandra demo using the open-source **[Spark Cassandra Connector]**

There are 2 packages with 2 distinct demos

* _us.unemployment.demo_
<ul>
    <li> Ingestion
        <ol>
            <li> <strong>FromCSVToCassandra</strong>: read US employment data from CSV file into Cassandra</li>
            <li> <strong>FromCSVCaseClassToCassandra</strong>: read US employment data from CSV file, create case class and insert into Cassandra</li>
        </ol>
    </li>
    <li> Read
        <ol>
            <li> <strong>FromCassandraToRow</strong>: read US employment data from Cassandra into <strong>CassandraRow</strong> low-level object</li>
            <li> <strong>FromCassandraToCaseClass</strong>: read US employment data from Cassandra into custom Scala case class, leveraging the built-in object mapper</li>
            <li> <strong>FromCassandraToSQL</strong>: read US employment data from Cassandra using <strong>SparkSQL</strong> a the connector integration
        </ol>
    </li>        
</ul>

* _twitter.stream_
<ul>
    <li> <strong>TwitterStreaming</strong>: demo of Twitter stream saved back to Cassandra (<strong>stream IN</strong>). To make this demo work, you need to start the job with the following info:

        <ol>
            <li>-Dtwitter4j.oauth.consumerKey="value"</li>
            <li>-Dtwitter4j.oauth.consumerSecret="value"</li>
            <li>-Dtwitter4j.oauth.accessToken="value"</li>
            <li>-Dtwitter4j.oauth.accessTokenSecret="value"</li>
        </ol>
        
        If you don't have a Twitter app credentials, create a new apps at <a href="https://apps.twitter.com/" target="_blank">https://apps.twitter.com/</a>
  </li>
</ul>
 
* _weather.data.demo_
<ul>
    <li> Data preparation
        <ol>
            <li> Go to the folder main/data</li>
            <li> Execute <em>$CASSANDRA_HOME/bin/cqlsh -f weather_data_schema.cql</em> from this folder. It should create the keyspace <strong>spark_demo</strong> and some tables </li>
            <li> Download the <em>Weather_Raw_Data_2014.csv.gz</em> from <strong><a target="blank_" href="https://drive.google.com/file/d/0B6wR2aj4Cb6wOF95QUZmVTRPR2s/view?usp=sharing">here</a></strong> (&gt;200Mb)</li>
            <li> Unzip it somewhere on your disk </li>
        </ol>
    </li>
    <li> Ingestion
        <ol>
            <li> <strong>WeatherDataIntoCassandra</strong>: read all the <em>Weather_Raw_Data_2014.csv</em> file (30.10<sup>6</sup> lines) and insert the data into Cassandra. It may take some time before the ingestion is done so go take a long coffee ( &lt; 1 hour on my MacBookPro 15") 
            Please do not forget set the path to this file by changing the <strong>WeatherDataIntoCassandra.WEATHER_2014_CSV</strong> value</li>
        </ol>
        This step should take a while since there are 30.10<sup>6</sup> lines to be inserted into Cassandra
    </li>
    <li> Read
        <ol>
            <li> <strong>WeatherDataFromCassandra</strong>: read all raw weather data plus all weather stations details, 
            filter the data by French station and take data only between March and June 2014. 
            Then compute average on temperature and pressure</li>
        </ol>
        This step should take a while since there are 30.10<sup>6</sup> lines to be read from Cassandra
    </li>        
</ul>

[Spark Cassandra Connector]: https://github.com/datastax/spark-cassandra-connector

