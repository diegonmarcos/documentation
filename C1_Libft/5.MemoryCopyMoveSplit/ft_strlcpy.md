sons : [ft_strlen](ft_strlen.md) [ft_memcpy]([ft_memcpy)
tags : #memcopy
# ft_strlcpy 
``` c 
size_t ft_strlcpy(char *dst, const char *src, size_t dstsize);
```
<br>
<br>

# Manual
**Brief:**  
Copies up to `dstsize` - 1 characters from the string `src` to `dst`, NUL-terminating the result if `dstsize` is not 0.

**File:** `ft_strlcpy.c` / **Date:** 2024-06-22  
**Author:** Diego N. Marcos <dnepomuc@student.42barcelona.com>

**Library/Header:**  
* `string.h`

**Description:**
The `ft_strlcpy()` function copies up to `dstsize - 1` characters from the string `src` to `dst`, NUL-terminating the result if `dstsize` is not 0.  It is designed to be a safer, more consistent, and less error-prone replacement for the standard `strncpy()` function.

**Input Values:**
* `dst`: The destination buffer to copy the string to.
* `src`: The source string to copy from.
* `dstsize`: The maximum number of characters to copy to `dst` (including the null terminator).

**Return Value:**
* The total length of the string they tried to create (the length of `src`). This allows for easy truncation detection if the destination buffer is too small.

**Note:**
- If `src` is longer than `dstsize - 1`, the resulting string in `dst` will be truncated, but it will still be NUL-terminated.
- If `dstsize` is 0, the function does not modify `dst` and returns the length of `src`.

**Example:**
```c
char dst[15];
char src[] = "Hello, world!";

size_t result = ft_strlcpy(dst, src, 15); // Copies "Hello, world!" to dst (13 characters + '\0')
printf("%s\n", dst);   // Output: Hello, world!
printf("%zu\n", result); // Output: 13 (length of src)
```

<br>
<br>

# Code Explanation
**Source Code:**
``` C
size_t	ft_strlcpy(char *dst, const char *src, size_t dstsize)
{
	size_t	src_len;

	src_len = ft_strlen(src);
	if (src_len + 1 < dstsize)
		ft_memcpy(dst, src, src_len + 1);
	else if (dstsize != 0)
	{
		ft_memcpy(dst, src, dstsize - 1);
		dst[dstsize - 1] = 0;
	}
	return (src_len);
}


```


# Takeaways
### Keynotes
- Overflow is secured then it will truncate it
- NULL terminator is guaranteed
-  Input size must + 1 for the NULL terminator

### Learnings
