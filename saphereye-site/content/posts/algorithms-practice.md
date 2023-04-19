---
title: "All Algorithms"
draft: false
---

Algorithms are cool, so let's implement them
![](https://upload.wikimedia.org/wikipedia/commons/b/b6/Rubik%27s_cube_v3.svg)

## Table of Contents
- [Table of Contents](#table-of-contents)
  - [Searching](#searching)
    - [Binary search](#binary-search)

### Searching
#### Binary search

| Complexity       | Complexity (?) |
| ---------------- | -------------- |
| Time Complexity  | O(log(n))      |
| Space Complexity | O(1)           |

```cpp
// C++ implementation
int binary_search(int* array, size_t array_size, int target) {
    if(array_size < 1)
        return -1;
    
    size_t left_index = 0;
    size_t right_index = array_size-1;
    size_t middle_index = 0;

    while(left_index <= right_index) {
        // Trying to evade integer overflow :)
        middle_index = left_index/2 + right_index/2;
        
        if(array[middle_index] == target)
            return middle_index;
        
        if(array[middle_index] > target) {
            if(middle_index == 0)
                return -1;
            
            right_index = middle_index - 1;
        }

        if(array[middle_index] < target) {
           left_index = middle_index + 1;
        }
    }

    // Target is not in array
    return -1;
}
```

