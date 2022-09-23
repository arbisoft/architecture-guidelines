# Frontend Development Guidelines

This document aims to serve as a baseline for the majority of medium to large-scale front-end / JavaScript-based projects in Arbisoft. We&#39;ve curated the best practices in one place in order to ensure adherence to the quality level, performance, and extensibility of the products we deliver. Beyond all of the guidelines mentioned here, the most important thing to make an effort for is developing a culture of creating quality among ourselves; the rest will follow automatically.

_Note: The recommendations of tools and libraries present in this document are suggested based on their long-standing past experiences and great track record in the industry for their performance and maintainability. Nonetheless, we know that the JS world is continuously evolving with innovation. Therefore if there is any library/tool superior to the suggested ones in this document, please discuss with the committee and we shall incorporate it in our guidelines._

**Definitions**

| **Marker** | **Title** | **Definition** |
| --- | --- | --- |
| ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
| Highest Priority | _Must be_ implemented or followed. This can not be compromised in any case. |
| ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)
| Medium Priority | _Should_ be implemented or followed. This can only be left over with a fairly justifiable rationale and a future plan to handle later on. |
| ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)
| Low Priority | _Good to Have_but can be ignored in the interest of available resources and project priorities. |

## 1. Choice of Framework for Frontend

Choose a framework for a frontend that can build applications that are able to be used by thousands and millions of users. Keep performance, extensibility, and community support in mind when choosing a framework. Our recommendations of the framework(s) are:

### 1.1 Recommended Framework ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

