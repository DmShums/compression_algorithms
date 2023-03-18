# Compression algorithms

## Huffman algorithm
Huffman encoding is a variable-length prefix code used for lossless data compression. It assigns shorter codes to frequently occurring symbols and longer codes to less frequent symbols. 

The algorithm works by constructing a table that maps each symbol to its corresponding variable-length code. The table is constructed by starting with the two least frequent symbols and combining them into a new symbol with a frequency equal to the sum of their frequencies. This process is repeated until all symbols are combined into a single root node, which represents the entire symbol set. 

The resulting codes are formed by concatenating the binary digits of the path from the root node to the leaf node representing each symbol. The codes are stored in the Huffman table and used to encode the input data. 

### Encoding:
- Read a file, count the frequency of occurrence of every symbol (func make_items), make list of tuples (symbol, frequency)
- Add two the least frequent symbols and make a tuple ((symbol_1, symbol_2), summary_frequency)
- Replace their tuples with this one in the list
- Repeat step 2 and step 3 until list contains only 1 element
- Divide the existing set into two parts that existed during the previous addition
- Add 0 to the code of the set with a higher frequency and 1 to the set with a lower frequency
- Repeat until you'll have a unique code for every symbol (dict: {symbol: code})

### Decoding:
- Take one symbol from file, check if it's a code
- Append to it next one if not, else write this code's key
- Repeat steps 1 and 2 until you will get your original message

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

## Deflate algorithm
The Deflate algorithm is a widely used compression algorithm that is used to reduce the size of files, such as text, images, audio, and video. The algorithm was first introduced in 1993 by Phil Katz and is commonly used in popular file formats like ZIP, PNG, and gzip.

The Deflate algorithm works by first replacing repeated sequences of characters in the input file with shorter symbols. This process is called "literal/length encoding." Next, the algorithm builds a dictionary of repeated sequences of characters, which it stores separately in a "distance encoding" table. Finally, the algorithm compresses the entire file using Huffman coding, which assigns shorter codes to more frequent characters and longer codes to less frequent characters.

### Encoding:
- Read file and transform it to str
- Compress using Lz77
- Comress using Huffman
- Output compressed data
## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.

## Contributors

Anastasia Pelekh: Huffman, Lz77, Deflated

Dmytro Shumskyi: LZW, Lz77, Deflated

## License

[MIT](https://choosealicense.com/licenses/mit/)
