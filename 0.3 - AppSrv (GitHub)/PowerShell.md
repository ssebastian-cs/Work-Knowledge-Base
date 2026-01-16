**I. Architectural Foundation: The .NET Integration**

- **Substrate Layer:** PowerShell is not a standalone utility; it functions as a high-level **abstraction layer** (or "management wrapper") built atop the **.NET Framework/Core**.
- **Composition:** The relationship is intrinsic rather than superficial.
    - **Cmdlets** (PowerShell commands) are effectively compiled .NET classes.
    - PowerShell leverages the extensive .NET class library to perform complex system administration tasks.
- **Interoperability:** Because it resides within the .NET ecosystem, PowerShell grants direct access to the underlying Framework, allowing users to instantiate .NET objects directly within the shell.

**II. Paradigm Shift: Text vs. Object-Oriented Processing**

Traditional shells (e.g., Bash, Zsh) operate on a **String-Based Paradigm**, whereas PowerShell utilizes an **Object-Oriented Paradigm**.

|**Feature**|**String-Based Shells (Bash)**|**Object-Oriented (PowerShell)**|
|---|---|---|
|**Output Type**|Unstructured Text (Strings)|Structured **.NET Objects**|
|**Data Handling**|Requires RegEx, `grep`, `awk`, or `sed` to parse data.|Properties and methods are natively accessible.|
|**Pipeline Behavior**|Passes a stream of characters.|Passes the entire object (data + metadata).|
> **Key Insight:** In PowerShell, when a command is executed, the output is a "living" entity. For instance, a file is not just a name (text); it is a `System.IO.FileInfo` object containing properties (size, creation date) and methods (Delete, Move).

**III. The "Object" Advantage**

- **Metadata Retention:** Data integrity is maintained across the pipeline. You do not lose "structure" when passing data from one command to the next.
- **Efficiency:** Eliminates the "parsing tax." Instead of writing complex logic to extract the third column of a text block, you simply query the property: `Selection.Name`.

To see the connection and which version of .NET your current PowerShell session is using:
``` PowerShell
$PSVersionTable
```
Look for the **CLRVersion** (Common Language Runtime) or **RuntimeVersion** property. The CLR is the specific part of .NET that manages the execution of PowerShell code.

---

For **creating a new empty file** using *PowerShell terminal* commands we can use:
```PowerShell
ni main.rs
```
`ni` is the alias for `New-Item`

*we can also use:*
```PowerShell
echo $null > main.rs
```

the standard command to create an empty file in *macOS and Linux* is called `touch` we can use it on PowerShell by creating a permanent alias for it:
```PowerShell
Set-Alias -Name touch -Value New-Item
```

to **open this new file**:
```PowerShell
code main.rs
```

To **compile Rust program files** in the terminal:
```terminal
rustc file-name.rs
```

To **run** the file-name.exe:
```terminal
./file-name
```

