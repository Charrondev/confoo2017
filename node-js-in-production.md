## Node.js in Production

#### Previous node versioning 
* Even === Stable

  `0.10, 0.12, 4,6`

* Odd === Beta

  `0.11, 5`

#### New versioning - LTS releases

<p><img src="https://github.com/nodejs/LTS/raw/master/schedule.png" alt="LTS Schedule"/></p>

### Docker to test deployment

* Don't need to install anything on host

### Lock down dependancy version

You can use shrinkwrap to lock down dependancies

`$ npm shrinkwrap`

or use yarnpkg instead

`$ yarn`

alternatively you can hardcode your package versions for all dependancies.

### Security

[https://nodesecurity.io](https://nodesecurity.io)

[Snyk](http://snyk.io)

Checks your dependancies for secutity vulnerabilities.

### Single threaded

Only one event loop

If you have very CPU intensive task?

* Maybe don't use Node. Try something like GoLang which is oriented better for that task

* Use 100's of 1000's of docker containers running node with NGINX running in front as a load balancer. With other NGINX instances running as proxy on each process.

### OpenTracing - [Zipkin](https://github.com/openzipkin/zipkin-js)

Breaking up the monolithic node app into many docker containers makes debugging more difficult.

[Zipkin](https://github.com/openzipkin/zipkin-js) adds information onto each request before it hits the microservicing and allows you to monitor the various requests properly.