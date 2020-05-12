`# Reverse Engineering Challenges

## Time to Eat

In this challenge, we are given a python script. Immediately, we noticed that it's heavily obfuscated with poorly named variables and functions. Furthermore, we see the condition we need to meet with our input in order to get the flag starting on line 47:

```python
if eateat == "E10a23t9090t9ae0140":
    flag = "eaten_" + eat
    EaT("absolutely EATEN!!! CTFlearn{",flag,"}")
```

Trying to input this string does not give us the flag, as the previous functions change our input considerably (sort of like a hashing function). We can begin reversing this by changing the function names to something less confusing, the best way to do this is to use find and replace in the text file editor of your choice. 

| Original | New |
|:-----------|:--------------|
| `Eating` | `Function1` |
| `EAt` | `Function2` |
| `aten` | `Function3` |
| `eaT` | `Function4` |
| `aTE` | `Function5` |
| `Ate` | `Function6` |
| `Eat` | `Function7` |

```python
# I wrote and debugged this code with all the convoluted "EAT" variable names.
# Was it confusing? Yes. Was debugging hard? Yes.
# Did I spend more time than I should have on this problem? Yes

EAT = int
eAT = len
EaT = print
ATE = str
EATEATEATEATEATEAT = ATE.isdigit

def Function1(eat):
    return ATE(EAT(eat)*EATEATEAT)

def Function2(eat, eats):
    print(eat, eats)
    eat1 = 0
    eat2 = 0
    eateat = 0
    eAt = ""
    while eat1 < eAT(eat) and eat2 < eAT(eats):
        if eateat%EATEATEAT == EATEATEATEATEAT//EATEATEATEAT:
            eAt += eats[eat2]
            eat2 += 1
        else:
            eAt += eat[eat1]
            eat1 += 1
        eateat += 1
    return eAt

def Function3(eat):
    return eat[::EATEATEAT-EATEATEATEAT]

def Function4(eat):
    return Function1(eat[:EATEATEAT]) + Function3(eat)

def Function5(eat):
    return eat#*eAT(eat)

def Function6(eat):
    return "Eat" + ATE(eAT(eat)) + eat[:EATEATEAT]

def Function7(eat):
    if eAT(eat) == 9:
        if EATEATEATEATEATEAT(eat[:EATEATEAT]) and\
            EATEATEATEATEATEAT(eat[eAT(eat)-EATEATEAT+1:]):
                eateat = Function2(Function4(eat), Function6(Function5(Function3(eat))))
                if eateat == "E10a23t9090t9ae0140":
                    flag = "eaten_" + eat
                    EaT("absolutely EATEN!!! CTFlearn{",flag,"}")
                else:
                    EaT("thats not the answer. you formatted it fine tho, here's what you got\n>>", eateat)
        else:
            EaT("thats not the answer. bad format :(\
            \n(hint: 123abc456 is an example of good format)")
    else:
        EaT("thats not the answer. bad length :(")

EaT("what's the answer")
eat = input()
EATEATEAT = eAT(eat)//3
EATEATEATEAT = EATEATEAT+1
EATEATEATEATEAT = EATEATEAT-1
Function7(eat)
```

Now, we can rename and remove the first five variables declared in the beginning of the script. Be careful with `EAT` and `ATE` since they are included in other larger variables, such as `EATEATEATEATEATEAT`, even with case sensitivity. 

| Original | New |
|:-----------|:--------------|
| `EAT` | `int` |
| `eAT` | `len` |
| `EaT` | `print` |
| `ATE` | `str` |
| `EATEATEATEATEATEAT` | `str.isdigit` |

```python
def Function1(eat):
    return str(int(eat)*EATEATEAT)

def Function2(eat, eats):
    print(eat, eats)
    eat1 = 0
    eat2 = 0
    eateat = 0
    eAt = ""
    while eat1 < len(eat) and eat2 < len(eats):
        if eateat%EATEATEAT == EATEATEATEATEAT//EATEATEATEAT:
            eAt += eats[eat2]
            eat2 += 1
        else:
            eAt += eat[eat1]
            eat1 += 1
        eateat += 1
    return eAt

def Function3(eat):
    return eat[::EATEATEAT-EATEATEATEAT]

def Function4(eat):
    return Function1(eat[:EATEATEAT]) + Function3(eat)

def Function5(eat):
    return eat#*len(eat)

def Function6(eat):
    return "Eat" + str(len(eat)) + eat[:EATEATEAT]

def Function7(eat):
    if len(eat) == 9:
        if str.isdigit(eat[:EATEATEAT]) and\
            str.isdigit(eat[len(eat)-EATEATEAT+1:]):
                eateat = Function2(Function4(eat), Function6(Function5(Function3(eat))))
                if eateat == "E10a23t9090t9ae0140":
                    flag = "eaten_" + eat
                    print("absolutely EATEN!!! CTFlearn{",flag,"}")
                else:
                    print("thats not the answer. you formatted it fine tho, here's what you got\n>>", eateat)
        else:
            print("thats not the answer. bad format :(\
            \n(hint: 123abc456 is an example of good format)")
    else:
        print("thats not the answer. bad length :(")

