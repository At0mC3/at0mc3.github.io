I found myself trying to map a PE file in memory for one of my personal project recently and i thought showing what i learned a long the way would help so here it is!

The format is well known and Microsoft has a quite good documentation about the file format but mapping the file properly isn't documented at all or the information is generally scattered around.

![PEFormat](https://upload.wikimedia.org/wikipedia/commons/7/70/Portable_Executable_32_bit_Structure_in_SVG.svg)

{% highlight cpp %}
std::uint8 buffer = 
{
	4D 5A 90 00 03 00 00 00 04 00 00 00 FF FF 00 00 B8 00 00 00 
	00 00 00 00 40 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	F8 00 00 00 0E 1F BA 0E 00 B4 09 CD 21 B8 01 4C CD 21 54 68
};
{% endhighlight %}
