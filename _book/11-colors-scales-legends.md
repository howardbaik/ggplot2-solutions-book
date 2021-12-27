# Colour scales and legends




## Exercises



```r
drv_labels <- c("4" = "4wd", "f" = "fwd", "r" = "rwd")

ggplot(mpg, aes(displ, hwy)) + 
  geom_point(aes(colour = drv)) +
  scale_colour_discrete(labels = drv_labels)
```

<img src="11-colors-scales-legends_files/figure-html/unnamed-chunk-2-1.png" width="672" />


- We store the labels inside `drv_labels` and use it in `scale_colour_discrete()`


## Exercises

**1.** How do you make legends appear to the left of the plot?
`
- `theme(legend.position = "left")` make legends appear to the left of the plot. 
- Other options: `theme(legend.position = "right")`, `theme(legend.position = "bottom")`, and `theme(legend.position = "none")`


<br>

**2.** What's gone wrong with this plot? How could you fix it?

- There are two separate legends for the same variable (`drv`). We need to combine these two legends into one. To do this, both `color` and `shape` need to be given shape specifications.


```r
ggplot(mpg, aes(displ, hwy)) + 
  geom_point(aes(colour = drv, shape = drv)) + 
  scale_colour_discrete("Drive train",
                        breaks = c("4", "f", "r"),
                        labels = c("4-wheel", "front", "rear")) +
  scale_shape_discrete("Drive train",
                        breaks = c("4", "f", "r"),
                        labels = c("4-wheel", "front", "rear"))
```

<img src="11-colors-scales-legends_files/figure-html/unnamed-chunk-3-1.png" width="672" />


<br>

**3.** 


```r
ggplot(mpg, aes(displ, hwy, colour = class)) + 
      geom_point(show.legend = FALSE) + 
      geom_smooth(method = "lm", se = FALSE) + 
      theme(legend.position = "bottom") + 
      guides(colour = guide_legend(nrow = 1))
#> `geom_smooth()` using formula 'y ~ x'
```

<img src="11-colors-scales-legends_files/figure-html/unnamed-chunk-4-1.png" width="672" />

> Note: The answers to these "recreate the code for this plot" questions are provided in the source code of the book.
