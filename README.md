# Pass the Buck

A super simple spring-boot proxy that just delegates upsteam. Useful for demos with chains of services (e.g. for tracing or service meshes).

## Build

``` mvn clean package```

## Use

All it requires is for you to set the UPSTREAM environment variable to some other service. E.g. see below for the world clock service.

```export UPSTREAM=http://worldclockapi.com/; java -jar target/pass-the-buck-1.0.0.jar```

```
curl -s http://localhost:8080/api/json/gmt/now | jq
{
  "$id": "1",
  "currentDateTime": "2019-11-14T07:10+00:00",
  "utcOffset": "00:00:00",
  "isDayLightSavingsTime": false,
  "dayOfTheWeek": "Thursday",
  "timeZoneName": "GMT Standard Time",
  "currentFileTime": 132181890053011970,
  "ordinalDate": "2019-318",
  "serviceResponse": null
}
```