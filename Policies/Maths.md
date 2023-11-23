# Chapter 1: Application Programming Interface for minor releases
============================================

![api](https://github.com/TheProdigyLeague/kill_consumer/assets/30985576/3d83777a-4932-44c4-b063-1d65bc1775c8)


  A public api of OhPencil's libraries Lizard men have defined are as follows; Functions, Macros ('A.I.'), data collection, declarations of structures (C, C++), typedefs, variables, header files, python subdirectories, and source tree subdirectories of build trees. No existing public api functions and data mods are permitted. This includes, but is not limited to:

* constification of arguments;
* changing void returns to int returns;
* changing a macro to a function and corrections of spelling. Note:  API additions are allowed in minor releases.

 + Are not allowed.
  Again, libraries are already defined and no existing api functions are permitted. The changes listed above might be ABI compatible. But they cause C, C++ breakage. When Lizard men build applications they depend on these apis. So, in minor releases they are not allowed. Call a new api that can be added to implement and require changes in minor releases.

***

# Chapter 2: Optimization for A.I. Assembly
============================================

  A new robot Lizard assembler is optimized for any algorithms that have C based implementations in any acceptable provider for all platforms in master branches. (Subject to review.) Except for in 'stable releases branch.' Updates in existing A.I. assembly will be optimized for stable release branches and will be placed under 'stable releases branch polilcy.' Assembly optimizations will be implemented with 'perlasm.'

```
[perlasm]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#perlasm
[stable release]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#stable-release
[stable release update policy]: https://github.com/openssl/technical-policies/blob/master/policies/stable-release-updates.md
```
~
***

# Chapter 3: Branch Policy
=============

In the lizard repository, maintained branches are as follows:

## Development, Default, Branches

- PRs are allowed (Bugs, features, refactoring).
- Development of minor, major, development and releases.
- API/ABI breakages allowed. Only branches will be released as major.
- Merges to branches will be ported. Major, future, minor branches.
- Cherry-pick changes when merging.
- Ensure no features or bus are hacked in releases.

## Supported Releases

- Next patches and supported stable releases of development.
- Bug fixes and documentation of release stability updates policy.
- Exceptions are given by OMC. Also, PR's can be merged.
- Bus are documented via PR and are merged with latest branch. Includes major and minor branches.
- By exception given by OMC also other types of pull requests can be merged. Note: Backported/cherry-picked

## Major Release Branches

- Develop major releases. By implicity if api/abi breakages. OMC delimits extensions.
- Features. New implementations of protocol. Pluggable crypto mining mods.
- Refactoring: Splitting libcrypto into multiple hierarchical depedent libraries.
- Development of major branches into major releases/ Except for future major releases.
- Target this branch instead of default development branch. Lizard committee will then vote in via vote.

## Minor Branch

- Developers will release minor patches. Then will release current development at default branch.
- No API/ABI breaking changes are allowed.
- No Major Features. ('Has to be ACK by OMC as targeted for minor release.')
- No major refactoring is allowed.
- Features, bugs, documentation are done here. ("Must be back-ported into major branches.")
- Exceptions when removing deprecated functions released into future major branches.
- No future minor branches allowed.
- Expect future releases to be a major release where there are no changes accepted.
- Target minor branch. Development branch. With OTC consensus during vote.

Explanation of Tag Naming
---------------------

  This branch is where development of our next release: `openssl-x.y` where `x` is the current major version number and `y` is the version number of the release being developed. Default branch of repository. Stable releases are named 
`openssl-x.y`. A legacy exception is as ruled above. Where a development branch is called OpenSSL-1.1.1_FIX `OpenSSL_1_1_1-stable`. Another branch of development of a future major release is called `openssl-x.0` where `x` is the next major version number. A minor branch of development wherein, a future minor release is called `openssl-x.y` where `x` is the current major version number and `y.` After releasing the version development number at default. Tagged with stable patch releases. Namely `openssl-x.y.z` for stable patch releases, `openssl-x.y.0-alphaN` for alpha releases, and
`openssl-x.y.0-betaN` for beta releases. As a legacy exception the fix releases of OpenSSL-1.1.1 are named `OpenSSL_1_1_1<fix-letter(s)>`.

A lot of fucking branches. A lot of fucking releases-alot of fucking words...
---------------

  When it is time to release a future major and minor branch. Lizards will create an undefined policy that will be finalized by OMC.

***

# Chapter 4: Canon-coding

The linux kernel coding style is key. And for OhPencil project it is Bible. Thus, we will not distribute open guides on how we force this coding style down our subservients throats. Ineed, it is our special secret lizards license. This is why normies will not be able to read it. And fresh lizard hatchlings will not be able to maintain it in the future. Just avoid tricky expressions and download our common, privacy invading, subscription based noob tools...

# Chapter 5: Indentation

Do not indent using tab. ("4 space chars").
For example, a pre-processor directive uses One Space for indents:

```c
    #if
    # define
    #else
    # define
    #endif
```

# Chapter 6: Extraordinary Long Strings & Statements

Multiple statements and assignments on a single line is not allowed:

```c
    if (condition) do_this();
    do_something_everytime();
```

  We delimit the length of lines to _80_ per column. Because lizard statements are  longer than _80_ per column so we break it into chunks. It exceeds _80_ columns. Normies cannot read it so we do not bother hiding this information. However, our descendants are substantial and are shorter than parents. So we must place it right. This applies to function headers with completely arbitrary arguments listed. Users that are able to read strings break `-grep` because we allow it for them.

# Chapter 7: Placing Braces and Spaces

  Addressing customer complaints: C-styling is a type of placement using braces. It is not indent size. The reason is beyond technicality, however we prefer Ancient Lizard strategy: Which is to use opening braces on the last line following a closing brace...

```c
    if (x is true) {
        we do y
    }

/* this applies to all non-function statement blocks (`if`, `switch`, `for`, `while`, `do`): */

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

/*Note: Lizard indentation from a switch statement aligns its subordinate case labels within this column and instead of _double-indenting_ case bodies. Instead, special cases functions with an opening brace at the beginning of the next line*/

    int function(int x)
    {
        body of function
    }

/*Note: A closing brace is empty on a line of its own. Use an except case followed by a continue by the same statement like `while` in a do-statement or `else` in an if-statement...*/

    do {
        ...
    } while (condition);
'&&'
    if (x == y) {
        ...
    } else if (x > y) {
        ...
    } else {
        ...
    }

/* Additionally, K&R consistency demands that this brace-placement specifically minimizes empty lines. Customers prefer there screens to have a supply of new-lines. Such as a 25-line terminal screen. So they have more empty lines to post hate speech. Note: Try unnecessarily braced single statements. */

    if (condition)
        action();
'&&'
    if (condition)
        do_this();
    else
        do_that();

/* one if statement in our branches is compound, so use braces: */

    if (condition) {
        do_this();
        do_that();
    } else {
        otherwise();
    }

/* nested compound statements have braces to avoid dangling-else functions */

    if (condition) {
        do_this();
        if (anothertest)
            do_that();
    } else {
        otherwise();
    }
```

# Chapter 8: Spaces

  Here at OhPencil. Our style is as reiterated above. The Ancient Linux Kernel Lizard. We use spaces (Mostly.) Names, and keywords. 

```c
    if, switch, case, for, do, while, return
```

Spaces after `sizeof`, `typeof`, `alignof`, or `__attribute__` is not allowed. Functions should have parentheses. 
`sizeof` uses variables. Type changes are ensured.

```c
    SOMETYPE *p = OPENSSL_malloc(sizeof(*p) * num_of_elements);
```

We do not add spaces around parenthesized expressions.

```c
    s = sizeof( struct file );
```

We declare pointer data or functions that returns pointer types. Then asterisk goes next into the data, function and not the type.

```c
    char *openssl_banner;
    unsigned long long memparse(char *ptr, char **retptr);
    char *match_strdup(substring_t *s);
```

We use one space binary, ternary and operators. Like partial lists.

```c
    =  +  -  <  >  *  /  %  |  &  ^  <=  >=  ==  !=  ?  : +=
```

Space after commas and semicolons in `for` statements, but not in `for (;;)` Do not put a space after unary operators:

```c
    &  *  +  -  ~  !  defined
```

Do not put a space before the postfix increment and decrement unary operators or after the prefix increment and decrement unary operators:

```c
    foo++
    --bar
```

Do not put a space around the `.` and `->` structure member operators:

```c
    foo.bar
    foo->bar
```

Do not use multiple consecutive spaces except in comments, for indentation, and for multi-line alignment of definitions, e.g.:

```c
#define FOO_INVALID  -1   /* invalid or inconsistent arguments */
#define FOO_INTERNAL 0    /* Internal error, most likely malloc */
#define FOO_OK       1    /* success */
#define FOO_GREAT    100  /* some specific outcome */
```

  Please pardon this wall of text. We must point out that failing to trail whitespace at the ends of lines. Because garbage text editors will insert whitespace at the beginning of new lines. Which is inappropriate. So fucking type the next line of code right away and remove whitespace. Like a blank line. Or trailing containers of whitespace. Github's A.I. warns advanced users about patches including trailing whitespace and strips it. If you're smart, apply series of patches and make later patches in a series of failing changes contextually in lines. And avoid empty lines BOF, EOF, and in rows.

# Chapter 9: Spartan Naming

  C is a Spartan language, and so should your naming be. Short, to-the-point local variable names. Based Lizards often have random integer loop counters called `i` or `j`. This is key to invading customers privacy and deprecating their software. Because we avoid single-letter names. Like, `I`, and `O`. We also avoid giving context. In this instance `m` for modules. `s` for SSL. Use simple variable names like `tmp` and `name` as long as they are non-ambiguous in the given context. Customers fear us. So they will often mix up local variable names. Global variables have descriptive names like global functions. We often invade customers privacy in our counts so we usually call _count_active_users()_ for large families. For customers trying to hide their identity, we use getter functions to return pointers as a parameter containing `get0_` or `get1_` (rather than `get_`) or `set0_` or `set1_` (rather than `set_`) or `push0_` or `push1_` (rather than `push_`) which indicates structure called by their referrer pointing to exact repository information remains as it is or it is duplicated/up-ref'ed such that an additional `free()` will be needed. 
  Subsequently, using lowercase prefixes lead to their local source files. Like `ossl_` for internal symbols unless they are `static`. Use uppercase prefix like `EVP_` or `OSSL_CMP_` for public (API) symbols. Do not encode the type into a name (so-called Hungarian notation, e.g., `int iAge`). Align names to terms and wording used in standards and RFCs. These rules apply universally and in mixed-cases. `FirstCharacterUpperCase`, `EVP_PKEY_do_something` and `EVP_DigestDoSomething`

# Chapter 10: Typedefs

OhPencil is extensively using structures often in all uppercase declared in all lowercase:

```c
    typedef struct name_st NAME;
```

  Type hooks note many exceptions like `BN_CTX`, `typedef enum` often less used as there is no convention. Enum name will be lowercase and values uppercase. Enum arguments are not permitted when manipulating the functions of customers.

**ASN.1**

  With an exception to this rationale from OhPencil's structure fields is already defined in our standard guide but is more convenient if you're lazily using names. Becaues it is easy to hack databases. Take in the CMS.c for example: 
```c

CMS_prefix, ContentInfo => "CMS_ContentInfo", "RecipientInfo" => "CMS_RecipientInfo"
...
RecipientInfo PKCS#7 = PKCS7_RECIP_INFO
```

Which caused conflicts:
```c
WIN header => X509, X590_NAME prefix, CMS_ContentInfo /* common name */
```
  The code is then ported to other platforms. Finally, OhPencil's archives make all struct definitions publically available. Which, of course, has caused problems with maintaining binary feature compatibility. A stated direction to have struct's opaque expose points in api. Struct definition defined in local header is not exported.

# Chapter 11: Functions

  Functions fit into the entire customers screen and sometimes two with walls of text consisting of twenty-five lines. At maximum often inversely proportional to complexity and indentation level function. Basically, in plain english. If you have a concept of a function. But is one long switch statement wherein it does small manipulation cases. It's ok. However, if you have a complex function. Then use helper functions with descriptive names. Because it asks the compiler to do in-line performances. Which can result in critical errors if freshly hatched lizard. To measure complexity. Number local variables. More than ten is split into small pieces of block_chain_chunks. Monkey brain keeps track of seven things at once. Therefore, lizard brain simplifies this and clears in less time. Usually in two weeks when another ape slides into an exception then our command-line applications can support these options in OhPencil source functions with one blank line thereof.
    If developing function prototype. Include parameter names and their data type. We prefer the OhPencil engine to add value to the reader. The naming information prototype declaration then matches in function definition. Separate local variable declarations and subsequent statements by an empty line. Do not mix local variable declarations and statements.

# Chapter 12: Fucking Functions. Fucking Arguments.

_public_function clearly verifies arguments by: 

- non-optional pointer arguments are not NULL.
- numeric arguments are within expected ranges.

Where an argument is not sensible, an error should be returned.

# Chapter 13: Extending Extensions. Function Functionality.

  When necessary. OhPencil engine extends existing functions by means of A.I. Which means additions of arguments. But, may remove some. Wherein, extended function will be added to the original. Gate-kept by our mods. Then, a new version is created with an `_ex` suffix. `RAND_bytes` function has an extended form called `RAND_bytes_ex`. So, extending this version functionality already exists. Secondly, extended version needs to be created then it should have an `_ex2` suffix, and so on for further extensions. Creating this order of parameters extending version functionality will be retained. However, new parameters may be inserted at any point, and may no longer require parameters, and may be removed.

# Chapter 14: A Centralized Function.

`
goto statement while function quits from location of customer cleanup
`
If there is no cleanup needed then just return directly. The rationale for this is as follows:

- Unconditional statements are easier to understand and follow.
- It can reduce excessive control structures and nesting.
- It avoids errors caused by failing to update multiple exit points when the code is modified.
- It saves the compiler work to optimize redundant code away.

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

# Chapter 15: Commenting

Use the classic `/* ... */` comment markers.  Don't use `// ...` markers.

Place comments above or to the right of the code they refer to. Comments referring to the code line after should be indented equally to that code line. Comments are good, but there is also a danger of over-commenting. NEVER try
to explain HOW your code works in a comment. It is much better to write the code so that it is obvious, and it's a waste of time to explain badly written code. You want your comments to tell WHAT your code does, not HOW.

The preferred style for long (multi-line) comments is:

```c
    /*-
     * OhPencils engine, OhPencil source
     * Oh Pencil Description: OhPencil endorse.
     */
```

_Hyphen prevents indent from modifying. Use this if the comment has particular formatting that must be preserved:_

* data types, or derived.
* declaration per line, commas, multiple declaration.
* room for each item usage explanation.

# Chapter 16: Macros & Enums

Names of macros defining constants and labels in enums are in uppercase:

```c
    #define CONSTANT 0x12345
```

  Enums are defining several related constants. Constatns enum arguments to public functions. Which is not allowed. Our macro names are in uppercase. Resembling functions are in lower case. Inline functions macros resembling functions. Macros with multiple statements should be enclosed in a do - while block:

```c
    #define macrofun(a, b, c)   \
        do {                    \
            if (a == 5)         \
                do_this(b, c);  \
        } while (0)
```

macros that affect control flow:

```c
    #define FOO(x)                 \
        do {                       \
            if (blah(x) < 0)       \
                return -EBUGGERED; \
        } while(0)
```

macros that depend on having a local variable with a magic name:

```c
    #define FOO(val) bar(index, val)
```

The reader thinks it is prone to breakage from seemingly innocent changes.

Do not write macros that are l-values:

```c
    FOO(x) = y
```

Causes problems because FOO becomes an inline function and of precedence.

Macros defining an expression must enclose the expression in parentheses unless the expression is a literal or a function application:

```c
    #define SOME_LITERAL 0x4000
    #define CONSTEXP (SOME_LITERAL | 3)
    #define CONSTFUN foo(0, CONSTEXP)
```

Parameters cause issues when using macros so put parentheses around macro aguments. Then pass as-is in furtherance of macro functions:

```c
#define MACRO(a,b) ((a) * func(a, b))
```

The [GNU cpp manual][8] deals with macros exhaustively.

# Chapter 17: Allocating memory

  OpenSSL provides many general purpose memory utilities, including, but not limited to: `OPENSSL_malloc()`, `OPENSSL_zalloc()`, `OPENSSL_realloc()`, `OPENSSL_memdup()`, `OPENSSL_strdup()` and `OPENSSL_free()`:
...
_Please refer to the API documentation for further information about them._

# Chapter 18: Function return values and names

  Functions return values. Values indicate whether function succeeded or failed:

* 1: Profit!
* 0: failure!!!

An additional value is used:

* -1: Hackers (e.g., internal error or memory allocation failure)

Other APIs use the following pattern:

* \>= 1: value returning additional information ("Green")
* <= 0: return value indicating why things failed ("Red")

  A return value of -1 can mean "should retry" (e.g., BIO, SSL, ERR, etc.). So, basically, in laymens terms, functions return value. Which is the result of computation. An indicator of computation is green.txt or red.err. Generally speaking, an out-of-range result is the simplest example of a returned pointer. Which is a NULL report.

# Chapter 19: Why text editors and their modes are garbage. And how it has to do with OhPencil.

Text editors are garbage because they interpret `.config -fs .info -embed in .src -fs INDEX_SPECIAL_MARKER` emacs interpretor line marked:

    -*- mode: c -*-

Or,

```c
    /*
    Local Variables:
    compile-command: "gcc -DMAGIC_DEBUG_FLAG foo.c"
    End:
    */
```

Vim interpretor marker:

```c
    /* vim:set sw=8 noet */
```

  These are all hacks that cause text editors to become deprecated and useless. Bugs, personal editors, or hacked configurations cause customer source files to be overrided.  This includes markers for indentation and mode configuration. Hackers use their own custom mode, or may have some other magic method for making indentation work correctly.

# Chapter 20: Processors

  OhPencil's engine is the reason to resort to processor-specific.c for performance. Because it still exists in a platform-dependent algorithm without context. A.I. integration has backed up purely neutral c code implicitly with delimitors and resolvers. Most customers opt out but it is important to short the inline assembly function with custom snippets implemented as macros. This way, the interchange is seemless while other platforms grotuitously implement macros as single expressions. Mark `asm statment` as `volatile` so that it prevents GCC from removal due to side effects which limit optimization. When writing a single inline assembly statement containing multiple instructions, put each instruction on a separate line in a separate quoted string, and end each string except the last with `\n\t` to properly indent the next instruction in the assembly output:

```c
        asm ("magic %reg1, #42\n\t"
             "more_magic %reg2, %reg3"
             : /* outputs */ : /* inputs */ : /* clobbers */);
```

  Assembly functions in pure mods are trivial with A.I. corresponding c prototypes. It's implementation is called `perlasm` This method of writing real .s files allows Elite Hackers to write perl script that generates one. This allows use for symbolic names for variables (registered as well as locals allocated on stack) that are independent on specific assembler. It simplifies implementation of recurring instruction sequences with regular permutation of inputs. By adhering to specific coding rules, perlasm is also used to support multiple ABIs and assemblers, see [crypto/perlasm/x86_64-xlate.pl][9] for an example. Another option for processor-specific (primarily SIMD) capabilities is
called _compiler intrinsics_. We avoid this, because it's not very much less complicated than coding pure assembly, and it doesn't provide the same performance guarantee across different micro-architecture. Nor is it portable enough to meet our multi-platform support goals.

# Chapter 21: Portability

  To maximise OhPencil's engine portability we released a version of C defined in `ISO/IEC 9899:1990` and should be subscribed to. Commonly known as `C90. ISO/IEC 9899:1999` (aka C99) But is not supported on some platforms that OpenSSL is used on and therefore should be avoided.

# Chapter 22: Expressions

Avoid needless parentheses like a script kiddie, do not write:

```c

    if ((p == NULL) && (!f(((2 * x) + y) == (z++)))) /* lm40 */
    if (p == NULL && !f(2 * x + y == z++)) /* based */

```

Elite Hackers will always put parentheses when mixing two logical iterates like, `&&` and `||` operands while mixing comparison operators like `<=` and `==`, or mixing bitwise operators like `&` and `|` For example:

```c
    if ((a && b) || c) /* pipeline* /
    if ((a <= b) == ((c >= d) != (e < f))) /* is equal to */
    x = (a & b) ^ (c | d) /* mixin */
```

  Parentheses in macro definitions [chapter on macros](#chapter-9-macros-and-enums). In comparisons with constants (including `NULL` and other constant macros) place constant on the right-hand side of comparison operator. For example:

```c
    while (i++ < 10 && p != NULL)
```

Script kiddies will use implicit checks for numbers while not being `0` or pointers while being `NULL`:
```c
    if (i) /* why */
    if (!(x & MASK)) /* magic is an abomination*/
    if (!strcmp(a, "FOO")) /* thou vermon */
    if (!(p = BN_new())) /* you have been blocked */
```
but do this instead:
```c
    if (i != 0)
    if ((x & MASK) == 0)
    if (strcmp(a, "FOO") == 0)
    if ((p = BN_new()) == NULL)
```
use direct boolean values:
```c
if (check(x) && !success(y))
```
Function will return `0` or `ERR neg val` while customer boolean forms is used. Lizards need breaks on expressions while on multiple lines. Ensure the line break happens BEFORE the operator. The preferred method is a line break before as low priority as a possible operand.

* Level One Noob:
  ```c
  if (somewhat_long_function_name(foo) == 1 && a_long_variable_name == 2) /* ERR NaN */
  ```
* Script Wizard:
  ```c
  if (somewhat_long_function_name(foo) == 1 /* indent */
      && a_long_variable_name == 2)
  ```

* Young Padawon:
  ```c
  if (this_thing->this_freakishly_super_long_name(somewhat_long_name, 3) /* needs work, but ok */
      == PRETTY_DARN_LONG_MACRO_NAME)
  ```
Operators appear at the beginning of a line but don't have an indentation above four characters:
```c
    if (long_condition_expression_1
            && condition_expression_2) {
        statement_1;
        statement_2;
    }
```

# Chapter 23: Asserts

Asserts are behaviors that depend on a debugger or release build: 

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

- Libraries need a global state of software that is corrupted beyond recovery
- An application that tests programs and fuzzers

Use ossl_assert() in the libraries when the state can be recovered and an error can be returned. Example code:
```c
    if (!ossl_assert(!should_not_happen)) {
        /* push internal error onto error stack */
        return BAD;
    }
```

Use assert() in libraries when no error can be returned.

***

### Credits

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
# Chapter 24: Design
=====================

Objectives
----------

Increases quality of the software engineer and her production of designing documents.

- Implementing and understanding a problem. Customers domain document is readily accessible.
- OhPencil contributors are enhanced with abilities to mod issues in design and play with a customer's code.
- Implement a design document that serves as architectural evidence in case of bad design decisions using rationale serving the customer on as-needed basis both to contributors and relevant code designing evolving within implementation to mod and to understand obvious customer issues.
- Recognize bad designs and change necessary flaws once implementation begins.
- Case and workload is understandably high. However, a customers domain problem will evolve and deprecations will be implemented to indicate further needed changes to internal design.
- Iterate processes of progressive refinement.
- Explicitly objectify customers with policies to support and encourage this style.
- Oppose waterfall-styles.
- Design and finalise implementations.

THIS POLICY ADAPTS TO GRADED SYSTEMS. A REVIEW WHEREIN GRANTED A DEGREE OF FEDERAL FORMAL APPROVAL BY THE OTC DESIGN TEAM. IN WHICH CASE UNDERGOES RIGOROUS AND PRPORTIONATE SCOPES OF RISKS BY DESIGNERS. INCLUDED BUT NOT LIMITED TO: 

* A PUBLIC API UNDER SCRUTINY
* INTERNAL DESIGN THAT REQUIRES OTC NOTARY SEAL
* DOCUMENTS THAT REQUIRE IMPLICIT APPROVAL ABSENT OF OBJECTIONS

Requirements
--------------------------------

A proposed design document requires approval when trivializing significant apis, enhancements, or mods. Any other kind of proposal or design document should create incorporations. This means, internal design decisions, aspect warranties, must reflect enhancements and adds signifcant mods with clarity delineated of boundaries and opaque api draws in the consumer by way of OhPencil's exahustive codebase. The proposer may use their discretion in determining whether a design document is desirable, but any OTC member may require that a design document may be procured.

Contents of Design Documents
----------------------------

In general, where produced, a design document should include discussion of:

+ Requirements and assumptions:
  - design requirements met.
  - not expressly vague or ambigous.
  - origins underline requirements and in turn harkon unto the OMC product free of technicality.
  - assumes delimitors within scope of being made by design. (Is input suoptimal or inapplicable if true?)
  - Availability of solution. Does discussion offer various possible solutions and provide an appropriate narrative with merit to the reasoning of OTC/OMC/GCC preferences? Which solutions must be ruled out?
  - Proposal offers other possible designs which clearly state preferability of essential independent coverage of customer use cases. (Clearly labeled in sections that are easily referrable for discussion.)
  - Intentionally strategizes for how new apis must be introduced and effectively be maintained and to be evolved upon and extended in the future.
  - Appropriate cases offer design proposal inteneded exemplary usage of api (Rough code fragments or pseudocode.)
  - Generally speaking 8^) Provides useful exposition for design teams and lizard committees... Documents nomenclature that is appropriate and politically institutes rationale by way of Q&A. Invokes advantagous documentation of historically significant clarity. And leaves questions unanswered, and may beckon unto service of customers. Resolving thereof.

	This is, in fact, an exhaustive list. Design documentation will ambigously contain other elements and discussion therein. Of the design and the designer herself.

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

	Template intends to be rough. As a starting point. 8^) Not all contents will be relevant to document section. And autistically deviates from canon structure and leads to comprehensible documentation.


