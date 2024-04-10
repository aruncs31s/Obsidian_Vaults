---
By: Laurie Kirk
defcon: "31"
---
# Runtime Riddles - Abusing Manipulation Points in the Android Source
Created : 2024-04-10 01:00

![[Def Conf/Pasted image 20240410012134.png]]
## Contents
![[Def Conf/Pasted image 20240410010432.png]]
![[Def Conf/Pasted image 20240410010539.png]]
![[Def Conf/Pasted image 20240410010609.png]]
- Its to load aditional code into android runtime
- Trying to defeat static analysis of android application

- Methods used for dynamic code loading
![[Def Conf/Pasted image 20240410010908.png]]
found inside of android framework

[[Dalvik]] ? executable

- android app decompiler jdex

- Hooks method while running 
	- Medusa 
	- Frida

#### Manipulating ANdroid ART
	 ![[Def Conf/Pasted image 20240410011325.png]]
ART takes codes from the disk and transforms apps into runtime objects 
ART is responsible for taking binaries that are defined on disk and parsing out all of the code inside of those into actual android runtime environment , mapping those into memory and making the relevent potions executable and actually executing the entry point of the perticular excutable binary

## References
1. https://youtu.be/Bq7Z3X4xwCE?si=hmZbtz21c9uyO53R