import csv

def read_csv_file(file_path):
    """
    Read data from a CSV file and return it as a list of dictionaries.
    Each dictionary represents a row in the CSV file.
    """
    data = []
    with open(file_path, 'r') as file:
        reader = csv.DictReader(file)
        for row in reader:
            data.append(row)
    return data

def process_data(input_data):
    """
    Process the input data.
    For demonstration purposes, let's just convert the values in the 'value' column to integers.
    """
    for row in input_data:
        row['value'] = int(row['value'])
    return input_data

def write_csv_file(data, file_path):
    """
    Write the processed data to a CSV file.
    """
    with open(file_path, 'w', newline='') as file:
        fieldnames = data[0].keys()
        writer = csv.DictWriter(file, fieldnames=fieldnames)
        writer.writeheader()
        for row in data:
            writer.writerow(row)

def main():
    # Read data from the input CSV file
    input_file_path = 'input.csv'
    input_data = read_csv_file(input_file_path)

    # Process the data
    processed_data = process_data(input_data)

    # Write the processed data to an output CSV file
    output_file_path = 'output.csv'
    write_csv_file(processed_data, output_file_path)

    print("Data processing complete. Results written to", output_file_path)

if __name__ == "__main__":
    main()
