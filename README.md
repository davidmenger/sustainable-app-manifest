# Sustainable App Manifest

Developing of scalable, easy to maintain applications whitepaper.

-------------------------

### function tldr () {

  1. [**Snappy documentation**](#snappy-documentation)

    + "Purpose over solution" for each module
    + Public API documetation

  2. [**Ready For Scale**](#ready-for-scale)

    + Runs and scales in containers without vendor locking
    + Is [12-Factor](https://12factor.net) compliant

  3. [**Good Enough Test Coverage**](#good-enough-test-coverage)

    + Everyone know, what's expected behavior
    + No uninformed update breaks the application

  4. [**Community Approved Coding Standard**](#community-approved-coding-standard)

    + Uses linter profile like [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
    + Has feature based project structure

  5. [**Well Known Technology**](#well-known-technology)

    + Only documented and maintained dependencies
    + Best practice over unusual solution

  6. [**Explicit Dependency Injection**](#explicit-dependency-ijection)

    + No hidden connections or dependencies
    + Easy to replace modules

### };

-------------------------

## Snappy documentation

  Documentation should be small as possible, but not smaller. Use Markdown,
  because it has best portability (IDE's, Github).

  1. **Root README.md with domain**

    - Sumarizes a purpose of application and its parts
    - Defines [Ubiquitous Language](http://martinfowler.com/bliki/UbiquitousLanguage.html)
      dictionary
    - Contains "how-to-run" tutorial with defined requirements
    - Documents build process

  2. **Module documentation**

    - Documents only Business Logic and Purpose, not interfaces
    - Each module should have own `README.md`

  3. **Public API documentation**

    - All REST/HTTP/Socket comunication API should be documented
    - [API blueprint](https://apiblueprint.org) standard for documentation


## Ready For Scale

  Noone knows, when an application reaches its limits, but it must be ready
  for it. Motivation is obvious:

  - Ability to run in Cloud platforms
  - Scale by additional processes
  - Minimal divergence between development and production
  - Continous integration and deployment


  Following list is inspired by [The twelve factor app](https://12factor.net),
  which describes the idea of modern scalable application.

  1. **Environment based configuration**

    Application is configured from the outside by enviromental variables. So
    it's easy and fast to change database connection or any other backing service.

  2. **App runs as a stateless process**

    Important requirement for scaling is ability to run as one or
    more stateless processes.

  3. **Treat logs as event streams**

    It's important forward logs outside an application and concentrate them
    in storage, which allows introspecting an app’s behavior over time.


## Good Enough Test Coverage

  Automatic test coverage is most important for scaling of development. It brings safer updates,
  easier maintenance and provides knowledge for developers, who are unfamiliar
  with an application.

  1. **Integration tests for business processes**

    Each business process should have automatic API-to-DB test, which
    ensures their functionality.

  2. **Reusable code covered by unit tests**

    Code, which is used more then once (utilities, components) should be
    covered by unit tests

  3. **Front-end Components tested in browsers**

    Front-end code should be tested in own environment: in browser.


  > In JavaScript environment the Mocha tester for serverside testing and
  > Karma based testers for browserside code seems to be good enough solution.

## Community Approved Coding Standard

  Everyone loves, when code looks good. But is's good to ensure it.

  1. **Best style is common style**

    Like [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript),
    which refers to Javascript, Node.js, React and more.

  2. **Code quality is controlled by automatic linter as a part of CI**

    Code, which stinks should not be merged to upstream.

  3. **Feature based file structure**

    It's most common solution which can reduce dependencies among features.


  > The more the strict linter is, the better the code will be.
  > [ESLint](http://eslint.org) with
  > [AirBnB preset](https://www.npmjs.com/package/eslint-config-airbnb)
  > seems to be the best solution for JavaScript.

## Well Known Technology

  Lowering learning curve of a project makes it easier to maintain. Just prefer
  complete documented solution.

  1. **Use only dependencies with documentation**

    Avoid using of poorly documented libraries and external dependencies.

  2. **Avoid using of unmaintained modules**

    Modules with lastest version older then one year should be avoided.

  3. **Most favourite module == best practice**

    The more the module is known, the more proven solution it is.


  > Keep mind, that developing own solution requires also documentation,
  > teststing and maintanance. Is it still better, then just linking
  > 3rd party library?

## Explicit Dependency Injection

  1. **Don't link different feature files directly. Use DI.**

    Avoiding deeply interconnected features, your code will be clearer and testable.

  2. **Each feature should have dependencies defined on just one place.**

    Explicitly defined relations between features will simplify subsequent development.


  > The most simple solution is injecting dependencies only in root `index.js` file
  > of each feature.


