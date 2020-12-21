#   Decoded String at Index

## Problem
An encoded string S is given.  To find and write the decoded string to a tape, the encoded string is read one character at a time and the following steps are taken:

If the character read is a letter, that letter is written onto the tape.
If the character read is a digit (say d), the entire current tape is repeatedly written d-1 more times in total.
Now for some encoded string S, and an index K, find and return the K-th letter (1 indexed) in the decoded string.

## Analysis
Missing in my thoughts again.

Thoughts:
Record every new sequence in the word and then we can track from the end to get the Kth character

Improve:
We can use only one array to do this

```java
class Solution {
    public String decodeAtIndex(String S, int K) {
                long tapeSize = 0;
        int idx = 0;
        char c = 'A';
        int[] sizeArr = new int[S.length()];
        // forward
        while (tapeSize < K) {
            c = S.charAt(idx);
            if (c >= '2' && c <= '9') {
                int r = c - '0';
                tapeSize *= r;
            } else {
                tapeSize++;
            }
            sizeArr[idx] = (int)tapeSize;
            idx++;
        }
        idx--;
//        System.out.printf("fxirst iteration tape size: %d, idx: %d\n", tapeSize, idx);

        // backward
        while (idx >= 0) {
            c = S.charAt(idx);
            if (c > '1' && c < ':') {
                int r = c - '0';
                tapeSize = tapeSize / r;
                K = K % sizeArr[idx - 1]; } else {
                if (tapeSize == K || K == 0) {
                    break;
                } else {
                    tapeSize--;
                }
            }
            idx--;
        }

        return new String(new char[] { c } );

    }
}
```