print("what's the answer")
eat = input()
EATEATEAT = len(eat)//3
EATEATEATEAT = EATEATEAT+1
EATEATEATEATEAT = EATEATEAT-1
Function7(eat)
```

Next, we can change the variables declared at the bottom script. On line 37, it shows that our input must have a length of 9 characters in order to proceed further. With this in mind, we can remove some of the variables at the bottom entirely and replace them with the values associated with using nine character long input.  

| Original | New |
|:-----------|:--------------|
| `eat` | `userInput` |
| `EATEATEAT` | `3` |
| `EATEATEATEAT` | `4` |
| `EATEATEATEATEAT` | `2` |

```python
def Function1(userInput):
    return str(int(userInput)*3)

def Function2(userInput, eats):
    print(userInput, eats)
    eat1 = 0
    eat2 = 0
    eateat = 0
    eAt = ""
    while eat1 < len(userInput) and eat2 < len(eats):
        if eateat%3 == 2//4:
            eAt += eats[eat2]
            eat2 += 1
        else:
            eAt += userInput[eat1]
            eat1 += 1
        eateat += 1
    return eAt

def Function3(userInput):
    return userInput[::3-4]

def Function4(userInput):
    return Function1(userInput[:3]) + Function3(userInput)

def Function5(userInput):
    return userInput#*len(userInput)

def Function6(userInput):
    return "Eat" + str(len(userInput)) + userInput[:3]

def Function7(userInput):
    if len(userInput) == 9:
        if str.isdigit(userInput[:3]) and\
            str.isdigit(userInput[len(userInput)-3+1:]):
                eateat = Function2(Function4(userInput), Function6(Function5(Function3(userInput))))
                if eateat == "E10a23t9090t9ae0140":
                    flag = "eaten_" + userInput
                    print("absolutely EATEN!!! CTFlearn{",flag,"}")
                else:
                    print("thats not the answer. you formatted it fine tho, here's what you got\n>>", eateat)
        else:
            print("thats not the answer. bad format :(\
            \n(hint: 123abc456 is an example of good format)")
    else:
        print("thats not the answer. bad length :(")

print("what's the answer")
userInput = input()
Function7(userInput)
```

Lastly, I renamed the last remaining variables used with the eat naming convention in `Function2`, as well as all of the arguments as `arg` and `arg2` in every function except `Function7`. 

| Original | New |
|:-----------|:--------------|
| `eats` | `arg2` |
| `eat1` | `x` |
| `eat2` | `y` |
| `eateat` | `z` |
| `eAt` | `emptyString` |

```python
def Function1(arg1):
    return str(int(arg1)*3)

def Function2(arg1, arg2):
    print(arg1, arg2)
    x = 0
    y = 0
    z = 0
    emptyString = ""
    while x < len(arg1) and y < len(arg2):
        if z%3 == 2//4:
            emptyString += arg2[y]
            y += 1
        else:
            emptyString += arg1[x]
            x += 1
        z += 1
    return emptyString

def Function3(arg1):
    return arg1[::3-4]

def Function4(arg1):
    return Function1(arg1[:3]) + Function3(arg1)

def Function5(arg1):
    return arg1#*len(arg1)

def Function6(arg1):
    return "Eat" + str(len(arg1)) + arg1[:3]
```

After renaming everything to make it easier to read and understand, we can begin trying to understand what the functions are doing to our input. 

`E10a23t9090t9ae0140` is the result of `Function2` taking the result of `Function4`, and `Function6(Function5(Function3(userInput)))`, so lets first figure out what those four functions do. 

`Function6` adds "Eat" to the length and the first characters of the given argument. 

`Function5` just returns whatever we give it, since half of it is commented out. 

`Function3` returns its arguement in reverse.

`Function1` returns its argument multiplied by 3 as a string.

`Function4` returns a string that consists of the first 3 characters of the argument multiplied by 3 appended with the argument reversed.

With this in mind, try working backwards and see how `E10a23t9090t9ae0140` was created from `Function2`. 

My fully de-obfuscated code looked something liek this: 

```python
def Function1(arg1): # Returns argument multiplied by 3 as a string
    return str(int(arg1)*3)

def Function2(arg1, arg2):
    print(arg1, arg2)
    x = 0
    y = 0
    z = 0
    emptyString = ""
    while x < len(arg1) and y < len(arg2):
        if z%3 == 2//4:
            emptyString += arg2[y]
            y += 1
        else:
            emptyString += arg1[x]
            x += 1
        z += 1
    return emptyString

def Function3(arg1): # Returns its argument in reverse
    return arg1[::3-4]

def Function4(arg1):
    return Function1(arg1[:3]) + Function3(arg1)

def Function5(arg1): # Returns original input
    return arg1#*len(arg1)

def Function6(arg1): # Returns a string that starts with "Eat", the length of the argument given, and the first three characters of the argument. 
    return "Eat" + str(len(arg1)) + arg1[:3]

def Function7(userInput):
    if len(userInput) == 9:
        if str.isdigit(userInput[:3]) and str.isdigit(userInput[len(userInput)-3+1:]):
                eateat = Function2(Function4(userInput), Function6(Function5(Function3(userInput))))
                if eateat == "E10a23t9090t9ae0140":
                    flag = "eaten_" + userInput
                    print("absolutely EATEN!!! CTFlearn{",flag,"}")
                else:
                    print("thats not the answer. you formatted it fine tho, here's what you got\n>>", eateat)
        else:
            print("thats not the answer. bad format :(\
            \n(hint: 123abc456 is an example of good format)")
    else:
        print("thats not the answer. bad length :(")

print("what's the answer")
userInput = input()
Function7(userInput)
```

The input that will get the flag is `341eat009`.

The flag for this level is `CTFlearn{eaten_341eat009}`