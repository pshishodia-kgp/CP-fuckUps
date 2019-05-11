CP - fuckUps

1. `if(a & b == c)` isn't `(a&b) == c`, but instead `a & (b == c)`, because the precedence of & is less than == and !=. 
Note : Use brackets around bitwise operators. 

2. To access second last element of a container 
`auto it = s.rbegin(); it--; ` is wrong as `it` is reverse iterator and thus it-- moves forward, thus pointing to undefined address. so use,
`auto it = s.rbegin(); it++; `

3. 2^20 > 10^6, and not 2^15. 

4. To convert number into string use `int x = 5; string s = to_string(x);`

5. To convert number into binary string use, `int x = 5; string s = bitset<3>(5).to_string();`, i.e, `bitset<Max_bits> (num).to_string()`
