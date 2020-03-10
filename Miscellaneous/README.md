# Miscellaneous challenges

## Where Can My Robot Go?

This challenge hints us at looking at this web sites [robots.txt file](https://www.robotstxt.org/). We can do this by navigating to `https://ctflearn.com/robots.txt`.

<img src="images/WhereCanMyRobotGo-1.png">

There, we see the directory that ctflearn specifically disallowed the directory `/70r3hnanldfspufdsoifnlds.html`. Navigating to this directory gives us the flag. 

<img src="images/WhereCanMyRobotGo-2.png"> 

The flag for this level is `CTFlearn{r0b0ts_4r3_th3_futur3}`

## Reversal of fortune

This challenge gives us a string we have to decode. Looking at the string, we see that its written backwards. We can use a simple Python script to print the sentence backwards.

```python
string = ".nac uoy fi tIe$reveRpilF eldnah ym gnisu em egassem ,avaj yllacificeps ,gnidoc emos htiw pleh deen I ,deifitnedi tegrat txeN"
print(string[::-1])
```

<img src="images/ReversalOfFortune-1.png">

The flag for this level is `FlipRever$eIt`
