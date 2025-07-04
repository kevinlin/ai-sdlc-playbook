# Django rules

To create a new Cursor Rule:

1. Enter the name as `django`
2. Copy & paste the file content from below

For more information, visit the [Project rules](https://docs.cursor.com/context/rules#project-rules).


```markdown
---
description: Django rules
globs: **/*.py, **/models.py, **/views.py
alwaysApply: false
---


# Django rules

- Use `python manage.py startapp` to create a new application in the project
- Save models in `models.py` and register them in `admin.py` to use the admin interface
- Use Django's ORM instead of raw SQL queries
- Use `select_related` and `prefetch_related` to avoid N+1 query problems:

```python
# Good mode
users = User.objects.select_related('profile')
posts = Post.objects.prefetch_related('tags')
```

- Use Django forms for validation:

```python
class UserForm(forms.ModelForm):
    class Meta:
        model = User
        fields = ['username', 'email']
```

- Create custom model managers for common queries:

```python
class ActiveUserManager(models.Manager):
    def get_queryset(self):
        return super().get_queryset().filter(is_active=True)
```

- Use Django's built-in authentication system
- Store settings in environment variables and access them via `settings.py`
```