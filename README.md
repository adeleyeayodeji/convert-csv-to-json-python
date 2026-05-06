# convert-csv-to-json-python
convert csv to json python

```python

import csv
import json
import sys

# Check if both input and output file arguments were provided
if len(sys.argv) < 3:
    print("Usage: python3 convert.py <input.csv> <output.json>")
    sys.exit(1)

input_csv = sys.argv[1]
output_json = sys.argv[2]

# Convert CSV to JSON with location as key and phone as value
data = {}
with open(input_csv, 'r', encoding='utf-8') as csv_file:
    csv_reader = csv.reader(csv_file)
    for row in csv_reader:
        if row and row[0].strip():  # Skip empty rows
            location = row[0].strip()
            phone = row[1].strip() if len(row) > 1 else ""
            data[location] = phone

with open(output_json, 'w', encoding='utf-8') as json_file:
    json.dump(data, json_file, indent=4)

print(f"Successfully converted {input_csv} to {output_json}")


```
