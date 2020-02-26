---
type: slides
---

# Slicing with Pandas

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

Congratulations on writing your first code! This is great! We have read in our data and know the dimensions. What now? Let's go over how we would **index**, **slice** and  **select** certain columns or rows of our data.

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>


---
## Cereal Data

Before doing anything let's bring in some new data called `cereal.csv`

```python
import pandas as pd

df = pd.read_csv('cereal.csv')
df.head()
```

```out


```

<img src='module1/cereal-head.png'>


Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---
## Indexing Dataframes

```out


```

<img src='module1/cereal-head.png'>

We can see all the columns of the dataframe and the first 5 rows of the data.
let's say we only want certain rows of the whole dataframe or certain columns.

We talked about how `df.head()` will generate the first 5 rows of a df but what if we wanted rows 5-10?

The first column of this dataframe is called the `index` each row is given a name as well as a position. In this case the name and index are both numbers.
but what if we they were not?

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

<img src='module1/cereal15.png' width="60%">

Now the index has been set as the name of the cereal (we will talk about how to do this later)

Let's talk about `Almond Delight`.  It's index name is "Almond Delight" but it's index position is 4th.    
If you just double counted and started screaming "5!" at the screen that's ok. In the Python language we start counting at position 0 (then 1, 2, 3, and 4 for Almond Delight). So it's important that we relearn counting from childhood to include 0.




Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

So now let's say we want 5 rows past `Almond Delight` so we want rows with the index names "Apple Cinnamon Cheerios" to "Cap'n'Crunch".  

How would we do this?   

There are 3 main ways:
- `.loc[]` using index names
- `.iloc[] ` using index position
- Using `[]` brackets (we will get into that more next module)

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

In the first case:

``` Python
df.loc[ "Apple Cinnamon Cheerios" : "Cap'n'Crunch"]
```


```out


```

<img src='module1/apple-captain.png'>

 This essentially means the _dataframe location from Apple Cinnamon Cheerios" to "Cap'n'Crunch"._   
What about if we only wanted certain columns as well?

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

Perhaps we were only interested in the `calories` to `fiber` columns of those rows?


``` Python
df.loc[ "Apple Cinnamon Cheerios" : "Cap'n'Crunch", "calories" : "fiber"]
```


```out


```

<img src='module1/cals-fiber.png'>


So `loc` is used to slice columns and rows by **name** and within an interval.

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

What if we wanted all the rows of the dataframe but only the columns "calories" to "fiber"?

we would simply use `:` to indicate from "end" to "end" for rows.

``` Python
df.loc[ : , "calories" : "fiber"]
```


```out


```

<img src='module1/rows-somecols.png' width="60%">



Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

What about if we only wanted certain columns as well?
Perhaps we were only interested in the `calories` to `fiber` columns?

``` Python
df.loc[ "Apple Cinnamon Cheerios": "Cap'n'Crunch", "calories" : "fiber"]
```


```out


```

<img src='module1/cals-fiber.png'>


Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

We discussed slicing when the indices are named with words but that's not always the case. What if they are named with a numbers?
Let's go back to our original cereal dataframe we had when we uploaded it.

<img src='module1/cereal-index-num.png'>


Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

We can use the same format before but now since our rows are named with numbers we no longer need to express the row names in "quotations". So now we would use row names without quotations.

`df.loc[ row-name-start : row-name-end , "column name start" : "column name end"]`

Let's give our past example a shot. We again want rows "Apple Cinnamon Cheerios" to "Cap'n'Crunch" with all the columns but now the indices are named with numbers.

``` Python
df.loc[ 5 : 10 ]
```


```out


```

<img src='module1/cereal510.png'>

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---
What if we wanted only certain columns again too? Note that now `name` is a column now.

``` Python
df.loc[ 5 : 10 , "calories" : "fiber"]
```


```out


```

 <img src='module1/cereal-510-cf.png'>

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

The sliced dataframe no longer has `name` in it so we would have to include it in our slice. In the next slide deck we will talk about selecting specific columns and rows that are not consecutive.  

``` Python
df.loc[ 5 : 10 , "name" : "fiber"]
```


```out


```

 <img src='module1/cereal-510-nf.png'>

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

## So Far

`loc` is used to slice columns and rows by **name** and within an interval.
We always specify **row** indexing first, then **columns**.

```
df.loc[ "row name start" : "row name end", "column name start" : "column name end"]
```

- If we arn't slicing any columns we can simply say `df.loc[ "row name start" : "row name end"]` since columns specification follow row's.
- However, the reverse is not true. If we want all the rows with only specific columns, we specify rows first and therefore we would need to make it clear with `df.loc[  : , "column name start" : "column name end"]`.
- We can read `:` as *"to"*
- If the indices are named numbers we do not need "quotations" when calling them.

Notes: Script here.
<html>
<audio controls >
  <source src="placeholder_audio.mp3" />
</audio></html>

---

# let’s apply what we learned!

Notes: Script here
<html>
<audio controls >
  <source src="572_placeholder_audio.mp3" />
</audio></html>
