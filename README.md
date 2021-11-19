# simple-camelk-service
Simple example of a CamelK service

#Deploy service that takes an array

To run/deploy, execute the following command from the `camelk` directory:
```
kamel run rest-service.xml -d camel-jackson
```

To send a test request execute the following `curl` command from anywhere:
```
curl -X POST -H "content-type: application/json" -d '[ "5", "After our recent aq?", "Architecture" ]' http://`oc get route rest-service -o jsonpath='{..spec.host}'`/questions
```
or the following `curl` command from the `camelk` directory:
```
curl -X POST -H "content-type: application/json" -d "@data/array-payload.json" http://`oc get route rest-service -o jsonpath='{..spec.host}'`/questions
```
#Deploy service that takes a complex object ("Cloud" service), from which the array used in the previous example is extracted

Deploy:
```
kamel run --name cloud-rest-service cloud-rest-service.xml -d camel-jackson
```

Test:
```
curl -X POST -H "content-type: application/json" -d "@data/cloud-payload.json" http://`oc get route cloud-rest-service -o jsonpath='{..spec.host}'`/cloudQuestions
```
