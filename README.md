# simple-camelk-service
Simple example of a CamelK service

To run/deploy, execute the following command from the `camelk` directory:
```
kamel run rest-service.xml -d camel-jackson
```

To send a test request:
```
curl -X POST -H "content-type: application/json" -d '[ "5", "After our recent aq?", "Architecture" ]' http://`oc get route rest-service -o jsonpath='{..spec.host}'`/questions
```
