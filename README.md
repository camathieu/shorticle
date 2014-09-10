Vert.x url shortner
===================

Live running at http://x26.eu

Backed up by redis if provided in the json.config else default to sharedMap ( no persistence ).

Configuration
-------------

Edit or provide config.json file.

```
{
    "host" : "localhost",                   // interface to listen to
    "port" : 2688,                          // port to listen to
    "domain" : "http://localhost:2688",     // base domain
    "startLen" : 2,                         // base length for string generation
    "tries" : 900,                          // minimum successive fail tries before increasing length
    "redis" : "localhost"                   // redis server address ( optional )
    "hashkey" : "shorticle.url_store",      // redis / vert.x hash key ( optional )
}
```

Run
---

Building a fatJar including all dependencies.

```
mvn clean package
mvn vertx:fatJar
java -jar target/shorticle-1.0-fat.jar -conf config.json
```

Running right from maven cli

```
mvn clean package
mvn vertx:runMod
```

Api
===

Status 200 is OK

```
curl -X POST -d 'url=http://foo.bar' http://127.0.0.1:2688
{"status":200,"value":"http://localhost:2688/ix"}
```