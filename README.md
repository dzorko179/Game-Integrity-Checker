# Game-Integrity-Checker
C++17 tool for game file integrity verification using SHA-256.
Game Integrity Checker

A C++17 command-line tool for verifying game file integrity using SHA-256 cryptographic hashes.

Overview

Game Integrity Checker is a personal cybersecurity project focused on file integrity verification. It creates a baseline of trusted file hashes and compares them against files in a game directory to identify unexpected modifications or missing files.

The project explores fundamental concepts used in software integrity monitoring and defensive game security.

Features

- SHA-256 Hashing — calculates cryptographic hashes using OpenSSL.
- Baseline Creation — records hashes of files in a selected directory.
- Integrity Verification — compares current file hashes against a trusted baseline.
- Change Detection — identifies modified and missing files.
- Command-Line Interface — simple commands for creating and checking baselines.
- C++17 Filesystem — traverses directories and processes files.

Technologies

- C++17
- OpenSSL
- CMake
- SHA-256
- Filesystem analysis

Requirements

- A C++17-compatible compiler
- CMake 3.16 or later
- OpenSSL development libraries

Build Instructions

Clone the repository:

git clone https://github.com/Aimaniacdev/Game-Integrity-Checker.git
cd Game-Integrity-Checker

Configure and build:

cmake -S . -B build
cmake --build build --config Release

Usage

1. Create a baseline

Generate a baseline from a trusted game directory:

game-integrity-checker baseline "/path/to/game" "trusted-baseline.txt"

This records SHA-256 hashes for the files found in the selected directory.

2. Verify file integrity

Run the checker again to compare files with the baseline:

game-integrity-checker check "/path/to/game" "trusted-baseline.txt"

The program reports files that have changed or are missing.

Windows Example

.\build\Release\game-integrity-checker.exe baseline "C:\Games\Example" "C:\Security\trusted-baseline.txt"

.\build\Release\game-integrity-checker.exe check "C:\Games\Example" "C:\Security\trusted-baseline.txt"

Executable paths may differ depending on your compiler and build configuration.

Example Output

[OK] game.exe
[CHANGED] data.pak
[MISSING] config.ini

Verification summary
Files checked: 2
Changed or unsafe: 0
Missing: 1

The example is illustrative; actual output depends on the files being checked.

Security Considerations

- Create baselines only from trusted files.
- Store the baseline outside the game directory.
- Protect the baseline against unauthorized modification.
- A changed hash indicates a difference, not necessarily malicious activity.
- The current version does not report newly added files.
- This project is an educational integrity-checking tool, not a production anti-cheat solution.

Future Improvements

- Detect newly added files.
- Add automated unit tests.
- Support signed baselines to improve baseline authenticity.
- Generate machine-readable JSON reports.
- Add configurable file exclusions.
- Improve cross-platform testing on Windows, Linux, and macOS.

Disclaimer

This project is intended for educational and defensive cybersecurity purposes. Use it only on files and systems you own or are authorized to inspect.

