![image](images/confluent-logo-300-2.png)

* Confluent Platform components
  * Schema Registry + Kafka Connect worker (Datagen Source connector plugin installed) + Confluent Control Center + REST Proxy + ksqlDB 

# cp-all-in-one

1. [`cp-all-in-one`](cp-all-in-one)
   1. == Confluent Platform's Confluent Enterprise License version
   2. == Confluent Server + Schema Registry + Kafka Connect worker (/ Datagen Source connector plugin installed) + Confluent Control Center + REST Proxy + ksqlDB + Flink
2. [`cp-all-in-one-community`](cp-all-in-one-community)
   1. == Confluent Platform's Confluent Community License version
   2. == Kafka broker + Schema Registry + Kafka Connect worker (/ Datagen Source connector plugin installed) + Confluent Control Center + REST Proxy + ksqlDB + Flink
3. [`cp-all-in-one-cloud`](cp-all-in-one-cloud)
   1. == Docker Compose files
   2. uses
      1. run Confluent Platform components -- against -- Confluent Cloud 
4. [`cp-all-in-one-security/oauth`](cp-all-in-one-security/oauth)
   1. == Confluent Platform's Confluent Enterprise License version /
      1. provie -- via [Keycloak](https://www.keycloak.org/) identity provider -- Confluent Platform's OAuth 2.0

# Usage as a GitHub Action

- `service`
  - == service | docker-compose.yml / -- to -- run
  - by default, none
    - == ALL services run
- `github-branch-version`
  - == [cp-all-in-one](https://github.com/confluentinc/cp-all-in-one)'s GitHub branch -- to -- run
  - by default, `latest`
- `type`
  - ALLOWED values
    - `cp-all-in-one` 
      - == -- based on -- Confluent Server
      - _Example:_ | Confluent Platform `7.7.1`
        ```yaml
        
            steps:
        
              - name: Run Confluent Platform (Confluent Server)
                uses: confluentinc/cp-all-in-one@v0.1
                with:
                  service: broker
                  github-branch-version: 7.7.1-post
        ```
    - `cp-all-in-one-community` 
      - == -- based on -- Apache Kafka
      - _Example:_ | `latest`
        ```yaml
        
            steps:
        
              - name: Run Confluent Platform (Confluent Server)
                uses: confluentinc/cp-all-in-one@v0.1
                  type: cp-all-in-one-community
        ```

# | use Docker, service's ports

- Kafka broker: 9092
- Kafka broker JMX: 9101
- Confluent Schema Registry: 8081
- Kafka Connect: 8083
- Confluent Control Center: 9021
- ksqlDB: 8088
- Confluent REST Proxy: 8082
- Flink Job Manager: 9081
