# Bishwos Page on the web

## Repositories

[Simple Sidescroller game using html canvas](https://github.com/bishwos/simple-sidescroller-game)

[Play](https://bishwos.github.io/simple-sidescroller-game/)
````
https://github.com/bishwos/simple-sidescroller-game.git
````
[Nepse Scraper using cherio](https://github.com/bishwos/nepse-floorsheet-scraper)

````
https://github.com/bishwos/nepse-floorsheet-scraper.git
````

[Spring base for Restful APIs](https://github.com/bishwos/rest_base)
````
https://github.com/bishwos/rest_base.git
````

[Hacker rank tests](https://github.com/bishwos/hackerrank_tests)
````
https://github.com/bishwos/hackerrank_tests.git
````

Practicing TDD
````
TODO
````

2D Collision Detection

https://stackoverflow.com/questions/306316/determine-if-two-rectangles-overlap-each-other?rq=1
````
This is a very fast way to check with C++ if two rectangles overlap:

````
````
return std::max(rectA.left, rectB.left) < std::min(rectA.right, rectB.right)
    && std::max(rectA.top, rectB.top) < std::min(rectA.bottom, rectB.bottom);
````
````
It works by calculating the left and right borders of the intersecting rectangle, and then comparing them: if the right border is equal to or less than the left border, it means that the intersection is empty and therefore the rectangles do not overlap; otherwise, it tries again with the top and bottom borders.

What is the advantage of this method over the conventional alternative of 4 comparisons? It's about how modern processors are designed. They have something called branch prediction, which works well when the result of a comparison is always the same, but have a huge performance penalty otherwise. However, in the absence of branch instructions, the CPU performs quite well. By calculating the borders of the intersection instead of having two separate checks for each axis, we're saving two branches, one per pair.

It is possible that the four comparisons method outperforms this one, if the first comparison has a high chance of being false. That is very rare, though, because it means that the second rectangle is most often on the left side of the first rectangle, and not on the right side or overlapping it; and most often, you need to check rectangles on both sides of the first one, which normally voids the advantages of branch prediction.

This method can be improved even more, depending on the expected distribution of rectangles:

If you expect the checked rectangles to be predominantly to the left or right of each other, then the method above works best. This is probably the case, for example, when you're using the rectangle intersection to check collisions for a game, where the game objects are predominantly distributed horizontally (e.g. a SuperMarioBros-like game).
If you expect the checked rectangles to be predominantly to the top or bottom of each other, e.g. in an Icy Tower type of game, then checking top/bottom first and left/right last will probably be faster:
return std::max(rectA.top, rectB.top) < std::min(rectA.bottom, rectB.bottom)
    && std::max(rectA.left, rectB.left) < std::min(rectA.right, rectB.right);
If the probability of intersecting is close to the probability of not intersecting, however, it's better to have a completely branchless alternative:
return std::max(rectA.left, rectB.left) < std::min(rectA.right, rectB.right)
     & std::max(rectA.top, rectB.top) < std::min(rectA.bottom, rectB.bottom);
(Note the change of && to a single &)

---Pedro Gimeno
````

````
if (RectA.Left < RectB.Right && RectA.Right > RectB.Left &&
     RectA.Top > RectB.Bottom && RectA.Bottom < RectB.Top ) 
or, using Cartesian coordinates

(With X1 being left coord, X2 being right coord, increasing from left to right and Y1 being Top coord, and Y2 being Bottom coord, increasing from bottom to top -- if this is not how your coordinate system [e.g. most computers have the Y direction reversed], swap the comparisons below) ...

if (RectA.X1 < RectB.X2 && RectA.X2 > RectB.X1 &&
    RectA.Y1 > RectB.Y2 && RectA.Y2 < RectB.Y1) 
Say you have Rect A, and Rect B. Proof is by contradiction. Any one of four conditions guarantees that no overlap can exist:

Cond1. If A's left edge is to the right of the B's right edge, - then A is Totally to right Of B
Cond2. If A's right edge is to the left of the B's left edge, - then A is Totally to left Of B
Cond3. If A's top edge is below B's bottom edge, - then A is Totally below B
Cond4. If A's bottom edge is above B's top edge, - then A is Totally above B
So condition for Non-Overlap is

NON-Overlap => Cond1 Or Cond2 Or Cond3 Or Cond4
Therefore, a sufficient condition for Overlap is the opposite.

Overlap => NOT (Cond1 Or Cond2 Or Cond3 Or Cond4)
De Morgan's law says
Not (A or B or C or D) is the same as Not A And Not B And Not C And Not D
so using De Morgan, we have

Not Cond1 And Not Cond2 And Not Cond3 And Not Cond4
This is equivalent to:

A's Left Edge to left of B's right edge, [RectA.Left < RectB.Right], and
A's right edge to right of B's left edge, [RectA.Right > RectB.Left], and
A's top above B's bottom, [RectA.Top > RectB.Bottom], and
A's bottom below B's Top [RectA.Bottom < RectB.Top]
Note 1: It is fairly obvious this same principle can be extended to any number of dimensions.
Note 2: It should also be fairly obvious to count overlaps of just one pixel, change the < and/or the > on that boundary to a <= or a >=.
Note 3: This answer, when utilizing Cartesian coordinates (X, Y) is based on standard algebraic Cartesian coordinates (x increases left to right, and Y increases bottom to top). Obviously, where a computer system might mechanize screen coordinates differently, (e.g., increasing Y from top to bottom, or X From right to left), the syntax will need to be adjusted accordingly

--Charles Bretana

````

## TODO
- [ ] TDD
- [ ] Mathematics Notes
- [ ] Machine learning excercises
- [ ] Kotlin graphql server

Left here for reference to markdown for future use

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
