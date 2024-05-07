# A tool to manage dependencies on python projects (it is cargo for python)

- To select the python versión for the project
  - ``poetry env use 3.10/version``
- To add a dependency
  - ``poetry add dependency/pytest/flask/django/sqlalchemy``
- To run tests
  - ``poetry run pytest``
- To run tests but with printing to console enabled cause poetry eats up de stdin
  - ``poetry run pytest -s``
