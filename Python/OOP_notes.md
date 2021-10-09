OOP is a method of structring a program so that related properties and behaviours can be budled into individual objetcs. 

Main purpose of OOP is python is to bunch data and related functions togethere in a class and make it reusable.

class is a outline for creating object. data belonging to class are called attributes, functions in a class are called methods. 

Class is like a blueprint. Using it we can create multiple instances.

init method in class is run automatically

Example code for creating class

```python
class Employee:
    
    def __init__(self,first,last,pay):
        
        self.first_name = first
        self.last_name = last
        self.pay = pay

#first_name, last_name, pay are attributes of class

##create a instance of above class

emp_1 = Employee("test","user",70000)

print(emp_1.first_name, emp_1.last_name, emp_1.pay)

```

below example of creating a meth0d inside a class

```python
class Employee:
    
    def __init__(self,first,last,pay):
        
        self.first_name = first
        self.last_name = last
        self.pay = pay
        
        
    def full_name(self):
        
        return '{} {}'.format(self.first_name, self.last_name)
        
        
emp_1 = Employee("ravi","teja",50000)

#for using a method you have to give () after it.for attributes it is not required
print(emp_1.full_name())
```

A python class variable is created when a class is being made. It is not made inside any method. it is shared by all object instances
a list or dictionary or tuple can also be given as a class variable

Class variables can be updated directly or even using a method

example code about class variables

```python

class Employee:
    
    employee_count = 0
    
    def __init__(self,first,last,pay):
        
        self.first_name = first
        self.last_name = last
        self.pay = pay
        Employee.employee_count =+1
        
        
    def full_name(self):
        
        return '{} {}'.format(self.first_name, self.last_name)
    
        
        
emp_1 = Employee("ravi","teja",50000)

print(emp_1.pay)
print(emp_1.full_name())
print(emp_1.employee_count)
print(Employee.employee_count)
```

you can also use a method 
```python
class Employee:
    
    employee_count = 0
    
    def __init__(self,first,last,pay):
        
        self.first_name = first
        self.last_name = last
        self.pay = pay
        
        
        
    def full_name(self):
        
        return '{} {}'.format(self.first_name, self.last_name)
    
    def raise_count(self):
        Employee.employee_count =+1
        
    
        
        
emp_1 = Employee("ravi","teja",50000)

print(emp_1.pay)
print(emp_1.full_name())


print(emp_1.employee_count)
print(Employee.employee_count)

emp_1.raise_count()

print(emp_1.employee_count)
print(Employee.employee_count)

```

Regular methods take self as 





ref : https://www.youtube.com/playlist?list=PL-osiE80TeTsqhIuOqKhwlXsIBIdSeYtc
