# holbertonschool-AirBnB_clone
The first piece is to manipulate a powerful storage system. This storage engine will give us an abstraction between “My object” and “How they are stored and persisted”. This means: from your console code (the command interpreter itself) and from the front-end and RestAPI you will build later, you won’t have to pay attention (take care) of how your objects are stored.
This abstraction will also allow you to change the type of storage easily without updating all of your codebase.
The console will be a tool to validate this storage engine. The console will consist of first creating our data model. The console will allow us to manage, meaning create, update, destroy, etc., objects via a command interpreter. This system will help store and persist objects to a JSON file.

Tasks:
0. Write a README.md with a description of the project and a description of the command interpreter consisting of how to start it, how to use it and an example.

1. Write beautiful code that passes the pycodestyle checks.

2. All your files, classes, functions must be tested with unit tests.

3. Write a class BaseModel that defines all common attributes/methods for other classes.

4. Previously we created a method to generate a dictionary representation of an instance (method to_dict()).

Now it’s time to re-create an instance with the dictionary representation provided and Update models/base_model.py.


5. We need to convert the dictionary representation to a JSON string. JSON is a standard representation of a data structure.

We will also write a class FileStorage that serializes instances to a JSON file and deserializes JSON file to instances:
models/engine/file_storage.py.

Update models/__init__.py: to create a unique FileStorage instance for your application

Update models/base_model.py: to link your BaseModel to FileStorage by using the variable storage


6. Write a program called console.py that contains the entry point of the command interpreter:
You must use the module cmd

Your class definition must be: class HBNBCommand(cmd.Cmd):

Your command interpreter should implement:
quit and EOF to exit the program

help (this action is provided by default by cmd but you should keep it updated and documented as you work through tasks)

a custom prompt: (hbnb)

an empty line + ENTER shouldn’t execute anything

Your code should not be executed when imported


7. Update your command interpreter (console.py) to have these commands:
create: Creates a new instance of BaseModel, saves it (to the JSON file) and prints the id.Ex: $ create BaseModel

show: Prints the string representation of an instance based on the class name and id.
Ex: $ show BaseModel 1234-1234-1234.

destroy: Deletes an instance based on the class name and id (save the change into the JSON file).
Ex: $ destroy BaseModel 1234-1234-1234.

all: Prints all string representation of all instances based or not on the class name.
Ex: $ all BaseModel or $ all.

update: Updates an instance based on the class name and id by adding or updating attribute (save the change into the JSON file).
Ex: $ update BaseModel 1234-1234-1234 email "aibnb@mail.com".

Some additional rules:
You can assume arguments are always in the right order
Each arguments are separated by a space
A string argument with a space must be between double quote
The error management starts from the first argument to the last one


8. Write a class User that inherits from BaseModel:
models/user.py

Public class attributes:
email: string - empty string
password: string - empty string
first_name: string - empty string
last_name: string - empty string

Update FileStorage to manage correctly serialization and deserialization of User.

Update your command interpreter (console.py) to allow show, create, destroy, update and all used with User.
