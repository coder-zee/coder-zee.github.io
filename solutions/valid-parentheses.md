Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.

```
function isValid(s: string): boolean {
    const stack = Array<string>();
    for(let symbol of [...s]){
        if(isOpeningSymbol(symbol)){
            stack.push(symbol);
        }
        else {
            if(!isMatchingParentheses(stack.at(-1), symbol)) return false;
            stack.pop();
        }
    }
    return stack.length === 0
};
    
function isOpeningSymbol(symbol: string): boolean {
    return symbol === '(' || symbol === '{' || symbol === '[';  
}

function isMatchingParentheses(left: string, right: string) {
    return left === '(' && right === ')' || left === '{' && right === '}'  || left === '[' && right === ']';
}
```
