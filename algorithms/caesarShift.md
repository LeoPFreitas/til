# caesarShift

## Input example

- Some string as input
- -4

## Output example

- Okia opnejc wo ejlqp

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String phase = scanner.nextLine();
        int n = scanner.nextInt();

        System.out.println(caesarShift(phase, n));

    }

    public static String caesarShift(String input, int shift) {
        // handle negative
        while (shift < 0)
            shift += 26;

        int l = input.length();
        StringBuffer output = new StringBuffer();

        for (int i = 0; i < l; i++) {
            char c = input.charAt(i);
            char newLetter = c;

            if (c >= 'a' && c <= 'z') { // lowercase
                newLetter = (char) ((c - 'a' + shift) % 26 + 'a');
            } else if (c >= 'A' && c <= 'Z') { // uppercase
                newLetter = (char) ((c - 'A' + shift) % 26 + 'A');
            }

            output.append(newLetter);
        }

        return output.toString();
    }
}
```
