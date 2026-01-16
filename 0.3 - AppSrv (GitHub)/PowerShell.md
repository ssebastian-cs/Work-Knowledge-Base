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