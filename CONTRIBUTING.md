# <a name="py-coding-style-and-formatting"></a>Python coding style and formatting

Summary:

- [General](#py-style-general)
- [Naming](#py-style-naming)
- [Conditionals](#py-style-conditionals)
- [Classes](#py-style-classes)

## <a name="py-style-general"></a>General
- Try to limit lines of code to a maximum of 70 characters.
    - Note that this does not mean you should try and use all 70 characters every time you have the chance. Typically with well formatted code, you normally shouldn't hit a line count of anything over 50 or 60 characters.
- The indentation style we use is 4 spaces per level.
- The opening brace for namespaces, classes, functions, enums, structs, unions, conditionals, and loops go on the next line.
  - With array initializer lists and lambda expressions it is OK to keep the brace on the same line.
- Math operators and equals should have spaces. `x = 3 + 4` not `x=3+4`.
- Don't use multi-line comments (`''' Comment text '''`), use single-line comments (`# Comment text`) instead.
  - Multiline comments are accepted for elaborate descriptions of functions.
  - Yes:

  ```python
  # This is a comment.

  def AddFunction(x: int, y: int):
      '''
      Function
      Adds x and y together.
      x - integer
      y - integer
      '''
      return x + y
  ```
  - No:
  ```python
  '''This is a comment.'''
  def AddFunction(x: int, y: int)::
      # Adds x and y.
      return x + y
  ```
- Don't collapse single line conditional or loop bodies onto the same line as its header. Put it on the next line.
  - Yes:

    ```python
    if condition:
        return False

    while x > 0:
        var -= 1
    ```
  - No:

    ```python
    if condition: return False

    while x != 0: x -= 1
    ```

## <a name="py-style-naming"></a>Naming
- All class and function names should be in upper CamelCase. If the name contains an abbreviation uppercase it.
  - `class SomeClassName():`
  - `def AddFunction(x: int, y: int):`
- All constants, such as tuples, should be fully uppercased. With constants that have more than one word in them, use an underscore to separate them.
  - `PI = 3.14159`
  - `ACE_OF_SPADES = (1, 'spades')`
- All variables should be lowercase with underscores separating the individual words in the name.
  - `this_variable_name = 'abc123'`
- Class self variables should be named `self`.
  - Yes:

  ```python
  class ThisClass():
      def __init__(self):
          pass
  ```
  - No:

  ```python
  def ThisClass():
      def __init__(this):
          pass
  ```

## <a name="py-style-conditionals"></a>Conditionals
- In most cases, use `else if` instead of `elif`. (`elif` is still okay but is not as clear.)
  - Yes:

    ```python
    if condition:
        return True
    else if:
        return False
    ```
  - Acceptable in some cases:

    ```python
    if condition:
        return True
    elif:
        return False
    ```

## <a name="py-style-classes"></a>Classes
- As mentioned above, name classes in upper CamelCase and call the self variable `self`.
- Create getters and setters for each class variable.
  - Setters should use `value` as the parameter name.

    ```python
    class ExampleClass():
        def __init__(self):
            self.variable_a = 1
            self.variable_b = 2
        def GetVariableA():
            return self.variable_a
        def SetVariableA(value):
            self.variable_a = value
        def GetVariableB():
            return self.variable_b
        def SetVariableB(value):
            self.variable_b = value
    ```
