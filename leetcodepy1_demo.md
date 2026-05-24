# /leetcodepy1 命令使用说明

## 功能描述
通过输入 `/leetcodepy1` 命令，可以快速输出 LeetCode 第一题的 Python 解法代码。

## 输出内容
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        d = {}
        for i, x in enumerate(nums):
            if (y := target - x) in d:
                return [d[y], i]
            d[x] = i
```

## 使用方法
1. 在 Rime 输入法中切换到支持符号命令的输入方案（如五笔·拼音）
2. 输入 `/leetcodepy1`
3. 从候选列表中选择对应的 Python 代码
4. 按空格或回车键输出完整代码

## 配置位置
此功能通过修改 `symbols.custom.yaml` 文件实现，位于：
- `/storage/emulated/0/Yuoek/rime/external/data/rime/symbols.custom.yaml`

## 配置内容
```yaml
punctuator:
  symbols:
    "/leetcodepy1": ["class Solution:\n    def twoSum(self, nums: List[int], target: int) -> List[int]:\n        d = {}\n        for i, x in enumerate(nums):\n            if (y := target - x) in d:\n                return [d[y], i]\n            d[x] = i"]
```

## 注意事项
- 需要重新部署 Rime 配置才能生效
- 确保输入方案已启用符号命令功能
- 代码中的 `List` 类型提示需要导入 `typing` 模块