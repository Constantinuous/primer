# RichCode
## Chapter 2: DRY - Don't Repeat Yourself
Don't Duplicate anything! The problem with redundant things is always that you forget about the duplication. And then you change one thing and don't know about the other or forget to update it. 

* Don't write redundant comments in your code! Express the domain language with code. If you cannot express it with code, that usually means you need to refactor.
* Don't write redundant documentation for code! __Automatically__ generate documentation from the code!

You can get away with slight duplication when you can somehow ensure the duplication is never stale and out-of-date. 

* Write specifications in a format that can automatically be verified (Given, when, then). This ensures the specifications never grow stale.
* Database structures need to be accessed from your code. Creating a class for each table in the database would be duplication. You can however generate the classes automatically and continuously from the table create scripts or - even better - directly from a running database instance. If you change a field in a table in the database the corresponding class file would then be updated and produce design-time errors.
