.algorithm
==========

algorithm(C++)

Number Theroy

Modular arithmetic

  To compute modular exponentiation (x ^ y) mod N, since (x ^ y) may be very large, that means it is too large to present and process by compute neither int nor long long.
Consider two rules of modular arithmetic:
(a * b) mod p = ((a mod p) * (b mod p)) mod p 
(a ^ b) mod p = (a mod p) ^ b mod p

So here’s an idea: calculate x ^ y mod N by repeatedly multiplying by x modulo N,

x mod N → x2 mod N → x3 mod N → · · · → x ^ y mod N,

Luckily, we can do better: starting with x and squaring repeatedly modulo N , we get

x mod N → x2 mod N → x4 mod N → x8 mod N → · · · → x ^ (2 * log y) mod N.

Each takes just O(log 2 N ) time to compute, and in this case there are only log y multiplications.

Here is the example code for this algorithm(C++.):


/*this function wiil return 

 *(x^y) mod N
 
 */
 
 
int modPower(int x, int y, int N)  {

  	if (y == 0)
  	
		return 1;
		
	int z = modPower(x, y / 2, N);
	
	if ( (y & 1) ) {
	
		return (z * z * x) % N;
		
	} else {
	
		return  ( z * z ) % N;
		
	}
}




