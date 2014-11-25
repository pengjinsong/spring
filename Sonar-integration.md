## Introduction

This document defines the quality profile the Spring Framework is using for Sonar. It is primarily intended as a revision history of the rules the team has decided to enable (or disable) and why.

## Quality profile

The `Spring Framework` quality profile is based on the standard `Sonar Way` profile. Note that no findbugs-related rule can be enabled as Java8 support is not there yet.

The `Sonar Way` brings 114 rules by default.

### Disabled rules

These are the rules that we have disabled:

* **Right curly brace and next "else", "catch" and "finally" keywords should be located on the same line**: our [Spring Framework Code Style](https://github.com/spring-projects/spring-framework/wiki/Spring-Framework-Code-Style) uses a different style
* **Useless parentheses around expressions should be removed to prevent any misunderstanding**: we actually use such extra parentheses, especially with the [ternary operator](https://github.com/spring-projects/spring-framework/wiki/Spring-Framework-Code-Style#ternary-operator)
* **Tabulation characters should not be used**: we do ask our code to use tabs and not spaces
* **Throwable and Error classes should not be caught**: framework code requires such arrangement in many places
* **Generic exceptions Error, RuntimeException, Throwable and Exception should never be thrown**: same as above
* **Constant names should comply with a naming convention**: states that any `public static final` field is a constant. We address this specifically in [constant names](https://github.com/spring-projects/spring-framework/wiki/Spring-Framework-Code-Style#constant-names)
* **Loggers should be "private static final" and should share a naming convention**: framework code requires non static loggers and some use cases require several loggers in the same class.
* **Methods should not be empty**: as the framework uses this mechanism for all kinds of extensions points.
* **Return an empty array instead of null.** as we disagree with this rule the way we use it. `null` has an additional semantic that we use compared to the one provided by an empty array
* **Thread.run() and Runnable.run() should not be called directly** as framework code actually requires such call

## Under consideration

These are the rules that we may decide to disable eventually:

* **Throws declarations should not be redundant**: this violation is thrown when an `@Override` method declares a `RuntimeException`
* **Avoid commented-out lines of code**
* **Expressions should not be too complex**