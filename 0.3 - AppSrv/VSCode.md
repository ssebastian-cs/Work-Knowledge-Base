tag: [[AppSrv]]
## VSCode Shortcuts 

ctrl + shift + e is the shortcut for explorer menu
ctrl + k + s to open keyboard shortcuts for VS Code
ctrl + k then ctrl + left/right arrow OR ctrl + 1, 2, 3...n - to move between windows
ctrl + \ - to split windows
ctrl + shift + p - open command palette
ctrl + p - search files
alt + z - wrap text in editor window
ctrl + shift + g source control
## VS Code Configuration Consistency

To maintain a consistent VS Code configuration across different launch elevations (normal user vs. administrator) on a single machine, follow these steps:

1. **User Installer Installation:** Install VS Code using the **User Installer**. This ensures the application and its configurations are stored within your specific Windows user profile, rather than system-wide.
    
2. **Single Settings Sync:** Activate VS Code's built-in **Settings Sync** feature once, linking it to your preferred GitHub (or Microsoft) account.
    

This approach ties your editor preferences (settings, extensions, themes, etc.) to a single cloud profile. Consequently, the same VS Code installation for that Windows user account will consistently apply these configurations, regardless of whether it's launched with normal or elevated (administrator) permissions. While this method ensures consistency, it's generally recommended to run VS Code as a normal user for day-to-day operations.

To run C++ files in *debug* and *release* modes -

When you first ran your program, a new file called _tasks.json_ was created under the _.vscode_ folder in the explorer pane. Open the _tasks.json_ file, find _“args”_, and then locate the line _“${file}”_ within that section.

Above the _“${file}”_ line, add a new line containing the following command (one per line) when debugging:  
`"-ggdb",`

Above the _“${file}”_ line, add new lines containing the following commands (one per line) for release builds:  
`"-O2",`  
`"-DNDEBUG",`

Increasing the warning levels - 

In the tasks.json file, inside args, above the _“${file}”_ line, add new lines containing the following commands (one per line):

```
"-Wall",
"-Weffc++",
"-Wextra",
"-Wconversion",
"-Wsign-conversion"
```

To configure Intellisense to use the same language standard. For C++20, in `settings.json`, change or add the following setting on its own line: `"C_Cpp.default.cppStandard": "c++20"`.

Command Palette (`ctrl + shift + p`) and then:
1. `Create: New Jupyter Notkebook`
2. `Notebook: Select Notebook Kernel`

