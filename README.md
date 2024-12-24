# Baby Names Utility (`bn`)

The **Baby Names Utility (`bn`)** is a command-line tool written entirely in Bash that processes historical baby name rankings in the U.S. Using the dataset provided by the Social Security Administration, this utility allows users to search for rankings of baby names for specific years and genders. The project demonstrates the use of Bash scripting concepts, including pipes, filters, regular expressions, and error handling.

## Features
- Rank Search: Determine the ranking of baby names for a specified year and gender.
- Multi-Gender Search: Supports queries for male, female, or both genders.
- Error Handling: Provides detailed error messages for invalid inputs or missing data.
- Help Option: Includes a `--help` flag for usage guidance.

## Usage

### Command Syntax
bn <year> <assigned gender: f|F|m|M|b|B>

### Input Description
- Year: A four-digit integer representing the year of interest.
- Assigned Gender:
  - f or F: Female names
  - m or M: Male names
  - b or B: Both male and female names
- Names: List of whitespace-separated names provided through standard input.

### Example Commands
1. Search for rankings of male names in 1969:
   bn 1969 M
2. Search for both male and female rankings in 2000:
   bn 2000 b
3. Display help information:
   bn --help

### Expected Output
1. If the name is found:
   <year>: <name> ranked <rank> out of <total> <gender> names.
2. If the name is not found:
   <year>: <name> not found among <gender> names.

### Example Input and Output
Input (via standard input):
sam SCOTT Bob

Output:
1969: sam ranked 318 out of 5042 male names.
1969: SCOTT ranked 12 out of 5042 male names.
1969: Bob ranked 380 out of 5042 male names.

## Error Handling
- Invalid Arguments: Outputs usage string to stderr with exit code 1.
- Incorrect Argument Format: Outputs an error message to stderr with exit code 2.
- Invalid Name Format: Outputs an error message for names containing non-alphabetic characters to stderr with exit code 3.
- Missing Data: Outputs an error message if the data file for the selected year is not available with exit code 4.

Example Error Output:
Badly formatted assigned gender: x
bn <year> <assigned gender f|F|m|M|b|B>

## How to Build and Run

### Prerequisites
- Bash: Ensure a Bash shell is available on your system (default for most Linux and macOS systems).
- Git: To clone the repository and manage version control.

### Setup Instructions
1. Clone the repository:
   git clone https://github.com/yourusername/bn.git
   cd bn
2. Copy the us_baby_names directory:
   cp -r path_to_us_baby_names ./us_baby_names

### Running the Utility
1. Make the script executable:
   chmod +x bn.sh
2. Run the script:
   ./bn.sh <year> <assigned gender>
3. Pipe in names through standard input:
   echo "sam SCOTT Bob" | ./bn.sh 1969 M

## Help Option
To display the help text:
./bn.sh --help

Example Output:
Baby Names Utility v1.0.0
Search U.S. baby name rankings by year and gender.

Usage: bn.sh <year> <assigned gender: f|F|m|M|b|B>
Options:
  --help   Display this help message.

Arguments:
  year           Four-digit integer representing the year of interest.
  assigned gender f|F|m|M|b|B (f/F for female, m/M for male, b/B for both)

## Testing and Continuous Integration (CI)

### Test Cases
- Valid queries with different gender options.
- Invalid arguments and name formats.
- Missing or corrupted data files.

### CI Pipeline
The repository includes a GitHub Actions CI pipeline. On each push, the pipeline:
1. Runs the test_script to verify functionality.
2. Uploads the test results as an artifact.

To view the configuration:
.github/workflows/test.yml

## Contributing
Contributions are welcome! Please fork the repository, make your changes, and submit a pull request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
