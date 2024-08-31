def decode_message(file_path):
    pyramid = []
    
    # Read the file and create the pyramid
    with open(file_path, 'r') as file:
        for line in file:
            parts = line.split()
            numbers = [int(part) for part in parts[:-1]]
            word = parts[-1]
            pyramid.append((numbers, word))
    
    decoded_message = ""
    current_index = 1
    
    # Traverse the pyramid and extract the words at the end of each line
    for numbers, word in pyramid:
        if current_index in numbers:
            decoded_message += word
            current_index = numbers[-1] + 1
    
    return decoded_message

# Example usage
file_path = 'your_input_file.txt'  # Replace with the actual file path
result = decode_message(file_path)
print("Decoded Message:", result)
