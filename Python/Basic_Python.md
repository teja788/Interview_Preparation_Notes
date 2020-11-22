
## Datatypes in python

* **Numbers(float, interger)**
* **String**
* **List**
* **Tuple**
* **sets**
* **Dictionary** - Unordered mapping of unique keys and values. values can be any python object. They are created in form of hash tables. looking up values is faster

### lambda, map, reduce
* lambda - creates a anonymus function. can be used for short one use functions

### pass, continue, break
* **pass** - do nothing. used in some for loops and if statements
* **continue** - halt execution of current element and pass to next element
* **break** - halt the execution of loop


### Difference between list and tuple
* Lists are mutable. things can be added, removed etc from list
* tuples are un-mutable

## iterables and iterators

* iterable: any object we can run for loop on is an iterator. ex: lists, tuples etc
* iterators: these are objects which know there state and can fetch next item
* iterables object contains **__iter__** dunder method. iterator contains both iter and **__next__** method as well.

```python

nums = [1,2,3,4] # iterable but not iterator, next(nums) won't work

iter_num = iter(nums) # iterator 
print(next(nums))
```


## Generators
* Generators are a object used to give one value at a time instead of giving memory to whole list or range.
* It is advantageous in terms of memeory and processing over large lists

```python
def squared_num(nums):
  for i in nums:
    yield(i*i)

#you can access values from generator using next or for loop

squ_num = squared_num([1,2,3,4,5])

print(next(squ_num))

for num in squ_num:
  print(num)

#another way of making a generator
squared_nums = (i*i for i in nums)

print(list(squared_nums))

```

