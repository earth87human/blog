---
title: Leetcode 13 Roman to Integer
date: 2023-05-01
tags: 
    - easy
    - array
categories:
    - Leetcode
---

## Problem :

### Description

> Roman numerals are represented by seven different symbols : <kbd>I</kbd> , <kbd>V</kbd> , <kbd>X</kbd> , <kbd>L</kbd> , <kbd>C</kbd> , <kbd>D</kbd> and <kbd>M</kbd>.

> **Symbol**   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   **Value**  
>  I         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     1  
>  V         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     5  
>  X         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     10  
>  L         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     50  
>  C         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    100  
>  D         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    500  
>  M         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    1000  

> For example , <kbd>2</kbd> is written as <kbd>II</kbd> in Roman numeral , just two ones added together . <kbd>12</kbd> is written as <kbd>XII</kbd> , which is simply <kbd>X + II</kbd> . The number <kbd>27</kbd> is written as <kbd>XXVII</kbd> , which is <kbd>XX + V + II</kbd> .  

> Roman numerals are usually written largest to smallest from left to right . However, the numeral for four is not <kbd>IIII</kbd> . Instead , the number four is written as <kbd>IV</kbd> . Because the one is before the five we subtract it making four . The same principle applies to the number nine , which is written as <kbd>IX</kbd> . There are six instances where subtraction is used : 
> * <kbd>I</kbd> can be placed before <kbd>V</kbd> (5) and <kbd>X</kbd> (10) to make 4 and 9. 
> * <kbd>X</kbd> can be placed before <kbd>L</kbd> (50) and <kbd>C</kbd> (100) to make 40 and 90. 
> * <kbd>C</kbd> can be placed before <kbd>D</kbd> (500) and <kbd>M</kbd> (1000) to make 400 and 900.

> Given a roman numeral , convert it to an integer .

### Example 1

> **Input** : s = "III"  
> **Output** : 3  
> **Explanation** : III = 3  

### Example 2

> **Input** : s = "LVIII"    
> **Output** : 58   
> **Explanation** : L = 50 , V= 5 , III = 3  

### Example 3

> **Input** : s = "MCMXCIV"  
> **Output** : 1994    
> **Explanation** : M = 1000 , CM = 900 , XC = 90 and IV = 4   

### Constraints

* <kbd>1 <= s.length <= 15</kbd>
* <kbd>s</kbd> contains only the characters <kbd>('I', 'V', 'X', 'L', 'C', 'D', 'M')</kbd>.
* It is **guaranteed** that <kbd>s</kbd> is a valid roman numeral in the range <kbd>[1, 3999]</kbd>.

## Solution 1 : 

```c++
class Solution {
public:
    int romanToInt(string s) {
        unordered_map<char, int> m;
        
        m['I'] = 1;
        m['V'] = 5;
        m['X'] = 10;
        m['L'] = 50;
        m['C'] = 100;
        m['D'] = 500;
        m['M'] = 1000;
        
        int ans = 0;
        
        for(int i = 0; i < s.length(); i++){
            if(m[s[i]] < m[s[i+1]]){
                ans -= m[s[i]];
            }
            else{
                ans += m[s[i]];
            }
        }
        return ans;
    }
};

# 時間複雜度 Ｏ(n)
# 空間複雜度 Ｏ(1)
```