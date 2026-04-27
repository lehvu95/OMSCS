N/A means that a value was not found because some criteria wasn't met, so the TSLCompiler tool defaults to "not applicable." In some cases, this is perfectly fine because it means that the value of that choice doesn't matter since it's not going to be used. For example, it would be fine in the following scenario:

```
Inventory for beach:
    Towel and sunscreen. [property towel]
    Sunscreen.           
Color of towel:
    Purple.  [if towel]
    Pink.    [if towel]
    Rainbow. [if towel]
```
This is because there will a choice of not selecting a towel and selecting only sunscreen. Since I didn't grab a towel, not only will you be missing a towel when you get to the beach, but also the category "Color of towel" is unecessary, or "not applicable" (that is, N/A), so you will get a test frame such as this one:
```
Test Case 4
        Inventory for beach  : Sunscreen 
        Color of towel       : N/A
```

However, there may other cases where the value of the category being N/A does matter but the TSLCompiler tool thinks it is not applicable. In these cases, it means that there are partitions in a category that are not being described because it doesn't fit any of the previously set constraints for that category. Although this is not an error, it might make it more difficult to implement the frames as JUnit tests since N/A doesn't describe anything meaningful for that partition.

For example, this can happen for the following "Shape" category:
```
Color:
    red. [property red]
    yellow.
Shape:
    circle. [if red]
```

because if I select yellow, then there will be no shape assigned to it, resulting the following frame:
```
Test Case 2
        Color  : yellow 
        Shape  : N/A
```

And then the color yellow will be sad and shapeless.