[React.JS](https://reactjs.org/) with [Redux](https://redux.js.org/)

### 1.2 Scaffolding ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

- [create-react-app (CRA)](https://github.com/facebook/create-react-app) / [react-boilerplate](https://github.com/react-boilerplate/react-boilerplate)
- [react-slingshot](https://github.com/coryhouse/react-slingshot)

### 1.3 UI Development ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

- UI Library for the project should be implemented using [storybooks](https://storybook.js.org/)
- Kick-start UI Libraries: [rebass.js](http://rebass.js/) | [blueprint](https://github.com/palantir/blueprint) | [ant-design](https://github.com/ant-design/ant-design) | [material v4](https://material-ui.com/blog/material-ui-v4-is-out/)

### 1.4 Optimizing Ubiquitous Feature Aspects ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png) ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

- Folder Structure Which [folder structure is ideal](https://marmelab.com/blog/2015/12/17/react-directory-structure.html) is a long-running discussion with varying subjective opinions. It is an important aspect to discuss nonetheless and the experience of working with large-scale applications tells that _Component Folder Pattern_[[1]](https://medium.com/styled-components/component-folder-pattern-ee42df37ec68)[[2]](https://nikitajajodia.com/2018/05/04/component-folder-pattern-in-react-js/) is the best one in terms of scaling for growing codebases.
- Forms A common pitfall is to implement custom form-handling because it is so easy to do it in React.JS - instead choose a mature &amp; stable library like [formik](https://github.com/jaredpalmer/formik) or [react-final-form](https://github.com/final-form/react-final-form) to handle all forms and their respective validations in a consistent, performant manner. ([DO NOT use](https://github.com/redux-form/redux-form/issues/4171)[redux-form](https://youtu.be/WoSzy-4mviQ) as its deprecated; [react-final-form](https://github.com/final-form/react-final-form) is the newest library from the same author) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Date and Time Handling Usually the de-facto choice for handling date and time (w.r.t. to time-zones) in JS apps is moment.js, but it has a [huge footprint](https://bundlephobia.com/result?p=moment-timezone@0.5.28) on the bundle size of the app and is now in maintenance mode. Therefore it is recommended to use new light-weight alternatives like [luxon](https://moment.github.io/luxon/#/) or [date-fns](https://date-fns.org/) instead. ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Utility Functions [Lodash](https://github.com/lodash/lodash) is a great utility for working with reference data-types (objects, arrays, strings, nested structures) in order to manipulate or search them. However, it also has a [large footprint](https://github.com/lodash/lodash) on the bundle size of the app. Therefore it is advised to use [individual lodash functions](https://www.npmjs.com/~jdalton) as packages. This way you can avoid installing the whole library. ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Immutability With the increasing demands of data-driven front-end apps, it is more than ever important to achieve immutability while working with JS reference types to achieve a predictable behavior of the language and avoid hard-to-debug errors. Therefore we recommend using [immer](https://github.com/immerjs/immer). ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

### 1.5 CSS Framework ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

- [CSS in JS](https://github.com/MicheleBertoli/css-in-js)frameworks like [styled-components](https://styled-components.com/)

### 1.6 Language for Development ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- [JavaScript](http://javascript.info/) (Duh!) - [ES2015+ aka ES6](https://github.com/lukehoban/es6features) ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)
- [TypeScript](https://github.com/basarat/typescript-book)

### 1.7 Lint Your Code ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- JavaScript / TypeScript / JSX / Node.js: [ESLint](https://eslint.org/) with thorough [Linting Rules](https://www.npmjs.com/package/jslint-configs) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- CSS / SCSS / CSS in JS: [StyleLint](https://stylelint.io/) ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)
- Setup Linting as pre-commit Hook: [Husky and Lint-Staged](https://codeburst.io/continuous-integration-lint-staged-husky-pre-commit-hook-test-setup-47f8172924fc)

## 2. Optimize React Apps for Speed &amp; Extensibility

### 2.1 React.JS ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- Use React.JS as **V** iew of MVC Although React.JS provides built-in APIs (State, Context) to work with the data, it is still better to treat React as a View technology, i.e., React part of the codebase should only be responsible for rendering dumb UI. This translates into React code mainly using Presentational (Functional) Components instead of Class Components and being free from any kind of data manipulation. Use _selectors_ (explained later) to perform data manipulation and inject it as props to the respective Presentational Component and dispatch actions to perform any async operations. The biggest benefit of _not using_ React&#39;s State for data manipulation is that one won&#39;t need to implement the lifecycle hook of React like shouldComponentUpdate to do performance because React will only be rendering dumb UI. [[3]](https://spin.atomicobject.com/2017/06/07/react-state-vs-redux-state/)[[4]](https://github.com/krasimir/react-in-patterns/blob/master/book/chapter-13/README.md) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Prefer React Hooks over React Class Components For using React&#39;s Lifecycle hooks, use the [new](https://youtu.be/dpw9EHDh2bM?t=706) API of [React Hooks](https://reactjs.org/docs/hooks-intro.html) instead of React&#39;s Class components. ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Create as many components as possible Even for the smallest UI elements ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Never use [Indexes as Keys](https://github.com/vasanthk/react-bits/blob/master/anti-patterns/06.using-indexes-as-key.md) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Define [PropTypes](https://www.andreasreiterer.at/react-proptypes/) of Components ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Lifting UI state in Global Store The pattern of using React.JS also advocates lifting the state of application&#39;s UI elements from React&#39;s state into a global state like Redux (with the only exception being Forms), such that there is a single state-tree for the whole application. This also strengthens the deterministic nature of the application. [Reference](https://gist.github.com/InamTaj/eef0d629736bb9b96d2597ab35f5c94a) ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

### 2.2 Redux ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- Decompose Reducers Split up Reducers into maintainable, extensible chunks.[[5]](https://redux.js.org/recipes/structuring-reducers/splitting-reducer-logic/) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Managing Side Effects [with redux-saga](https://redux-saga.js.org/docs/introduction/BeginnerTutorial.html) Sagas is hands-down the best option to manage async processes (aka side-effects) for large-scale applications because they can handle async-chaining of side-effects by completely avoiding callback hell (redux-thunks cannot do this without a messy, buggy code). Sagas encourage clean and reusable code with minimum boilerplate and encourage explicitly, yet consistent error-handling of async actions. Sagas provide a very clean way of accessing stores _(sorry thunks)_ and are capable of handling parallel processes, forking, spawning, canceling, and a lot more. [[6]](https://survivejs.com/blog/redux-saga-interview/)[[7]](https://medium.com/netscape/when-should-i-use-a-saga-708cb3c75e9a)[[8]](https://medium.com/@js_tut/the-great-escape-from-callback-hell-3006fa2c82e)[[9]](https://shift.infinite.red/using-redux-saga-to-simplify-your-growing-react-native-codebase-2b8036f650de)[[10]](https://neal.codes/blog/common-redux-saga-scenarios) ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)
- Use Selectors (with Memoization) Most of the components will need some dynamic data to be injected as props. For that purpose, an anti-pattern is to subscribe to the store (with connect() binding) and manipulate the props inside the component. This is completely wrong and any local manipulation of the data should be performed in selector functions. One should also use selectors for getting static data into the components, instead of hard-coding the static data in components. [[11]](https://www.nan-labs.com/blog/selector-pattern-in-react-redux-apps/)[[12]](https://read.reduxbook.com/markdown/part1/07-selectors.html)[[13]](https://blog.brainsandbeards.com/advanced-redux-patterns-selectors-cb9f88381d74) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Data Normalization Implementing DRY in Redux means that one should also manage data duplication in the global store. This means that for large-scale apps, one should treat the application&#39;s global storage as a database. [[14]](https://redux.js.org/recipes/structuring-reducers/normalizing-state-shape)[[15]](https://blog.brainsandbeards.com/advanced-redux-patterns-normalisation-6b9a5aa46e1f) ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)
- Reduce Boilerplate with Ducks Ever tried scaffolding your types/actions/reducers code? Use [Ducks Pattern](https://github.com/erikras/ducks-modular-redux) to minimize the repetitive codebase and ensure naming consistency in the redux entities. ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

## 3. Performance Optimization

### 3.1 JavaScript ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- Eliminate unused code with Tree-shaking Use ES6 Modules to import only required components in your code files, instead of importing default modules as a whole. When using destructured imports Webpack performs tree-shaking and eliminates dead-code in the production build. [[16]](https://developers.google.com/web/fundamentals/performance/optimizing-javascript/tree-shaking)[[17]](https://webpack.js.org/guides/tree-shaking/)
- Remove render-blocking JavaScript JavaScript blocks the normal parsing lifecycle of HTML documents, so when the parser reaches a \&lt;script\&gt; tag inside the \&lt;head\&gt;, it stops to fetch and run it. Adding async or defer is highly recommended if your scripts are placed at the \&lt;header\&gt; of the page. [[18]](https://developers.google.com/speed/docs/insights/BlockingJS)[[19]](https://varvy.com/pagespeed/defer-loading-javascript.html)
- Reduce JavaScript Payloads with Code Splitting A common anti-pattern is to load the whole bundle when a user lands on the website, even though the landing page doesn&#39;t need JS of all 30 other pages. In order to optimize the downloading times and bundle size of the application, use Code Splitting for your application.[[20]](https://developers.google.com/web/fundamentals/performance/optimizing-javascript/code-splitting)[[21]](https://reactjs.org/docs/code-splitting.html)

### 3.2 CSS ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- Divide CSS per-component basis Component level CSS helps keep the main CSS bundle lightweight which can also help at the time of code-splitting.
- Maximize Reusability Using frameworks like [styled-components](https://styled-components.com/), you can easily achieve maximum reusability of CSS by making as many generic styles as possible.
- Remove Render Blocking CSS CSS files need to be non-blocking to prevent the DOM from taking time to load.
- Eliminate unused CSS CSS files that need to be non-blocking to prevent the DOM from taking time to load. Make sure your bundler can handle this.

### 3.3 HTML ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- Use HTML5 Elements with Correct Semantics [[22]](https://htmlreference.io/)
- Have Error Pages Configured (for 400, 500 errors with Inline CSS)
- Minify HTML for Production
- Place CSS tags before JS To avoid render-blocking in CSS Having your CSS tags before any JavaScript enables better, a parallel download which speeds up browser rendering time. [[23]](https://varvy.com/pagespeed/style-script-order.html)

### 3.4 Bundler Performance Optimization ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

### Modern web applications often use bundling tools like Webpack or Parcel. Whatever bundler you use, there are certain aspects to take care of.

- Decrease Bundle Size By minification of code, optimizing images, breaking to vendor vs. app bundles, lazy loading on routing level, etc.
- Use long-term Caching Effective use of caching can save client&#39;s time on re-fetching bundles, hence ensuring low bandwidth usage and greater speed of application.
- Guide To Webpack&#39;s Optimization [[24]](https://developers.google.com/web/fundamentals/performance/webpack/)

### 3.5 Wholistic App Optimization Principles

- [Page Load Time](https://www.thinkwithgoogle.com/marketing-resources/data-measurement/mobile-page-speed-new-industry-benchmarks/) \&lt; 3 seconds | [Page Weight](https://www.thinkwithgoogle.com/marketing-resources/data-measurement/mobile-page-speed-new-industry-benchmarks/) \&lt; 500 KB (before gzipped) ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- TTFB (Time To First Byte) [[25]](https://scaleyourcode.com/blog/article/27) \&lt; 1.3 seconds | Time To Interact \&lt; 5 sec [[26]](https://tools.pingdom.com/) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Continuously Monitor app bundle for smaller size [[27]](https://evilmartians.com/chronicles/size-limit-make-the-web-lighter)[[28]](https://github.com/ai/size-limit) ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Continuously Profile app&#39;s rendering performance [[29]](https://www.smashingmagazine.com/2012/06/javascript-profiling-chrome-developer-tools/)[[30]](https://developers.google.com/web/tools/chrome-devtools/rendering-tools/js-execution)

## 4. Configuration, Deployment, Release, Monitor

### 4.1 Mange Secrets and App Constants as Configurations ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- Secrets and App-level Constants as Configurations Hardcoding of secrets, 3rd-party URLs is a major security risk, therefore moving such constants out of the codebase to environment variables is highly recommended. This also lets you separate out secrets for multiple environments.[[31]](https://serverless-stack.com/chapters/environments-in-create-react-app.html)[[32]](https://levelup.gitconnected.com/how-create-react-app-fakes-environment-variables-a08a9cb6e581)

### 4.2 Reproducibility with Containerization ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

- Containerize the Application _&quot;It works on my machine&quot;_ syndrome should be handled early on in the development lifecycle to ensure reproducibility of the application&#39;s artifacts. This can save a lot of time later on at the time of deployment to test and production environments. Docker is the de-facto standard for achieving containerization.[[33]](https://mherman.org/blog/dockerizing-a-react-app/)[[34]](https://medium.com/greedygame-engineering/so-you-want-to-dockerize-your-react-app-64fbbb74c217) For mono-repos, it is best to use [docker-compose](https://www.baeldung.com/docker-compose).

### 4.3 Dev/Prod Separation

- Separate out build-configuration per Environment ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)
- Separate out docker-builds per Environment ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)
- Track Configurations (not Secrets) under app/confs (or separate org/configs repo) ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

### 4.4 Setup CI ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

- Integrate CI to continuously Lint and Test codebase against each PR in your Platform such as CircleCI, GitHub Actions, GitLab CI, etc. [[35]](https://www.freecodecamp.org/news/how-to-set-up-continuous-integration-and-deployment-for-your-react-app-d09ae4525250/)

### 4.5 Monitor for Events in Production ![](RackMultipart20211203-4-u3tvt3_html_66cb5022a13fa937.png)

- Monitor for app&#39;s crashes or unexpected behaviors with services such as [Sentry](https://sentry.io/for/react/) or [Rollbar](https://rollbar.com/)

## 5. Test Your Code

## Testing is an essential part of the application lifecycle and it increases the maturity of the codebase with increasing feature-set. [Jest](https://github.com/facebook/jest) provides the most advanced test-runner with a lot of built-in assertions. [react-testing-library](https://github.com/testing-library/react-testing-library)

### 5.1 Snapshot Testing ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

This is a low-friction, low-return type of testing using which with a few lines of code, one can persist the Markup of UI components and track accidental changes.

### 5.2 Integration Testing ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

### You should write e2e integration tests that can fire up some actions, trigger sagas to execute processes of application, and then finally test the expected state of reducers. This is the most crucial part of testing and if the project uses redux-sagas, the testing experience is really intuitive and meaningful. This is another reason to ditch redux-thunks in favor of sagas.

### 5.3 Setup Unit Testing of Utilities ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

### With simple test assertions of Jest, one should write unit tests for all utility functions/helpers present in the codebase to ensure correct behavior.

### 5.4 Monitor and Achieve a Higher Code Coverage ![](RackMultipart20211203-4-u3tvt3_html_666ee53c5fb5cbf7.png)

- Using Jest&#39;s built-in code-coverage reports, keep an eye on the code coverage and always aim for higher code coverage. Use tools like [codecov](https://codecov.io/) to integrate into your development workflow and test code coverage against each PR in your CI pipeline.

### 5.5 Automation of Acceptance Testing ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

- Automate the Acceptance / Black Box Testing of the application with [Cypress.io](https://www.cypress.io/) and integrate it in your CI pipeline to ensure that the new feature-set does not break the application.

### 5.6 Setup Code Contribution Insights ![](RackMultipart20211203-4-u3tvt3_html_c0079acf9e4a7d0a.png)

- Using tools like [codeclimate](https://codeclimate.com/) you can set up engineering analytics and help Engineering Managers understand the productivity of developers and detect bottlenecks in the delivery of features by extracting information from code commits and pull requests.