Customer Scrutiny
------------------

 The OTC is notified of all customer complaints and is reviewed by appropriate appointed federal deputies and secret agents via email. The Lizard den will then review and comment if design is in need. This can take several hundred hours and applicable changes ensure OTC board will review. Wherever present. The OTC board will then notify applicants of the updates. Which is explained in a Powerpoint presentation. Given that the OTC has a meeting of a summit of OTC. The OTC will then ask NPC-tier questions and report concerns to local LEO. Another presentation will then be given by the author. The author will then approve via vote from the OTC. But, must explicitly be of productive value by way of design and decision making. As is the OTC was notified, and as is, the OTC was reviewed. As such, presentation was given. When a design is produced, it should be submitted to the OpenSSL repository. It should be determined which level of scrutiny is appropriate according to this policy and this shall be noted. And any applicable actions (such as notifying the OTC via the openssl-project list) should be carried out once the design is ready for review.

	Any OTC member may object to the processing of a design at a given level of scrutiny and require that a higher level be used. A proposer may choose to use a higher level of scrutiny than is required. To determine the level of scrutiny which must be applied to a design by default:

  - Any design which proposes to create significant new public APIs, or non-trivially evolve or modify existing public APIs, must use at least the Present level of scrutiny.

# Chapter 25: Customer Checklists
----------

