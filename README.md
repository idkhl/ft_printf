# ft_printf: A Custom Implementation of printf()

## Project Summary

ft_printf is the second foundational project in the 42 curriculum. The objective is to recreate the functionality of the standard C library function `printf()`, which is one of the most versatile and used functions in C.

The primary skill acquired in this project is learning how to work with variadic functions — functions that accept a variable number of arguments—by utilizing the macros defined in the `<stdarg.h>` header (specifically `va_list`, `va_start`, `va_arg`, and `va_end`). This requires building a robust parser to correctly handle different format specifiers and corresponding argument types. 

---

## How to Compile and Use

### Requirements

* A C compiler (`cc` / `gcc`)
* The standard `make` utility
* **Libft:** This project is authorized to use functions from your `Libft`. It is assumed that your `libft` source files are included and compiled alongside `ft_printf`.

### Compilation

To build the library, clone the repository and use the included **Makefile**. The result is a static library, **`libftprintf.a`**.

| Command | Description |
| :--- | :--- |
| `make` or `make all` | Compiles the mandatory part and creates the static library **`libftprintf.a`**. |
| `make clean` | Removes all generated object files (`.o`). |
| `make fclean` | Removes all object files (`.o`) and the final library file (`libftprintf.a`). |
| `make re` | Performs `fclean` followed by `all`. |

### Usage

1.  **Include the Header:** In your C source files, include the main header:
    ```c
    #include "ft_printf.h"
    ```
2.  **Compile and Link:** Compile your program, ensuring you link with the generated library:
    ```bash
    cc -Wall -Wextra -Werror main.c -L. -lftprintf -o my_program
    ```
    (Note: If `ft_printf` depends on `libft.a`, you may need to link both: `-lftprintf -lft`)

---

## Mandatory Conversions

The `ft_printf` function must correctly parse the format string and handle the following required conversion specifiers:

| Specifier | Argument Type | Description |
| :--- | :--- | :--- |
| `%c` | `int` | Prints a single character. |
| `%s` | `char *` | Prints a string. |
| `%p` | `void *` | Prints the pointer address in lowercase hexadecimal format. |
| `%d` | `int` | Prints a signed decimal integer (base 10). |
| `%i` | `int` | Prints a signed integer (base 10). |
| `%u` | `unsigned int`| Prints an unsigned decimal integer (base 10). |
| `%x` | `unsigned int`| Prints a number in lowercase hexadecimal (base 16). |
| `%X` | `unsigned int`| Prints a number in uppercase hexadecimal (base 16). |
| `%%` | *(None)* | Prints a literal percent sign. |

The function must return the total number of characters printed, just like the original `printf()`.

---

## Key Learning Outcomes

* **Variadic Functions:** Gained mastery over the `<stdarg.h>` library to handle a flexible number and type of function arguments.
* **Modular Design:** Developed a highly modular and extensible codebase, where each format specifier (`%c`, `%s`, `%d`, etc.) is handled by a dedicated helper function. This design pattern is critical for easily adding new features (like flags, width, and precision) in the bonus part.
* **Base Conversion Logic:** Implemented custom logic for converting numerical types (`int`, `unsigned int`, `void *`) into their string representations in decimal, and both lowercase and uppercase hexadecimal bases.
* **Code Reusability:** Successfully integrated and utilized the helper functions from the `Libft` project (e.g., `ft_putchar_fd`, `ft_putstr_fd`).
