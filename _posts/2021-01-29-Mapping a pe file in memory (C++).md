I found myself trying to map a PE file in memory for one of my personal project recently and i thought showing what i learned a long the way would help so here it is!:smile:

The format is well known and Microsoft has a quite good documentation about the file format but mapping the file properly isn't documented at all or the information is generally scattered around.

<img src="https://upload.wikimedia.org/wikipedia/commons/7/70/Portable_Executable_32_bit_Structure_in_SVG.svg" alt="drawing" width="800" style="background-color: white;"/>

The DOS Header has 80 bytes and the first **2** bytes are the signature of the file which is `0x5A4D` (big endian) -> **MZ**. The rest of the values are not really necessary, what we are the most interested in is the last **4** bytes which is `0x000000F8`, this points to the PE Header which is where we need to go next for the mapping of the file.

```cpp
std::uint8_t buffer = 
{   
	0x4D 0x5A 0x90 0x00 0x03 0x00 0x00 0x00 0x04 0x00 0x00 0x00 0xFF 0xFF 0x00 0x00 
	0xB8 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x40 0x00 0x00 0x00 0x00 0x00 0x00 0x00 
	0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 
	0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0xF8 0x00 0x00 0x00 <--- Pointer to PE Header
};
```