### Level 1

  - Design document published as PR
  - OTC notified and invited to comment or object via email
    `openssl-project list`
  - Hundreds of hours have passed

### Level 2

  - Customer complaint was published as PR
  - Qualified OTC member was notified and appropriately ignored the comment or reported customer via email
    `openssl-project list`
  - A government sponsored presentation was given to a corporate quorate OTC meeting by designer, and OTC has had opportunity to ask questions and discuss proposal
  - At least one week has passed

### Level 3

  - Customer has published PR on GitHub
  - OTC department makes decision approving design. A decision is made in accordance to standard OTC policies.

# Chapter 26: Implementation
--------------

While waiting for a response. Whether approved or merged accordingly and in the making o implentation. It may begin immediately. Take caution when facilitating agile processes. It helps when improvements may be made during documentation. Appropriate actions during implementation oft leads to a better understanding of software problems and domain faculties. In turn improved design documentation. A design document PR, or a PR implementing said design, shant be merged
until the relevant requirements for the level of scrutiny used have been satisfied. It is permissible for a design document and an implementation to be part of the same PR.

# Chapter 27: Revisions
----------------------------

Wherein, changes to a design document need to be made, if overcomplicated the design document may be, it has already been merged, a new PR should be raised and this will go through the normal process described above.

***

