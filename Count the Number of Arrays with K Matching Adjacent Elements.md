# HARD
Can be done using Permutation and Combination 
**3405**
Will do the python solution on 22nd June with explanation

```cpp
int MOD = 1e9+7;
class Solution {
public:
    //Binary exponentiation T.C : O(log(b))
    int findPower(long long a, long long b) {
        if(b == 0)
            return 1;

        long long half = findPower(a, b/2);
        long long result = (half * half) % MOD;

        if(b%2 == 1) {
            result = (result * a) % MOD;
        }

        return result;
    }

    //nCr ka formula apply karne k lie
    long long nCr(int n, int r, vector<long long>& factorial, vector<long long>& fermatFact) {
        //n!/((n-r)! * r!)) % MOD
        //n! * 
        return factorial[n] * fermatFact[n-r] % MOD * fermatFact[r] % MOD; //O(1)
    }

    int countGoodArrays(int n, int m, int k) {
        vector<long long> factorial(n+1, 1);
        factorial[0] = 1;
        factorial[1] = 1;
        for(int i = 2; i <= n; i++) {
            factorial[i] = (factorial[i-1] * i) % MOD;
        }

        //Inverse factorial precalculate - Fermat's little theorem
        vector<long long> fermatFact(n+1, 1);
        for(int i = 0; i <= n; i++) {
            fermatFact[i] = findPower(factorial[i], MOD-2);
        }

        long long result = nCr(n-1, k, factorial, fermatFact); //n-1Ck

        result = result * m % MOD;

        result = result * findPower(m-1, n-k-1) % MOD; //T.C : log(n-k-1)


        return result;
    }
};
```

# COMBINATORICS CODE:

```CPP
const int mod=1e9+7;
class Solution {
public:
    static inline long long modPow(long long x, int exp, int Mod=mod){
        if (exp==0) return 1;
        int y=(exp&1)?x:1;
        return modPow(x*x%Mod, exp>>1)*y%Mod;
    }

    // Euclidean algo finds x, y, d such that ax+by = d where d=gcd(a, b
    static inline int modInverse(int a, int b=mod) {//mod is prime d=1
        int x0 = 1, x1 = 0;
        int r0 = a, r1 = b;
        while (r1 != 0) {
            int q = r0/r1, rr = r1, xx = x1;
            r1 = r0-q * r1;
            x1 = x0-q * x1;
            r0 = rr;
            x0 = xx;
        }
        if (x0 < 0) x0+= b;
        return x0;
    }
    static long long comb(int n, int k){
        if (n<2*k) return comb(n, n-k);
        long long denominator=1;
        for(int i=1; i<=k; i++){
            denominator*=i;
            if (denominator>mod) denominator%=mod;
        }
        long long ans=modInverse(denominator);
        for (int i=n; i>=n-k+1; i--){
            ans*=i;
            if (ans>mod) ans%=mod;
        }
        return ans;
    }
    static int countGoodArrays(int n, int m, int k) {
        return m*modPow(m-1, n-k-1)%mod*comb(n-1, k)%mod;
        
    }
};
```

