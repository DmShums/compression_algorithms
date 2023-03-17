# Compression algorithms

## Lz77 algorithm

LZ77 is a lossless data compression algorithm that was published by Abraham Lempel and Jacob Ziv in 1977. It is a dictionary-based algorithm that achieves compression by replacing repeated occurrences of data with references to a single copy of that data existing earlier in the uncompressed data stream.

Encoder:

- There is given some string that contains text(ex. ‘abacacaccadba’)
- Call *lz77_encode* function:
    - Take first element of string and place it to out message
    - Set <offset; length; next> to each word
    - Using while loop analyse string until it’s empty
    - Check different situations: different offsets, lengths or next values
    - If initial message reaches the end, finish execution
    - Outout list of tuples

Decoder:

- There is given code in the format [(0, 0, 'a'), (0, 0, 'b'), (1, 1, 'c'), (3, 3, None)]
- If offset and length is 0, add 1 word
- If offset and length is more than 0, analyse buffer(return offset symbols back, and copy elements of length)

## LZW

LZW (Lempel-Ziv-Welch) is a lossless data compression algorithm developed by Abraham Lempel, Jacob Ziv, and Terry Welch in 1977.

The LZW algorithm works by replacing repeated occurrences of substrings of data with a single code, which represents that substring. It builds a dictionary of substrings encountered during encoding and assigns a code to each substring. The codes can be variable length, and the length of the code is determined by the size of the dictionary. The algorithm is used in a wide range of applications, including GIF image format.

In this code, you can observe implementation of LZW encoder and decoder:

Encoder:

- There is given some string that contains text(ex. ‘abacacaccadba’)
- Call *lzw_compress* function:
    - Test word's uniqueness and add them to empty array
    - Set variable to save previous word(in the end if values are equal twice we have reached the end)
    - Using while loop analyse string until it’s empty
    - Append words and code of word at the same time
    - If previous message == initial message break
    - Return index of each entered word

Decoder:

- There is given code in the format [0, 1, 0, 2, 6, 6, 7, 3, 5] and first n values of words that have length 1.
- If code < len(out message) append element to dictionary and out message
- In other situation append dictionary[code] + dictionary[code][0]


## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## Contributors

Anastasia Pelekh: Huffman, Lz77, Deflated

Dmytro Shumskyi: LZW, Lz77, Deflated

## License

[MIT](https://choosealicense.com/licenses/mit/)
