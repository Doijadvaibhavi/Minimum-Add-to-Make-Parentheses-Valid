# Minimum-Add-to-Make-Parentheses-Valid

A parentheses string is valid if and only if:

It is the empty string,
It can be written as AB (A concatenated with B), where A and B are valid strings, or
It can be written as (A), where A is a valid string.
You are given a parentheses string s. In one move, you can insert a parenthesis at any position of the string.

For example, if s = "()))", you can insert an opening parenthesis to be "(()))" or a closing parenthesis to be "())))".
Return the minimum number of moves required to make s valid.

 

Example 1:

Input: s = "())"
Output: 1
Example 2:

Input: s = "((("
Output: 3
 

Constraints:

1 <= s.length <= 1000

s[i] is either '(' or ')'.

# SOLUTION

Intuition
Objective: Determine the minimum number of parentheses to add to make a string valid.

Goal: Keep two counters: one for open parentheses and one for the number of unmatched closing parentheses.

Approach
Traverse the string character by character.
Keep track of:
Open parentheses that still need to be matched.
Unmatched closing parentheses.
For every open parenthesis '(', increase the count of open parentheses.
For every closing parenthesis ')', check if there's an unmatched open parenthesis available to pair it with:
If yes, decrease the open parenthesis count.
If not, increase the unmatched closing parenthesis count.
At the end of the traversal, the result is the sum of unmatched open and unmatched closing parentheses, which indicates how many parentheses are needed to make the string valid.

Complexity

Time complexity: O(N)

Space complexity: O(1)

# JAVA CODE

class Solution {

    public int minAddToMakeValid(String s) {
    
        int open_c = 0;
        
        int close_c = 0;

        for (char c : s.toCharArray()) {
        
            if (c == '(') {
            
                open_c++;
                
            } else if (c == ')' && open_c > 0) {
            
                open_c--;
                
            } else {
            
                close_c++;
                
            }
            
        }
        
        return open_c + close_c;
    }
}
