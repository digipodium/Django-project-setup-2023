# Django Models Tutorial - part 1

Welcome to this tutorial on Django models! In this tutorial, we will cover the basics of Django models and show you how to work with models, perform queries, and apply filters to retrieve data from the database.
Before we get started, let's first understand what Django models are and why they are essential in web development.

## Introduction to Django Models

Django is a powerful Python web framework that provides an Object-Relational Mapping (ORM) tool called models. Models allow you to define the structure and behavior of your application's data.

In simple terms, a model represents a table in a database. Each attribute in a model represents a field in the corresponding table. Models provide an easy way to interact with the database without writing any SQL code. Django takes care of creating the tables, querying the data, and performing related operations.

## Defining a Model

Now let's define a model within our app. Open the `models.py` file inside the `myapp` or `<your_app>` directory, and write the following code:

```python
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    roll_number = models.IntegerField()
    grade = models.CharField(max_length=2)
    marks = models.IntegerField()

    def __str__(self):
        return self.name
```

In the above code, we have defined a `Student` model with four fields: `name`, `roll_number`, `grade`, and `marks`. Each field is an instance of a Django model field, which represents a column in the database table.

The `__str__` method is defined to display the name of the student when printed.

## Running Migrations

Django uses migrations to create database tables based on your models. To create the necessary tables, run the following command in your command prompt or terminal from the project directory:

```bash
python manage.py makemigrations
python manage.py migrate
```

These commands will generate the required SQL and apply it to the database.

## Performing Queries and Filters

Now that the setup is complete, let's see how to interact with the database using Django models.

### Creating Objects

To create a new student object, you can use the following code in your Python code or Django shell:

```python
from myapp.models import Student

student = Student(name="John Doe", roll_number=1, grade="9A", marks=95)
student.save()
```

This code creates a new student object and saves it to the database.

### Retrieving Objects

To retrieve objects from the database, you can use various queries and filters provided by Django.

#### Get all students:

```python
students = Student.objects.all()
```

This query retrieves all instances of the `Student` model from the database.

#### Filter objects:

```python
students = Student.objects.filter(grade="9A")
```

This query retrieves all students whose grade is "9A".

#### Get a single student:

```python
student = Student.objects.get(name="John Doe")
```

This query retrieves a specific student with the name "John Doe".

### Updating Objects

To update an existing object, you can retrieve it from the database, modify its attributes, and then save it again.

```python
student = Student.objects.get(name="John Doe")
student.marks = 98
student.save()
```

This code updates the `marks` attribute of the student with the name "John Doe".

### Deleting Objects

To delete an object, you can use the `delete()` method.

```python
student = Student.objects.get(name="John Doe")
student.delete()
```

This code deletes the student with the name "John Doe" from the database.

## Conclusion

Congratulations! You have successfully learned the basics of Django models, including creating models, performing queries, and applying filters. Models are an essential component of Django and provide a convenient way to interact with databases.

Remember to consult the Django documentation or other resources for more advanced features and concepts related to Django models.

If you have any questions or need further clarification, feel free to reach out to [Digipodium](https://www.digipodium.com) for assistance.

Happy coding!
