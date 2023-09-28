# -*- coding: utf-8 -*-

import base64
import sys
import os
import signal

def is_base64(sb):
    try:
        if isinstance(sb, str):
            sb_bytes = bytes(sb, 'ascii')
        elif isinstance(sb, bytes):
            sb_bytes = sb
        else:
            raise ValueError("Argument must be string or bytes")
        return base64.b64encode(base64.b64decode(sb_bytes)) == sb_bytes
    except Exception:
        return False

def main():
    # Validate the arguments
    if len(sys.argv) < 6:
        print("Error: missing arguments.")
        print("Usage: python3 base64loopdecoenc.py -f <file name> -t <number of times up to 50> -E <For Encoding> |-D <For Decoding>")
        sys.exit(1)

    # Check if the file exists
    filename = sys.argv[2]
    if not os.path.exists(filename):
        print("Error: file does not exist.")
        sys.exit(1)

    # Get the number of repetitions
    repetitions = int(sys.argv[4])

    # Limit the number of repetitions to 50
    if repetitions > 50:
        print("Error: number of times is limited to 50.")
        sys.exit(1)

    # Get the operation type
    operation = sys.argv[5]

    # Set up the signal handler
    signal.signal(signal.SIGINT, signal_handler)

    # Separate the basename and extension
    basename, extension = os.path.splitext(filename)

    # Open the file
    with open(filename, "rb") as f:
        data = f.read()

    # Perform operation
    if operation == "-D":
        base64_file_content = data
        # Verify if the content is base64
        if not is_base64(base64_file_content):
            print("File is not Base64 Encoded.")
            return
        # Decode the file
        for i in range(1, repetitions + 1):
            print("Iteration #%d" % i)
            data = base64.b64decode(data)
        output_filename = f"{basename}_decoded_X{repetitions}.txt"
    elif operation == "-E":
        # Encode the file
        for i in range(1, repetitions + 1):
            print("Iteration #%d" % i)
            data = base64.b64encode(data)
        output_filename = f"{basename}_encoded_X{repetitions}.txt"
    else:
        print("Error: invalid operation.")
        sys.exit(1)

    # Write to the output file
    with open(output_filename, 'wb') as f:
        f.write(data)

    # Print the output file name
    print("Task finished. Output file saved as " + output_filename)

def signal_handler(signal, frame):
    print("Control-C received, exiting...")
    sys.exit(0)

if __name__ == "__main__":
    main()
