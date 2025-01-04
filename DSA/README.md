# Lecture - 2 : Data Structures and Algorithms

## Data Structure Interfaces

- A data structure is a way to store data, with algorithms that support operations on the data
- Collection of supported operations is called an interface (also API or ADT)
- Interface is a specification: what operations are supported (the problem!)
- Data structure is a representation: how operations are supported (the solution!)
- In this class, two main interfaces: Sequence and Set 

## Sequence Interface (L02, L07)
- Maintain a sequence of items (order is extrinsic)
- Ex: (x0, x1, x2, . . . , xn−1) (zero indexing)
- (use n to denote the number of items stored in the data structure)
- Supports sequence operations: 

| **Category** | **Operation**      | **Description**                                    |
|--------------|--------------------|----------------------------------------------------|
| **Container**| `build(X)`         | Given an iterable `X`, build sequence from items in `X`. |
|              | `len()`            | Return the number of stored items.                 |
|--------------|--------------------|----------------------------------------------------|
| **Static**   | `iter_seq()`       | Return the stored items one-by-one in sequence order. |
|              | `get_at(i)`        | Return the `i`th item.                             |
|              | `set_at(i, x)`     | Replace the `i`th item with `x`.                   |
|--------------|--------------------|----------------------------------------------------|
| **Dynamic**  | `insert_at(i, x)`  | Add `x` as the `i`th item.                         |
|              | `delete_at(i)`     | Remove and return the `i`th item.                 |
|              | `insert_first(x)`  | Add `x` as the first item.                        |
|              | `delete_first()`   | Remove and return the first item.                |
|              | `insert_last(x)`   | Add `x` as the last item.                         |
|              | `delete_last()`    | Remove and return the last item.                 |

(Note that insert / delete operations change the rank of all items after the modified item.)



### Special case interfaces:
 - stack | insert last(x) and delete last()
 - queue | insert last(x) and delete first()

## Set Interface (L03-L08)
- Sequence about extrinsic order, set is about intrinsic order
- Maintain a set of items having unique keys (e.g., item x has key x.key)
- (Set or multi-set? We restrict to unique keys for now.)
- Often we let key of an item be the item itself, but may want to store more info than just key
- Supports set operations: 

| **Category** | **Operation**    | **Description**                                                    |
|--------------|------------------|--------------------------------------------------------------------|
| **Container**| `build(X)`       | Given an iterable `X`, build sequence from items in `X`.          |
|              | `len()`          | Return the number of stored items.                                |
|--------------|------------------|--------------------------------------------------------------------|
| **Static**   | `find(k)`        | Return the stored item with key `k`.                              |
|--------------|------------------|--------------------------------------------------------------------|
| **Dynamic**  | `insert(x)`      | Add `x` to the set (replace item with key `x.key` if one already exists). |
|              | `delete(k)`      | Remove and return the stored item with key `k`.                   |
|--------------|------------------|--------------------------------------------------------------------|
| **Order**    | `iter_ord()`     | Return the stored items one-by-one in key order.                  |
|              | `find_min()`     | Return the stored item with the smallest key.                     |
|              | `find_max()`     | Return the stored item with the largest key.                      |
|              | `find_next(k)`   | Return the stored item with the smallest key larger than `k`.     |
|              | `find_prev(k)`   | Return the stored item with the largest key smaller than `k`.     |


### Special case interfaces:
- dictionary | set without the Order operations

## Array Sequence
- Array is great for static operations! get at(i) and set at(i, x) in Θ(1) time!
- But not so great at dynamic operations...
- (For consistency, we maintain the invariant that array is full)
- **Inserting and Removing Items Requires:**
  - [ ] Reallocating the array
  - [ ] Shifting all items after the modified item
 



```
class Array_Seq:
    def __init__(self):              # O(1)
        self.A = []
        self.size = 0
        
    def __len__(self):               # O(1)
        return self.size
        
    def __iter__(self):             # O(n)
        for i in range(len(self)):
            yield self.A[i]          # O(n) iter_seq

    def build(self, X):      
        self.A = [a for a in X]     # pretend this builds a static array
        self.size = len(self.A)
        
    def get_at(self, i):
        return self.A[i]           # O(1)

    def set_at(self, i, x):
        self.A[i] = x       # O(1)

```
