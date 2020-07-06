# Tips for TRM

1. Instead of a typical README, **USE MARKDOWN**! This website is written in Markdown.
2. Instead of using `os.system("cls")`, use the following code (it's cross-platform):
```
print(chr(27)+'[2j') #First attempt at clearing the screen with ANSI escape codes.
print('\033c') #Second attempt at clearing the screen with ANSI escape codes.
print('\x1bc') #Third attempt at clearing the screen with ANSI escape codes.
```
3. Make EVERYTHING open source on a __PUBLIC__ GitHub repo!
4. Instead of the program crashing whenever you enter a letter in e.g. an `int(input())` line, use `try`, `except`, and `finally`. Here's how they work:
```
try:
    #code that might raise an error
    number = int(input("enter the number: ")
except ValueError: #if you use just `except: ' it will also catch ^C, ^D, and exit() statements, if you want to catch every error possible see the line after the next
    print("Invalid input!")
#except Exception:
    #print("Error") #This is not useful in any way, it doesnt show WHAT error. Fix this by using this block:
except Exception as ename:
    print("Error: %s" % ename) #this will output WHICH exception
finally:
    #put code here that you want to run WHETHER OR NOT an error occurs
```
You can put ALL your code into a try statement by just either putting it all into a function, and then at the end of the program `whateverYouNamedTheFunction()` inside of a try statement.

Or...make a file named `runthis.py` or something similar, and put this code in:
```
import runpy
try:
    runpy.run_path(path_name="filename.py")
except Exception as ename: 
    print("Error:%s" % ename)
finally:
    import sys
    sys.exit(0)
```
5. Instead of having  it so that if you have a functions file (e.g. in my calculator `func.py`) that holds functions (e.g. `area()`), if the user RUNS the functions file directly it just exiting without saying anything, here is a useful block of code:
```
if __name__ == "__main__":
    import sys
    print("Please dont run this file directly")
    sys.exit(1)#exits with exit code 1
```
If you're confused about what this does, here is an explanation.

When you run `import MODULE`, the magic variable `__name__` switches to the name of the module that ran `import MODULE`. So if I had a file called `palc.py` and it ran `import func` (to import func.py), `__name__`'s value would be switched to `palc` because that's the name of the module that ran `import func`. However, if you run a file DIRECTLY with e.g. `python3 func.py`, `__name__` is changed to the value of `__main__`. So if you run `if __name__ == "__main__", you're running a test to see if the user ran the file directly.

# Those are a bunch of tips I find useful; I hope you enjoyed them.
