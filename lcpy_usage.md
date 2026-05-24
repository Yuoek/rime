# lcpy 批量功能使用说明

## 功能描述
通过输入 `lcpyaa`、`lcpyab` 等命令可以快速输出对应的 LeetCode Python 代码模板。

## 支持的输入法方案
- 五笔·拼音 (wubi_pinyin)
- 朙月拼音 (luna_pinyin)

## 使用方法
1. 切换到支持的输入法方案
2. 输入对应的代码命令（如 `lcpyaa`、`lcpyab` 等）
3. 从候选列表中选择代码模板

## 当前可用的代码映射

### `lcpyaa` - Two Sum 问题
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        d = {}
        for i, x in enumerate(nums):
            if (y := target - x) in d:
                return [d[y], i]
            d[x] = i
```

### `lcpyab` - Add Two Numbers 问题
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(
        self, l1: Optional[ListNode], l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        dummy = ListNode()
        carry, curr = 0, dummy
        while l1 or l2 or carry:
            s = (l1.val if l1 else 0) + (l2.val if l2 else 0) + carry
            carry, val = divmod(s, 10)
            curr.next = ListNode(val)
            curr = curr.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        return dummy.next
```

## 扩展方法
要添加新的代码映射，只需编辑 `code.txt` 文件：
1. 添加新的输入命令（以 `lcpy` 开头，如 `lcpyaa`、`lcpyab` 等）
2. 在下一行开始添加对应的 Python 代码
3. 用空行分隔不同的代码映射

## 部署说明
配置已自动部署到以下文件：
- `lua/leetcode_translator.lua` - Lua 脚本实现（支持批量映射）
- `code.txt` - 代码映射配置文件
- `wubi_pinyin.custom.yaml` - 五笔·拼音方案配置
- `luna_pinyin.custom.yaml` - 朙月拼音方案配置
- `rime.lua` - Lua 脚本注册

重启 Rime 输入法后即可使用此功能。