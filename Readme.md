This is Nginx compatible oauth proxy that acts as oauth client and performs authentication flows

##Usage
-----
```
Usage: <main class> [-h] [-cb=<redirectUri>] [-ci=<clientId>]
                    [-cs=<clientSecret>] [-i=<issuer>] [-p=<port>]
      -cb, --callback=<redirectUri>
                          Callback URI
                            Default: http://127.0.0.1:8089/p/callback
      -ci, --clientId=<clientId>
                          Client Id of OAuth client
                            Default: oic-proxy-app
      -cs, --clientSecret=<clientSecret>
                          Client Secret of OAuth client
                            Default: mysecretoicclient
  -h, --help              display this help message
  -i, --issuer=<issuer>   Token issuer url, OpenID issuer url
                            Default: http://127.0.0.1:5556/dex
  -p, --port=<port>       Http port to run this proxy on
                            Default: 8090
```

##Endpoints
---------
It exposes the following endpoints:

`/p/login` - This is entry point for authentication flows.

`/p/callback` - Endpoint to handle OAuth resource server callbacks. This exchanges auth code with access token. Also routes back to original request.

`/p/auth` - Used by nginx to check if given request is authenticated.

##Start server
------------
`java -jar target/oauthproxy-1.0-SNAPSHOT.jar`

##Help
------------
`java -jar target/oauthproxy-1.0-SNAPSHOT.jar --help`

##Docker Image
`docker run phx.ocir.io/oicpaas1/sumagant/oauthproxy:latest`

##Kubernetes deployment
`kubectl apply -f oauthproxy/src/main/resources/dex-k8s.yaml`
