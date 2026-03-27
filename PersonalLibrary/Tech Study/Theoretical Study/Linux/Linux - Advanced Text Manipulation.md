# 1. `regex` (Regular Expressions)

Regular expressions, often shortened to regex, are a powerful tool for pattern-based selection. Understanding them is fundamental to mastering text manipulation in Linux. While there are many apps to learn Linux, diving into core concepts like `regular expression linux` is the quickest way to linux advanced proficiency. They use special notations, some of which are similar to wildcards like `*`.

Let's explore some of the most common regex operators, which are nearly universal across programming languages. We will use the following text as our example:

	`sally sells seashells`
	`by the seashore`

### Anchoring to the Start of a Line

The caret `^` symbol matches the beginning of a line. It ensures that your pattern appears only at the start.

`^by`

This pattern would match the line "by the seashore" but not "sally sells seashells"

### Anchoring to the End of a Line

The dollar `$` symbol matches the end of a line. It is the counterpart to the `^` anchor.

`seashore$`

This pattern would match the line "by the seashore" because it ends with "seashore".

### Matching any Single Character

The period `.` is a wildcard that matches any single character.

`b.`

In our example, this would match "by".

### Using Brackets for Character Sets

Brackets `[ ]` allow you to specify a set of characters to match. This provides more control than the `.` wildcard.

`s[ae]lls`

This would match "sells" and would also match "salls".

You can also use brackets to specify what *not* to match. When the caret `^` is the first character inside the brackets, it negates the set, matching any character *except* those listed.

`s[^e]lls`

This would match "salls" but not "sells".

Finally, brackets support ranges to define a large set of characters efficiently.

`d[a-c]g`

This pattern will match "dag", "dbg", and "dcg". Be aware that ranges are case-sensitive. For example, `[a-c]` will not match `A`, `B`, or `C`. 

