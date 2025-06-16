Possible causes:
- The Kafka's server is not allow outbound traffic on port 5671 (AMQP over SSL)
- The Event Hub networking setting is not allow access from the Kafka's server
- The server might not be able to resolve psa-eventhub-uat-03.servicebus.windows.net (DNS timeouts or misconfiguration)
- Connection string credentials may be invalid or revoked (token expired, )