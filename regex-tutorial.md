# Regex Tutorial: Matching an Email Regular Expression

This tutorial provides a comprehensive guide on matching email regular expressions (regex) using JavaScript within the domain of Computer Science. The aim is to offer a clear understanding of regex components to both novices and scholars through detailed explanations and example analysis. Throughout this tutorial, we will explore the intricacies of email regex, dissecting the components of a regex pattern designed to validate email addresses. We will elucidate how each part contributes to ensuring accurate and reliable email validation.

## Summary

This tutorial will focus on the analysis of the featured regular expression (regex) shown below, examining each regex component to ensure that both novices and scholars can comprehend the material with utmost clarity. 

Featured Regular Expression:
```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
The tutorial will provide a detailed breakdown of each component, explaining its role and functionality within the email validation regex pattern. By the end of this tutorial, readers will have gained a thorough understanding of how these components work together to create an effective and reliable email validation regex.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping](#grouping)
- [Bracket Expressions](#bracket-expressions)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors are special characters in regular expressions that define the position of the pattern within the input string. In the context of email validation, such as in the regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, anchors ensure that the entire input string matches the specified pattern, rather than just a part of it.

There are 2 main types of anchors:
- Start Anchor "^": Asserts that the pattern must match the start of the string.
- End Anchor "$": Asserts that the pattern must match the end of the string.

Anchors define the boundaries of the text that the regular expression should match. Consider the following examples:

- The regex `^hello$` matches only the exact string "hello". It won't match "hello world" or "say hello" because the pattern is not at the start or end of the string, respectively.
- The regex `^[A-Z][a-z]+$` matches strings that start with an uppercase letter, followed by one or more lowercase letters, and nothing else. It will match "John" but not "john" or "John Doe".

In email validation, anchors are crucial because they ensure that the entire email address adheres to the specified pattern. This is essential for accurate validation, as it prevents partial matches or unwanted results. By setting boundaries at the start and end of the string, anchors guarantee that the pattern matches only the intended text.

In summary, anchors play a vital role in defining the position of the pattern within the input string and ensure accurate and reliable validation, particularly when validating email addresses using a regex like `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`.

### Quantifiers

Quantifiers in regular expressions specify the number of times a preceding pattern should match. They are placed after a character, character class, or group to determine the minimum and maximum occurrences of the pattern. Understanding quantifiers is crucial for creating precise and flexible regular expressions.

In the email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, there are two types of quantifiers used:

1. `+` quantifier: Matches one or more occurrences of the preceding pattern.
- In the first capturing group `([a-z0-9_\.-]+)`, the `+` quantifier ensures that the pattern `[a-z0-9_\.-]` (lowercase letters, digits, underscores, dots, or hyphens) occurs at least once, but can also occur multiple times consecutively.
- The second capturing group `([\da-z\.-]+)` uses the `+` quantifier to match one or more digits, lowercase letters, dots, or hyphens.
2. `{2,6}` quantifier: Matches between 2 and 6 occurrences of the preceding pattern.
- The third capturing group `([a-z\.]{2,6})` uses the `{2,6}` quantifier to match a sequence of 2 to 6 lowercase characters or dots. This ensures that the email address ends with a valid two to six letter top-level domain.

Here's an example of how quantifiers work in the email validation regex:

- `([a-z0-9_\.-]+)`: Matches one or more lowercase characters, digits, underscores, dots, or hyphens before the @ symbol.
- `([\da-z\.-]+)`: Matches one or more digits, lowercase characters, dots, or hyphens after the @ symbol and before the period.
- `([a-z\.]{2,6})`: Matches a sequence of 2 to 6 lowercase letters or dots after the period, representing the top-level domain.

In summary, the email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` matches a valid email address that follows this pattern:

1. Begins with one or more lowercase letters, hyphons, numbers, dots, or underscores
2. Next followed by the @ symbol
3. Next followed by one or more lowercase letters, numbers, dots, or hyphens
4. Next followed by a period
5. Ending with a two to six character top-level domain

Quantifiers are essential for controlling the number of occurrences of a pattern in regex. By understanding and properly using quantifiers, you can create more precise and flexible regular expressions for various use cases.

### Character Classes

Character classes, sometimes called character sets, are regular expressions that represent targeted sets of characters. They allow you to simplify and shorten regex patterns, making them more readable and easier to understand.

In the email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, various character classes and related elements are used to ensure accurate matching of email addresses. These elements include character sets, metacharacters, and repeating character classes.

#### Character Sets:
Character sets are defined within square brackets and represent a single character match from the specified range. The email validation regex uses the following character sets:

- `[a-z0-9_\.-]`: Matches any lowercase letter, digit, underscore, dot, or hyphen
- `[\da-z\.-]`: Matches any digit, lowercase letter, dot, or hyphen
- `[a-z\.]`: Matches any lowercase letter or dot

