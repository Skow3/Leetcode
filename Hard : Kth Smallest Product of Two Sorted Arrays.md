# HARD
2040

I was not able to think of any other solution rather than bruteforce :

#### This question helped me pickup these concepts:
* Binary search more clear view of it
* How to approach differently , got a major point over it.
* How to optimize a problem like this

#### CPP SOLUTION [cred : MIK]
```cpp
class Solution {
public:

    long long findCountSmallest(vector<int>& nums1, vector<int>& nums2, long long midProduct) { 
        long long productsCount = 0;

        int n = nums2.size();

        for(int i = 0; i < nums1.size(); i++) {
            //nums1[i]

            if(nums1[i] >= 0) {
                int l = 0;
                int r = n-1;
                int m = -1; //invalid index on left hand side

                while(l <= r) {
                    int mid = l + (r-l)/2;
                    long long product = 1LL * nums1[i] * nums2[mid];

                    if(product <= midProduct) {
                        m = mid;
                        l = mid+1;
                    } else {
                        r = mid-1;
                    }
                }
                productsCount += (m+1); //covered by nums1[i]
            } else {
                //product will be negative and right hand side will contain smaller products and left hand side larger
                int l = 0;
                int r = n-1;
                int m = n; //invalid index on the right hand side

                while(l <= r) {
                    int mid = l + (r-l)/2;
                    long long product = 1LL * nums1[i] * nums2[mid];

                    if(product <= midProduct) {
                        m = mid;
                        r = mid-1;
                    } else {
                        l = mid+1;
                    }
                }
                                                    
                productsCount += (n - m);
            }
        }
        return productsCount;
    }

    long long kthSmallestProduct(vector<int>& nums1, vector<int>& nums2, long long k) {
        long long result = 0;

        long long l = -1e10; //min product possible
        long long r = 1e10; //max product possible

        while(l <= r) {
            long long midProduct = l + (r-l)/2;

            //check if this is kth smallest or not

            long long countSmallest = findCountSmallest(nums1, nums2, midProduct);

            if(countSmallest >= k) {
                result = midProduct;
                r = midProduct-1;
            } else {
                l = midProduct+1;
            }
        }
        return result;
    }
};
```

## UNDERSTOOD THIS SOLUTION :
1. Used binary search to search for elements <= midProduct
2. Used If-else for checking of negatives
3. This midProduct thing was quite different approahc from what i was thinking of.

Went for more better solutions in the solutions tab
```PYTHON
class Solution:
    def kthSmallestProduct(self, nums1, nums2, k):
        def separate(A):
            A1 = []
            A2 = []
            for a in A:
                if a < 0:
                    A1.append(-a)
                else:
                    A2.append(a)
            A1.reverse()
            return A1, A2

        def numProductNoGreaterThan(A, B, m):
            count = 0
            j = len(B) - 1
            for a in A:
                while j >= 0 and a * B[j] > m:
                    j -= 1
                count += j + 1
            return count

        A1, A2 = separate(nums1)
        B1, B2 = separate(nums2)

        negCount = len(A1) * len(B2) + len(A2) * len(B1)
        sign = 1

        if k > negCount:
            k -= negCount
        else:
            k = negCount - k + 1
            sign = -1
            B1, B2 = B2, B1

        l, r = 0, int(1e10)

        while l < r:
            m = (l + r) // 2
            if numProductNoGreaterThan(A1, B1, m) + numProductNoGreaterThan(A2, B2, m) >= k:
                r = m
            else:
                l = m + 1

        return sign * l
```


WILL COME TO THIS CODE AGAIN WHEN I'LL MOVE ON TO BINARY SEARCH AGAIN COMING TOPIC WISE
