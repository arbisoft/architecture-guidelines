# Code Quality

### Linting

A code linter is a program that performs static analysis of your source code for potential errors. The kinds of errors a linter can detect include:

- syntax errors
- structural problems like the use of undefined variables
- best practices or code style guideline violations

A linter could help you develop faster, keep your code organized, and do less syntax mistakes that potentially could cause errors and break your code.

Ideally, linting should be a part of our workflow. Before committing the code, linters should inspect the code and raise errors in case of any discrepancies.

#### Python Linters

Python has several good options for code linters. Following two are mostly used for linting:

##### [Flake8](https://pypi.org/project/flake8/)

It&#39;s fast and has a low rate of false positives. Flake8 is actually a combination of several other tools, mainly the Pyflakes static analysis tool and the Pycodestyle (former pep8) code style checker.

Checkout this documentation to integrate Flake8 with git hooks [https://flake8.pycqa.org/en/latest/user/using-hooks.html](https://flake8.pycqa.org/en/latest/user/using-hooks.html)

##### [Pylint](https://pypi.org/project/pylint/)

Pylint is another good choice. It takes a little more effort to set up than Flake8 and also triggers more false positives. On the other hand, it provides a more comprehensive analysis.

To integrate pylint with github flow, please refer to this link

[https://git-pylint-commit-hook.readthedocs.io/en/latest/usage.html](https://git-pylint-commit-hook.readthedocs.io/en/latest/usage.html)

#### JS Linters

##### [ESlint](https://eslint.org/)

ESlint helps a team to follow unified rules increasing readability and purity of code. ESlint is highly flexible and allows customizing rules for errors, best practices, variable declarations, ES6 etc.

ESlint works with a set of rules that you define. The most commonly used linting rules are [Airbnb](https://github.com/airbnb/javascript), which bills itself as &quot;a mostly reasonable approach to JavaScript.&quot; And their linting rules are popular because they are simple, sensible, and beautifully consistent.

A good guide to integrate ESlint as part of your workflow is:

[https://medium.com/quick-code/how-to-integrate-eslint-prettier-in-react-6efbd206d5c4](https://medium.com/quick-code/how-to-integrate-eslint-prettier-in-react-6efbd206d5c4)