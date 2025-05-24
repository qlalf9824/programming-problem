# Merge Strings Alternately

[Problem Link](https://leetcode.com/problems/merge-strings-alternately/?envType=study-plan-v2&envId=leetcode-75)

## Problem

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

### Example 1

Input: word1 = "abc", word2 = "pqr"
Output: "apbqcr"
Explanation: The merged string will be merged as so:
word1: a b c
word2: p q r
merged: a p b q c r

### Example 2

Input: word1 = "ab", word2 = "pqrs"
Output: "apbqrs"
Explanation: Notice that as word2 is longer, "rs" is appended to the end.
word1: a b
word2: p q r s
merged: a p b q r s

### Example 3

Input: word1 = "abcd", word2 = "pq"
Output: "apbqcd"
Explanation: Notice that as word1 is longer, "cd" is appended to the end.
word1: a b c d
word2: p q
merged: a p b q c d

### Constraints:

1 <= word1.length, word2.length <= 100
word1 and word2 consist of lowercase English letters.

## solution

```
function mergeAlternately(word1: string, word2: string): string {
    let margedString = "";
    while(!(word1.length === 0 && word2.length === 0)) {
        if(word1.length !== 0) {
            margedString += word1[0];
            word1 = word1.slice(1)
        }
        if(word2.length !== 0) {
            margedString += word2[0];
            word2 = word2.slice(1)
        }
    }
    return margedString;
};
```

First, check if word1's length is 0. If not zero, append word1's first character to mergedString and remove the first character from word1. Then apply the same logic to word2. Continue this process until both word1 and word2 are empty.

## Better Than

```
function mergeAlternately(word1: string, word2: string): string {
    let result = "";
    const maxLength = Math.max(word1.length, word2.length);

    for (let i = 0; i < maxLength; i++) {
        if (i < word1.length) result += word1[i];
        if (i < word2.length) result += word2[i];
    }

    return result;
}
```
