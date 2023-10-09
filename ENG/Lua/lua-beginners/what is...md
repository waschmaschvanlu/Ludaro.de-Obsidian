#WhatIs #FiveM #LearnScripting #Scripting #en

# A Variable

Variables are a fundamental concept in programming used to store values. In Lua, the programming language of FiveM, there are various types of variables:

- **String:** A string is a sequence of characters, such as letters, numbers, or symbols. Strings are enclosed in double quotes `"` or single quotes `'`. For example:

  ```lua
  local name = "Hello, World!"
  ```

  Here, `name` is a variable of type string.

- **Integer:** An integer is a whole number without decimal places. For example:

  ```lua
  local age = 25
  ```

  The variable `age` is of type integer and contains the value 25.

- **Float:** A float is a number with decimal places. For example:

  ```lua
  local pi = 3.14159
  ```

  The variable `pi` is of type float and contains the value of Pi (π).

- **Boolean:** A boolean can be either `true` or `false`. They are often used for conditional statements and loops. For example:

  ```lua
  local isTrue = true
  ```

  The variable `isTrue` is of type boolean and contains the value `true`.

- **Table:** A table is a complex data structure that can store various values in an ordered list or as key-value pairs. Tables are a powerful concept in Lua and are used for many purposes. For example:

  ```lua
  local player = {name = "Max", score = 100}
  ```

  The variable `player` is of type table and contains information about a player, including their name and score.

Understanding these different variable types is crucial for effective programming. You can use these variables to store, manipulate, and utilize information in your FiveM scripts.

# A Function

A function in Lua is a named group of instructions designed to perform a specific task. Functions in Lua are often used to structure, reuse, and organize code. They allow you to call the same code from different parts of your script, improving code readability and maintainability.

Here is the basic structure of a function in Lua:

```lua
function functionName()
    -- Code of the function goes here
end
```

Think of a function like a page in a book. When you open the book and read that page, you execute all the instructions written on that page.

Here's a simple example of how we use a function to perform the calculation of 2 * 2:

```lua
function calculateResult()
    local result = 2 * 2
    print(result)
end

-- Now we call the function to display the result
calculateResult()
```

In this example, we've created a function named `calculateResult`. Inside this function, we perform the calculation of 2 * 2, store the result in the `result` variable, and then print it to the console.

We then call the `calculateResult()` function, which executes the code within it. The result displayed on the console is `4`.

**Passing Arguments to Functions:**

Functions can also take arguments that provide information to them. Here's an example:

```lua
function multiply(number1, number2)
    local result = number1 * number2
    print(result)
end

-- Now we call the function and pass two numbers to it
multiply(3, 5)
```

In this case, we've created a function named `multiply` that expects two arguments: `number1` and `number2`. Inside the function, these arguments are used to perform the multiplication and display the result.

When we call the function (`multiply(3, 5)`), we pass the values `3` and `5` as arguments. The function uses these values to calculate `15` and prints it to the console.

Using arguments allows functions to be flexible and reusable for different input values without having to change the code constantly.

# `while (true)` Loops

A `while (true)` loop is a basic looping structure in programming designed to repeatedly execute a specific code block.

**What is it?**

A `while (true)` loop is a type of loop that continues to iterate as long as the condition is `true`. It's often used to repeat tasks that need to run continuously without stopping.

Here's a simple example in Lua:

```lua
while true do
    -- This code block will be repeated endlessly
    print("This will keep running forever!")
end
```

In this example, the text "This will keep running forever!" will be printed to the console infinitely because the condition `true` never becomes false.

However, it's essential to note that `while (true)` loops should be used with caution as they can potentially block your application if the condition never becomes `false`. You should ensure there's a way to exit the loop when necessary. For instance, you can check for a specific condition within the loop and use `break` to exit it when that condition is met.

# A Thread

In the context of FiveM, a thread is created using the `Citizen.CreateThread` function.

**What is a Thread?**

A thread, also referred to as a coroutine outside of FiveM, is a function that executes code outside the normal flow of execution. Suppose you have code that needs to wait for 300 seconds. In that case, that code is executed within a "separate execution environment" when placed inside a thread. Let me explain what that means:

Imagine you have code that needs to wait for 300 seconds. When you place this code inside a thread, a new "instance" of this code is created. This instance has its own sense of time and executes the code without blocking the rest of your application. This means that the main part of your application can continue to function normally while the thread works in the background.

Threads in FiveM are often used for `while true` loops, such as checking if a player is near a coordinate. CAUTION! This should not be done too frequently, as it can cause server instability. You can control the frequency by using `Citizen.Wait(milliseconds)` within your script.

A thread doesn't have to run every millisecond. You can control this by including the following in your thread (either at the beginning or end of it):

```lua
ms = 5000 -- how many milliseconds to wait

Citizen.Wait(ms)
```

This tells the thread how long to wait during each iteration. For example, if we want to print "Heyo!" every 5 seconds, we would write it like this:

```lua
Citizen.CreateThread(function()
    while true do
        Citizen.Wait(5000) -- 5000 milliseconds are 5 seconds
        print("Heyo")
    end
end)
```

# An NUI (Natural User Interface)

Unfortunately, NUI does not stand for "Native UI" but for "Natural User Interface." NUIs are HTML websites integrated into FiveM, acting as menus with JavaScript in between. They are more complex and challenging for beginners to use.

# NativeUI

NativeUI is a native menu that already exists in GTA 5. This is what we'll primarily use since I'm a fan of it.

# Server/Client Event

A server/client event is a function that can only be used by the client or the