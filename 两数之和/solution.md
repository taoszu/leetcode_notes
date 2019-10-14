数组是无序的，比较便捷的方法就是按照k-v(元素-下标)形式将数据元素进行判断和存储，判断差是否在k中有存储，若有，说明存在，否则把元素进行存储。因为只需要扫描一遍，时间复杂度O(n)，空间复杂度O(n)。。

```java
public class Q1_TwoSum {
	public int[] twoSum(int[] nums, int target) {
		if (null == nums || nums.length < 2)
			return null;
		//保留結果
		int[] result = new int[2];
		Map<Integer, Integer> resultMap = new Hashtable<Integer, Integer>();
		for (int i = 0; i < nums.length; i++) {
			//求差
			int differ = target - nums[i];
			//存在k，说明符合条件
			if (resultMap.containsKey(differ)) {
				int tmpResult = resultMap.get(differ);
				if (tmpResult > i) {
					//输出正确的数组下标
					result[0] = i;
					result[1] = tmpResult;
				} else {
					result[0] = tmpResult;
					result[1] = i;
				}
				return result;
			} else {
				//k-v存储
				resultMap.put(nums[i], i);
			}
		}
		return null;
	}
}
```