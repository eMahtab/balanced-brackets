# Balanced Brackets (Valid Parentheses)


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
