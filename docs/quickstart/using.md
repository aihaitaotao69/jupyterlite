import random
from itertools import combinations

# 给定的数字列表
numbers = [
    10, 12, 14, 15, 22, 23, 25, 26, 27, 28,
    31, 32, 34, 36, 37, 38, 39, 40, 42, 46,
    47, 48, 49, 51, 54, 58, 59, 60, 61, 63,
    64, 67, 68, 69, 70, 71, 72, 73, 75, 76,
    78, 79, 80
]

# 生成100组有效的20个数字组合
valid_combinations = []

while len(valid_combinations) < 10:
    # 随机选择20个数字
    combo = random.sample(numbers, 20)
    combo = sorted(combo)
    diffs = [combo[i + 1] - combo[i] for i in range(len(combo) - 1)]
    diff_sum = sum(diffs)
    
    # 检查差值条件
    if (2 <= sum(1 for d in diffs if d == 1) <= 6) and \
       (2 <= sum(1 for d in diffs if d == 2) <= 5) and \
       (1 <= sum(1 for d in diffs if d == 3) <= 4) and \
       (0 <= sum(1 for d in diffs if d == 4) <= 4) and \
       (0 <= sum(1 for d in diffs if d == 5) <= 3) and \
       (0 <= sum(1 for d in diffs if d == 6) <= 2) and \
       (0 <= sum(1 for d in diffs if d == 7) <= 2) and \
       (0 <= sum(1 for d in diffs if d == 8) <= 2) and \
       (0 <= sum(1 for d in diffs if d == 9) <= 1) and \
       (0 <= sum(1 for d in diffs if d == 10) <= 1) and \
       ( diff_sum==73):
        valid_combinations.append(combo)

# 输出100组有效组合
for idx, valid_combo in enumerate(valid_combinations, start=1):
    print(f"组合 {idx}: {valid_combo}")
