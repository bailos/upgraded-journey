# THE EXCEPTIONS IN PYTHON
### INTRODUCTION
In computer science, when executing a program, there is always a risk of error. That's why every good language has a basic error handling that concretely corresponds to the display of an error message informing us about the type of error detected and (often) to the stopping of the program execution after the error has been detected.
In this article, we will present : 
- the design of exceptions in python 
- the theory of exceptions in python 
- Use case examples and uses related to data analysis.
- Potential alternatives to exceptions with python 

### PRESENTATION OF THE CONCEPT
### What is an exception in Python?
First of all, we need to know what an error means in Python. In fact, there are two types of errors in Python:
Syntax errors ;
And exceptions.
Syntax errors are those that can be made when writing the program. It can be the call of a variable not managed by the program, an error in the writing of a statement (": " not put, a parenthesis not closed, etc..) or the call of a module not declared beforehand. These errors can be corrected immediately, because Python reports them before the program is executed. Indeed, it points a small arrow on the part where the error is located so that you can modify them according to the right syntax to write.
As for exceptions, they occur rather because of an invalid execution inside the program. This can be an error coming from the user, for example the input of an input that does not correspond to the expected value. It can also come from a programming error, i.e. a manipulation made by the developer which, during execution, leads to an operation not supported by the language. Exceptions are only raised when they occur, so they cannot be detected when the program is being developed. This is why it is important to handle them with the try...except instruction of Python, otherwise the solution may crash.
As for exceptions, they occur rather because of an invalid execution inside the program. This can be an error coming from the user, for example the input of an input that does not correspond to the expected value. It can also come from a programming error, i.e. a manipulation made by the developer which, during execution, leads to an operation not supported by the language. Exceptions are only raised when they occur, so they cannot be detected when the program is being developed. This is why it is important to handle them with the try...except instruction of Python, otherwise the solution may crash.
In this article we will focus on the exceptions. 
### PRESENTATION OF THE EXCEPTIONS
In Python, exceptions are thrown after the execution of an invalid statement Let's look at a small example of illustration.
The last three lines contain the context in which the exception occurred. This is the module concerned and the number of the line in which the error occurred. The last line specifies the type of exception generated. Here, it is the division by 0 that was triggered using the ZeroDivisionError exception class. 
![exception]( https://drive.google.com/file/d/133BTC0s-Pv8hrLPqhonhp3rYwS2RsJRI/view?usp=share_link )
There are several exception classes in Python representer in a hierarchical graph 
On this graph all exceptions inherit from the BaseException class. And as for the frequently encountered exceptions, they come from the Exception class. The ones illustrated in the flowchart are the so-called native exceptions.
![organization](https://drive.google.com/file/d/1jENPPnjPhv8IFwYHid5eMsoI-qc4H5f4/view?usp=share_link)
### GESTION DES EXCEPTIONS AVEC try...except Python
"try...except" is a statement that allows you to catch exceptions that your application may generate and execute other statements accordingly.
The program executes the instructions in the try clause. If it encounters an exception, it interrupts the execution. And if this exception matches the class or classes specified in the except clause, it switches to the instructions contained in the except clause. Note that you can specify several exceptions in the except clause. 
However, if the exception that occurs is not mentioned in the except clause, the language exception itself generates an error.
Illustration program 
```
def test():
    try :
    resultat = 10/0
    print(resultat)
except ZeroDivisionError:
     print("pas de devision par  0")
```

### ELSE CLAUSE IN A try...except Python
It is possible to add the else clause after the except clause to specify the instructions to execute if no exception is thrown.
You can put an else clause after an except clause to specify the instructions to execute if there is no exception raised.
Let's go back to our previous example for this illustration 
```json
def test():
    try :
    resultat = 10/2
except ZeroDivisionError:
    print("pas de division par o")    
    else :
        print(resultat)
```
### CLAUSE finally
 The statements contained in the finally clause will be triggered regardless of the result of the execution of the try...except statement in Python. This allows, among other things, to clean up the program before continuing it.
Example 
```
def test():
    try : 
    resultat = 10 * (1/0)
except ZeroDivisionError:
     print("pas division par 0")
   
 else :
        print(resultat)
finally :
    print("fin de l'operation")`.
```
### THE RAISE INSTRUCTION
It is possible to raise an exception ourselves. This operation is performed with the raise statement. It can also be used to propagate exceptions not handled by the except clause.

We can mention the exception to be raised without putting a parameter or specify in the parameter the message to be displayed when the exception is raised. And as for the propagation of exceptions, you just have to write it without anything else
```
 def test1(a):
     if a == 0 :
        raise ZeroDivisionError("il y a une division par 0")
         try:
            resultat1 = 10/a
            except Exception as exc:
                    raise RuntimeError from exc
def test2(a):
     try:
        resultat2 = 10/a
    except Exception :
         print("il y a une erreur")
             raise

        else :
            print(resultat2)
        finally :
            print("la gestion est terminée")`.
```
### THE KEYWORD PASS
The pass keyword is useful when you want to raise an exception without performing a specific instruction.
```
def exemple():
    try:
     resultat2 = 10/0
 except Exception as exc:
     pass
 print("fin de l'operation")
```
Example of exception use case in data analysis 
In the development of a program, whether for data analysis or for any other purpose, there is always a risk of generating errors. 
```
Y = [1,23,45,0,2,5,0]
def divide(x, y):
    try:
        result = x / y
    except ZeroDivisionError:
        print("division by zero!")
    else:
        print("result is", result)
    finally:
        print("executing finally clause")
```
### WRITE YOUR OWN EXCEPTIONS IN PYTHON
We can design our own exception to fit our application. All the classes we will create must inherit from the "Exception" class. This practice is the one recommended. 
We will create a class in pyton to better illustrate this 
```
class MyException(Exception):
        def __init__(self, x):
            self.x = x
        def __str__(self):
        return "Erreur dans {0} ".format(self.message)
        def test():
            resultat = 10/0
            raise MyException("test")
```


