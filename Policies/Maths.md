Application Programming Interface for minor releases
============================================

![api](https://github.com/TheProdigyLeague/kill_consumer/assets/30985576/3d83777a-4932-44c4-b063-1d65bc1775c8)


The public API of the OpenSSL libraries is defined as functions, macros, data structure declarations, typedefs, and data variables in header files in the include/openssl subdirectory of the source tree and include/openssl subdirectory of the build tree.

No changes to existing public API functions and data are permitted. This includes, but is not limited to:

constification of arguments;
changing void returns to int returns;
changing a macro to a function and
corrections of spelling.
Only API additions are allowed in minor releases.

Although the changes as listed above might be regarded as ABI compatible, they cause various possible breakage when building applications depending on these APIs and thus they are not allowed in minor releases.

If necessary, a new API call can be added to implement the required changes in minor releases.
***
Policy for Accepting Assembler Optimisations
============================================

New assembler optimisations for any algorithm having a C based implementation in
any provider are always acceptable (subject to standard review procedures) for
all platforms in the master branch.

New assembler optimisations are never acceptable for any platform or provider in
a [stable release] branch.

Updates to existing assembler optimistations in a stable release branch are only
acceptable where such updates would be allowed under the
[stable release update policy].

Where assembler optimisations are acceptable they should be implemented using
[perlasm].

[perlasm]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#perlasm
[stable release]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#stable-release
[stable release update policy]: https://github.com/openssl/technical-policies/blob/master/policies/stable-release-updates.md

***
Branch Policy
=============

The openssl repository contains the following maintained branches:

### The default development branch

- Any type (bug fix, feature, refactoring, ...) of pull requests is allowed.
- The development of the next minor or major release happens there.
  API/ABI breaking changes are allowed on this branch only if the next
  release will be a major release.
- Any changes merged to this branch must be ported to the future major
  and future minor branches if they are applicable. This can be done by
  directly cherry-picking the changes when merging if there are no conflicts.
  By this we must ensure that no features or bug fixes are unintentionally
  lost in future major or minor releases.

### The supported release branches

- The development of the next patch releases of supported stable releases
  happens there.
- According to [stable release update policy] only bug fixes and
  documentation changes are allowed.
- By exception given by OMC also other types of pull requests can be merged.
- Bug fix and documentation pull requests must be always merged to the
  latest branch where the bug or documentation deficiency is present including
  the future major and minor branches.
  It can be then merged (backported or directly cherry-picked) to all
  older branches where the deficiency is present.

### A future major branch

- The development of a future major release happens there. Implicitly it
  means that any API/ABI breaking changes are allowed but OMC can (and
  usually will) limit the extent of the breakage allowed.
- Major features are allowed. Examples of a major feature: A completely
  new implementation of a protocol. New API for pluggable crypto modules.
- Major refactoring is allowed. Examples of major refactoring: Splitting
  libcrypto into multiple hierarchically dependent libraries.
- There might be no future major branch if the currently developed release
  is a major release and there are no changes accepted for a future major
  release yet.
- All changes specifically targetting this branch instead of the default
  development branch must be approved by OTC by consensus during
  a meeting or a formal vote.

### A future minor branch

- The development of the minor release that is supposed to be released
  after the release currently being developed at the default development branch
  happens there.
- No API/ABI breaking changes are allowed.
- No major features are allowed unless explicitly acked by OMC as targeted for
  the minor release.
- No major refactoring is allowed.
- Any changes (features, bug-fixes, documentation, ...) done on the future
  minor branch must be ported or directly cherry-picked to the future major
  branch if applicable.
- Exceptions are possible for example when we are removing deprecated
  functionality in the future major branch.
- There might be no future minor branch when the expected future release would
  be a major release or there are no changes accepted for a future minor
  release yet.
- All changes specifically targetting this branch instead of the default
  development branch must be approved by OTC by consensus during
  a meeting or a formal vote.

Branch and tag naming
---------------------

The branch where the development of the next release is happening is called
`openssl-x.y` where `x` is the current major version number and `y` is the
version number of the release being developed. This is the default branch
of the repository.

The existing stable release branches are also named `openssl-x.y`.

As a legacy exception to the rule above, the branch where the development of
OpenSSL-1.1.1 fix releases is happening is called `OpenSSL_1_1_1-stable`.

Future-major: The branch where the development of the future major release is
happening is called `openssl-x.0` where `x` is the next major version number.

Future-minor: The branch where the development of a future minor release is
happening is called `openssl-x.y` where `x` is the current major version number
and `y` is the version number of a version that will be released after the
version currently developed at the default development branch.

Release tags: The releases are tagged with tags named `openssl-x.y.z` for stable
patch releases, `openssl-x.y.0-alphaN` for alpha releases, and
`openssl-x.y.0-betaN` for beta releases. As a legacy exception the fix releases
of OpenSSL-1.1.1 are named `OpenSSL_1_1_1<fix-letter(s)>`.

Branch creation
---------------

The exact times when the future major and minor branches are created are
undefined by the policy as that is an OMC responsibility to decide.

[stable release update policy]: https://github.com/openssl/technical-policies/blob/master/policies/stable-release-updates.md

***
# OpenSSL coding style

This document describes the coding style for the OpenSSL project. It is
derived from the [Linux kernel coding style][1].

This guide is not distributed as part of OpenSSL itself. Since it is
derived from the Linux Kernel Coding Style, it is distributed under the
terms of the [kernel license][2].

Coding style is all about readability and maintainability using commonly
available tools. OpenSSL coding style is simple. Avoid tricky expressions.

## Chapter 1: Indentation

Indentation is four space characters. Do not use the tab character.

Pre-processor directives use one space for indents:

```c
    #if
    # define
    #else
    # define
    #endif
```

## Chapter 2: Breaking long lines and strings

Don't put multiple statements, or assignments, on a single line.

```c
    if (condition) do_this();
    do_something_everytime();
```

The limit on the length of lines is _80_ columns. Statements longer
than _80_ columns must be broken into sensible chunks, unless exceeding
_80_ columns significantly increases readability and does not hide
information. Descendants are always substantially shorter than the parent
and are placed substantially to the right. The same applies to function
headers with a long argument list. Never break user-visible strings,
however, because that breaks the ability to grep for them.

## Chapter 3: Placing Braces and Spaces

The other issue that always comes up in C styling is the placement
of braces. Unlike the indent size, there are few technical reasons to
choose one placement strategy over the other, but the preferred way,
following Kernighan and Ritchie, is to put the opening brace last on the
line, and the closing brace first:

```c
    if (x is true) {
        we do y
    }
```

This applies to all non-function statement blocks (`if`, `switch`, `for`,
`while`, `do`):

```c
    switch (suffix) {
    case 'G':
    case 'g':
        mem <<= 30;
        break;
    case 'M':
    case 'm':
        mem <<= 20;
        break;
    case 'K':
    case 'k':
        mem <<= 10;
        /* fall through */
    default:
        break;
    }
```

Note, from the above example, that the way to indent a switch statement
is to align the switch and its subordinate case labels in the same column
instead of _double-indenting_ the case bodies.

There is one special case, however. Functions have the
opening brace at the beginning of the next line:

```c
    int function(int x)
    {
        body of function
    }
```

Note that the closing brace is empty on a line of its own, __except__ in the
cases where it is followed by a continuation of the same statement, such
as a `while` in a do-statement or an `else` in an if-statement, like this:

```c
    do {
        ...
    } while (condition);
```

and

```c
    if (x == y) {
        ...
    } else if (x > y) {
        ...
    } else {
        ...
    }
```

In addition to being consistent with K&R, note that that this brace-placement
also minimizes the number of empty (or almost empty) lines. Since the
supply of new-lines on your screen is not a renewable resource (think
25-line terminal screens here), you have more empty lines to put comments on.

Do not unnecessarily use braces around a single statement:

```c
    if (condition)
        action();
```

and

```c
    if (condition)
        do_this();
    else
        do_that();
```

If one of the branches is a compound statement, then use braces on both parts:

```c
    if (condition) {
        do_this();
        do_that();
    } else {
        otherwise();
    }
```

Nested compound statements should often have braces for clarity, particularly
to avoid the dangling-else problem:

```c
    if (condition) {
        do_this();
        if (anothertest)
            do_that();
    } else {
        otherwise();
    }
```

### Chapter 3.1: Spaces

OpenSSL style for use of spaces depends (mostly) on whether the name is
a function or keyword. Use a space after most keywords:

```c
    if, switch, case, for, do, while, return
```

Do not use a space after `sizeof`, `typeof`, `alignof`, or `__attribute__`.
They look somewhat like functions and should have parentheses
in OpenSSL, although they are not required by the language. For `sizeof`,
use a variable when at all possible, to ensure that type changes are
properly reflected:

```c
    SOMETYPE *p = OPENSSL_malloc(sizeof(*p) * num_of_elements);
```

Do not add spaces around the inside of parenthesized expressions.
This example is wrong:

```c
    s = sizeof( struct file );
```

When declaring pointer data or a function that returns a pointer type,
the asterisk goes next to the data or function name, and not the type:

```c
    char *openssl_banner;
    unsigned long long memparse(char *ptr, char **retptr);
    char *match_strdup(substring_t *s);
```

Use one space on either side of binary and ternary operators,
such as this partial list:

```c
    =  +  -  <  >  *  /  %  |  &  ^  <=  >=  ==  !=  ?  : +=
```

Put a space after commas
and after semicolons in `for` statements, but not in `for (;;)`.

Do not put a space after unary operators:

```c
    &  *  +  -  ~  !  defined
```

Do not put a space before the postfix increment and decrement unary
operators or after the prefix increment and decrement unary operators:

```c
    foo++
    --bar
```

Do not put a space around the `.` and `->` structure member operators:

```c
    foo.bar
    foo->bar
```

Do not use multiple consecutive spaces except in comments,
for indentation, and for multi-line alignment of definitions, e.g.:
```c
#define FOO_INVALID  -1   /* invalid or inconsistent arguments */
#define FOO_INTERNAL 0    /* Internal error, most likely malloc */
#define FOO_OK       1    /* success */
#define FOO_GREAT    100  /* some specific outcome */
```

Do not leave trailing whitespace at the ends of lines. Some editors with
_smart_ indentation will insert whitespace at the beginning of new lines
as appropriate, so you can start typing the next line of code right away.
But they may not remove that whitespace if you leave a blank line, however,
and you end up with lines containing trailing, or nothing but, whitespace.

Git will warn you about patches that introduce trailing whitespace, and
can optionally strip the trailing whitespace; however, if applying
a series of patches, this may make later patches in the series fail by
changing their context lines.

Avoid empty lines at the beginning or at the end of a file.

Avoid multiple empty lines in a row.

## Chapter 4: Naming

C is a Spartan language, and so should your naming be.

Local variable names should be short, and to the point. If you have
some random integer loop counter, it should probably be called `i` or `j`.

Avoid single-letter names when they can be visually confusing,
such as `I` and `O`.
Avoid other single-letter names unless they are telling in the given context.
For instance, `m` for modulus and `s` for SSL pointers are fine.

Use simple variable names like `tmp` and `name`
as long as they are non-ambiguous in the given context.

If you are afraid that someone might mix up your local variable names,
perhaps the function is too long;
see the [chapter on functions](#chapter-6-functions).

Global variables (to be used only if you REALLY need them) need to
have descriptive names, as do global functions. If you have a function
that counts the number of active users, you should call that
_count_active_users()_ or similar, you should NOT call it _cntusr()_.

For getter functions returning a pointer
and functions setting a pointer given as a parameter,
use names containing `get0_` or `get1_` (rather than `get_`)
or `set0_` or `set1_` (rather than `set_`)
or `push0_` or `push1_` (rather than `push_`)
to indicate whether the structure referred to by the pointer remains as it is
or it is duplicated/up-ref'ed such that an additional `free()` will be needed.

Use lowercase prefix like `ossl_` for internal symbols
unless they are `static` (i.e., local to the source file).

Use uppercase prefix like `EVP_` or `OSSL_CMP_` for public (API) symbols.

Do not encode the type into a name (so-called Hungarian notation, e.g., `int iAge`).

Align names to terms and wording used in standards and RFCs.

Avoid mixed-case unless needed by other rules.
Especially never use `FirstCharacterUpperCase`.
For instance, use `EVP_PKEY_do_something` rather than `EVP_DigestDoSomething`.

Make sure that names do not contain spelling errors.

## Chapter 5: Typedefs

OpenSSL uses typedef's extensively. For structures, they are all uppercase
and are usually declared like this:

```c
    typedef struct name_st NAME;
```

For examples, look in [types.h][7], but note that there are many exceptions
such as BN_CTX. Typedef'd enum is used much less often and there is no
convention, so consider not using a typedef. When doing that, the enum
name should be lowercase and the values (mostly) uppercase.  Note that enum
arguments to public functions are not permitted.

The ASN.1 structures are an exception to this. The rationale is that if
a structure (and its fields) is already defined in a standard it's more
convenient to use a similar name. For example, in the CMS code, a CMS_
prefix is used so ContentInfo becomes CMS_ContentInfo, RecipientInfo
becomes CMS_RecipientInfo etc. Some older code uses an all uppercase
name instead. For example, RecipientInfo for the PKCS#7 code uses
PKCS7_RECIP_INFO.

Be careful about common names which might cause conflicts. For example,
Windows headers use X509 and X590_NAME. Consider using a prefix, as with
CMS_ContentInfo, if the name is common or generic. Of course, you often
don't find out until the code is ported to other platforms.

A final word on struct's. OpenSSL has historically made all struct
definitions public; this has caused problems with maintaining binary
compatibility and adding features. Our stated direction is to have struct's
be opaque and only expose pointers in the API. The actual struct definition
should be defined in a local header file that is not exported.

## Chapter 6: Functions

Ideally, functions should be short and sweet, and do just one thing.
A rule of thumb is that they should fit on one or two screenfuls of text
(25 lines as we all know), and do one thing and do that well.

The maximum length of a function is often inversely proportional to the
complexity and indentation level of that function. So, if you have a
conceptually simple function that is just one long (but simple) switch
statement, where you have to do lots of small things for a lot of different
cases, it's okay to have a longer function.

If you have a complex function, however, consider using helper functions
with descriptive names. You can ask the compiler to in-line them if you
think it's performance-critical, and it will probably do a better job of
it than you would have done.

Another measure of complexity is the number of local variables. If there are
more than five to 10, consider splitting it into smaller pieces. A human
brain can generally easily keep track of about seven different things;
anything more and it gets confused. Often things which are simple and
clear now are much less obvious two weeks from now, or to someone else.
An exception to this is the command-line applications which support many
options.

In source files, separate functions with one blank line.

In function prototypes, include parameter names with their data types.
Although this is not required by the C language, it is preferred in OpenSSL
because it is a simple way to add valuable information for the reader.
The name in the prototype declaration should match the name in the function
definition.

Separate local variable declarations and subsequent statements by an empty line.

Do not mix local variable declarations and statements.

### Chapter 6.1: Checking function arguments

A _public_ function should verify that its arguments are sensible.
This includes, but is not limited to, verifying that:
- non-optional pointer arguments are not NULL and
- numeric arguments are within expected ranges.

Where an argument is not sensible, an error should be returned.

### Chapter 6.2: Extending existing functions

From time to time it is necessary to extend an existing function. Typically this
will mean adding additional arguments, but it may also include removal of some.

Where an extended function should be added the original function should be kept
and a new version created with the same name and an `_ex` suffix. For example,
the `RAND_bytes` function has an extended form called `RAND_bytes_ex`.

Where an extended version of a function already exists and a second extended
version needs to be created then it should have an `_ex2` suffix, and so on for
further extensions.

When an extended version of a function is created the order of existing
parameters from the original function should be retained. However new parameters
may be inserted at any point (they do not have to be at the end), and no longer
required parameters may be removed.

## Chapter 7: Centralized exiting of functions

The goto statement comes in handy when a function exits from multiple
locations and some common work such as cleanup has to be done. If there
is no cleanup needed then just return directly. The rationale for this is
as follows:

- Unconditional statements are easier to understand and follow
- It can reduce excessive control structures and nesting
- It avoids errors caused by failing to update multiple exit points when the code is modified
- It saves the compiler work to optimize redundant code away ;)

For example:

```c
    int fun(int a)
    {
        int result = 0;
        char *buffer = OPENSSL_malloc(SIZE);

        if (buffer == NULL)
            return -1;

        if (condition1) {
            while (loop1) {
                ...
            }
            result = 1;
            goto out;
        }
        ...
    out:
        OPENSSL_free(buffer);
        return result;
    }
```

## Chapter 8: Commenting

Use the classic `/* ... */` comment markers.  Don't use `// ...` markers.

Place comments above or to the right of the code they refer to.
Comments referring to the code line after
should be indented equally to that code line.

Comments are good, but there is also a danger of over-commenting. NEVER try
to explain HOW your code works in a comment. It is much better to write
the code so that it is obvious, and it's a waste of time to explain badly
written code. You want your comments to tell WHAT your code does, not HOW.

The preferred style for long (multi-line) comments is:

```c
    /*-
     * This is the preferred style for multi-line
     * comments in the OpenSSL source code.
     * Please use it consistently.
     *
     * Description:  A column of asterisks on the left side,
     * with beginning and ending almost-blank lines.
     */
```

Note the initial hyphen to prevent indent from modifying the comment.
Use this if the comment has particular formatting that must be preserved.

It's also important to comment data, whether they are basic types or
derived types. To this end, use just one data declaration per line (no
commas for multiple data declarations). This leaves you room for a small
comment on each item, explaining its use.

## Chapter 9: Macros and Enums

Names of macros defining constants and labels in enums are in uppercase:

```c
    #define CONSTANT 0x12345
```

Enums are preferred when defining several related constants.  Note, however,
that enum arguments to public functions are not permitted.

Macro names should be in uppercase, but macros resembling functions may
be written in lower case. Generally, inline functions are preferable to
macros resembling functions.

Macros with multiple statements should be enclosed in a do - while block:

```c
    #define macrofun(a, b, c)   \
        do {                    \
            if (a == 5)         \
                do_this(b, c);  \
        } while (0)
```

Do not write macros that affect control flow:

```c
    #define FOO(x)                 \
        do {                       \
            if (blah(x) < 0)       \
                return -EBUGGERED; \
        } while(0)
```

Do not write macros that depend on having a local variable with a magic name:

```c
    #define FOO(val) bar(index, val)
```

It is confusing to the reader and is prone to breakage from seemingly
innocent changes.

Do not write macros that are l-values:

```c
    FOO(x) = y
```

This will cause problems if, e.g., FOO becomes an inline function.

Be careful of precedence.
Macros defining an expression must enclose the expression in parentheses
unless the expression is a literal or a function application:

```c
    #define SOME_LITERAL 0x4000
    #define CONSTEXP (SOME_LITERAL | 3)
    #define CONSTFUN foo(0, CONSTEXP)
```

Beware of similar issues with macros using parameters.
Put parentheses around uses of macro arguments
unless they are passed on as-is to a further macro or function.
For example,
```c
#define MACRO(a,b) ((a) * func(a, b))
```

The [GNU cpp manual][8] deals with macros exhaustively.

## Chapter 10: Allocating memory

OpenSSL provides many general purpose memory utilities, including, but
not limited to: `OPENSSL_malloc()`, `OPENSSL_zalloc()`, `OPENSSL_realloc()`,
`OPENSSL_memdup()`, `OPENSSL_strdup()` and `OPENSSL_free()`.
Please refer to the API documentation for further information about them.

## Chapter 11: Function return values and names

Functions can return values of many different kinds, and one of the
most common is a value indicating whether the function succeeded or
failed. Usually this is:

* 1: success
* 0: failure

Sometimes an additional value is used:

* -1: something bad (e.g., internal error or memory allocation failure)

Other APIs use the following pattern:

* \>= 1: success, with value returning additional information
* <= 0: failure with return value indicating why things failed

Sometimes a return value of -1 can mean "should retry" (e.g., BIO, SSL, et al).

Functions whose return value is the actual result of a computation,
rather than an indication of whether the computation succeeded, are not
subject to these rules. Generally they indicate failure by returning some
out-of-range result. The simplest example is functions that return pointers;
they return NULL to report failure.

## Chapter 12: Editor modelines

Some editors can interpret configuration information embedded in source
files, indicated with special markers. For example, emacs interprets
lines marked like this:

    -*- mode: c -*-

Or like this:

```c
    /*
    Local Variables:
    compile-command: "gcc -DMAGIC_DEBUG_FLAG foo.c"
    End:
    */
```

Vim interprets markers that look like this:

```c
    /* vim:set sw=8 noet */
```

Do not include any of these in source files. People have their own personal
editor configurations, and your source files should not override them.
This includes markers for indentation and mode configuration. People may
use their own custom mode, or may have some other magic method for making
indentation work correctly.

## Chapter 13: Processor-specific code

In OpenSSL's case the only reason to resort to processor-specific code
is for performance. As it still exists in a general platform-independent
algorithm context, it always has to be backed up by a neutral pure C one.
This implies certain limitations. The most common way to resolve this
conflict is to opt for short inline assembly function-like snippets,
customarily implemented as macros, so that they can be easily interchanged
with other platform-specific or neutral code. As with any macro, try to
implement it as single expression.

You may need to mark your `asm` statement as `volatile`, to prevent GCC from
removing it if GCC doesn't notice any side effects. You don't always need
to do so, though, and doing so unnecessarily can limit optimization.

When writing a single inline assembly statement containing multiple
instructions, put each instruction on a separate line in a separate quoted
string, and end each string except the last with `\n\t` to properly indent
the next instruction in the assembly output:

```c
        asm ("magic %reg1, #42\n\t"
             "more_magic %reg2, %reg3"
             : /* outputs */ : /* inputs */ : /* clobbers */);
```

Large, non-trivial assembly functions go in pure assembly modules, with
corresponding C prototypes defined in C. The preferred way to implement this
is so-called "perlasm": instead of writing real .s file, you write a perl
script that generates one. This allows use symbolic names for variables
(register as well as locals allocated on stack) that are independent on
specific assembler. It simplifies implementation of recurring instruction
sequences with regular permutation of inputs. By adhering to specific
coding rules, perlasm is also used to support multiple ABIs and assemblers,
see [crypto/perlasm/x86_64-xlate.pl][9] for an example.

Another option for processor-specific (primarily SIMD) capabilities is
called _compiler intrinsics_. We avoid this, because it's not very much
less complicated than coding pure assembly, and it doesn't provide the
same performance guarantee across different micro-architecture. Nor is
it portable enough to meet our multi-platform support goals.

## Chapter 14: Portability

To maximise portability the version of C defined in ISO/IEC 9899:1990
should be used. This is more commonly referred to as C90. ISO/IEC 9899:1999
(also known as C99) is not supported on some platforms that OpenSSL is
used on and therefore should be avoided.

## Chapter 15: Expressions

Avoid needless parentheses as far as reasonable.
For example, do not write
```c
    if ((p == NULL) && (!f(((2 * x) + y) == (z++))))
```
but
```c
    if (p == NULL && !f(2 * x + y == z++)).
```

For clarity, always put parentheses
when mixing the logical `&&` and `||` operators,
mixing comparison operators like `<=` and `==`,
or mixing bitwise operators like `&` and `|`.
For example,
```c
    if ((a && b) || c)
    if ((a <= b) == ((c >= d) != (e < f)))
    x = (a & b) ^ (c | d)
```

Regarding parentheses in macro definitions see the
[chapter on macros](#chapter-9-macros-and-enums).

In comparisons with constants (including `NULL` and other constant macros)
place the constant on the right-hand side of the comparison operator.
For example,
```c
    while (i++ < 10 && p != NULL)
```

Do not use implicit checks for
numbers (not) being `0` or pointers (not) being `NULL`.
For example, do not write
```c
    if (i)
    if (!(x & MASK))
    if (!strcmp(a, "FOO"))
    if (!(p = BN_new()))
```
but do this instead:
```c
    if (i != 0)
    if ((x & MASK) == 0)
    if (strcmp(a, "FOO") == 0)
    if ((p = BN_new()) == NULL)
```
Boolean values shall be used directly as usual, e.g.,
```c
if (check(x) && !success(y))
```
Note: Many functions can return `0` or a negative value on error
and the Boolean forms need to be used with care.

If you need to break an expression into multiple lines,
make the line break before an operator, not after.
It is preferred that such a line break is made
before as low priority an operator as possible.
Examples:

* not this:
  ```c
  if (somewhat_long_function_name(foo) == 1 && a_long_variable_name
      == 2)
  ```
  but rather:
  ```c
  if (somewhat_long_function_name(foo) == 1
      && a_long_variable_name == 2)
  ```

* This is, however, still ok:
  ```c
  if (this_thing->this_freakishly_super_long_name(somewhat_long_name, 3)
      == PRETTY_DARN_LONG_MACRO_NAME)
  ```

When appearing at the beginning of a line,
operators can, but do not have to, get an extra indentation (+ 4 characters).
For example,
```c
    if (long_condition_expression_1
            && condition_expression_2) {
        statement_1;
        statement_2;
    }
```

## Chapter 16: Asserts

We have 3 kind of asserts. The behaviour depends on being a debug or release build:

<table>
<tr><th>Function</th>
    <th>failure release</th>
    <th>failure debug</th>
    <th>success release</th>
    <th>success debug</th>
</tr>
<tr><td>assert</td>
    <td>not evaluated</td>
    <td>abort</td>
    <td>not evaluated</td>
    <td>nothing</td>
</tr>
<tr><td>ossl_assert</td>
    <td>returns 0</td>
    <td>abort</td>
    <td>returns 1</td>
    <td>returns 1</td>
</tr>
<tr><td>OPENSSL_assert</td>
    <td>abort</td>
    <td>abort</td>
    <td>nothing</td>
    <td>nothing</td>
</tr>
</table>

Use OPENSSL_assert() **only** in the following cases:
- In the libraries when the global state of the software is corrupted and there is no way to recover it
- In applications, test programs and fuzzers

Use ossl_assert() in the libraries when the state can be recovered and an error can be returned. Example code:
```c
    if (!ossl_assert(!should_not_happen)) {
        /* push internal error onto error stack */
        return BAD;
    }
```

Use assert() in libraries when no error can be returned.

## Chapter 17: References

[The C Programming Language][3], Second Edition
by Brian W. Kernighan and Dennis M. Ritchie.
Prentice Hall, Inc., 1988.
ISBN 0-13-110362-8 (paperback), 0-13-110370-9 (hardback).

[The Practice of Programming][4]
by Brian W. Kernighan and Rob Pike.
Addison-Wesley, Inc., 1999.
ISBN 0-201-61586-X.

[GNU manuals][5] - we're in compliance with K&R and this text - for cpp, gcc,
gcc internals and indent.

[WG14][6] is the international standardization working group for the programming
language C.

[1]: <https://www.kernel.org/doc/Documentation/process/coding-style.rst> "Linux Kernel Coding Style"
[2]: <https://www.kernel.org/pub/linux/kernel/COPYING> "Linux Kernel License"
[3]: <https://openlibrary.org/works/OL4617640W/The_C_Programming_Language> "The C Programming Language, Second Edition"
[4]: <https://openlibrary.org/works/OL15333872W/The_Practice_of_Programming_(Addison-Wesley_Professional_Computing_Series)> "The Practice of Programming"
[5]: <https://www.gnu.org/manual/> "GNU manuals"
[6]: <http://www.open-std.org/JTC1/SC22/WG14/> "International standardization working group for the programming language C"
[7]: <https://github.com/openssl/openssl/blob/master/include/openssl/types.h> "include/openssl/types.h"
[8]: <https://gcc.gnu.org/onlinedocs/> "GCC online documentation"
[9]: <https://github.com/openssl/openssl/blob/master/crypto/perlasm/x86_64-xlate.pl> "crypto/perlasm/x86_64-xlate.pl"

***
Design Process Policy
=====================

Objectives
----------

The objective of the design process is to increase the quality of the software
engineering process. The production of design documents confers the following
benefits:

  - Prior to implementation, the present understanding of the problem domain is
    documented in a readily accessible fashion. The understanding of other
    OpenSSL contributors is enhanced, as is their ability to identify any
    potential issues in the design, or to make related code contributions.

  - After implementation, the design document serves as documentation of
    the architectural and design decisions and rationale which served as the
    basis for the implementation of the relevant functionality. This is
    beneficial both to contributors who wish to understand the relevant code,
    or evolve the implementation, but also to contributors who wish to implement
    related functionality or understand non-obvious rationales behind given
    design decisions.

It is recognised that designs will often necessarily change once implementation
begins. In the majority of cases, the understanding of the problem domain will
evolve and improve after implementation begins and this will indicate further
changes to the design. This is an iterative process of progressive refinement.
It is an explicit objective of this policy to support and encourage this
agile-style process, as opposed to a waterfall-style process in which designs
must be approved and finalised prior to implementation.

This policy adopts a graded system of review in which the degree of formal
approval by the OTC which a design must undergo is proportionate to the scope
and risks of the design. For example, a design which involves new or evolved
public APIs may require a greater amount of scrutiny, whereas a purely internal
design may require that the OTC simply be notified of the design document and
invited to comment, with implicit approval in the absence of objections.

Requirement for Design Documents
--------------------------------

A design document is required for any proposed enhancement which adds
significant new APIs or non-trivially evolves or modifies existing APIs.

For any other kind of proposed enhancement, a design document should be created
if it incorporates design decisions or aspects significant enough to warrant
one. For example, if an enhancement adds a new internal module with clearly
delineated boundaries with a documented internal API which can be consumed by
other code internal to OpenSSL, a design document is desirable. This example is
not exhaustive. The proposer may use their discretion in determining whether a
design document is desirable, but any OTC member may require that a design
document be produced.

Contents of Design Documents
----------------------------

In general, where produced, a design document should include discussion of:

- Requirements and assumptions, in particular:

    - the requirements that the design is seeking to meet;

    - anything which is expressly not a requirement;

    - the origins or underlying motivations of those requirements (or
      non-requirements) in turn (for example, do the requirements originate from the
      OMC or are they themselves a product of other technical requirements?);

    - significant assumptions or limitations of scope being made as part of the
      design (which might cause a design to become suboptimal or inapplicable if
      those assumptions cease to be true) as a result of the input requirements.

- The available solution space; discuss the various possible solutions and
  provide narrative discussion of their relative merits, and the reasoning
  for any preferences. Which solutions are preferable and why? Which solutions
  are ruled out based on the requirements and why?

- The proposed design. Alternatively, a design document may propose a couple
  of possible designs (for example, if it is not yet clear which is preferable,
  or if multiple essentially independent designs will be needed to cover all use
  cases). If multiple proposals are present, they should be clearly labeled
  in different sections so they can be referred to easily for discussion.

- What the intended strategy is for how any new APIs being introduced can be
  effectively maintained, evolved and extended in the future, if at all.

- In some cases, it may be appropriate to offer examples of motivating use cases
  for the design (given in prose) or examples of intended exemplary usage of an
  API, given as rough code fragments or pseudocode.

- More generally, it is sometimes also useful to provide exposition for the
  motivations behind a design by offering a Q&A section posing design questions
  and their answers with rationale. This has the advantage of documenting the
  historical design decisions which were made and why, and makes it clear when a
  significant decision is being made. Some questions may be left unanswered
  in a design document which is not yet complete, which serves to document
  design questions which have yet to be resolved.

This is not an exhaustive list and design documents will obviously contain other
elements, such as discussion of the design itself.

Based on the above, the recommended template for a design document is as
follows:

    Requirements/Problem Statement
    Problem Discussion
    Proposal 1
        API Maintenance Considerations
    [...Proposal 2, if applicable, etc...]
        [...API Maintenance Considerations...]
    Examples
        Motivating Use Cases
        Usage Examples
    Q&A

This template is intended as a rough starting point only. Not all of its
sections will be relevant to all design documents, and design document authors
can and should deviate from this structure where this leads to a more
comprehensible or useful document.

Levels of Scrutiny
------------------

There are three levels of scrutiny which can be applied to a design, listed
below in ascending order of severity:

 - Notify
 - Present
 - Approve

These levels work as follows:

 - At the **Notify** level, the OTC is notified of a new design
   when it is available for review, via an email to the openssl-project mailing list.
   OTC members and committers and the public can review and comment on the design.
   A minimum waiting time of one week after the notification is made applies to
   ensure OTC members have the opportunity to review the design.

   The notification does not need to be made by the author of the design
   document.

 - At the **Present** level, the OTC is notified of a new design
   in the same way that it is at the Notify level. The same minimum waiting time
   applies. The design is also introduced and explained in a presentation given
   to the OTC in a meeting of the OTC. The OTC has opportunities to ask
   questions and raise concerns at this meeting. This presentation may be given
   by the author of the design but need not be.

 - At the **Approve** level, the OTC must explicitly approve the design
   by making a decision as the OTC. The OTC should be notified of a
   new design in the same way they are notified at the Notify level.
   A presentation to the OTC may be made but is not required.

When a design is produced, it should be submitted to the OpenSSL repository as a
PR. It should be determined which level of scrutiny is appropriate according to
this policy and this should be noted in the PR. Any applicable actions (such as
notifying the OTC via the openssl-project list) should be carried out once the
design is ready for review.

Any OTC member may object to the processing of a design at a given level of
scrutiny and require that a higher level be used.

A proposer may choose to use a higher level of scrutiny than is required.

Selecting a Level
-----------------

To determine the level of scrutiny which must be applied to a design by default,
follow the following process:

  - Any design which proposes to create significant new public APIs, or
    non-trivially evolve or modify existing public APIs, must use at least the
    Present level of scrutiny.

  - Any other design may use the Notify level of scrutiny.

Checklists
----------

### Checklist for the Notify Level

  - Design document published as a PR on GitHub
  - OTC notified and invited to comment or object via an email to
    openssl-project list
  - At least one week has passed from OTC notification

### Checklist for the Present Level

  - Design document published as a PR on GitHub
  - OTC notified and invited to comment or object via an email to
    openssl-project list
  - Presentation given to a quorate OTC meeting by the design's proposer, and
    OTC has had opportunity to ask questions and discuss the proposal
  - At least one week has passed from OTC notification

### Checklist for the Approve Level

  - Design document published as a PR on GitHub
  - OTC makes a decision approving the design. The decision is made according to
    standard OTC policies.

Implementation
--------------

It is not required to wait for a design document to be approved and merged
before beginning implementation. Implementation can begin immediately. This
facilitates an agile process and helps to improve the design document, as
implementation will often lead to an improved understanding of the problem
domain, leading in turn to an improved design document.

A design document PR, or a PR implementing said design, should not be merged
until the relevant requirements for the level of scrutiny used have been
satisfied. It is permissible for a design document and an implementation to be
part of the same PR.

Revisions to Pending Designs
----------------------------

Where changes to a design document need to be made (for example, due to an
evolved understanding of the problem domain arising from an implementation in
progress), if the design document has already been merged, a new PR should be
raised and this will go through the normal process described above.

If the design document has not yet merged:

  - if the Notify or Present level of scrutiny is being used, it may be changed
    by the proposer freely. Another notification to the openssl-project list may
    be made if the changes are deemed very major but is not required.

  - if the Approve level of scrutiny is being used, and the approval has already
    been finalised or a vote is ongoing, the design should not be changed and a
    new PR should be raised. The document may be changed freely if it has been
    decided that the Approve level of scrutiny is to be used but a vote has not
    yet opened.


***
# OpenSSL documentation policy

This document describes the code documentation and commenting
requirements for the OpenSSL project.

The project's documentation is all about making the libraries and tools
more accessible to our users and making the code more maintainable.
This policy applies to new submissions, existing code is below par and will
be gradually improved.

## Chapter 1: Command line commands and arguments

All new or modified arguments to the commands must be documented in the
`doc/man1` directory.  This documentation is in _POD_ format.

All new commands must be documented in the `doc/man1` directory.  This
documentation is in _POD_ format.

## Chapter 2: Public symbols in the libraries

All new public symbols must be documented in a _POD_ manual page in the
`doc/man3` directory.  This includes both macros and functions.

The allowed exceptions are:

- guard macros preventing a header file being included twice
- new OPENSSL_NO_DEPRECATED_ macros
- new symbols generated automatically via `make update` (errors, objects, etc)

## Chapter 3: Overviews, conventions, et al

Where additional user facing information is required, it should be
included in the `doc/man7` section.  This includes, but is not limited to:

- descriptions of data structures and their usage
- provider calls and call backs
- algorithm descriptions and parameters
- descriptions of architectural decisions

## <a name="fsgm"></a>Chapter 4: Internal functions, structures, globals and macros

Internal functions and macros are those defined in the `include/crypto`
and `include/internal` directories.

These should all be documented at the point of implementation.  A comment
describing their purpose and the input and output arguments and return value
for functions suffices.

For _trivial_ items, where their operation is obvious from their
implementation, the documentation requirement is not mandated.  The following
are generally representative of trivial items, however it is quite
possible for any of these to be non-trivial in specific instances and
therefore require documentation:

- OSSL_DISPATCH tables
- upref functions
- free functions
- simple getter/setter functions
- wrappers for other functions (a function that calls a more recent `_ex`
  variant or a group of functions that call a common internal routine)

For structures, each of the fields should be commented stating its
purpose.  Again, a _trivial_ exception applies where the purpose is
obvious.  Some representative examples:

- `OSSL_LIB_CTX *ctx;` where there is only one library context referenced in
  the structure.
- `struct *next;` in a linked list implementation.
- `CRYPTO_REF_COUNT refcnt;`

## Chapter 5: Static functions and globals and local structures and macros

These are functions, structures, globals and macros local to a specific
C file or defined for a single directory as part of a local .h file.

These should all be documented at the point of implementation.  Follow the
rules and exceptions listed [above](#fsgm).  In some cases slightly more
leniency with respect to _trivial_ can be tolerated.

## Chapter 6: Code comments

Comments in code should explain what the algorithm is doing and why.
It should not parrot the effect of each statement.  As the complexity of
the code increases, the size and detail of comments should also increase.

## Chapter 7: Assembly code

Assembly code should include a good description of the algorithm and
approach being used.  This should be followed by a performance comparison
and then the assembly code itself.  The assembly code should be well
commented, but it isn't necessary to comment every line.  A comment
describing each block of code suffices.

There are no _trivial_ exceptions for assembly code.

## Chapter 8: Configure options

New options added to the configuration scripts must be documented in the
`INSTALL.md` file.

## Chapter 9: Changes and news

Significant modifications should be documented in the [CHANGES] file.

Very significant features and changes should be documented in the [NEWS]
file.

In both cases, the added note should be short and to the point.

## Chapter 10: Automated sanity checking

The `make doc-nits` command should be run before submitting a pull
request and any problems it locates must be addressed.

## <a name="language"></a>Chapter 11: Language

The language used for documentation shall be _British English_.
In general the language, abbreviations, layout and formatting should also
correspond to the [LDP] guidelines.

## Chapter 12: Common sense

Comments in the code are to improve readability and comprehension.
Where the code is obvious, there is no need to include a comment.
However, common sense applies.  Always err in favour of including more
comments than less or none.  Code that you've just written that is
_obvious_ will not necessarily be to someone else two years later.


[CHANGES]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#changes
[NEWS]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#news
[LDP]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#ldp

***
Policy on Proposing Technical Policy Changes
============================================

This policy represents the way that any additions or changes to the
existing policies are proposed, edited, finalized, and approved.

The process for minor changes is described in the
[Minor Edits](#minor-edits) section.

Policy Change Proposal
----------------------

The policy changes or additions are submitted as pull requests in the
technical-policies repository on GitHub OpenSSL project. Anyone with
a GitHub account can submit a policy change proposal pull request.

Each policy is placed in an individual file in Markdown format in the
policies subdirectory.

Any policy change proposal can modify any number of policies as required.

Any policy change proposal SHOULD have a single topic.

The description of the pull request SHOULD provide an overview of the changes
and the reasons why the change is proposed.

After the pull request has been created the author MUST announce the policy
change proposal on the openssl-project mailing list.

The Review Process
---------------------

If the submitter is not a member of OTC, an OTC member is selected to watch
over the review process and propose the final approval vote.

Adjustments to the change proposal happen via the normal GitHub pull request
review interaction. The pull request MUST be opened for at least two weeks
after the initial announcement of the change proposal.

The OTC SHOULD discuss the proposal during a meeting.

The OTC SHOULD seek consensus when finalizing the policy change however
it is not an absolute requirement.

The review process is fully public in the sense that anyone can add
comments to the pull request and see comments made by others.

Withdrawal
----------

To withdraw the change the submitter of the pull request just closes the
pull request.

The Approval Process
--------------------

When there are no further changes proposed on the pull request and the
minimum time for which it must be open passes the pull request is marked
with the `Ready To Vote` label. The pull request is frozen for any changes
other than typo fixes or minor formatting changes after that.

The policy change is approved by means of a regular OTC vote. If the vote
passes, the policy change is approved, otherwise it is rejected.

Approval is marked by labelling the pull request with the `Accepted` label.

Rejection is marked by labelling the pull request with the `Rejected` label
and closing the pull request without merging.

If the policy change is approved, the pull request is merged to the
master branch of the technical-policies repository.

Minor Edits
-----------

Minor policy edits that do not change the meaning of the edited
policies do not require this voting process. Typical examples of such edits
are spelling, grammar, and formatting fixes.

These edits are done via pull requests that are approved by two OTC members
where neither of them is the author of the submission. The pull request
should be labelled with the `minor edit` label.

Approved submissions shall only be applied after a 24-hour delay from the
approval.

***
Release Requirements Policy
===========================

The OpenSSL project team creates the following 5 types of OpenSSL software
releases:

- [alpha] (pre-)releases
- [beta] (pre-)releases
- [major] releases
- [minor] releases
- [patch] releases

This policy defines the requirements on the state of a branch in the source
tree that must be met before a release from that branch can be done.

Alpha Pre-releases
------------------

As this is just a preview release for testing things that have been worked
on in the development branch, the requirements are minimal.

- The CI must pass on the tip of the development branch before the release
  commits were added to the tree.

Beta Pre-releases
-----------------

The API and ABI should be stable and the source code should be feature complete
by the first beta pre-release. The following release requirements apply to beta
pre-releases.

- [ ] The code is functionally complete in regards to the particular release
  objectives as set by OMC and OTC.
- [ ] There is no remaining refactoring required by OMC or OTC for the release.
- [ ] There are no remaining API changes required for the release.
  _This applies only to beta releases of a major release as API changes
  are not allowed on minor releases._
- [ ] There are no remaining API additions required for the release.
- [ ] All issues [triaged] as regressions on the development branch from which the
  release is to be done must have a milestone assigned.
  _Regressions are considered from the previous stable release or previous
  beta release._
- [ ] All issues or pull requests with the milestone for the beta release
  are closed.
- [ ] There are no outstanding untriaged Coverity issues.
- [ ] Coveralls coverage has not decreased overall from the previous release.
- [ ] The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- [ ] The tree must be frozen for at least 3 business days. No changes apart from
  regression or security fixes should be merged during the freeze.
- [ ] For 2 days before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- [ ] In case of the first beta release the OTC should explicitly approve
  that the source is ready for a release with a vote.

Major and Minor Releases
------------------------

As the release comes after the beta releases there is no need to repeat the
stability requirements as those should be held already by the beta releases.

- [ ] All issues [triaged] as regressions on the development branch from which the
  release is to be done must have a milestone assigned.
  _Regressions are considered from the previous stable release series._
- [ ] All issues or pull requests with the milestone for the release are closed.
- [ ] There are no outstanding untriaged Coverity issues.
- [ ] Coveralls coverage has not decreased overall from the previous release from
  the particular development branch.
- [ ] The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- [ ] The tree must be frozen for at least 7 days. No changes apart from regression
  or security fixes should be merged during the freeze.
- [ ] For 2 days before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- [ ] The OTC should explicitly approve that the source is ready for a release with
  a vote.

Patch Releases
--------------

The patch releases follow a similar process to major and minor releases with
some simplifications as they are much more frequent and the tree stability
requirements for the stable development branches should ensure there is
a minimum amount of regressions in between the patch releases.

- [ ] All issues [triaged] as regressions on the development branch from which the
  release is to be done must have a milestone assigned.
  _Regressions are considered from the previous minor, major or patch release
  from the development branch._
- [ ] All issues or pull requests with the milestone for the release are closed.
- [ ] The CI must pass on the tip of the development branch before the release
  commits are added to the tree, including the daily CI builds.
- [ ] The tree must be frozen for at least 3 business days. No changes apart from
  regression or security fixes should be merged during the freeze.
- [ ] For 2 days before the release there should be no changes to ensure the daily
  CI builds run on the development tree tip.
- [ ] Embargoed security fixes are excepted from the rule above as they cannot
  be merged to the public tree before the release is being prepared.

Triage Process
--------------

The issues and pull requests in GitHub must be assigned a `triaged: *` label by
an OTC member according to what is the type (feature, bug, documentation,
refactoring, ...) of the issue or pull request. When the triage happens for an
issue or pull request that is a bug/bug fix, it must be assessed whether the
bug is a regression or not.

In general regressions should be fixed as soon as possible, optimally before
the next release from the development tree is done. However sometimes that
might not be reasonably possible due to time, resource, or fix complexity
constraints.

In that case OTC should explicitly acknowledge that the regression is not to be
fixed before the release is done. That is done by assigning a milestone by
which the regression must be fixed and the `triaged: OTC evaluated` label.

The triage ideally happens as soon as possible, however the triage process can
sometimes be costly, so we aim to have issues triaged no later than 4 days
after they are reported.

Responsibilities
----------------

The OTC is responsible to ensure the releases conform to these requirements.
How exactly the OTC handles this responsibility is undefined here on purpose
except for the explicit votes required for the first beta release and the
major or minor releases.

For example the responsibility to follow the release requirements can be
delegated by the OTC to the person (or the team) preparing the release.

[alpha]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#alpha-release
[beta]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#beta-release
[major]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#major-release
[minor]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#minor-release
[patch]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#patch-release
[triaged]: #triage-process

***
Stable Release Updates Policy
=============================

This policy covers allowed changes on stable release branches.

Definitions
-----------

A **stable release** is a series beginning with a major or minor release that
is not a pre-release, and all its updates.

A **patch release** is an update within a stable release.

A **public interface** is any function, structure or macro declared in a public
header file.

A **bug fix** is a fix of functionality of the libraries, modules,
applications, or the build system that (all or any items might apply):

- makes the functionality conform with the existing end-user documentation
  where such a change does not break existing common usage
- makes the end-user documentation conform with the existing behavior of the
  software

A **bug fix** is also a fix for an unexpected behavior (not explicitly
documented in one way or another) of the software when such unexpected behavior
is a security vulnerability.

A **bug fix** is also a fix for an unexpected behavior of the following kinds
even if such behavior is not a security vulnerability:

- a memory leak
- a crash
- a hang/deadlock or a race condition
- an out of bounds read or write
- an uninitialized value read
- a memory use after free
- C language undefined behavior

A **bug fix** is also a build failure or test failure fix for platforms that
are noted as supported for the stated release.

A **bug fix** might also be a fix for an unexpected behavior (not explicitly
documented in one way or another) where the implementation does not conform to
existing public specifications that we claim to conform to. Where the
documentation explicitly contradicts the specifications the documented behavior
is what matters.

A **bug fix** is **not**:

- performance enhancement
- memory usage reduction
- replacement implementation of algorithms
- refactoring
- addressing deviations from the [coding style policy].

[coding style policy]: https://github.com/openssl/technical-policies/blob/master/policies/coding-style.md

An **end-user documentation** is:

- manual pages and other documentation in `doc` directory excluding the
  `doc/internal` directory
- various documentation files in the top-level directory
- demo code in `demos`

An **end-user documentation** is **not**:

- comments in the code (including public header files)
- internal documentation (doc/internal)

Changes allowed in stable releases
----------------------------------

No API or ABI breaking changes are allowed in a minor or patch release.

Only bug fixes, fixes for security issues, and end-user documentation
additions and fixes are allowed in stable releases.

The **addition** of new platforms to LTS branches is acceptable so long as the
required changes consist solely of **additions to configuration**.

A documentation addition allowed in stable releases is any addition to the
documentation that documents the existing behavior of the software. I.e., the
documentation additions in stable releases cannot add new API contract
constraints, or implicitly create new bugs in the software by documenting
behavior that is different from the existing behavior of the software.

Comment or whitespace fixes are allowed only as part of a bug fix to avoid
later merge conflicts.

New tests and test cases are allowed only as part of a bug fix.

Patch release commits are obviously allowed (updates to CHANGES.md, NEWS.md,
version, and copyright updates).

**Exceptions to this policy require OTC approval.**

***
Testing Policy
==============

This applies to all [stable] and development branches of the main code repository.

Within this policy _functional behaviour_ means what the system does, i.e.
given a set of inputs it will produce a set of outputs. This does not include
how the system does it. For example refactoring or performance improvements do
not affect _functional behaviour_.

Except where noted below:

- All Pull Requests adding new functionality to the applications, libraries,
  providers or engines must include suitable tests.
- All Pull Requests fixing a _functional behaviour_ defect in the applications,
  libraries, providers or engines must include a test for that defect.

Pull Requests that do not change the _functional behaviour_ of the applications,
libraries, providers or engines do not require tests to be added. For example
the following types of changes do not require tests:

- Changes to comments, formatting, internal naming or similar
- Fixes for performance
- Refactoring

To be explicit the above statement means that tests are not required for changes
in:

- Documentation (including [CHANGES]/[NEWS])
- The test suite
- perl utilities
- Include files
- Build system
- Demos

Pull Requests that only affect minor cosmetic output do not require tests.

It is acceptable for the tests to be added via a different Pull Request to the
main Pull Request.

A test may be omitted where writing the test would result in disproportionately
more effort than writing the code being tested. For example, difficult to
reproduce error conditions.

Triage Labels
-------------

Before approving a PR, the applicability of the testing policy to the PR must
be assessed and an appropriate label applied to the PR. One of the following
labels must be applied:

- `tests: present`, to be added where suitable tests are included in the same PR.
- `hold: tests needed`, where the testing policy requires tests but they are not
  currently included in a PR.
- `tests: exempted`, where tests are not included in a PR but are not required
  by this policy (for example, because the PR concerns only documentation,
  or because writing the test would result in disproportionately more effort;
  see above).
- `tests: deferred`, where the tests are required by the testing policy
  but it is intended to add these tests in a subsequent PR. The label should
  be removed (for example from a closed PR) once subsequent tests have
  been merged.

The `hold: tests needed` label blocks merging of the PR and constitutes a hold.
None of the other labels listed above block merging of a PR.

Only one of the above labels should be set on a PR at a given time.

It will generally be readily apparent which label is applicable
at any given time. However, if there is a lack of agreement over the
status of a PR in regards to the test policy, this should be resolved
via the normal review process. For example, OpenSSL Committers are not required
to agree to use of the `tests: deferred` label if they do not feel it is
appropriate.

Use and approval of the `tests: deferred` label is at the discretion of the
OpenSSL Committers. It is recommended that this label be used only when a
subsequent PR with tests is anticipated, but no specific rule is imposed on when
`tests: deferred` may be used at this time. The intention is to begin
surveillance and obtain visibility into how decisions under the testing policy
are being made prior to making any more specific prescriptions. For example,
this labelling allows obtaining a list of merged PRs for which a decision was
made to defer adding tests, but for which tests have not yet been added.

Performance Testing
-------------------

Performance testing should be performed automatically via [CI] on a regular basis
for certain components as defined by the [OTC].

Examples of performance testing that should be considered include:

- Individual algorithm performance operating over different input sizes
- SSL/TLS handshake time over multiple handshakes and for different protocol
  versions and resumption/non-resumption handshakes

Performance figures should be collected and tracked over time.

Recommendations
---------------

This section makes recommendations that are not mandatory but should be
considered.

Pull requests that implement significant new functionality should consider
whether fuzz tests should be added.

As per the policy wording above, pull requests that implement refactoring are
not required to add new tests. However before refactoring is a good time to
check that there are sufficient tests and that all corner cases are covered.

Where performance fixes are implemented consideration should be given to whether
we need to add a performance test to the performance testing suite.


[CHANGES]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#changes
[CI]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#ci
[NEWS]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#news
[OTC]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#otc
[stable]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#stable-release

***
The Public Voting Procedure of OTC
==================================

The following regulations complement the [OTC Voting Procedures] stated
in the project bylaws. This policy affects only public votes.

[OTC Voting Procedures]: https://www.openssl.org/policies/omc-bylaws.html#otc-voting

Vote Proposal
-------------

The votes are proposed in pull requests and issues of the technical-policies
repository on GitHub OpenSSL project.

The vote regarding a policy change proposal is recorded directly in the
pull request of the policy change proposal.

Any other votes are recorded as separate issues in the repository.

All votes governed by this procedure must be announced through an
e-mail to the [OpenSSL Project mailing list].
The announcement email must contain a hyperlink to the GitHub issue
or pull request where the vote is carried out.

Casting the Votes
-----------------

The individual members of [OTC] cast their votes directly in the issue or
pull request where the vote was proposed.

When the votes are cast during an OTC meeting, the person responsible for
taking the meeting minutes or the proposer of the vote copies the votes
cast during the meeting into the issue.

The Final Vote Records
----------------------

After the vote is closed the proposer of the vote records the final outcome
and individual member votes in a separate file in the votes subdirectory of
the repository. The commit with the vote record is pushed directly into
the master branch of the repository. No pull request is needed.

The file is formatted as follows:

```
Topic: .
Proposed by: .
Issue link: https://github.com/openssl/technical-policies/issues/...
Public: yes
Opened: yyyy-mm-dd
Closed: yyyy-mm-dd
Accepted:  yes/no  (for: X, against: Y, abstained: Z, not voted: T)

  OTC Member A  [  ]
  OTC Member B  [  ]
  ...
```

The individual member votes are recorded as `[+1]` a vote in favour, `[-1]`
a vote against, `[+0]` an abstention with an inclination in favour,
`[ 0]` a neutral abstention, `[-0]` an abstention with an inclination
against, and `[  ]` meaning not voted.

The vote files are named `vote-yyyymmdd-vote-short-id.txt` where the `yyyymmdd`
is the date when the vote was proposed and the `vote-short-id` is a short
mnemonic identifier of the vote such as `voting-procedure` or `accept-pr-1234`
or similar.

Closing the Issue
-----------------

The issue or pull request where the vote was proposed is then labelled with
the `Accepted` or `Rejected` label based on whether the vote was accepted or
not.

The issue is then closed. In case the vote is in a pull request for a policy
change and the vote passed the pull request for the policy change is squashed
and merged into the repository.

[OTC]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#otc
[OpenSSL Project mailing list]: https://mta.openssl.org/mailman/listinfo/openssl-project
