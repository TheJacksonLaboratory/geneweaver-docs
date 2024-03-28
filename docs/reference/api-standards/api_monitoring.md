# API Monitoring
> These guiding principles will help stability, uptime, and awareness for your applications.

Actuator endpoints let you monitor and interact with your application. For language
specific tutorials (please see here)[/Development/Tutorials/Monitoring/endpoints]. 

## Monitoring
Our endpoints for monitoring and info will exist at 

```
/api/monitor/<resource>/<type>
```

## Health Endpoint

<span style="color:red">**Required**</span>


This endpoint provides health information, mainly the status of the application. It will be the
primary target for monitoring services.

Location:
```
http://127.0.0.1/api/monitor/server/health
```
Example Response:
````
{"name":"Fancy Application","status":"UP","details":"Everything seems okay."}
````

| Status Text      | Http Status Code                     |
| ----------- | ------------------------------------ |
| `UP`        |  200 |
| `UNKNOWN`   |  200 |
| `DOWN`      |  503 |
