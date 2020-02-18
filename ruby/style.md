Ruby Style Guide
================
* Avoid conditional modifiers (lines that end with conditionals).
* Avoid multiple assignments per line (one, two = 1, 2).
* Avoid organizational comments (# Validations).
* Avoid ternary operators (boolean ? true : false). Use multi-line if instead to emphasize code branches.
* Avoid explicit return statements.
* Avoid using semicolons.
* Avoid bang (!) method names. Prefer descriptive names.
* Don't include spaces after (, [ or before ], ).
* Don't use self explicitly anywhere except class methods (def self.method) and assignments (self.attribute =).
* Don't vertically align tokens on consecutive lines.
* If you break up a chain of method invocations, keep each method invocation on its own line. Place the . at the end of each line, except the last.
* If you break up a hash, keep the elements on their own lines and closing curly brace on its own line.
* Indent continued lines two spaces.
* Indent private methods equal to public methods.
* Name variables created by a factory after the factory (user_factory creates user).
* Prefer nested class and module definitions over the shorthand version
* Prefer detect over find.
* Prefer select over find_all.
* Prefer map over collect.
* Prefer reduce over inject.
* Prefer double quotes for strings.
* Prefer && and || over and and or.
* Prefer ! over not.
* Prefer &:method_name to { |item| item.method_name } for simple method calls.
* Prefer if over unless.
* Use _ for unused block parameters.
* Prefix unused variables or parameters with underscore (_).
* Suffix variables holding a factory with factory (user_factory).
* Use 2 space indentation (no tabs).
* Use a leading underscore when defining instance variables for memoization.
* Use an empty line between methods.
* Use spaces after commas, after colons and semicolons, around { and before }.
* Use %{} for single-line strings containing double-quotes that require interpolation.
* Use {...} for single-line blocks. Use do..end for multi-line blocks.
* Use ? suffix for predicate methods.
* Use def with parentheses when there are arguments.
* Don't use spaces after required keyword arguments.
* Use each, not for, for iteration.
* Use a trailing comma after each item in a multi-line list, including the last item.
* Use heredocs for multi-line strings.
* Prefer private over protected for non-public attr_readers, attr_writers, and attr_accessors.
* Order class methods above instance methods.
* Prefer method invocation over instance variables.