**Example**: The character set `[a-zA-Z0-9]` matches any single alphanumeric character, which can be an uppercase letter, a lowercase letter, or a digit.

#### Metacharacters:

Metacharacters are characters with special meanings in regex, such as the dot `(.)`. Inside character classes, some metacharacters lose their special meaning and are treated as literals. In the email validation regex:

- The hyphen `(-)` and the dot `(.)` are metacharacters placed inside character sets `[a-z0-9_\.-]` and `[\da-z\.-]`. They do not need to be escaped with a backslash and are treated as literal characters.
- The hyphen `(-)` is used as a literal character without escaping because it is placed at the beginning or end of the character set.

**Example**: The character set `[a-z0-9\.-]` matches any lowercase letter, digit, dot, or hyphen. The dot `(.)` and hyphen `(-)` are treated as literal characters inside the character set.

#### Repeating Character Classes:
The email validation regex uses quantifiers to indicate repeating character classes:

- The + quantifier matches one or more occurrences of the preceding character class or set, as in `[a-z0-9_\.-]+ and [\da-z\.-]+`
- The `{2,6}` quantifier defines a specific range of repetitions for the preceding character class or set, as in `[a-z\.]{2,6}`, which matches 2 to 6 occurrences of lowercase letters or dots

**Example**: The regex pattern `[a-z]{3,5}` matches a string containing lowercase letters repeated 3 to 5 times, such as "abc", "defg", or "hijkl".

#### Conclusion
Character classes are essential for creating concise and readable regular expressions. They allow us to define specific sets of characters and patterns using simple syntax. By understanding how to use character sets, metacharacters inside character classes, and repeating character classes, we can create efficient and effective regex patterns for various use cases, such as validating email addresses.

### Grouping

Grouping is a construct in regular expressions are used to group together one or more characters or sub-expressions and treat them as a single unit within the expression. They are enclosed in parentheses `()` and serve the following purposes:

- Applying quantifiers to a group of characters
- Capturing a specific part of the match for later use
- Creating backreferences to previously matched groups
- Applying alternation to a group of characters

The email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` contains three grouping constructs enclosed in parentheses `()`. Each group captures a different part of the email address:

- Local-Part: `([a-z0-9_\.-]+)`
- Domain: `([\da-z\.-]+)`
- Top-Level Domain: `([a-z\.]{2,6})`

#### Local-Part:
The first grouping construct `([a-z0-9_\.-]+)` matches the username of the email address (the part before the @ symbol). It ensures that the username follows a valid format and matches one or more characters that can be lowercase letters, numbers, underscores, dots, or hyphens.

**Example**: Consider the email address `john_doe.123@example.com`. The local-part `john_doe.123` matches the regex `([a-z0-9_\.-]+)` because it contains lowercase letters, numbers, underscores, and dots, all of which are allowed characters in the local-part of an email address.

#### Domain

The second grouping construct `([\da-z\.-]+)` matches the domain name of the email address. It ensures that the domain name follows a valid format and matches one or more characters that can be numbers, lowercase letters, dots, or hyphons.

**Example**: Consider the email address `john.doe@sub-domain.example.com`. The domain `sub-domain.example` matches the regex `([\da-z\.-]+)` because it contains lowercase letters, dots, and hyphens, all of which are allowed characters in the domain part of an email address.

#### Top-Level Domain

The third grouping construct `([a-z\.]{2,6})` matches the top-level domain of the email address. It ensures that only valid top-level domains are accepted and matches between 2 to 6 characters that can be:

- Lowercase letters: `a-z`
- Dots: `.`

**Example**: Consider the email address `john.doe@example.com`. The top-level domain com matches the regex `([a-z\.]{2,6})` because it contains lowercase letters and has a length of 3 characters, which falls within the valid range of 2 to 6 characters.

#### Conclusion
Grouping constructs are essential for validating different parts of an email address using regex. The email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` uses three grouping constructs to capture and validate the local-part, domain, and top-level domain of an email address. By understanding how these grouping constructs work together, you can effectively validate email addresses and ensure they adhere to the accepted standards.

### Bracket Expressions

Bracket expressions define a set of characters that can be matched within a single position in a text string. They are denoted by square brackets `[...]`, and any character enclosed within these brackets becomes part of the allowed set. Bracket expressions can contain individual characters and even define character ranges using a hyphen -, such as a-z for all lowercase letters or 0-9 for digits. The purpose of bracket expressions is to create flexible patterns that match various combinations of characters in your target text.

In the email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, there are three main bracket expressions, each corresponding to a different part of the email address:

- Local address: `[a-z0-9_\.-]`
- Domain address: `[\da-z\.-]`
- Top-Level Domain address: `[a-z\.]`

Let's break down each of these bracket expressions:

