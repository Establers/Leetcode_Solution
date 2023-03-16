# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
입력으로 들어올 수 있는 num 의 범위는 `-10^9 <= nums[i] <= 10^9` 이므로
매우 크다고 판단해서 리스트로는 못한다고 생각했고

시간을 따졌을 때 $O(n^2)$ 보다는 작게해야 한다고 해서
list를 순회하면 안된다고 생각함

그래서 dictionary로 값을 조회하기로 했음
인덱스를 찾아서 리턴하는 문제이기 때문에
num : idx 로 관리해서 숫자를 기준으로 인덱스를 찾으려고 함

# Approach
<!-- Describe your approach to solving the problem. -->
1. a + b = target 일 때, target - b 가 diff 라고 하고 diff가 dict에 있다면 a + b = target 을 만족하는 a가 있다는 것

2. 그래서 diff in num_dict 으로 조사를 한다.
3. 만약 있다면 num_diff[diff] 는 순서상 먼저 들어가 있기에 먼저 넣고, i를 넣는다
4. 없다면 받은 num 값을 i의 인덱스로 딕셔너리에 넣는다. 

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ --> 

- Space complexity: $O(n)$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->


# Code
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int] :
        num_dict = {}

        for i, num in enumerate(nums) : 
            diff = target - num

            if diff in num_dict : 
                if num_dict[diff] != i :
                    return [num_dict[diff], i]
            
            num_dict[num] = i

        
```
