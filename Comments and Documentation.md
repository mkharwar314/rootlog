> Learn how to explain code, document program behavior, and make software easier to understand, maintain, and audit.

## 1. Introduction

Comments and documentation help programmers understand how code works and why particular decisions were made.

Although both explain code, they serve slightly different purposes.

- **Comments:** Explanations written inside source code.
    
- **Documentation:** Structured information describing a program, its features, usage, configuration, and behavior.
    

Good documentation makes code easier to maintain, debug, review, and collaborate on.

## 2. Comments in Programming

A comment is text written in source code that is ignored by the compiler or interpreter as executable instructions.

Comments help explain:

- The purpose of code.
    
- Complex logic.
    
- Important decisions.
    
- Known limitations.
    
- Temporary development notes.
    

### 2.1 Single-Line Comments

A single-line comment explains a particular statement or section.

**Python:**

```
# Store the user's age
age = 18
```

**C:**

```
// Store the user's age
int age = 18;
```

**JavaScript:**

```
// Store the user's age
let age = 18;
```

### 2.2 Multi-Line Comments

Multi-line comments can explain larger sections of code.

**C and JavaScript:**

```
/*
This program calculates
the total of two numbers.
*/
```

```
/*
This function validates
a username.
*/
```

Python does not have a separate multi-line comment syntax. Multiple `#` lines are commonly used:

```
# This program calculates
# the total of two numbers.
```

### 2.3 Inline Comments

Inline comments appear on the same line as a statement.

```
port = 443  # Default HTTPS port
```

Use inline comments only when they clarify something useful. Avoid explaining obvious operations.

## 3. Comments in Python

Python supports comments using the `#` symbol.

### Example

```
# Accept a port number
port = int(input("Enter port: "))

# Check whether the port is valid
if 1 <= port <= 65535:
    print("Valid port")
```

### Important Python Documentation Distinction

Triple-quoted strings are often used for documentation strings, also called _docstrings_.

They are not technically Python comment syntax.

```
"""
This program checks
whether a port number is valid.
"""

port = 443
print(port)
```

A docstring becomes documentation when it is placed in an appropriate location, such as at the beginning of a module, class, or function.

## 4. Docstrings in Python

A docstring describes what a module, class, or function does.

### Example

```
def add_numbers(a, b):
    """
    Add two numbers.

    Args:
        a: First number.
        b: Second number.

    Returns:
        The sum of both numbers.
    """
    return a + b
```

You can access a function's docstring using:

```
print(add_numbers.__doc__)
```

### Common Docstring Information

A useful function docstring may describe:

|Element|Description|
|---|---|
|Purpose|What the function does|
|Parameters|Values accepted by the function|
|Return value|What the function returns|
|Exceptions|Errors that may occur|
|Examples|How to use the function|

## 5. Documentation in C and JavaScript

Different languages and development environments use different documentation conventions.

### 5.1 Documentation in C

C programs commonly use comments to describe functions and important operations.

```
#include <stdio.h>

/*
 * Displays a welcome message.
 */
void welcome() {
    printf("Welcome to ROOTLOG\n");
}

int main() {
    welcome();
    return 0;
}
```

Tools such as Doxygen can generate structured documentation from specially formatted comments.

### 5.2 Documentation in JavaScript

JavaScript commonly uses JSDoc-style comments.

```
/**
 * Adds two numbers.
 *
 * @param {number} a - First number.
 * @param {number} b - Second number.
 * @returns {number} Sum of the numbers.
 */
function addNumbers(a, b) {
    return a + b;
}
```

JSDoc tools can use these comments to generate documentation.

## 6. Types of Software Documentation

Documentation exists at different levels.

### 6.1 Code Documentation

Explains individual functions, classes, modules, and complex logic.

### 6.2 API Documentation

Explains how developers can interact with an application's programming interface.

It may include:

- Endpoints.
    
- HTTP methods.
    
- Request parameters.
    
- Authentication requirements.
    
- Response formats.
    
- Error codes.
    

### 6.3 User Documentation

Explains how users operate a software application.

Examples:

- Installation instructions.
    
- User guides.
    
- Frequently asked questions.
    
- Troubleshooting instructions.
    

### 6.4 Technical Documentation

Explains the internal design and technical operation of a system.

Examples:

- System architecture.
    
- Database structure.
    
- Configuration.
    
- Dependencies.
    
- Deployment procedures.
    

### 6.5 Project Documentation

Explains the purpose, setup, usage, and contribution process of a software project.

A common example is a `README.md` file.

## 7. README Files

A README file is usually the starting point for understanding a software project.

It is commonly written in Markdown.

### Common README Sections

|Section|Purpose|
|---|---|
|Project Title|Identifies the project|
|Description|Explains what it does|
|Features|Lists important capabilities|
|Requirements|Lists dependencies|
|Installation|Explains setup|
|Usage|Shows how to use the project|
|Examples|Demonstrates functionality|
|License|Describes usage permissions|
|Contributing|Explains contribution guidelines|

### Example README

```
# Port Validator

A simple Python program that validates
network port numbers.

## Features

- Accepts a port number.
- Checks numeric input.
- Validates the permitted range.

## Requirements

- Python 3

## Usage

Run:

python port_validator.py

## Example

Input: 443
Output: Valid port
```