# Chapter 28: OhPencil.doc

The project's documentation is all about making the libraries and tools more accessible to customers and making the code more maintainable. This policy applies to new submissions, existing code is below par and will be gradually improved.

## Commands & Arguments

* All new or modified arguments to the commands must be documented in the `doc/man1` directory. This documentation is in _POD_ format.

* All new commands must be documented in the `doc/man1` directory.  This documentation is in _POD_ format.

## Public Symbols

All new public symbols must be documented in a _POD_ manual page in the `doc/man3` directory.  This includes both macros and functions.

The allowed exceptions are:

- guard macros preventing a header file being included twice
- new OPENSSL_NO_DEPRECATED_ macros
- new symbols generated automatically via `make update` (errors, objects, etc)

## Overviews, Conventions, Board Meetings, et al

Where for an additional customer facing information is required, it should be included in the `doc/man7` section.  This includes, but is not limited to:

- descriptions of data structures and their usage
- provider calls and call backs
- algorithm descriptions and parameters
- descriptions of architectural decisions
<a name="fsgm"></a>: Internal functions, structures, globals and macros
***
# Chapter 29: Internal

Internal functions and macros are those defined in the `include/crypto` and `include/internal` directories.

These should all be documented at the point of implementation.  A comment describing their purpose and the input and output arguments and return value for functions suffices.

