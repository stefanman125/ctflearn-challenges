# Programming challenges

## Simple Programming 

This challenge gives us a `.dat` file while a bunch a lines with ones and zeros. The goal outlined in the challenge is to count the number of lines that contain multiples, so the best way to achieve this would be to use [modulos](https://en.wikipedia.org/wiki/Modulo_operation).I wrote the script using Python.

SimpleProgramming.py
```python
#!/usr/bin/python3

line_num = 0 # Keep track of the number of lines counted.

data_file = open("data.dat", 'r') # Open the .dat file for reading.
for line in data_file: # Iterate through each line in the file
    zero_counter = 0 # Keep track of the number of zero's in the line (is reset with every new line)
    one_counter = 0 # Keep track of the number of one's in the line (is reset with every new line)
    for character in line: # Iterate through each character in the line 
        if character == '0':
            zero_counter += 1
        elif character == '1': 
            one_counter += 1
    if (zero_counter % 3 == 0) or (one_counter % 2 == 0): # Check if the amount of zeros is a multiple of three, or if the amount of zeroes is a multiple of 2
        line_num += 1
print(line_num)
```

The flag for this level is `6662`
