## Ansible role for Kafka cluster creation and management
- Installs [kafka](https://kafka.apache.org/)
- Is Kafka version 10.1.0 compatible

## Example Playbook
    - name: configure kafka nodes
    hosts: kafka
    roles:
    - sl.kafka

## Example group_vars:
    kafka_hosts: 'kafka-0.example.com:9092,kafka-1.example.com:9092'
    zookeeper_hosts: 'zk-0.example.com:2181,zk-1.example.com:2181'
    kafka_heap_opts: "-Xms2G -Xmx6G"
    kafka_num_partitions: 1

##Requirements
- kafka_hosts - comma separated list of host:port pairs in the cluster, defaults to 'ansible_fqdn:9092' for a single node
- zookeeper_hosts - comma separated list of host:port pairs.

##Optional
- kafka_id - specify the kafka cluster ID if one isn't available from kafka_hosts
- wait_for_period - The time in seconds for how long to wait for Kafka's port to be available after starting it. Default is 180 seconds.
- log_level - Log level to be used for Kafka logs. Defaults to WARN
- run_mode - One of Deploy, Stop, Install, Start, or Use. The default is Deploy which will do Install, Configure, then Start.
## SSL options not currently functional
