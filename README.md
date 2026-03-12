# 1. Model Definition Basics

Core constructs used when creating Django model classes.

* `models.Model` base class
* Declaring model attributes (fields)
* Field types

  * `CharField`
  * `TextField`
  * `IntegerField`
  * `FloatField`
  * `BooleanField`
  * `DateField`
  * `DateTimeField`
  * `EmailField`
  * `URLField`
  * `UUIDField`
  * `BinaryField`
* Field options

  * `null`
  * `blank`
  * `default`
  * `choices`
  * `unique`
  * `db_index`
  * `primary_key`

---

# 2. Relationship Fields

Defines relationships between database tables.

* `ForeignKey` (Many-to-One)
* `OneToOneField`
* `ManyToManyField`
* `related_name`
* `related_query_name`
* `on_delete` behaviors

  * `CASCADE`
  * `PROTECT`
  * `SET_NULL`
  * `SET_DEFAULT`
  * `DO_NOTHING`

---

# 3. Model Meta Options

Configuration using inner `Meta` class.

Common options:

* `db_table`
* `ordering`
* `verbose_name`
* `verbose_name_plural`
* `unique_together`
* `indexes`
* `constraints`
* `abstract`
* `proxy`
* `managed`

Example concept:

```python
class Meta:
    ordering = ['created_at']
    db_table = "blog_posts"
```

---

# 4. Model Methods

Custom logic inside models.

Common patterns:

* `__str__(self)`
* `save(self, *args, **kwargs)`
* `delete(self, *args, **kwargs)`
* custom instance methods
* static methods
* class methods

Example:

```python
class Product(models.Model):
    name = models.CharField(max_length=100)

    def __str__(self):
        return self.name
```

---

# 5. Model Managers

Custom database query interfaces.

Topics:

* `objects` default manager
* custom manager classes
* overriding `get_queryset()`
* adding query helper methods

Example concept:

```python
class ActiveManager(models.Manager):
    def get_queryset(self):
        return super().get_queryset().filter(active=True)
```

---

# 6. QuerySets Related to Models

How models interact with database queries.

Important methods:

* `Model.objects.create()`
* `Model.objects.get()`
* `Model.objects.filter()`
* `Model.objects.exclude()`
* `Model.objects.all()`
* `update()`
* `delete()`
* `exists()`
* `count()`
* `order_by()`

Advanced:

* `annotate()`
* `aggregate()`
* `select_related()`
* `prefetch_related()`

---

# 7. Model Inheritance

Different ways to extend models.

Types:

1. **Abstract Base Classes**

```python
class TimeStamped(models.Model):
    created = models.DateTimeField(auto_now_add=True)

    class Meta:
        abstract = True
```

2. **Multi-table inheritance**

3. **Proxy models**

---

# 8. Model Validation

Validation logic tied to model fields.

Topics:

* `clean()`
* `clean_fields()`
* `full_clean()`
* `validators`
* custom validators

---

# 9. Model Signals

Hooks triggered on model events.

Common signals:

* `pre_save`
* `post_save`
* `pre_delete`
* `post_delete`
* `m2m_changed`

---

# 10. Migrations (Model Schema Changes)

Schema evolution tied to model definitions.

Topics:

* `makemigrations`
* `migrate`
* migration files
* `RunPython`
* `RunSQL`
* schema vs data migrations

---

# 11. Database Constraints

Ensuring integrity at database level.

* `UniqueConstraint`
* `CheckConstraint`
* `Index`
* composite indexes

---

# 12. Advanced Model Fields

More specialized fields.

* `JSONField`
* `FileField`
* `ImageField`
* `DurationField`
* `SlugField`
* `AutoField`
* `BigAutoField`

---

# 13. Performance Topics Related to Models

Optimization techniques.

* `select_related`
* `prefetch_related`
* `only`
* `defer`
* `bulk_create`
* `bulk_update`
* `database indexing`
* **Top 30 model questions asked in Django interviews**
* **Advanced ORM topics most developers miss**.
