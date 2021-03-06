# <a name="py-coding-style-and-formatting"></a>Python coding style and formatting

Summary:

- [General Rules](#py-style-general)
- [Naming Scheme](#py-style-naming)
- [Conditionals and Loops](#py-style-conditionals)
- [Classes and Enumerations](#py-style-classes)

## <a name="py-style-general"></a>General Rules
- Try to limit lines of code to a maximum of 70 characters.
    - Note that this does not mean you should try and use all 70 characters every time you have the chance. Typically with well formatted code, you normally shouldn't hit a line count of anything over 50 or 60 characters.
- The indentation style we use is 4 spaces per level.
- Math operators and equals should have spaces. `x = 3 + 4` not `x=3+4`.
- Don't use multi-line comments (`''' Comment text '''`), use single-line comments (`# Comment text`) instead.
  - Multiline comments are accepted for elaborate descriptions of functions.
  - Yes:

  ```python
  # This is a comment.

  def addFunction(x: int, y: int):
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
  ''' This is a comment. '''
  def addFunction(x: int, y: int)::
      # Adds x and y.
      return x + y
  ```
## <a name="py-style-naming"></a>Naming Scheme
- All class names should be in upper CamelCase. If the name contains an abbreviation uppercase it.
  - `class SomeClassName():`
- Function names should use regular camelCase. Once again, if there is an abbrevation make it uppercase.
  - `def addFunction(x: int, y: int):`
- All constants, such as tuples, should be fully uppercased. With constants that have more than one word in them, use an underscore to separate them. Same with Enum variables.
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
  class ThisClass():
      def __init__(this):
          pass
  ```

## <a name="py-style-conditionals"></a>Conditionals and Loops
- Don't collapse single line conditional or loop bodies onto the same line as its header. Put it on the next line.
  - Yes:

    ```python
    if condition:
        return False

    while x > 0:
        x -= 1
    ```
  - No:

    ```python
    if condition: return False

    while x > 0: x -= 1
    ```

## <a name="py-style-classes"></a>Classes and Enumerations
- As mentioned above, name classes in upper CamelCase and call the self variable `self`.
- Create each class variable as a property instead of using getters and setters.
  - In order for the properties to work, variables must be declared as private by prefixing them with `__`.
  - Yes:

  ```python
  class ExampleClass:

      def __init__(self):
          self.__variable_a = 1
          self.__variable_b = 2

      @property
      def variable_a(self):
          return self.__variable_a
      @variable_a.setter
      def variable_a(self, variable_a):
          self.__variable_a = variable_a

      @property
      def variable_b(self):
          return self.__variable_b
      @variable_b.setter
      def variable_b(self, variable_b):
          self.__variable_b = variable_b

  test = ExampleClass()
  test.variable_a += 5
  print(test.variable_a) # Prints 6
  ```
  - No:

  ```python
  class ExampleClass:

      def __init__(self):
          self.variable_a = 1
          self.variable_b = 2

      def getVariableA(self):
          return self.variable_a

      def setVariableA(self, value):
          self.variable_a = value

      def getVariableB(self):
          return self.variable_b

      def setVariableB(self, value):
          self.variable_b = value

  test = ExampleClass()
  test.setVariableA(test.getVariableA() + 5)
  print(test.getVariableA()) # Also prints 6
  ```
- Enumerations should also be named in upper CamelCase. Enum members should be named in all caps with underscores.
  - Example:

  ```python
  from enum import Enum
  class Colours(Enum):  # UK spelling
    RED   = 0xFF0000
    GREEN = 0x00FF00
    BLUE  = 0x0000FF
  ```
