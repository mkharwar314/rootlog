> Learn how to install, update, remove, inspect, and manage Python libraries and their dependencies using package management tools.

## 1. What Is Package Management?

**Package management** is the process of installing, updating, configuring, and removing software packages.

In Python, packages provide reusable functionality that developers can include in their applications.

For example:

- `requests` — makes HTTP requests.
    
- `flask` — helps build web applications.
    
- `numpy` — supports numerical computing.
    
- `scapy` — supports packet manipulation and network analysis.
    
- `pandas` — supports data analysis.
    

Instead of writing every feature from scratch, developers can use existing packages.

## 2. What Is pip?

**pip** is Python's standard package installer.

It downloads and installs packages from package repositories, commonly the Python Package Index (PyPI).

Official website: [https://pypi.org/](https://pypi.org/)

Check pip:

```
python -m pip --version
```

Upgrade pip:

```
python -m pip install --upgrade pip
```

Using `python -m pip` helps ensure that pip operates with the Python interpreter you intend to use.

## 3. Installing Python Packages

Use the `install` command to install a package.

Example:

```
python -m pip install requests
```

Install multiple packages:

```
python -m pip install requests flask numpy
```

Install a specific version:

```
python -m pip install requests==2.32.3
```

Install a minimum version:

```
python -m pip install "requests>=2.30"
```

**Important:** Version constraints affect which package versions pip is allowed to select. Choose versions based on your project's compatibility requirements.

## 4. Viewing Installed Packages

List installed packages:

```
python -m pip list
```

Display information about a package:

```
python -m pip show requests
```

Check whether a package is installed:

```
python -m pip show flask
```

If the package is not installed in the active environment, pip will report that it cannot find it.

## 5. Updating Packages

To upgrade a package:

```
python -m pip install --upgrade requests
```

To upgrade pip itself:

```
python -m pip install --upgrade pip
```

**Security consideration:** Updating packages can fix vulnerabilities, but an update may introduce compatibility problems. Test important applications after changing dependency versions.

## 6. Uninstalling Packages

Remove an installed package:

```
python -m pip uninstall requests
```

pip asks for confirmation before uninstalling.

To skip the confirmation:

```
python -m pip uninstall -y requests
```

Uninstalling a package does not necessarily remove every dependency that was originally installed alongside it.

## 7. Understanding PyPI

**Python Package Index (PyPI)** is the public repository used to distribute Python packages.

Website: [https://pypi.org/](https://pypi.org/)

Developers can:

- Search for packages.
    
- Read package documentation.
    
- Check release histories.
    
- Inspect supported Python versions.
    
- Review project metadata.
    
- Find installation instructions.
    

Example:

```
python -m pip install requests
```

pip normally searches the configured package index, commonly PyPI.

## 8. Requirements Files

A requirements file records the dependencies needed by a project.

The common filename is:

```
requirements.txt
```

Example:

```
requests==2.32.3
flask==3.0.3
numpy==2.1.0
```

Install all listed packages:

```
python -m pip install -r requirements.txt
```

Generate a list of installed packages:

```
python -m pip freeze > requirements.txt
```

Inspect dependencies:

```
python -m pip freeze
```

**Difference:**

|Command|Purpose|
|---|---|
|`pip list`|Displays installed packages in a readable table|
|`pip show`|Displays details about a particular package|
|`pip freeze`|Outputs installed packages in requirements-file format|
|`pip install -r`|Installs packages listed in a file|

A frozen list is useful for reproducing an environment, but it may include packages that your application does not directly need.

## 9. Dependency Management

A **dependency** is an external package or library required by an application.

For example:

```
Main Application
       |
       v
    Flask
       |
       v
    Werkzeug
```

The application uses Flask, and Flask depends on other packages.

pip resolves and installs required dependencies during installation.

### Dependency Conflicts

A conflict occurs when packages require incompatible versions of another dependency.

Example:

```
Package A requires Library X >= 2.0
Package B requires Library X < 2.0
```

Both requirements cannot be satisfied by the same installed version.

Possible solutions:

1. Check package compatibility.
    
2. Use compatible package versions.
    
3. Separate projects into different virtual environments.
    
4. Review dependency requirements before upgrading.
    

## 10. Package Management Inside Virtual Environments

Package management should normally happen inside a project's virtual environment.

Example workflow:

Create a project:

```
mkdir PythonProject
cd PythonProject
```

Create a virtual environment:

Windows:

```
python -m venv .venv
```

Linux:

```
python3 -m venv .venv
```

Activate it.

Windows PowerShell:

```
.\.venv\Scripts\Activate.ps1
```

Linux:

```
source .venv/bin/activate
```

Install a package:

```
python -m pip install requests
```

Verify:

```
python -m pip list
```

This keeps the project's dependencies separate from other Python projects.

## 11. Understanding Package Versions

Package versions help developers identify releases and manage compatibility.

A common version format is:

```
MAJOR.MINOR.PATCH
```

Example:

```
2.32.3
```

Typically:

- **Major:** May introduce incompatible changes.
    
- **Minor:** May introduce new functionality while maintaining compatibility.
    
- **Patch:** Usually contains bug fixes.
    

This is a common convention, not a guarantee that every Python package follows semantic versioning exactly.

### Common Version Constraints

|Constraint|Meaning|
|---|---|
|`==2.0.0`|Exactly version 2.0.0|
|`>=2.0.0`|Version 2.0.0 or newer|
|`<=2.0.0`|Version 2.0.0 or older|
|`!=2.0.0`|Excludes version 2.0.0|
|`~=2.0`|Compatible release constraint|

Always check the package's actual compatibility requirements.

## 12. Alternative Python Package Management Tools

Although pip is widely used, other tools support additional workflows.

### 12.1 Conda

Conda manages packages and environments, including non-Python dependencies.

It is commonly used in scientific computing and data science.

Website: [https://conda.io/](https://conda.io/)

### 12.2 Poetry

Poetry manages Python project dependencies, packaging, and project metadata.

Website: [https://python-poetry.org/](https://python-poetry.org/)

### 12.3 uv

uv is a fast Python package and project management tool. It supports dependency management, virtual environments, and Python version management.

Website: [https://docs.astral.sh/uv/](https://docs.astral.sh/uv/)

### Comparison

|Tool|Main purpose|
|---|---|
|pip|Installing Python packages|
|Conda|Managing packages and environments|
|Poetry|Managing project dependencies and packaging|
|uv|Fast Python package and project management|

For beginners, start with `pip` and `venv`. Learn alternative tools when a project requires them.

## 13. Package Security

Installing a package means running or importing code developed by someone else. This introduces a software supply-chain risk.

Potential threats include:

- Malicious packages.
    
- Typosquatting packages with names similar to legitimate libraries.
    
- Compromised package maintainers or accounts.
    
- Vulnerable package versions.
    
- Untrusted installation sources.
    
- Dependency confusion attacks.
    

### Security Best Practices

1. Verify package names before installation.
    
2. Prefer established and maintained packages.
    
3. Review project documentation and release history.
    
4. Avoid installing packages from unknown sources.
    
5. Keep dependencies updated with compatibility testing.
    
6. Use virtual environments.
    
7. Review dependency vulnerabilities.
    
8. Avoid committing secrets or private credentials.
    
9. Use trusted package indexes.
    
10. Pin or constrain versions when reproducibility requires it.
    

**Important:** A package being available on PyPI does not automatically mean it is safe.

## 14. Checking Dependencies for Known Vulnerabilities

You can use security tools to inspect Python dependencies.

One example is `pip-audit`.

Install it:

```
python -m pip install pip-audit
```

Audit the active environment:

```
python -m pip_audit
```

Audit a requirements file:

```
python -m pip_audit -r requirements.txt
```

The tool checks installed or specified dependencies against known vulnerability information.

A clean audit does not prove that software is secure. Newly discovered vulnerabilities, malicious code, and application-level weaknesses may not be detected.

## 15. Practical Exercises

### Exercise 1 — Install a Package

Inside a virtual environment, install:

```
python -m pip install requests
```

### Exercise 2 — Inspect the Package

Run:

```
python -m pip show requests
```

Identify:

- Package version.
    
- Installation location.
    
- Dependencies.
    

### Exercise 3 — Generate a Requirements File

Run:

```
python -m pip freeze > requirements.txt
```

Open the file and inspect the recorded versions.

### Exercise 4 — Reinstall Dependencies

Create a fresh virtual environment and install the packages from your requirements file.

```
python -m pip install -r requirements.txt
```

### Exercise 5 — Perform a Dependency Audit

Install and run:

```
python -m pip install pip-audit
python -m pip_audit
```

Review the output. Do not automatically upgrade everything without checking compatibility.

## 16. Key Takeaways

- pip is Python's standard package installer.
    
- PyPI is a major public repository for Python packages.
    
- Package management includes installing, updating, inspecting, and removing dependencies.
    
- Requirements files help reproduce project environments.
    
- Virtual environments prevent dependency conflicts between projects.
    
- Version constraints control package compatibility.
    
- Third-party packages introduce software supply-chain risks.
    
- Dependency auditing helps identify known vulnerabilities.
    

## 17. Related Notes

- [[Introduction to Python]]
    
- [[Python Modules]]
    
- [[Python Virtual Environments]]
    
- [[Python for Cybersecurity]]
    
- [[Secure Coding]]
    
- [[Dependency Security]]
    
- [[Git and Version Control]]
    
- [[Automation and Scripting]]