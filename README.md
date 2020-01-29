Demonstrate pylint error when using rpm module constants.

Build with:
`podman build -t pylint/1739167:rawhide -f Dockerfile.rawhide`

Run with:
`podman run -it --rm pylint/1739167:rawhide`

(you can also use docker if you have it available)

Output will look like:
```
    1000
    ************* Module test-rpm
    /test-rpm.py:4:0: C0305: Trailing newlines (trailing-newlines)
    /test-rpm.py:1:0: C0103: Module name "test-rpm" doesn't conform to snake_case naming style (invalid-name)
    /test-rpm.py:1:0: C0114: Missing module docstring (missing-module-docstring)
    /test-rpm.py:3:6: E1101: Module 'rpm' has no 'RPMTAG_NAME' member (no-member)

    -------------------------------------
    Your code has been rated at -30.00/10
```
Fedora rawhide and f31 both have this problem. Fedora 30 does not.

The packages installed on rawhide are:
```
  pylint-2.4.4-2.fc32.noarch
  python3-astroid-2.3.3-6.gitace7b29.fc32.noarch
  python3-isort-4.3.21-6.fc32.noarch
  python3-lazy-object-proxy-1.4.3-2.fc32.x86_64
  python3-mccabe-0.6.1-14.fc32.noarch
  python3-pylint-2.4.4-2.fc32.noarch
  python3-setuptools-41.6.0-1.fc32.noarch
  python3-six-1.14.0-1.fc32.noarch
  python3-typed_ast-1.4.1-1.fc32.x86_64
  python3-wrapt-1.11.2-4.fc32.x86_64
  python3-rpm-4.15.1-2.fc32.x86_64
```

Fedora 31:
```
  pylint-2.3.1-2.fc31.noarch
  python3-astroid-2.3.3-4.gitace7b29.fc31.noarch
  python3-lazy-object-proxy-1.4.3-1.fc31.x86_64
  python3-isort-4.3.21-4.fc31.noarch
  python3-mccabe-0.6.1-12.fc31.noarch
  python3-pylint-2.3.1-2.fc31.noarch
  python3-setuptools-41.2.0-1.fc31.noarch
  python3-six-1.12.0-2.fc31.noarch
  python3-typed_ast-1.4.0-2.fc31.x86_64
  python3-wrapt-1.11.2-2.fc31.x86_64
  python3-rpm-4.15.0-6.fc31.x86_64
```

Fedora 30:
```
  pylint-2.3.1-1.fc30.noarch
  python3-astroid-2.2.5-1.fc30.noarch
  python3-isort-4.3.4-8.fc30.noarch
  python3-lazy-object-proxy-1.3.1-9.fc30.x86_64
  python3-mccabe-0.6.1-11.fc30.noarch
  python3-pylint-2.3.1-1.fc30.noarch
  python3-six-1.12.0-1.fc30.noarch
  python3-typed_ast-1.3.1-1.fc30.x86_64
  python3-wrapt-1.11.1-1.fc30.x86_64
  python3-rpm-4.14.2.1-5.fc30.x86_64
```
