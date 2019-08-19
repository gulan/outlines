# Scope the Project

  - Discover all Python libraries in use
  - Verify or build any needed CI/CD infrastructure
  - Document metrics for reporting progress

# The Code Refactoring Approach

Code refactoring is commonly used to clean-up a code base without
changing the code's functionality. The same well-known refactoring
techniques could easily be adapted to rewriting Python 2 code to Python
3.

Refactoring in brief:

1.  Choose a documented rewrite procedure and apply it to the code
2.  Run tests to ensure the code still works the same, and performance
    has not degraded
3.  Commit the changes, and repeat

Refactoring stops when all of the code meets the target standard.

The result is that code it transformed from "bad" to "good" in small,
confident steps.

# Project Time Line

To mitigate risk and complexity, consider doing the refactorings in
distinct project phases.

## Phase 1: Convert existing code to uniform Python 2.7

The goals are:

  - Ensure that we start with working code, fresh from a recent release
  - Ensure test suites are easy to run and have good coverage
  - Ensure that the code layout is uniform and easy to read (PEP 8)

## Phase 2: Convert Python 2 code to code that runs as either 2 or 3

Python modules that can run as either Python 2 or 3 are easier to
maintain in the transition period. Bug fixes need only be applied to one
code base, and a lot of integrations are avoided. Later, the Python 2
accommodations can be stripped-out with little fuss.

It is also a good idea to avoid adding in all the new Python 3 features
until after the initial conversion project is complete.

Activities:

  - Maintain a named catalog of refactoring, and discourage ad hoc
    edits.
  - Use tools like Six, Pylint and 2to3 to convert the modules in small
    steps
  - Run tests after every refactoring, and keep a fine-grained commit
    log in the SCR
  - Be wary of common conversion errors with Unicode, Numerics and such.
  - Have tests in place the will detect any drops in performance
  - Do regular diff tests on logs to find any anomalous behavior

## Phase 3: Convert Stage 2 code to pure, modern Python 3

Stripping-out the Python 2 code can be treated as refactorings, too.
Making small code changes followed by heavy testing ensures that editing
errors do not introduce bugs.

A lot of ideas about how to exploit the new features of Python 3 will
occur during Phase 2. But it is risky to add new techniques to an
changing code base. Having a distinct Phase 3 to the project lets the
new ideas be deferred but not forgotten.
