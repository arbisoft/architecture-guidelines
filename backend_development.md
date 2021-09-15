# Backend Development Guidelines

## 1. Choose a Proper Framework for Backend

It is important to choose a proper backend framework that meets the requirements of the project. There are different python web frameworks (or microframework) available like Django, Flask, Pyramid, web2py etc.

While in general different frameworks have different pros and cons ( this [link](https://hackernoon.com/top-10-python-web-frameworks-to-learn-in-2018-b2ebab969d1a) provides a good overview), Django along with Django Rest Framework seems to be a good choice in majority of the scenarios.

### Recommended Framework

[Django](https://www.djangoproject.com/) with [Django Rest Framework](https://www.django-rest-framework.org/)

#### Why DRF ?

- implicity, flexibility, quality, and test coverage of source code.
- Powerful serialization engine compatible with both ORM and non-ORM data sources.
- Pluggable and easy to customise emitters, parsers, validators and authenticators.
- Generic classes for CRUD operations.
- Clean, simple, views for Resources, using Django&#39;s class based views.
- Support for ModelResources with out-of-the-box default implementations and input validation (optional support for forms as input validation).
- HTTP response handling, content type negotiation using HTTP Accept headers.
- Pagination simplifies the process of returning paginated data in a way that can then be rendered to arbitrary media types.
- Publishing of metadata along with querysets.
- Permission classes and throttling management (API may feature a RESTrictive throttle for unauthenticated requests, a less RESTrictive throttle for authenticated requests, etc.).

## 2. Handling Credentials and Secrets

- Never store secrets (passwords, keys, etc.) in the sources in version control! It is very easy to forget they are there and the project source tends to end up in many places (developer machines, development test servers, etc) which unnecessarily increases the risk of an important secret being compromised
- They should be set and read from the environment
- [Django Environ](https://django-environ.readthedocs.io/en/latest/) supports upto 12 ways of safely managing the critical credentials

## 3. API Versioning (Optional)

- It is a good practice to have your API support versioning
- While the importance of versioning may not be too clear in purely web based apps (since we have control of client update in our hands), versioning is super critical, when the API is consumed by Mobile applications
- DRF provides different schemes to apply versioning, we can choose one that suits your scenario the best
- [https://www.django-rest-framework.org/api-guide/versioning/](https://www.django-rest-framework.org/api-guide/versioning/)

## 4. Separate Settings File for Each Environment

- There should be a separate settings file for each environment
- This reduces the chances of wrong configurations, that were updated for testing purposes, being pushed to the production environment
- Each developer should have a local\_settings file while, where the settings can be modified and this file should be added to [gitignore](https://git-scm.com/docs/gitignore)

## 5. Use Celery for Asynchronous Tasks

- We often have to perform tasks like sending emails, processing images, creating reports, updating internal usage stats, that are not required to be done in the request-response cycle.
- We can improve the user experience by doing these tasks in an asynchronous manner through task queues
- Celery&#39;s integration with django is pretty straight-forward [https://docs.celeryproject.org/en/latest/django/first-steps-with-django.html](https://docs.celeryproject.org/en/latest/django/first-steps-with-django.html)
- Celery provide following functionalities:
    - Execute tasks asynchronously.
    - Distributed execution of expensive processes.
    - Periodic/scheduled tasks.
    - Retrying tasks.

## 6. Error Logging and Alerts

- As applications become more complex, having good logs can be very useful, not only when debugging but also to provide insights for application issues and performance.
- Django provides a clear documentation, on how to add logging to your project
  [https://docs.djangoproject.com/en/2.2/topics/logging/](https://docs.djangoproject.com/en/2.2/topics/logging/)
- It&#39;s always a good practice to set up alerts in case of any error/exceptions. So that rapid actions can be taken to reduce the effects of the outages
- Django provides the option to inform the admins by email in case of exceptions (configuration is present in the link above)
- It is always a nice idea to integrate third party services that provide more detailed and comprehensive alerting mechanism like [sentry.io](https://sentry.io/welcome/) , elastic.io, etc

## 7. Performance Monitoring Tools

- As the user base grows, performance becomes more and more crucial
- It is a good practice to have tools that monitor the performance of the app and provide insights regarding the areas of improvements.
- These tools can provide helpful stats like
    - Number of requests
    - Average response time
    - Error rate
    - Revenue generated
    - Total Activity
    - Transactions time

- Some of these tools are
    - [New Relic](https://newrelic.com/)
    - [Datadog](https://www.datadoghq.com/)

## 8. Caching

- Caching plays a vital role in improving the performance of the app significantly
- Django supports different backends for caching, like
    - Memcache
    - Redis
    - Database
    - FileStorage
- Memcache and Redis are the most efficient ones among these options
- Caching can be implemented on different levels
    - [Per View Cache](https://docs.djangoproject.com/en/2.2/topics/cache/#the-per-view-cache)
    - [Template Fragment Caching](https://docs.djangoproject.com/en/2.2/topics/cache/#template-fragment-caching)
    - [Low Level Cache API](https://docs.djangoproject.com/en/2.2/topics/cache/#the-low-level-cache-api)

- Which form of caching has to be used, varies from scenario to scenario
- Low level cache API can be used to cache resource intensive queries
- Caching can backfire severely, if a proper cache busting mechanism is not in place. In addition to time based expiration, cache must be expired in case the underlying data updates.
- One example of cache busting is to listen for a Model&#39;s post\_save signals, and delete the cache associated with it

## 9. Test Coverage (Optional)

- Adding unit tests provide several advantages, some of them are
    - Make code updates easier and less prone to errors
    - Improves the quality of the code, helps in dividing the code into proper testable units
    - Provides a documentation of the system
- DRF provides some pre-builts methods to ease unit test writing process

[https://www.django-rest-framework.org/api-guide/testing/](https://www.django-rest-framework.org/api-guide/testing/)

- Ideally, we should have more than _ **90%** _ of our codebase covered by unit tests
- We can calculate the test coverage of our app by following this [documentation](https://docs.djangoproject.com/en/2.2/topics/testing/advanced/#integration-with-coverage-py)

## 10. Performance Improvements

Not the complete list\*

- Make sure to use [Django Debug Toolbar](https://django-debug-toolbar.readthedocs.io/en/latest/). It provides some very useful insights into the app performance. Most importantly it can provide a detailed analysis of the Database queries, that can help in highlighting the queries that are taking more time and bringing down the performance
- Use [select\_related](https://docs.djangoproject.com/en/2.1/ref/models/querysets/#select-related) and [prefetch\_related](https://docs.djangoproject.com/en/2.1/ref/models/querysets/#prefetch-related) to optimize the queries. They significantly reduce the number of queries that are made to the database and provide a performance boost.
- Implement caching (as mentioned above) to improve performance
- Use Raw SQL queries, when super complex and performance critical queries are to be performed
- If we&#39;re going to create more than one object at a time, use [bulk\_create](https://docs.djangoproject.com/en/2.1/ref/models/querysets/#bulk-create) instead of creating objects in a loop
- Similarly, perform the updates in [batches](https://docs.djangoproject.com/en/2.2/topics/db/queries/#updating-multiple-objects-at-once) too
- Use [values](https://docs.djangoproject.com/en/2.1/topics/db/aggregation/#values) and [values\_list](https://docs.djangoproject.com/en/2.1/ref/models/querysets/#values-list), when only certain fields are to be fetched