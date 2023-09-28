# Base64 Loop Decode/Encode Script

This Python script, [base64loopdecoenc.py](https://github.com/Acorzo1983/base64loopdecoenc/blob/main/base64loopdecoenc.py), allows you to repeatedly decode or encode a Base64-encoded file.

## Usage

$python3 base64loopdecoenc.py -f <file name> -t <number of times up to 50> -E <For Encoding> |-D <For Decoding>


### Arguments

- `-f <file name>`: Specify the input file name.
- `-t <number of times up to 50>`: Set the number of repetitions (limited to 50).
- `-E`: Encode the file.
- `-D`: Decode the file.

## Example

To encode a file named `input.txt` 20 times:

bash
$python3 base64loopdecoenc.py -f input.txt -t 20 -E


## Requirements

- Python 3.x

## Notes

- The script limits the number of repetitions to 50.
- For decoding, the script checks if the content is Base64 encoded before proceeding.

## Author

Albert Corzo

## License

This project is licensed under the [MIT License](LICENSE).
