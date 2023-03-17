# Compression algorithms

## LZW

LZW (Lempel-Ziv-Welch) is a lossless data compression algorithm developed by Abraham Lempel, Jacob Ziv, and Terry Welch in 1977.

The LZW algorithm works by replacing repeated occurrences of substrings of data with a single code, which represents that substring. It builds a dictionary of substrings encountered during encoding and assigns a code to each substring. The codes can be variable length, and the length of the code is determined by the size of the dictionary. The algorithm is used in a wide range of applications, including GIF image format.

In this code, you can observe implementation of LZW encoder and decoder:

Encoder:

- There is given file that contains text(ex. ‘abacacaccadba’)
- Read this file and save it in string
- Call *lzw_compress* function:
    - Test word's uniqueness and add them to empty array
    - Set variable to save previous word(in the end if values are equal twice we have reached the end)
    - Using while loop analyse string until it’s empty
    - Append words and code of word at the same time
    - If previous message == initial message break
    - Return index of each entered word

Decoder:

- There is given code in the format [0, 1, 0, 2, 6, 6, 7, 3, 5] and first n values of words that have length 1.
- In variable save previous code.
- If code < len(out message) append element of out message with index of code
- In other situation append sum of element of out message with index of previous code and


## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## Contributors

Anastasia Pelekh: Huffman, Lz77, Deflated

Dmytro Shumskyi: Lzw, Lz77, Deflated

## License

[MIT](https://choosealicense.com/licenses/mit/)
