---
description: Flask development best practices for building lightweight, modular web applications and APIs.
---

# Flask rules

To create a new Cursor Rule:

1. Create a file named `flask.md` in `.cursor/rules/`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: Flask rules
globs: **/*.py, app/**/*.py
alwaysApply: false
---


# Flask rules

- Use Blueprints to organize routes by function or resource
- Use Flask-SQLAlchemy to handle database models and ORM
- Use application factories to implement flexible application initialization
- Use Flask extensions to implement common features (Flask-Login, Flask-WTF, etc.)
- Store configuration in environment variables
- Use Flask-Migrate for database migrations
- Use error handlers to implement appropriate error handling
- Use Flask-RESTful or similar tools to build APIs
```