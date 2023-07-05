
# holbertonschool-AirBnB_clone

This project is the first step towards building a full web application: the AirBnB clone. The first piece is to manipulate a powerful storage system. This storage engine will give us an abstraction between “My object” and “How they are stored and persisted”. This means: from your console code (the command interpreter itself) and from the front-end and RestAPI you will build later, you won’t have to pay attention (take care) of how your objects are stored.
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

The commands available for this command interpreter are:

Name	     Description
*create	     Creates a new instance of the class passed by argument.
show	     Prints the string representation of an instance.
*destroy     Deletes an instance that was already created.
all	     Prints string representation of all instances or of all instances of a specified class.
*update	     Updates an instance attribute if exists otherwise create it.
help	     Show all commands or display information about a specific command.
quit	     Exit the console.
EOF	     Exit the console.

Commands usage:

Command	 Usage
create	 create <class_name>
show	 show <class_name> <object_id> ; <class_name>.show(<object_id>)()
destroy	 destroy <class_name> <object_id ; <class_name>.destroy(<object_id>)()
all	 all <class_name> ; <class_name>.all()
update	 update <class_name> <object_id> <attribute name> “<attribute value>” ; <class name>.update(<object_id>, <attribute name>, <attribute value>) ; <class name>.update(<object_id>, <dictionary representation>)
help	 help ; help <command_name>
quit	 quit
EOF	 EOF ; (ctrl + d)

The following are a couple of examples of how to interact with the commmand console.
Ex1: Using create, count and all commands

solid@DESKTOP-6PPFSAT:~/H/AirBnB_clone$ ./console.py 
(hbnb) all
[]
(hbnb) create Place
492f60f3-ff1e-43c7-bb11-f8407b04dd59
(hbnb) create BaseModel
99f01e9a-99c0-42af-8c10-c35cadee1d8f
(hbnb) BaseModel.count()
1
(hbnb) all
["[Place] (492f60f3-ff1e-43c7-bb11-f8407b04dd59) {'id': '492f60f3-ff1e-43c7-bb11	-f8407b04dd59', 'created_at': datetime.datetime(2020, 7, 1, 11, 36, 24,		576486), 'updated_at': datetime.datetime(2020, 7, 1, 11, 36, 24, 576530)	}", "[BaseModel] (99f01e9a-99c0-42af-8c10-c35cadee1d8f) {'id': '99f01e9a	-99c0-42af-8c10-c35cadee1d8f', 'created_at': datetime.datetime(2020, 7,		1, 11, 36, 30, 773211), 'updated_at': datetime.datetime(2020, 7, 1, 11,		36, 30, 773236)}"]
(hbnb)

Example 2: Using basic update with an Id and show command
(hbnb) update BaseModel 99f01e9a-99c0-42af-8c10-c35cadee1d8f first_name "Betty"
(hbnb) show BaseModel 99f01e9a-99c0-42af-8c10-c35cadee1d8f
[BaseModel] (99f01e9a-99c0-42af-8c10-c35cadee1d8f) {'id': '99f01e9a-99c0-42af-8c10-c35cadee1d8f', 'creat	ed_at': datetime.datetime(2020, 7, 1, 11, 36, 30, 773211), 'updated_at': datetime.datetime(2020,	 7, 1, 11, 36, 30, 773236), 'first_name': 'Betty'}
(hbnb) Place.update("492f60f3-ff1e-43c7-bb11-f8407b04dd59", "first_name", "John")
(hbnb) show Place 492f60f3-ff1e-43c7-bb11-f8407b04dd59
[Place] (492f60f3-ff1e-43c7-bb11-f8407b04dd59) {'id': '492f60f3-ff1e-43c7-bb11-f8407b04dd59', 'created_a	t': datetime.datetime(2020, 7, 1, 11, 36, 24, 576486), 'updated_at': datetime.datetime(2020, 7,		1, 11, 36, 24, 576530), 'first_name': 'John'}

Example 3: Using update with a dictionary
(hbnb) BaseModel.update("99f01e9a-99c0-42af-8c10-c35cadee1d8f", {'first_name': "Petter", "age": 45})
(hbnb) show BaseModel 99f01e9a-99c0-42af-8c10-c35cadee1d8f
[BaseModel] (99f01e9a-99c0-42af-8c10-c35cadee1d8f) {'id': '99f01e9a-99c0-42af-8c10-c35cadee1d8f', 'creat	ed_at': datetime.datetime(2020, 7, 1, 11, 36, 30, 773211), 'updated_at': datetime.datetime(2020,	7, 1, 11, 36, 30, 773236), 'first_name': 'Petter', 'age': '45'}

