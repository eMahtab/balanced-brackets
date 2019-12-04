# Balanced Brackets (Valid Parentheses)

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets are closed by the same type of brackets and in the correct order.

#### Note that an empty string is also considered valid.

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Stack;

public class App {
	public static void main(String[] args) {
	      String s = ")[]}";
	      System.out.println(isValid(s));
	}
	
	public static boolean isValid(String s) {
              Stack<String> stack = new Stack<String>();
	      Map<String,String> map = new HashMap<String,String>();
	      map.put("]", "[");  map.put(")", "(");  map.put("}", "{");
	      for(int i = 0; i < s.length(); i++) {
		   String st = Character.toString(s.charAt(i));
		   if(!map.containsKey(st)) {
			 stack.push(st);
		    } else {
			if(stack.isEmpty()) {
                            return false; 
			  } else {
                            String peek = stack.peek();
			    if(peek.equals(map.get(st))) {
			         stack.pop();
			     } else {
			        return false;
			     }
                          }
		    }
	     }
	  return stack.isEmpty();
    }
}


```
