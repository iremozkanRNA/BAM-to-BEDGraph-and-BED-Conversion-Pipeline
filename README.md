Overview
This script processes BAM files to generate strand-specific, normalized BEDGraph files and convert BAM files to BED format. It is designed to handle multiple BAM files in a directory, normalize coverage data using Reads Per Million (RPM), and annotate strand information for downstream analysis.
# Features
Normalization: Calculates total mapped reads in each BAM file and scales coverage to Reads Per Million (RPM).
Strand-Specific Coverage: Generates separate BEDGraph files for positive and negative strands.
Stranded BEDGraph: Combines strand-specific BEDGraph files into a single stranded BEDGraph with strand annotations.
BAM to BED Conversion: Converts BAM files to BED format for further analysis.
# Requirements
The following tools must be installed and available in your `PATH`:
samtools: For handling BAM files and counting reads.
bedtools: For generating coverage profiles and converting BAM to BED.
awk: For annotating strand information in BEDGraph files.
bash: To execute the script.
# Input and Output
# Input
A directory containing one or more `.bam` files.
The input directory is specified by the variable `INPUT_DIR` in the script.
# Output
The output directory is specified by the variable `OUTPUT_DIR` in the script. It will contain:
Strand-specific normalized BEDGraph files (`*_positive.bedgraph`, `*_negative.bedgraph`).
Annotated stranded BEDGraph file (`*_stranded.bedgraph`).
Converted BED file (`*.bed`).
# Usage Instructions
1. Prepare Input Files
  Place all `.bam` files that you want to process into a directory (e.g., `all5seqbams`).
2. Set Up the Script
  Update the variables `INPUT_DIR` and `OUTPUT_DIR` in the script to match your input and desired output directories.
3. Run the Script
  Execute the script using bash:
> bash bam_to_bedgraph_and_bed.sh

# Output Files
The processed files will be saved in the specified output directory (`OUTPUT_DIR`).
# File Descriptions
# Input Files
.bam`: Binary Alignment/Map format containing sequence alignment data.
# Output Files
1. Strand-Specific Normalized BEDGraph Files
  `<basename>_positive.bedgraph`: Coverage on the positive strand, normalized to RPM.
  `<basename>_negative.bedgraph`: Coverage on the negative strand, normalized to RPM.
2. Annotated Stranded BEDGraph File
  `<basename>_stranded.bedgraph`: Combined positive and negative strand coverage with strand annotations.
3. BED File
  `<basename>.bed`: Converted alignment data from BAM to BED format.
# Example Output Structure
If your input directory contains a file named `sample1.bam`, the output directory will contain:
# OUTPUT_DIR/
├── sample1_positive.bedgraph

├── sample1_negative.bedgraph

├── sample1_positive_annotated.bedgraph

├── sample1_negative_annotated.bedgraph

├── sample1_stranded.bedgraph

├── sample1.bed

# Notes
The script automatically creates the output directory if it does not exist.
If no `.bam` files are found in the input directory, the script will terminate with an error message.
Ensure that all required tools are installed and accessible before running the script.
# Troubleshooting
Common Issues
1. No BAM Files Found
Ensure that your input directory contains `.bam` files.
Verify that the `INPUT_DIR` variable is set correctly.
2. Empty Output Files
Check if your BAM file contains valid alignments.
Ensure that `samtools`, `bedtools`, and `awk` are properly installed.
3. Permission Denied
Ensure you have write permissions for the output directory.
4. Debugging Tips
Run individual commands from the script manually to identify issues.
Use verbose flags (`samtools view`, `bedtools genomecov`) for detailed error messages.

# License
This script is provided “as-is” without warranty of any kind. You are free to modify and distribute it as needed for your analysis.
Happy analyzing!
