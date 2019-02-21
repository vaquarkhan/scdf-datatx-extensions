Running the JDBC hive


Making a new jar


java -jar  target/jdbc-hive-source-kafka-2.1.0.JDBC-HIVE.jar --spring.datasource.driver-class-name=org.apache.hive.jdbc.HiveDriver  --spring.datasource.url="jdbc:hive2://host:port/databaseName;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=hiveserver2" --spring.datasource.username=hive --spring.datasource.password=hive --spring.cloud.stream.kafka.binder.brokers=localhost:9092 --spring.cloud.stream.kafka.binder.minPartitionCount=3  --logging.level=DEBUG  --spring.cloud.stream.bindings.output.contentType=application/json  --spring.cloud.stream.kafka.streams.binder.configuration.default.key.serde=org.apache.kafka.common.serialization.Serdes$StringSerde --spring.cloud.stream.bindings.output.nativeEncoding=false  --spring.cloud.stream.kafka.streams.binder.configuration.default.value.serde=org.apache.kafka.common.serialization.Serdes$StringSerde --spring.cloud.stream.kafka.streams.binder.configuration.value.serializer=org.apache.kafka.common.serialization.Serdes$StringSerde --jdbc.query="select to_char(due_date, 'YYYY-MM-dd HH:MI:SS:MS' ) as dueDate, match_key as matchKey, account_nbr as accountNbr,   primary_synchrony_id as primaryKey,
  secondary_synchrony_id as secondaryKey from account" --spring.cloud.stream.bindings.output.destination=account-master-input --jdbc.split=true  --trigger.cron="05 * * * * ?"
