# Note

## lab0

increase harness.c time_limit to let debug work.

## lab1

modify Makefile to disable check-format which require clang-format.

remove Makefile `-O1` to let debug work properly.

`fitsBits` test script.

```c
#include <stdio.h>

long test_fitsBits(long x, long n) {
    long TMin_n = -(1L << (n - 1));
    /* This convoluted way of generating TMax avoids overflow */
    long TMax_n = (long)((1UL << (n - 1)) - 1UL);
    return (long)(x >= TMin_n && x <= TMax_n);
}

int main() {
    printf("%d\n", test_fitsBits(0b11, 3));   // 0000000000000011
    printf("%d\n", test_fitsBits(0b100, 3));  // 0000000000000100
    printf("%d\n", test_fitsBits(0b101, 3));  // 0000000000000101
    printf("%d\n", test_fitsBits(-3, 3));     // 1111111111111101
    printf("%d\n", test_fitsBits(-4, 3));     // 1111111111111100
    printf("%d\n", test_fitsBits(-5, 3));     // 1111111111111011

    // output: 1 0 0 1 1 0
}
```

`trueFiveEighths` good answer: https://github.com/vectorpikachu/datalab-handout/blob/11a8871bfbd4a538645abf743186a044314aa80e/bits.c#L399
