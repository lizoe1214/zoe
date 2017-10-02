1. Identify the prefix free code and draw the decision tree.

|Xi|Code 1|Code 2|Code 3|Code 4|
|:---:|:---:|:---:|:---:|:---:|
|X1|0|0|0|00|
|X2|10|01|01|01|
|X3|110|001|011|10|
|X4|1110|0010|110|110|
|X5|1111|0011|111|111|

Ans: Code1、Code4
 
 code1:
 
      0/  \1
     X1 0/  \1
        X2 0/ \1
          X3 0/ \1
            X4   X5
    
   code4: 
   
      
     0/      \ 1
    0/ \1   0/ \1
    X1  X2 X3 0/\1
            X4   X5
    
    
    


2. Consider following symbols, compute a) the Huffman code, b) draw the code tree, c) the average code length, and d) the entropy of the code. 
{(A, 0.25), (B, 0.25), (C, 0.125), (D, 0.125), (E, 0.125), (F, 0.0625), (G, 0.0625)}

  1. 
Si	Pi	       Code
A   0.25         00
B   0.25         01
C   0.125       100
D   0.125       101
E   0.125       110
F   0.0625     1110
G   0.0625     1111
  
  
  
  
  ...2. 
  
 
  3. L = Σ{i=1:N} pili = 0.252 + 0.252 + 0.1253 + 0.1253 + 0.1253 + 0.06254 + 0.0625*4 = 0.5 + 0.5 + 0.375 + 0.375 + 0.375 + 0.25 + 0.25 = 2.625

  4. H = Σ{i=1:N} pi log2(1/pi) = 0.252 + 0.252 + 0.1253 + 0.1253 + 0.1253 + 0.06254 + 0.0625*4 = 0.5 + 0.5 + 0.375 + 0.375 + 0.375 + 0.25 + 0.25 = 2.625

3. Use LZW algorithm to encode "abcabcabcabcabcabcabc|abcabcabcabcabc".


|Current|Next|Output|Add to dictionay|Comments|
|:---:|:---:|:---:|:---:|:---|
|a 97|b 98|a 97|ab 256|'ab' not exist, add it to table|
|b 98|c 99|b 98|bc 257|'bc' not exist, add it to table|
|c 99|a 97|c 99|ca 258|'ca' not exist, add it to table|
|a 97|b 98|-|-|'ab' exists in table, 'abc' not|
|ab 256|c 99|ab 256|abc 259|add 'abc' to table|
|c 99|a 97|-|-|'ca' exists in table, 'cab' not|
|ca 258|b 98|ca 258|cab 260|add 'cab' to table|
|b 98|c 99|-|-|'bc' exists in table, 'bca' not|
|bc 257|a 97|bc 257|bca 261|add 'bca' to table|
|a 97|b 98|-|-|'ab' exists in table, 'abc' exists too, 'abca' not|
|abc 259|a 97|abc 259|abca 262|add 'abca' in table|
|a 97|b 98|-|-	|'ab' exists in table, so does 'abc' and 'abca', 'abcab' not|
|abca 262|b 98|abca 262|abcab 263|add 'abcab' in table|
|b 98|c 99|-|-|'bc' exists in table, bca' exist too, 'bcab' not|
|bca 261|b 98|bca 261|bcab 264|add 'bcab' to table|
|b 98|c 99|-|-|'bc' exist in table,'bca' exist too, bcab' exist too,'bcabc' not|
|bcab 264|c 99|bcab 264|bcabc 265|add 'bcabc' in table|
|c 99|a 97|-|-|'ca' exist in table,'cab' exist too, 'cabc' not|
|cab 260|c 99|cab 260|cabc 266|add 'cabc' in table|
|c 99|a 97|-|-|'ca' exist in table,'cab' exist too, 'cabc' exist too, 'cabca' not|
|cabc 266|a 97|cabc 266|cabca 267| add 'cabca' in table|
|a 97|b 98|-|-|'ab' exists in table, so does 'abc' and 'abca' and  'abcab' , 'abcabc' not|
|abcab 263|c 99|abcab 263|abcabc 268|add 'abcabc' in table|
|c 99|-|c 99|-|end|






