CP - fuckUps

1. `if(a & b == c)` isn't `(a&b) == c`, but instead `a & (b == c)`, because the precedence of & is less than == and !=. 
Note : Use brackets around bitwise operators. 

2. To access second last element of a container 
`auto it = s.rbegin(); it--; ` is wrong as `it` is reverse iterator and thus it-- moves forward, thus pointing to undefined address. so use,
`auto it = s.rbegin(); it++; `

3. 2^20 > 10^6, and not 2^15. 

4. To convert number into string use `int x = 5; string s = to_string(x);`

5. To convert number into binary string use, `int x = 5; string s = bitset<3>(5).to_string();`, i.e, `bitset<Max_bits> (num).to_string()`

6. To check equality of two vectors, 

```
bool check = true; 
if(a.size() != b.size())check = false;
for(int i=0;i<a.size();++i)if(a[i] != b[i])check = false;
```

is wrong, because if sizes are different it will give runtime error. Simplest way is

```
if(a == b)cout<<"Same\n"; 
else cout<<"Not Same\n"; 
```

7. 
```
int res[2][2], temp[2][2]; 
res = temp; 
```
Equating two 2d arrays works weirdly, maybe passes the address. 

8. a^b + c is a^(b + c)

9. Do add operations before remove in MO's algorithm, because otherwise it may lead to seg-fault, if you're trying to delete elements from some container. For example you start from (l, r) = (0, -1) and (curr_l, curr_r) = (3, 3). Then doing, 

```
while(l < curr_l)remove(a[l++]); 
```
will lead to seg fault. Right way : 
```
        while(l > curr_l)add(a[--l]); 
        while(r < curr_r)add(a[++r]); 
        while(l < curr_l)remove(a[l++]); 
        while(r > curr_r)remove(a[r--]); 
```

10. Wrong Knapsack 
```
        for(int i=0;i<n;++i)
                for(int j=0;j<=sum; ++j)dp[j + a[i]] |= dp[j]
```
Right knapsack 
```
        for(int i=0;i<n;++i)
                for(int j = sum; j >= 0; --j)dp[j + a[i]] |= dp[j]; 
```
Because in first case, dp[j] may alter dp[j + a[i]] which may alter dp[j+ 2a[i]] which is wrong..

11. s is a string, then `s.erase(id)` doesn't remove the character at position id but all the characters following position id. Correct syntax is `s.erase(id, len)` , where len is the number of characters to be deleted (starting at id). 

12. `prefix[i] = prefix[i - 1] + (condition)? 1 : 0;` doesn't work while
`prefix[i] = prefix[i - 1] + (condition? 1 : 0)` works. because the former translates to `(prefix[i - 1] + condition)?` because of higher priority of `?` over `+`
