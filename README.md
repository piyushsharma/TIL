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

### Resource IDs

#### Integers
Maintaining a serialized number requires consistency... one place that is the keeper of numbers. In large systems this can become a bottleneck, a single point of failure, or both. In distributed systems, it is common to start relaxing this constraint (Consistency) in favor of the other two.

There are strategies to maintain serialized numeric identities in distributed systems, like the HI-LO algorithm or its derivatives, but it is still very possible to skip large swaths of numbers in case of node failures.

#### UUIDs
Another common method is to use a UUID, a randomly generated identifer (which is twice the size of Int64), which has a pretty high (but not 100%) chance of being unique from any other generated UUID. It's basically just a very large random number. This is nice for client operations, because the client can generate it with a pretty good chance of uniqueness, and subsequently use it to identify or track things. But collisions (same ID being generated) are possible (especially if the client has a terrible RNG) and still must be dealt with.

Most likely youtube identifers are some shorter variation of a uuid which is then converted to a variation of base64 without punctuation. Because punctuation kills the ability to be used in links. Hence, it's a very large number (either random or serialized) that has been converted to text so that it is shorter.

#### Strings
One identifier format that is fairly popular is "entity-#" or "system-entity-#" if you have a number of inter-operating systems. The # is generated either consistently by the owning system (still distributed in the sense that there are multiple systems, microservices, whatever) or with a HI-LO variation. And for display purposes, it's fairly trivial to strip off the prefix and just use the number portion.

### Semantic Versioning (SEMVER)
[ X.Y.Z ] => [6.10.11] 
1. the first part is the MAJOR number - it is bumped when changes in release would break a previous release 
(eg. change in user facing API)
2. the second (middle) part is the MINOR number - it is bumped when there is new functionality added without breaking previuos releases
3. the last bit is the PATCH number - bumped when no new functionality + maintains backward compatibility (fixing bugs)







#### References
1. http://kunststube.net/encoding/
2. https://softwareengineering.stackexchange.com/questions/301620/why-do-some-prominent-web-sites-use-alphanumeric-strings-for-resource-ids-instea/301641#301641