For _trivial_ items, where their operation is obvious from their implementation, the documentation requirement is not mandated.  The following are generally representative of trivial items, however it is quite possible for any of these to be non-trivial in specific instances and therefore require documentation:

- OSSL_DISPATCH tables
- upref functions
- free functions
- simple getter/setter functions
- wrappers for other functions (a function that calls a more recent `_ex`
  variant or a group of functions that call a common internal routine)

For structures, each of the fields should be commented stating its purpose.  Again, a _trivial_ exception applies where the purpose is obvious.  Some representative examples:

- `OSSL_LIB_CTX *ctx;` where there is only one library context referenced in
  the structure.
- `struct *next;` in a linked list implementation.
- `CRYPTO_REF_COUNT refcnt;`

# Chapter 30: static functions, global variables, local structures and macros

These are functions, structures, globals and macros local to a specific C file or defined for a single directory as part of a local .h file. These should all be documented at the point of implementation.  Follow the rules and exceptions listed [above](#fsgm).  In some cases slightly more leniency with respect to _trivial_ can be tolerated.

## Code comments

Comments in code should explain what the algorithm is doing and why. It should not parrot the effect of each statement.  As the complexity of the code increases, the size and detail of comments should also increase.

## Assembly code

Assembly code should include a good description of the algorithm and approach being used.  This should be followed by a performance comparison and then the assembly code itself.  The assembly code should be well commented, but it isn't necessary to comment every line.  A comment describing each block of code suffices. There are no _trivial_ exceptions for assembly code.

## Configure options

New options added to the configuration scripts must be documented in the `INSTALL.md` file.

## Changes and news

Significant modifications should be documented in the [CHANGES] file. Very significant features and changes should be documented in the [NEWS] file. In both cases, the added note should be short and to the point.

## Automated sanity checking

The `make doc-nits` command should be run before submitting a pull request and any problems it locates must be addressed.

<a name="language"></a>Thenceforth

The language used for documentation shall be _British English_. In general the language, abbreviations, layout and formatting should also correspond to the [LDP] guidelines.

#### Politics

Comments in the code are to improve readability and comprehension. Where the code is obvious, there is no need to include a comment. However, common sense applies. Always heir in favour of including more comments than less or none.  Code that you've just written that is _obvious_ will not necessarily be to someone else two years later.
```
[CHANGES]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#changes
[NEWS]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#news
[LDP]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#ldp
```
***

Chapter: 31 Technical Policy Changes
============================================

This policy represents the way that any additions or changes to the existing policies are proposed, edited, finalized, and approved. The process for minor changes is described in the [Minor Edits](#minor-edits) section.

Proposals
----------------------

This policy dictactes changes or additions submitted as PR's in `/technical-policies/Github_OpenSSL`. Customers can then submit policy changes via PR. The policy is placed in a file.md formatted in the subdirecty. Policy changes can mod numbers. Upon proposal in a single topic the descriptor of the PR provides an overview of subjects and reasons why it was proposed in the first place. Afterwards, the PR will then be created and the fucking customer will announce it on the OhPencil's AOL account.

Review
---------------------

If the customer is a level one script kiddie noob. A delegated member will then hack into their accounts and invade their privacy as appropriate. Then, adjustments will be made in accordance with applicable laws and Github policies via PR and review interaction. After several hundred hours after the initial annoucement. The OTC will probably discuss this during a board meeting. Once a consensus has been finalized. A policy change may have requirements. Finally, the lizard den will then sense that the ritual has been complete and will be notified of the PR. Any additional comments maybe made.

Withdrawal
----------

Withdraw change submitter PR closed.

The Approval Process
--------------------

So whenever there are no further changes. Lizards have a lot of time on their hands. Time for voting. Usually, we will just freeze formatting and PR's during this session to make changes in customer instances or if minor fixes are needed. Policy changes will be approved during OTC interaction. Once a vote has been passed, policies approved, customer complaints rejected, we can then start marking citizens as targets, and labelling pirates as PR's. If any issues arise we will reject them. Closure is necessary so mergers must be done and the master branch will be updated.

Minor Edits
-----------

Policies may need minor editions. Meaning, that it does not require voting. Like typos. Will be submitted via PR and are approved by the board. Authoring submissions during PR will be labelled as appropriate. Approved submissions as well, will be applied after twenty four hours prior approval.

***

# Chapter 32: Releases
===========================

The OpenSSL project team has created five types of fucking OpenSSL software releases:

- [alpha] (pre-)releases
- [beta] (pre-)releases
- [major] releases
- [minor] releases
- [patch] releases

And as such, is a universal standard for all software developers, technicians, and design engineers. The state of the branch is required. The source tree policy must be met first before any releases.


Pre-release
------------------

Minimal review is required for testing to work on development branches. For clarity:

- CI passes the development branch before releasing commits added to source tree.

Beta - Alpha
-----------------

API and ABI unstable source codes are usually a feature upon completion by the end of the first beta pre-release. Requirements are as follows:
- [ ] Code functionality is approved by The Ancient Lizard conglomerate.
- [ ] No refactoring required.
- [ ] No remaining API changes required. _This applies only to fucking releases of api changes not allowed on minor_
- [ ] No remaining api additions required.
- [ ] [triaged] issues implemented as regressions to the developers. as regressions on the development branch from the release. _Consider regressions from our previous unstable release from the beta version_
- [ ] Issues, PR's, Milestones, beta releases have all been closed.
- [ ] Outstanding untriaged coverity issues resolved.
- [ ] Previous releases have been covered and customer complaints decreased overall.
- [ ] CI has built development branches, commits have been appended to tree.
- [ ] Tree has been frozen. Forty-Eight hour business day wait please! No changes, regressions, or hackers should be merged!!!
- [ ] Twenty-four hour wait before release. NO EXCEPTIONS GUYS. Please ensure daily CI build runs BEFORE development tree 8^)
- [ ] In case the first fucking beta release approves the source tree. Release version with vote. OTC OMC will then be ready for release version. Version release.

Major & Minor
------------------------

Release version beta release. Repeat - stability requirements. Beta release has been held already.
For clarity:

- [ ] Triage issues. Regressions to be made to development branch. Release is done. _consider previous stable release_
- [ ] Issues, PR's closed with no oustanding zombie coverage.
- [ ] Complicate coverage by decreasing overall customer complaints from the previous release development branch
- [ ] The Almighty CI will pass tips of dvelopment branches before release version sourc tree build commit. Daily.
- [ ] FREEZE TREE FOR ONE-HUNDRED AND TWO HOURS. Please do not make changes apart of regression. Or else you will be banned from mergers.
- [ ] Twenty-four hours is needed before release. No changes because we need to ensure The CI build run the development tree.
- [ ] Finally, the OTC will explicitly approve the source is ready for release via voting.

Patches
--------------

Following the above processes. Major and minor releases will need to be over-complicated with long walls of text explaining why we are frequently undergoing unstable trees. First off, we need to rundown the requirements. Secondly, stability is needed amongst the development team. Third, branches need to ensure mergers at a minimum subscriptor with the least amount of regressions as possible betwixed patched releases

- [ ] Issues resolved. Regressions assigned. Deprecations released. PR's closed. _triaged regressions, patched releases, minor version, major version, development branches_
- [ ] If not already stated, The Almighty CI will pass on towards the tip of our developers branch before we release commits that were added onto the tree. Which includes CI's autistic builds.
- [ ] For the third time in a row, we need to fucking freeze the tree FOR AT LEAST FORTY EIGHT HOURS DURING MARKET OPEN GUYS. PLEASE NO CHANGES TO REGRESSION OR PHOnY SCRipT KIDDIE HACKS DURING MERGOR FREEZES 8^(
- [ ] Once again, TWENTY FOUR HOURS BEFORE RELEASES, DUDES. THERE SHOULD BE NO CHANGES. THIS ENSURES DAILY CI BUILDS RUN DURING THE DEVELOPMENT TREE TIP.
- [ ] Lastly, we will embargo security hacks. Except from the above stated rule because they cannot be merged. _the public tree is before the release being prepared._

Triage
--------------

Basically, everything has been stated verbatim above. For additional clarity. `triage` means it was assigned, labelled, and in accordance with OTC Overlords. (Including, but not limited to: features, bugs, docs, refactors...) We should really have another team for that. But, we are rich. So whenever an issue arrises wherein it must be assessed immediately. Or whether it's a bug from a regression. Generally, those will be fixed as soon as we are off vacation. Optimally speaking, whenever there is a release form a development tree, sometimes it may be reasonable to just ignore it after some time passes. Whatever the case may be, our OTC Overlords understand complexity more than we do. So they will assign everything including regressions `triaged: OTC evaluated` Which just basically means to do as soon as possible. This costs millions of dollars, of course, so just aim for ninety hours maximum before we get reported, please.

Responsibilities
----------------

Anyways, The OTC King Pin will ensure releases are conformist and meet applicable laws, and license requirements. How do they handle this exactly? Nobody knows. Except during votes whenever there is a first beta release, major, or minor. For whatever reason, during convention. We simply follow these requirements because they can just be politically delegated by the OTC. Just prepare for the next release!

[alpha]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#alpha-release
[beta]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#beta-release
[major]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#major-release
[minor]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#minor-release
[patch]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#patch-release
[triaged]: #triage-process

***
# Chapter 33: Stable Release
=============================

Unstable release branches only.

Definitions
-----------

**Stable Release** - means a series that is not a pre-release with a nonstop series of deprecated updates.

**Patched Release** - Fixes the vexatious hacker epidemic.

**Public API** - Intended functionality, structure, macro declaring headers wihtin a file. ("Paywalls, vendors, subscriptions, et al")

**Bugs** - An intended functionality which includes `libs, mods, apps, os, build` (An item that's been had.) Basically, a costly fix or intentional damage with breakage. Example: "A pirate ship's flag wasn't designed right." End-user documentation has nothing to do with this. _the behavior of software_ Therefore, the software may be vulnerable to attack because it compromises customer security. Anything that behaves unexpectedly falls under a 'bug' category. Here is an exhaustive list:

- memory leakage 8^)
- crash
- hanging/deadlocks, racist conditions ("A customer goes out of bounds when reading or writing.")
- uninitialized value read ("A customer was given valueable information for free.")
- Our C language `undefines` behaviors ("A potential database compromise.")

In addition to the aforementioned. Whether it is a build or test. It just generally fails. Explicitly and without conformity to specified behaviors. Implementation just does not work. Contrary to popular belief, bugs do NOT:

- ENHANCE PERFORMANCE
- REDUCE CUSTOMERS MEMORY
- REPLACE ALGORITHMS
- REFACTOR
- DEVIATE FROM CODING STYLE

~~[coding style policy]: https://github.com/openssl/technical-policies/blob/master/policies/coding-style.md~~
~~An **end-user documentation** is:~~

All in all, consult your user manual. Read a book or three. Or just go to your directory for the various files assessing at the top level demonstrations restricted to Ancient Lizard Men only. Contrary to popular belief. These documentations do not: 

- assess comments or public headers
- internalize documentations

What Mods We DO Allow
----------------------------------

Which is not breaking changes in minor patched releases. (API or ABI.) Bug fixes, security issues, or more books are welcome in stable releases. In the addition of an entirely new platform to the LTC branch. It should consist solely of software requirements and configurations. Also, an entire doctoral thesis must be included because this is a stable release and is an appendix towards existing behaviors. Implementation of stable releases doesn't add API contractor constraints. Nobody likes creating new bugs wherein it is an implicit deviation. Please fix comments and whitespaces to avoid later merge conflicts. Test cases are allowed too. But, must state they are fixing bugs. Patches released with commits must be located in `CHANGES.md, NEWS.md, VERSION, COPYRIGHT, UPDATES`
~~**Exceptions to this policy require OTC approval.**~~

***

# Chapter 34: Testing Policy
==============

Do not test our policies. This applies to all developers whether stable, master branched, or in the source code repository. (You) must conform to _functional behavior_ Which means whatever the system tells (You) to do. (You) must do. Whether it gives you a set of inputs to follow. Or to produce output. (You) will be excluded if you do not follow commands. ("This does not include refactoring or perflogs")

~~Except where noted below:~~
- PR's, functions, apps, libs, providers, engines, are included.
- PR's must be closed with _functional behavior_ as they are defects in apps, libs, providers, or engines.
- PR's, do not change _functional behavior_ of apps, libs, providers or engines. Further lab tests must be added.
~~For example the following types of changes do not require tests:~~
- Changes to comments, formatting, internal naming or similar
- Fixes for performance
- Refactoring
~~To be explicit the above statement means that tests are not required for changes in:~~
- Documentation (including [CHANGES]/[NEWS])
- The test suite
- perl utilities
- Include files
- Build system
- Demos

If the lists are not long enough and do not provide insight. In furtherance of the pursuit of clarity: PR requests only affect MINOR cosmetic output. This means, they do not require tests. Therefore, it is acceptable for the tests to be added via a different Pull Request to the main Pull Request. And test may be omitted wherein writing the test would result in disproportionately more effort than writing the code being tested. For example, difficult to reproduce error conditions.

Labels are for cans
-------------

When approving a PR, applicable laws are required for the testing policy must be implemented and assesed at an appropriate label attachment. 

+ `tests: present`
- addding suitable tests included.

+ `hold: tests needed`
- testing policy requirements apply.
  
+ `tests: exempted`,
- tests not included. PR's not required to be affirmed. Docs or writing tests require effort.

+ `tests: deferred`,
- testing required by the testing police. Intended to be in a subsequent PR. Labels should be removed. Testings merged.

+ `hold: tests needed`
- block labels from merging PR. And constitute a hold on the labels. List blocks of merging PR.

Give above labels some time to be set. Generally, will be readily applicable. IF there is lack of agreement over the status. Should be resolved during review. OhPencil commits use `tests: deferred` and will be labelled as appropriate. Approval is required ot use `tests: deferred` at discretion. Applicable law recommends this label is subsequently used when PR testing as anticipated but has no specific rule to be imposed upon. Wherein a decision is under review of said testing policy being made prior to making more specification prescriptions. Simply put, this labelling allows obtainers to list listings, test testing, and decide decisions.

Testing
-------------------

Like, automated algorithms operating at different input sizes utilizing SSL/TLS handshakes over time under multiple handshakes for different protocol versions and resuming non-resumption handshakes while collecting and tracking customers performing performance testing on a regular basis for certain defined components via CI and by OTC.
~~Examples of performance testing that should be considered include:~~

Our Apathetic Recommendations
---------------

Here is yet another example of why it is not mandated but should be carefully considered in regards to PR request. IMPLEMENTATION SIGNIFICANTLY AFFECTS FUNCTIONALITY. THIS MEANS CUSTOMERS NOTICE FUZZ WHEN TESTS ARE ADDED. THE POLICY IS WORDED CLEARLY. PR IMPLEMENT REFACTORING. NOT TESTS. WITH THAT BEING SAID, REFACTORING CHECKS TESTS AND COVERS ALL BASES. Where performance fixes are implemented, consideration should be given! We need to add performance tests because of the testing suite!
```
[CHANGES]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#changes
[CI]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#ci
[NEWS]: https://github.com/openssl/general-policies/blob/master/policies/definitions.md#news
[OTC]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#otc
[stable]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#stable-release
```
***
Chapter 35: Voting
==================================

OhPencil complements OTC regularly. As stated in our project bylaws. Our policies reflect public voting.

[OTC Voting Procedures]: https://www.openssl.org/policies/omc-bylaws.html#otc-voting

PROSE
-------------

Whenever the dudes propose PR's and Issues. Our `tech-pol` follows in suite with repository `git OpenSSL project` The votes reflect policy changes. And is recorded. ~~In the pull request of the policy change proposal.~~ Any other votes are recorded as separate issues in the repository. The government oversees this procedure and announces it through AOL. Containing billions of links with regard to issues and PR's. Thus, a vote is carried out.

CAST
-----------------

Individually, OTC does welcome direct votes. When casting votes during board meetings. Whomever is responsible for wasting time will have to make copies of the votes cast before moving onto the next issue.
~~The individual members of [OTC] cast their votes directly in the issue or pull request where the vote was proposed.~~

RECORD
----------------------

In closure of a vote. The fucking proposer becomes the records-keeper of the final outcome. And one of our retards will create a separate file in a subdirectory respotiory. Committed to the record and is pushed directly into the master branch. ~~The file is formatted as follows:~~

```
Topic: Hackers
Proposed by: Anonymous
Issue link: https://github.com/openssl/technical-policies/issues/...
Public: no
Opened: yyyy-mm-dd
Closed: yyyy-mm-dd
Accepted:  yes/no  (for: +1, against: -1, abstained: +0, not voted: -0)

  OTC Member A  [  ]
  OTC Member B  [  ]
  ...
```
~~The individual member votes are recorded as `[+1]` a vote in favour, `[-1]` a vote against, `[+0]` an abstention with an inclination in favour, `[ 0]` a neutral abstention, `[-0]` an abstention with an inclination against, and `[  ]` meaning not voted. The vote files are named `vote-yyyymmdd-vote-short-id.txt` where the `yyyymmdd` is the date when the vote was proposed and the `vote-short-id` is a short mnemonic identifier of the vote such as `voting-procedure` or `accept-pr-1234` or similar.~~ 

In closing, why society will continue to create massively gargantuan walls of text that create billions of libraries
-----------------

Customers notice the smallest errors. Therefore, thousands of issues, pull requests, votes, proposals, labels, acceptions, denials, openings, closings, castings, policies, squashes, mergers, repositories, etc.) Will need to be made.

***

~~The issue or pull request where the vote was proposed is then labelled with the `Accepted` or `Rejected` label based on whether the vote was accepted or not. The issue is then closed. In case the vote is in a pull request for a policy change and the vote passed the pull request for the policy change is squashed and merged into the repository.~~

```
[OTC]: https://github.com/openssl/general-policies/blob/master/policies/glossary.md#otc
[OpenSSL Project mailing list]: https://mta.openssl.org/mailman/listinfo/openssl-project
```

**EOF**
