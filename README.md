# leetcode
Problem 3336 solution  on leetcode , 

class Solution:
    def subsequencePairCount(self, nums: List[int]) -> int:
        MOD = 10 ** 9 + 7
        @cache
        def dp(i, gcd1, gcd2):
            if i == len(nums):
                if gcd1 == gcd2 and gcd1 != -1: return 1
                return 0
            ans =  dp(i + 1, math.gcd(gcd1 if gcd1 != -1 else nums[i], nums[i]), gcd2) + dp(i + 1, gcd1,  math.gcd(gcd2 if gcd2 != -1 else nums[i], nums[i])) + dp(i + 1, gcd1, gcd2)
            return ans % MOD
        
        return dp(0, -1, -1)