## 8. Documentation and Version Control

Documentation should be maintained alongside source code.

Git makes it possible to track changes to both.

Useful Git commands:

```
git status
git add README.md
git commit -m "Update project documentation"
git log
```

This allows developers to understand when documentation changed and review its history.

Related note: [[Git and Version Control]]

## 9. Documentation in Cybersecurity

Documentation is especially important in cybersecurity because security work often requires reproducibility, evidence, and accountability.

### 9.1 Security Tool Documentation

Security tools should explain:

- Supported options.
    
- Required permissions.
    
- Input formats.
    
- Output formats.
    
- Limitations.
    
- Safe usage.
    

### 9.2 Digital Forensics Documentation

Forensic investigations require detailed records of actions and observations.

Documentation may include:

- Case identification.
    
- Evidence description.
    
- Acquisition details.
    
- Hash values.
    
- Tools and versions.
    
- Analysis steps.
    
- Findings.
    
- Limitations.
    

A forensic examiner should distinguish observed facts from assumptions and interpretations.

Related note: [[Digital Forensics]]

### 9.3 Vulnerability Reports

A vulnerability report should clearly describe:

1. Vulnerability title.
    
2. Affected system.
    
3. Description.
    
4. Steps to reproduce.
    
5. Evidence.
    
6. Impact.
    
7. Recommended remediation.
    

### 9.4 Incident Response Documentation

Incident response records help security teams understand:

- What happened.
    
- When it happened.
    
- Which systems were affected.
    
- What actions were taken.
    
- What evidence was collected.
    
- What remains unresolved.
    

## 10. Good Documentation Practices

1. Use clear and simple language.
    
2. Explain why complex code exists.
    
3. Keep documentation consistent with the actual code.
    
4. Update documentation when functionality changes.
    
5. Include examples where they improve understanding.
    
6. Document assumptions and limitations.
    
7. Avoid unnecessary comments.
    
8. Never include passwords, API keys, or private credentials.
    
9. Separate verified facts from assumptions.
    
10. Use meaningful names for functions and variables.
    

### Poor Comment

```
# Add 1 to count
count = count + 1
```

The code already explains the operation.

### Better Comment

```
# Retry count is limited to prevent endless authentication attempts.
retry_count += 1
```

The comment explains the reason behind the operation.

## 11. Documentation Security Risks

Documentation itself can introduce security risks if handled carelessly.

Examples:

- Publishing API keys or passwords.
    
- Exposing internal IP addresses or sensitive infrastructure details.
    
- Publishing unpatched software versions unnecessarily.
    
- Including private user information.
    
- Providing outdated security instructions.
    
- Documenting dangerous commands without explaining their impact.
    

**Best practice:** Review documentation before publishing it, especially when the project is public.

## 12. Common Documentation Tools

|Tool|Purpose|
|---|---|
|Markdown|Writing formatted documentation|
|README.md|Project overview|
|Doxygen|Documentation generation for several languages, including C and C++|
|JSDoc|JavaScript documentation|
|Sphinx|Documentation generation, commonly used with Python|
|MkDocs|Building documentation websites|
|Git|Tracking documentation changes|
|Obsidian|Organizing interconnected Markdown notes|

## 13. Key Takeaways

- Comments explain code inside source files.
    
- Documentation describes how software works and how to use it.
    
- Python uses `#` for comments and docstrings for structured documentation.
    
- C and JavaScript support documentation through comment conventions.
    
- README files provide an overview of software projects.
    
- API and technical documentation help developers understand systems.
    
- Cybersecurity documentation supports evidence, accountability, and reproducibility.
    
- Documentation must never expose secrets or sensitive information.
    

## 14. Questions and Doubts

1. What is a comment?
    
2. What is the difference between comments and documentation?
    
3. How do you write a single-line comment in Python?
    
4. What is a Python docstring?
    
5. What is the purpose of a README file?
    
6. What information belongs in API documentation?
    
7. Why is documentation important in digital forensics?
    
8. What security risks can result from publishing documentation?
    

## 15. Practical Tasks

### Task 1 — Add Comments

Write a Python program that accepts two numbers and calculates their sum.

Add useful comments explaining the program's purpose and important operations.

### Task 2 — Write a Docstring

Create a function named `validate_port()`.

Add a docstring describing:

- Its purpose.
    
- Its parameter.
    
- Its return value.
    

### Task 3 — Create a README

Create a `README.md` for your port validation program.

Include:

- Project title.
    
- Description.
    
- Features.
    
- Requirements.
    
- Installation or setup.
    
- Usage.
    
- Example output.
    

### Task 4 — Document a Security Tool

Choose Nmap or Wireshark and write a short technical description containing:

- Purpose.
    
- Main features.
    
- Basic usage.
    
- Limitations.
    
- Security considerations.
    

Use official documentation as a reference.

## Related Notes

- [[Introduction to Programming]]
    
- [[Programming Languages]]
    
- [[Variables and Constants]]
    
- [[Input and Output]]
    
- [[Functions and Modular Programming]]
    
- [[Python Programming]]
    
- [[C and C++ Programming]]
    
- [[JavaScript Programming]]
    
- [[Git and Version Control]]
    
- [[Digital Forensics]]
    
- [[Practical Labs]]