# Excel_filepath_Android
Upload data in excel by specifying a code.

# Specify the file path
file_path <- file.path("C:", "Users", "kumbalas-INS", "Downloads", "Sim_2.38134535.xls")

# Print the file path (optional)
cat("File Path:", file_path, "\n")

# Now, you can use this file path in your code, for example, reading the Excel file
# Assuming you want to use the readxl package to read Excel files
library(readxl)
data <- read_excel(file_path)

# Now 'data' contains your Excel data, and you can work with it in R.
