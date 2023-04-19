---
title: "All Algorithms (Under Construction)"
draft: false
help: https://www.linkedin.com/pulse/list-algorithms-computer-programming-pranam-bhat/
---

Algorithms are cool, so let's implement them
![](https://upload.wikimedia.org/wikipedia/commons/b/b6/Rubik%27s_cube_v3.svg)

## Table of Contents
- [Table of Contents](#table-of-contents)
  - [Searching](#searching)
    - [Binary search](#binary-search)
  - [Sorting](#sorting)
    - [Bubble sort](#bubble-sort)
    - ['Simplest' sorting algorithm](#simplest-sorting-algorithm)
    - [Naive string search](#naive-string-search)
    - [BWT sub-string search](#bwt-sub-string-search)
    - [Rabin-Karp algorithm](#rabin-karp-algorithm)
  - [Graphs](#graphs)
  - [Arrays](#arrays)
  - [Tree](#tree)
  - [Others](#others)

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

### Sorting
#### Bubble sort
```C++
// C++ implementation to sort array in ascending order
void bubble_sort(int* array, size_t size) {
    for(size_t i = 0; i < size; i++)
        for(size_t j = i+1; j < size; j++)
            if(array[i] > array[j])
                std::swap(array[i], array[j]);

}
```

#### 'Simplest' sorting algorithm
```C++
// Reference: polylog video
void simple_sort(int* array, size_t size) {
    for(size_t i = 0; i < size; i++)
        for(size_t j = 0; j < size; j++)
            if(array[i] > array[j])
                std::swap(array[i], array[j]);
}
```
#### Naive string search
```C++
// prints all occurences
void naive_string_search(string text, string pattern) {
    size_t text_index;
    size_t pattern_index;

    for (text_index = 0, pattern_index = 0; text_index < text.size(); text_index++) {
        // If word found
        if (pattern_index == pattern.size() - 1) {
            std::cout << text_index - pattern.size() + 1 << std::endl;
            pattern_index = 0;
            continue;
        }

        // If we find a matching letter
        if (text[text_index] == pattern[pattern_index]) {
            pattern_index++;
            continue;
        }

        // If we don't find matching letter :(
        pattern_index = 0;
    }
}
```

#### BWT sub-string search

#### Rabin-Karp algorithm

### Graphs

### Arrays

### Tree

### Others

