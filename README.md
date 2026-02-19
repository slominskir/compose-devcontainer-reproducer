# compose-devcontainer-reproducer
Demonstrate compose devcontainer issue

See: https://youtrack.jetbrains.com/issue/IDEA-385868/Build-devcontainer-from-VCS-fails-if-references-compose-file-in-project-root

# Steps to reproduce

1. In JetBrains Gateway build a devcontainer from VCS.   Screenshot:
<img width="1777" height="1315" alt="image" src="https://github.com/user-attachments/assets/41909c07-6910-46bc-a168-c9b960e9a021" />


2. Notice build fails here because it can't find "../compose.yaml".  Screenshot:
<img width="1777" height="1315" alt="image" src="https://github.com/user-attachments/assets/f4425eec-5e67-487d-b5e4-2addded6bcc0" />

# Expectation
This should work.  In fact, if you create a Local Project first and then use the "From Local Project" option to create the devcontainer, it works!

# Aside
When creating a devcontainer from a local devcontainer file via the Gateway app (Step 1), notice there is no option to choose if files should be cloned vs bind mounted and instead bind mount appears to always be used.   This is problematic since generally clone is needed to avoid file system permission issues (and performance issues) on Windows.  There is a way to choose clone via local devcontainer file, but it's extra steps and subltle - you must first create a local project (even if it has no chance of compiling on Windows) and then use the tiny little box icon that appears in the "gutter" when viewing the devcontainer.json file to choose a clone devcontainer option as pictured here:

<img width="1386" height="993" alt="image" src="https://github.com/user-attachments/assets/cfec4e8d-2cf3-4a5c-83f1-df55644b65c0" />

https://youtrack.jetbrains.com/issue/IJPL-235712/Gateway-new-devcontainer-from-local-no-volume-option
