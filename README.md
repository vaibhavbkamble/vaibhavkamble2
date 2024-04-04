# DotNetTest

Q1: Replace each array element by its corresponding rank
  Given an array of distinct integers, replace each array element by its corresponding rank in the array.

The minimum array element has the rank 1; the second minimum element has a rank of 2, and so on… For example,

Input:  { 10, 8, 15, 12, 6, 20, 1 } 
Output: { 4, 3, 6, 5, 2, 7, 1 }

import java.util.Arrays;
import java.util.HashMap;
import java.util.Map;

public class ReplaceWithRank {
    public static void main(String[] args) {
        int[] inputArr = {10, 8, 15, 12, 6, 20, 1};
        int[] outputArr = replaceWithRank(inputArr);
        System.out.println(Arrays.toString(outputArr));
    }
    public static int[] replaceWithRank(int[] arr) {
        int[] sortedArr = arr.clone();
        Arrays.sort(sortedArr);
        Map<Integer, Integer> rankMap = new HashMap<>();
        for (int i = 0; i < sortedArr.length; i++) {
            rankMap.put(sortedArr[i], i + 1);
        }
        int[] result = new int[arr.length];
        for (int i = 0; i < arr.length; i++) {
            result[i] = rankMap.get(arr[i]);
        }
        return result;
    }
}

Q2: Given a string s, find the length of the longest substring without repeating characters.
Example 1:
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
 
Constraints:

0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.


import java.util.HashMap;
import java.util.Map;

public class LongestSubstringWithoutRepeatingChars {
    public static void main(String[] args) {
        String inputStr = "abcabcbb";
        int outputLength = lengthOfLongestSubstring(inputStr);
        System.out.println(outputLength);
    }
    public static int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> charIndex = new HashMap<>();
        int maxLength = 0;
        int start = 0;
        for (int end = 0; end < s.length(); end++) {
            char currentChar = s.charAt(end);
            if (charIndex.containsKey(currentChar)) {
                start = Math.max(start, charIndex.get(currentChar) + 1);
            }
            charIndex.put(currentChar, end);
            maxLength = Math.max(maxLength, end - start + 1);
        }
        return maxLength;
    }
}

Q3:Find non-repeating characters in a string 
import java.util.HashSet;
import java.util.Set;

public class NonRepeatingCharacters {
    public static void main(String[] args) {
        String inputStr = "pwwkew";
        Set<Character> nonRepeatingChars = findNonRepeatingCharacters(inputStr);
        System.out.println(nonRepeatingChars);
    }
    public static Set<Character> findNonRepeatingCharacters(String s) {
        Set<Character> charSet = new HashSet<>();
        Set<Character> nonRepeatingChars = new HashSet<>();
        for (char c : s.toCharArray()) {
            if (charSet.contains(c)) {
                nonRepeatingChars.remove(c);
            } else {
                charSet.add(c);
                nonRepeatingChars.add(c);
            }
        }
        return nonRepeatingChars;
    }
}

Q4:You are given an array of integers. 
Write a C# program to find the frequency of each unique element in the array and 
store the results in a dictionary where the key is the element and the value is its frequency.
Then, print the elements and their frequencies.

Example:
Input:
int[] numbers = { 1, 2, 2, 3, 3, 3, 4, 4, 4, 4 };

Output:
Element: 1, Frequency: 1
Element: 2, Frequency: 2
Element: 3, Frequency: 3
Element: 4, Frequency: 4


import java.util.HashMap;
import java.util.Map;

public class ElementFrequency {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 2, 3, 3, 3, 4, 4, 4, 4};
        Map<Integer, Integer> frequencyMap = new HashMap<>();
        for (int num : numbers) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }
        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()) {
            System.out.println("Element: " + entry.getKey() + ", Frequency: " + entry.getValue());
        }
    }
}