#### Bracket Expression for Local Part:
The bracket expression `[a-z0-9_\.-]` matches any single character that is a lowercase letter `(a-z)`, a digit `(0-9)`, an underscore `(_)`, a dot `(\.)`, or a hyphen `(-)`. This expression is used to match the local part (username) of the email address.

**Example** : Consider the email address `john_doe.1234@example.com`. The local part `john_doe.1234` matches the bracket expression `[a-z0-9_\.-]` because it contains lowercase letters, digits, underscores, and dots.

#### Bracket Expression for Domain:
The bracket expression `[\da-z\.-]` matches any single character that is a digit `(\d)`, a lowercase letter `(a-z)`, a dot `(\.)`, or a hyphen `(-)`. This expression is used to match the domain part of the email address.

**Example**: Consider the email address `john.doe@sub-domain.example.com`. The domain part sub-domain.example matches the bracket expression [\da-z\.-] because it contains lowercase letters, dots, and a hyphen.

#### Bracket Expression for Top-Level Domain:
The bracket expression `[a-z\.]` matches any single character that is a lowercase letter `(a-z)` or a dot `(\.)`. This expression is followed by the quantifier `{2,6}`, which specifies that the matched characters must occur between 2 and 6 times, inclusive. This combination is used to match the top-level domain of the email address.

**Example**: Consider the email address `john.doe@example.co.uk`. The top-level domain part co.uk matches the bracket expression `[a-z\.]{2,6}` because it contains lowercase letters and a dot, and its length falls within the specified range of 2 to 6 characters.

#### Conclusion
The email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` utilizes bracket expressions to define character sets for the local part, domain, and top-level domain parts of an email address. These bracket expressions, combined with other regex components, ensure that the email address adheres to the proper structure and formatting. By understanding how bracket expressions work and their role in the overall regex pattern, you can effectively validate email addresses and extract specific parts of the address for further processing or analysis.

### Escape Character

Escape Characters are an essential aspect of regular expressions (regex), allowing for accurate pattern matching by treating special characters as literals and representing characters that cannot be directly typed. In the context of the email validation regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, escape characters play a crucial role in ensuring the correct interpretation of certain characters.

##### Backslash (\):
The backslash is a common escape character used to treat metacharacters as literals in regex. In the email validation regex, the dot `(.)` is escaped with a backslash, like this: `\.`. This ensures that the dot is treated as a literal period instead of a metacharacter with a special meaning.

Example: Consider the following email addresses:

- john.doe@example.com (valid)
- john@doe@example.com (invalid)

The email validation regex uses `\`. to match a literal period within the email address. This ensures that the regex correctly matches valid email addresses, like `john.doe@example.com`, while rejecting invalid ones, such as `john@doe@example.com`.

If the dot `(.)` were not escaped, it would act as a wildcard character, potentially matching any character in its place, leading to incorrect matches.

#### Metacharacters Inside Character Classes:

Metacharacters have special meanings in regex, but inside character classes, some of them lose their special meaning and are treated as literals. In the email validation regex, the hyphen `(-)` is used as a literal character inside the character classes `[a-z0-9_\.-]` and `[\da-z\.-]`. When placed at the beginning or end of a character class, the hyphen doesn't need to be escaped with a backslash.

Example: Consider the following email addresses:

- john-doe@example.com (valid)
- john--doe@example.com (valid)
- john_doe@example.com (valid)

The email validation regex uses the hyphen `(-)` as a literal character inside the character classes, allowing it to match valid email addresses containing hyphens, such as `john-doe@example.com` and `john--doe@example.com`. The underscore `(_)` is also included in the character class `[a-z0-9_\.-]`, enabling the regex to match email addresses with underscores in the username part, like `john_doe@example.com`.

#### Escape Sequences:

Escape sequences represent characters that cannot be directly typed or have special meanings. They start with a backslash `(\)` followed by a letter or combination of letters. In the email validation regex, `\d` is an escape sequence representing any digit from 0 to 9, serving as a shorthand for `[0-9]`.

Example: Consider the following email addresses:

- john2023@example.com (valid)
- john.doe123@example.com (valid)
- 2023john@example.com (invalid)

The escape sequence `\d` in the email validation regex allows it to match valid email addresses containing digits, such as `john2023@example.com` and `john.doe123@example.com`. However, it rejects email addresses where the domain part starts with a digit immediately after the `'@'` symbol, like `2023john@example.com`, as this is not allowed according to the regex pattern.

#### Conclusion
Character escapes are crucial for ensuring accurate pattern matching in regular expressions. They allow special characters to be treated as literals and represent characters that cannot be directly typed. By properly utilizing character escapes, such as the backslash, metacharacters inside character classes, and escape sequences, the email validation regex can effectively match valid email addresses while rejecting invalid ones.

## Author

Created by Joyce77777777

Deployed gist link: https://gist.github.com/Joyce77777777/19c44168ef8d8325e353d4488bcddc27

Repository link: https://github.com/Joyce77777777/Regex-Tutorial/
