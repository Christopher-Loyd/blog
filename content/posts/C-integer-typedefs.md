+++
title = 'C Integer Typedefs'
date = 2024-05-26T22:43:14-05:00
draft = false
+++

I have been learning C for the past several weeks and have been attracted to explicitly specifying the length and signedness(?) of integer types. `<stdint.h>` provides these explicit definitions, but unfortunately they're cumbersome to type out regularly with type names such as `uint8_t` and `int32_t`. 

To solve this problem, I create a header `<int.h>` that I can then import in with typedefs to rename these explicit type definitions anywhere I need to use them. The following is that `<int.h>` header that I'm using, for posterity purposes:

```c
/* File: <int.h>
   Author: Christopher Loyd (me@christopherloyd.com)
   Description: Typedefs to rename <stdint.h>'s explicit integer definitions to more usable names.
*/

#pragma once
#include <stdint.h>

typedef uint8_t  u8;
typedef uint16_t u16;
typedef uint32_t u32;
typedef uint64_t u64;

typedef int8_t   i8;
typedef int16_t  i16;
typedef int32_t  i32;
typedef int64_t  i64;
```

Example usage:

```c
// File: main.c

#include <stdio.h>
#include <sysexits.h>
#include "int.h"

int main(void)
{
    u8 a = 100;
    printf("%d\n", a);

    return EX_OK;
}

// Output: 100
