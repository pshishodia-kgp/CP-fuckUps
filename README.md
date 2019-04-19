CP - fuckUps

1. `if(a & b == c)` isn't `(a&b) == c`, but instead `a & (b == c)`, because the precedence of & is less than == and !=. 
Note : Use brackets around bitwise operators. 
