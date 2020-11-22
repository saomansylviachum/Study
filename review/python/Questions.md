# Questions

1. What is deractor?

   **Decorators** in Python are essentially functions that add functionality to an existing function in Python without changing the structure of the function itself. They are represented by the `@decorator_name` in Python and are called in bottom-up fashion. For example:

   ```
   # decorator function to convert to lowercase
   def lowercase_decorator(function):
       def wrapper():
           func = function()
           string_lowercase = func.lower()
           return string_lowercase
       return wrapper
   ```