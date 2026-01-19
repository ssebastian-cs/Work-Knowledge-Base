### Installation

Downloaded the Rust installation application from [here](https://rust-lang.org/tools/install/).

It ran the terminal command to download and install Rust.

![[Pasted image 20260116110538.png]]
![[Pasted image 20260116110842.png]]
![[Pasted image 20260116110914.png]]
![[Pasted image 20260116111014.png]]

Rust installation was successfully completed.

---
### Notes

Rust is a compiled programming language<sup>1</sup> know for its safety, concurrency, and performance. It is know for being a fast and powerful system programming<sup>2</sup> language. It is more useful for systems than applications, with the exception of web development<sup>3</sup>. Rust is used for Blockchain<sup>4</sup> technologies.

Rust doesn't have a garbage collector but it checks when needed. We can still manage memory. [Rust's memory management](https://www.google.com/search?q=Rust%27s+memory+management&rlz=1C1GCEA_enCA1175CA1175&oq=how+does+memory+management+work+in+Rust&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTINCAEQABiGAxiABBiKBTINCAIQABiGAxiABBiKBTINCAMQABiGAxiABBiKBTINCAQQABiGAxiABBiKBTIHCAUQABjvBTIHCAYQABjvBTIHCAcQABjvBdIBCTEwNTE1ajBqN6gCCLACAfEFITofIzDQokrxBSE6HyMw0KJK&sourceid=chrome&ie=UTF-8&ved=2ahUKEwi_jpCeuZCSAxXLGjQIHW-6FMwQgK4QegQIARAB) ==uses a unique **ownership system** with strict compile-time rules (ownership, borrowing, lifetimes) to guarantee memory safety without a garbage collector==, providing C/C++ speed with automated deallocation when owners go out of scope, preventing common bugs like [dangling pointers](https://www.google.com/search?q=dangling+pointers&rlz=1C1GCEA_enCA1175CA1175&oq=how+does+memory+management+work+in+Rust&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTINCAEQABiGAxiABBiKBTINCAIQABiGAxiABBiKBTINCAMQABiGAxiABBiKBTINCAQQABiGAxiABBiKBTIHCAUQABjvBTIHCAYQABjvBTIHCAcQABjvBdIBCTEwNTE1ajBqN6gCCLACAfEFITofIzDQokrxBSE6HyMw0KJK&sourceid=chrome&ie=UTF-8&ved=2ahUKEwi_jpCeuZCSAxXLGjQIHW-6FMwQgK4QegQIARAD) and leaks. Values have a single owner; ownership transfers when assigned (moving), or data can be temporarily accessed via **borrowing** (references). The **[borrow checker](https://www.google.com/search?q=borrow+checker&rlz=1C1GCEA_enCA1175CA1175&oq=how+does+memory+management+work+in+Rust&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTINCAEQABiGAxiABBiKBTINCAIQABiGAxiABBiKBTINCAMQABiGAxiABBiKBTINCAQQABiGAxiABBiKBTIHCAUQABjvBTIHCAYQABjvBTIHCAcQABjvBdIBCTEwNTE1ajBqN6gCCLACAfEFITofIzDQokrxBSE6HyMw0KJK&sourceid=chrome&ie=UTF-8&ved=2ahUKEwi_jpCeuZCSAxXLGjQIHW-6FMwQgK4QegQIARAE)** enforces rules like only one mutable reference or many immutable references at a time, ensuring safe concurrent access and automatic memory cleanup when the owner goes out of scope.

Cargo is Rust's Package Manager<sup>5</sup>.

![[Pasted image 20260119140817.png]]

Since Rust's `println!` is a **macro** it requires a string literal as its first argument to define how the output should be formatted. If we write `println!(variable);` the compiler would throw an error because it expects a format string (a literal "...") first, not a variable. The `println!` macro parses the string at **compile time**. The `{}` tells Rust: _"Expect a value here and format it using the `Display` trait."_ So we need to write it as:

```Rust
println!("{variable}");

// can also be written as
println!("{}", variable);
```

```Rust
let x = 5;
let y = 10;

println!("x is {x} and y is {y}");

// the braces act as slots for the variables that follow 
println!("x is {} and y is {}", x, y);
```

`{}` is the simplest form of a placeholder, and we can put instructions inside them to change how the data looks:
- `{:?}`: prints the value using **Debug** formatting
- `{:x}`: prints a number in **Hexadecimal**
- `{:.2}`: limits a float to **two decimal places** 








### Commands

To compile Rust program files in the terminal:
```terminal
rustc file-name.rs
```

How to initialize a new project using `cargo`:
```terminal
cargo new file_name
```
*Note*: when we create a project with cargo we tend to use `snake_case` instead of `camelCase` or `PascalCase`
- This will create a project folder and inside it a `src` folder, a `.gitignore` file, and a `Cargo.toml`<sup>6</sup> file
- This is a git initialized folder
- The `src` folder will already have a simple `main.rs` file with the code:
```Rust
fn main() {
	println!("Hello, world!");
}
```

To initialize a project within the current folder itself we can use:
```terminal
cargo init file_name
```

To build the project:
```terminal
cargo build
```
- we get a new folder called `target` and a `Cargo.lock`<sup>7</sup> file
- the `file_name.exe` file will be in the `project/target/debug` folder
- to run this file we can use the command (assuming we are already in the `project` folder):
```terminal
./target/debug/file_name
```
- the `Cargo.lock` file is not intended for manual editing and it locks the project's dependencies to specific versions

To run if we are inside the project folder we can also do:
```terminal
cargo run
```

We can also compile the code without producing the executable file `.exe` by using:
```terminal
cargo check
```

To get the release build we can do:
```terminal
cargo build --release
```
- this will give us a `release` folder with the files inside


---
### Definitions

1. A **compiled programming language** is ==a language whose source code is translated entirely into machine code (native binary instructions) by a program called a compiler _before_ the program is executed==. This results in a standalone executable file that the computer's processor can run directly.
2. A **system programming language** is ==a programming language used to write **system software**==—software that provides a platform for other software to run, such as operating systems, compilers, and device drivers. These languages are designed to provide a high degree of control over a computer's hardware and resources, allowing for efficient use of memory and processing power.
3. Web development is ==the process of creating, building, and maintaining websites and web applications==, involving everything from the visual design (front-end) that users see and interact with, to the complex logic and databases (back-end) that power them, using languages like HTML, CSS, and JavaScript, and frameworks for dynamic functionality. It covers coding, functionality, performance, and user experience to ensure smooth, efficient online experiences for users.
4. Blockchain is a **decentralized, immutable, and transparent digital ledger** that securely records transactions across a network of computers. Instead of a central authority (like a bank), all network participants maintain a synchronized copy of the ledger, making it highly resistant to tampering and fraud.
5. A package manager is ==an automated tool that simplifies installing, upgrading, configuring, and removing software by handling downloaded files, dependencies (other required software), and updates from central repositories, ensuring applications run smoothly without conflicts==. It replaces manual processes, making software management efficient for operating systems (like [APT for Linux](https://www.google.com/search?sca_esv=dd02f7078e0836d1&rlz=1C1GCEA_enCA1175CA1175&sxsrf=ANbL-n7Xsi7S-P2Yf6mouKdI4tHfe5-qJA%3A1768580218854&q=APT+for+Linux&sa=X&ved=2ahUKEwjZjs7dupCSAxUEJDQIHUTDHJ4QxccNegQIOBAB&mstk=AUtExfD5Z9puif72_Dz-AhajwtygJURzutyo7qzFB2NH83tLvHPIEcRl9Bl1DceYSxOU0MVEa525KRGjXxRZRkVc95roCPMFbb3Au9nPl0_SWTgzzuQbvtq-Eg0hma6wqHaspNfih_QRJItVTm9bmBklzq3TRx0MGBKnTQQ09t-g8BoH76Qehlebmn1yuG0iOo6flTuBBis6xBafdrfXeQcAXOQ9roSJ5r8JSaoJo0rTVyusVDnhOn8RmfAIQANANr7iUiosLyAiH5udzVS8x5OlX4s-&csui=3) or [WinGet for Windows](https://www.google.com/search?sca_esv=dd02f7078e0836d1&rlz=1C1GCEA_enCA1175CA1175&sxsrf=ANbL-n7Xsi7S-P2Yf6mouKdI4tHfe5-qJA%3A1768580218854&q=WinGet+for+Windows&sa=X&ved=2ahUKEwjZjs7dupCSAxUEJDQIHUTDHJ4QxccNegQIOBAC&mstk=AUtExfD5Z9puif72_Dz-AhajwtygJURzutyo7qzFB2NH83tLvHPIEcRl9Bl1DceYSxOU0MVEa525KRGjXxRZRkVc95roCPMFbb3Au9nPl0_SWTgzzuQbvtq-Eg0hma6wqHaspNfih_QRJItVTm9bmBklzq3TRx0MGBKnTQQ09t-g8BoH76Qehlebmn1yuG0iOo6flTuBBis6xBafdrfXeQcAXOQ9roSJ5r8JSaoJo0rTVyusVDnhOn8RmfAIQANANr7iUiosLyAiH5udzVS8x5OlX4s-&csui=3)) and programming languages (like [npm for Node.js](https://www.google.com/search?sca_esv=dd02f7078e0836d1&rlz=1C1GCEA_enCA1175CA1175&sxsrf=ANbL-n7Xsi7S-P2Yf6mouKdI4tHfe5-qJA%3A1768580218854&q=npm+for+Node.js&sa=X&ved=2ahUKEwjZjs7dupCSAxUEJDQIHUTDHJ4QxccNegQIOBAD&mstk=AUtExfD5Z9puif72_Dz-AhajwtygJURzutyo7qzFB2NH83tLvHPIEcRl9Bl1DceYSxOU0MVEa525KRGjXxRZRkVc95roCPMFbb3Au9nPl0_SWTgzzuQbvtq-Eg0hma6wqHaspNfih_QRJItVTm9bmBklzq3TRx0MGBKnTQQ09t-g8BoH76Qehlebmn1yuG0iOo6flTuBBis6xBafdrfXeQcAXOQ9roSJ5r8JSaoJo0rTVyusVDnhOn8RmfAIQANANr7iUiosLyAiH5udzVS8x5OlX4s-&csui=3) or [pip for Python](https://www.google.com/search?sca_esv=dd02f7078e0836d1&rlz=1C1GCEA_enCA1175CA1175&sxsrf=ANbL-n7Xsi7S-P2Yf6mouKdI4tHfe5-qJA%3A1768580218854&q=pip+for+Python&sa=X&ved=2ahUKEwjZjs7dupCSAxUEJDQIHUTDHJ4QxccNegQIOBAE&mstk=AUtExfD5Z9puif72_Dz-AhajwtygJURzutyo7qzFB2NH83tLvHPIEcRl9Bl1DceYSxOU0MVEa525KRGjXxRZRkVc95roCPMFbb3Au9nPl0_SWTgzzuQbvtq-Eg0hma6wqHaspNfih_QRJItVTm9bmBklzq3TRx0MGBKnTQQ09t-g8BoH76Qehlebmn1yuG0iOo6flTuBBis6xBafdrfXeQcAXOQ9roSJ5r8JSaoJo0rTVyusVDnhOn8RmfAIQANANr7iUiosLyAiH5udzVS8x5OlX4s-&csui=3), or [composer for PHP](https://www.google.com/search?q=composer+for+php&rlz=1C1GCEA_enCA1175CA1175&oq=composer+for+php&gs_lcrp=EgZjaHJvbWUyCQgAEEUYORiABDIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIICAQQABgWGB4yCAgFEAAYFhgeMggIBhAAGBYYHjIICAcQABgWGB4yCAgIEAAYFhgeMggICRAAGBYYHtIBCDMxMTFqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8)), ensuring consistent versions and removing unnecessary files.
6. TOML (==Tom's Obvious, Minimal Language==) is a human-friendly configuration file format designed to be easy to read and write, mapping unambiguously to a hash table (dictionary) for various programming languages, widely used in projects like Rust's Cargo and Python's packaging to separate settings from code with clear key-value syntax and minimal ambiguity.
7. The `Cargo.lock` file in Rust ==locks your project's dependencies to specific versions, ensuring reproducible builds by recording the exact crates and sub-crates used during a successful build==, preventing unexpected changes from upstream updates and guaranteeing consistency across development, testing, and production environments, a crucial feature for team collaboration and CI/CD. It's automatically generated by Cargo and should be committed to version control, unlike `Cargo.toml`, which specifies broad dependency requirements.
