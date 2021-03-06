### [Microservices: a definition of this new architectural term](https://martinfowler.com/articles/microservices.html) (6/6/17)
* "Monolithic applications can be successful, but increasingly people are feeling frustrations with them - **especially as more applications are being deployed to the cloud**."
  * FWC - so is this "cloud" piece essential or not in terms of marginal benefit?
* "When looking to split a large application into parts, often management focuses on the technology layer, leading to UI teams, server-side logic teams, and database teams. When teams are separated along these lines, even simple changes can lead to a cross-team project taking time and budgetary approval. A smart team will optimise around this and plump for the lesser of two evils - just force the logic into whichever application they have access to. Logic everywhere in other words. This is an example of Conway's Law"
    > Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure.
    > -- Melvyn Conway, 1967
* "The microservice approach to division is different, splitting up into **services organized around business capability**. Such services take a broad-stack implementation of software for that business area, including user-interface, persistant storage, and any external collaborations."
* "As well as decentralizing decisions about conceptual models, microservices also decentralize data storage decisions. ... Microservices prefer letting each service manage its own database, either different instances of the same database technology, or entirely different database systems - an approach called Polyglot Persistence."

### [Awesome Microservices](https://github.com/mfornos/awesome-microservices) (4/19/17)
* A curated list of Microservice Architecture related principles and technologies.

### [Why RESTful communication between microservices can be perfectly fine](https://www.innoq.com/en/blog/why-restful-communication-between-microservices-can-be-perfectly-fine/) (4/13/17)
* "Do not communicate with other services during your own service’s request/response cycle. Ultimately, the goal is for your service to be available to the end-user even if other services that are part of the whole system are offline or unhealthy."
* "*If you have to call other services in order to be able to serve a response to a request from a **public** client*, this is really an architectural problem. Don’t blame the protocol! It doesn’t matter whether you are using HTTP or asynchronous message passing (with a request-reply pattern), *the overall response time for the public client will be bad*, and your service will not be as resilient as it could be, because it is coupled in time to the service it depends on."
* "**Actors** are pretty nice for handling the communication with other services outside of your own request/response cycle, but any other mechanism using some kind of buffer or queue should work as well."
* "If your service relies on data that is located in another service, **replicate that data** into your own service’s data store, using eventual consistency."

### [API microservices, the Unix philosophy, and the Richardson Maturity Model](https://medium.com/@chrstphrhrt/microservices-the-unix-philosophy-and-the-richardson-maturity-model-425abed44826#.5nkrvzhsu) (4/12/16)

### [Microservices Theory](http://martinfowler.com/articles/microservices.html) (3/4/16)
* "To start explaining the microservice style it's useful to compare it to the monolithic style: a monolithic application built as a single unit. Enterprise Applications are often built in three main parts: a client-side user interface (consisting of HTML pages and javascript running in a browser on the user's machine) a database (consisting of many tables inserted into a common, and usually relational, database management system), and a server-side application"
* "Design for Failure"

### [Bruno Rocha: Microservices with Python, RabbitMQ and Nameko](http://brunorocha.org/python/microservices-with-python-rabbitmq-and-nameko.html) (3/4/16)

### [RESTful API Best Practices and Common Pitfalls](https://medium.com/@schneidsDotNet/restful-api-best-practices-and-common-pitfalls-7a83ba3763b5#.sii1bf1qe) (2/25/16)
* "Respect the change management process. Avoid introducing break changes to existing endpoints that people are using."
* Also discusses asynchronous query response.

### [How RESTful is Your API?](http://www.bitnative.com/2012/08/26/how-restful-is-your-api/) (2/25/16)
* "Pragmatic REST"
* Really good, succinct article that specifically covers REST sans discovery and what that means for an API.
* Also discusses pragmatic versioning in place of discovery.

### [Rescuing REST From the API Winter](http://intercoolerjs.org/2016/01/18/rescuing-rest.html) (2/1/16)
* Basically, JSON-based REST isn't REST because it doesn't have native support for links.
* Schema/Structure needs to be discovered at runtime which is what HATEOS is for.
* HATEOAS - Hypermedia as the Engine of Application State.
* HATEOAS is a bigger part of REST than anyone ever really realized.

### [Testing REST clients](https://www.kenneth-truyers.net/2016/01/29/testing-rest-clients/) (2/1/16)

### [REST Introduction](http://www.infoq.com/articles/rest-introduction) 1/9/16
* The beauty of the link approach using URIs is that the links can point to resources that are provided by a different application, a different server, or even a different company on another continent
* the representations of a resource should be in standard formats -- if a client "knows" both the HTTP application protocol and a set of data formats, it can interact with any RESTful HTTP application in the world in a very meaningful way
* i.e. the idea that every resource should respond to the same methods. But REST doesn't say which methods these should be, or how many of them there should be
* HTTP "instantiates" the REST uniform interface with a particular one, consisting of the HTTP verbs

### [REST Misconceptions Video](http://www.infoq.com/presentations/rest-misconceptions) (1/9/16)
* UriApi 25:00
  * As a client I have to have some knowledge about the structure of the URIs so that I can build them myself
  * Code is full of getting a customer and then appending slash-something to get to the orders--to get to the orders
  * URIs that I document publicly now become the API.  I've documented a UriAPi
  * It's perfectly fine not to do Rest, I'm just a fan of calling tings what they are--of useful terminology--so don't call it rest if it's not rest--that is not restful.
  * one of the reasons this is not restful is because assumptions about server details become facts
  * there's a an assumption here that if i have a customer and i append "orders" that i get a list of orders for that customer
  * Client is now relying on exact URI structure which is something i would like to avoid if in any way possible
  * I hate version number URIs--everybody does them--i don't mind, i hate them nonetheless.  you change the uris for no good reason
* versioning 27:00
  * ok to version data, documentation, and formats--just not APIs
  * use version numbers in apis to version the resource itself
  * create new resources for new aspects and reserve space for links (so new resources can be discovered from existing ones)
* Postel's Law 36:20
  * "be liberal in what you accept and conservative in what you send"
  * high chance of what you send will be recognized by others
* Client and Server rules 38:00
  * more dynamic 41:00
  * change something on server side and new client doesn't have to be rolled out again b/c it learns about it at runtime
  * e.g. identifiers pointing to suburls
  * pass state transition information from server to client (43:40)
  * Rule #1: Don't have clients build URIs using string concatenation (45:15) ...instead: provide recipes
* Summary (53:30)
  * Link context over pretty uris
  * hypermedia over uri apis
  * hypermedia flows over static links
  * generalized formats over services

### [A Brief Introduction to REST](http://www.infoq.com/articles/rest-introduction) (12/21/15 and 1/8/16)

### [Dr. Dobb's - RESTful Web Services: A Tutorial](http://www.drdobbs.com/web-development/restful-web-services-a-tutorial/240169069) (1/8/16)
* Don't use query parameters (except for "parameters to an operation that needs the data items")

### [Is REST Best in a Microservices Architecture?](http://capgemini.github.io/architecture/is-rest-best-microservices/) (12/21/15)

### [Why REST is important even for your internal API](https://medium.com/@_reneweb_/why-rest-is-important-even-for-your-internal-api-ab08a40d01d3#.o8uyilkxr) (12/9/15)