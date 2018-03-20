# TIL
Today I learned

### Encoding

To encode means to use something to represent something else. An encoding is the set of rules with which to convert something from one representation to another. Character Set, Charset - the set of characters that can be encoded in an encoding scheme. 
For eg. ASCII encoding - there are 128 characters in ASCII (all combinations of 7 bits). 

128 characters are too less, one byte is too small (since max possible combinations with one byte = 256)

Somebody finally set out to create one encoding standard to unify all encoding standards. This standard is Unicode. It basically defines a ginormous table of 1,114,112 code points that can be used for all sorts of letters and symbols. That's plenty to encode all European, Middle-Eastern, Far-Eastern, Southern, Northern, Western, pre-historian and future characters mankind. Unicode is big enough to allow for unofficial, private-use areas.

UTF-32 is such an encoding that encodes all Unicode code points using 32 bits. That is, four bytes per character. It's very simple, but often wastes a lot of space. UTF-16 and UTF-8 are variable-length encodings. If a character can be represented using a single byte (because its code point is a very small number), UTF-8 will encode it with a single byte. If it requires two bytes, it will use two bytes and so on.

If two systems are talking to each other, they always need to specify what encoding they want to talk to each other in. The simplest example of this is this website telling your browser that it's encoded in UTF-8.

In this day and age, the standard encoding is UTF-8 since it can encode virtually any character of interest, is backwards compatible with the de-facto baseline ASCII and is relatively space efficient for the majority of use cases nonetheless.

The days of one byte = one character are over and both programmers and programs need to catch up on this.



#### References
1. http://kunststube.net/encoding/
