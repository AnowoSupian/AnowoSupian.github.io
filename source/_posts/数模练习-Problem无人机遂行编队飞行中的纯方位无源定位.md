---
title: 数模练习-Problem无人机遂行编队飞行中的纯方位无源定位
date: 2025-08-04 21:47:26
tags: 数模
---

### 无人机遂行编队飞行中的纯方位无源定位






看了百万年才看懂到底怎么解决第一题，也是被语文给难住了家人们。

不过没关系啊，虽然我们16号才动笔，但是我觉得完全来得及啊

<!-- ![]() -->

上面的图中，其中圆心的无人机 $FY0_0$ 和编队中 $FY0_i$ 和 $FY0_j$ 是发射无人机，然后 $FY0_k$ 是接收无人机

不妨将整幅图看作极坐标，那么 $FY0_0$ 的位置是 $\left(0, 0\right)$， $FY0_i$ 是 $\left(R, a_i\right)$， $FY0_j$ 是 $\left(R, a_j\right)$， $FY0_k$ 是 $\left(\rho, \theta\right)$

**注意，这里所有的 $a_i$ $a_j$ 都是代表弧度制**

那么，根据我们二年级所学的正弦定理可知：

当 $a_{ij} = a_{ik} + a_{jk}$ 且 $\frac{\pi}{2} < a_{ij} < \pi$ 时，我们有

$$ \frac{r}{\sin a_{ij}} \mkern-2mu = \mkern-2mu \frac{\rho}{\sin(a_{ij} + \theta - a_j)} $$

联立以上两式，可以解出无人机FY0k的坐标为：

$$ \theta = \arctan (\frac{\sin(a_{ij}·\sin(a_{ij} + a_j)) - \sin(a_{ij})·\sin{a_{ik} - a_i}}{\sin(a_{jk}·\sin(a_{ik} - a_i)) - \sin(a_{ik})·\sin{a_{jk} + a_j}})

分别四个方向，不一一列举了



```python
import numpy as np


def locate_drone(r, alpha_i, alpha_j, alpha_ij, alpha_ik, alpha_jk, tol=1e-5):
    """
    根据四种角度关系计算接收无人机的位置

    参数:
    r: 圆周半径
    alpha_i: 无人机i的角度（弧度）
    alpha_j: 无人机j的角度（弧度）
    alpha_ij: 无人机i和j在接收点形成的夹角（弧度）
    alpha_ik: 无人机i和圆心在接收点形成的夹角（弧度）
    alpha_jk: 无人机j和圆心在接收点形成的夹角（弧度）
    tol: 浮点数比较容差

    返回:
    (rho, theta): 接收无人机的极坐标位置
    case_used: 使用的情况编号(1-4)
    """

    # 情况1: α_ij = α_ik + α_jk 且 π/2 < α_ij < π
    if abs(alpha_ij - (alpha_ik + alpha_jk)) < tol and (np.pi / 2 < alpha_ij < np.pi):
        num = np.sin(alpha_ik) * np.sin(alpha_jk + alpha_j) - np.sin(alpha_jk) * np.sin(alpha_ik - alpha_i)
        den = np.sin(alpha_jk) * np.cos(alpha_ik - alpha_i) - np.sin(alpha_ik) * np.cos(alpha_jk + alpha_j)
        theta = np.arctan2(num, den)
        rho = r * np.sin(alpha_ik - alpha_i + theta) / np.sin(alpha_ik)
        return (rho, theta), 1

    # 情况2: α_jk = α_ik + α_ij
    elif abs(alpha_jk - (alpha_ik + alpha_ij)) < tol:
        num = np.sin(alpha_ik) * np.sin(alpha_jk - alpha_j) - np.sin(alpha_jk) * np.sin(alpha_ik - alpha_i)
        den = np.sin(alpha_jk) * np.cos(alpha_ik - alpha_i) - np.sin(alpha_ik) * np.cos(alpha_jk - alpha_j)
        theta = np.arctan2(num, den)
        rho = r * np.sin(alpha_ik - alpha_i + theta) / np.sin(alpha_ik)
        return (rho, theta), 2

    # 情况3: α_ik = α_jk + α_ij
    elif abs(alpha_ik - (alpha_jk + alpha_ij)) < tol:
        num = np.sin(alpha_ik) * np.sin(alpha_jk + alpha_j) - np.sin(alpha_jk) * np.sin(alpha_ik - alpha_i)
        den = np.sin(alpha_jk) * np.cos(alpha_ik - alpha_i) + np.sin(alpha_ik) * np.cos(alpha_jk + alpha_j)
        theta = np.arctan2(num, den)
        rho = r * np.sin(alpha_ik - alpha_i - theta) / np.sin(alpha_ik)
        return (rho, theta), 3

    # 情况4: α_ij = α_ik + α_jk
    elif abs(alpha_ij - (alpha_ik + alpha_jk)) < tol:
        num = np.sin(alpha_ik) * np.sin(alpha_jk + alpha_j) - np.sin(alpha_jk) * np.sin(alpha_ik + alpha_i)
        den = np.sin(alpha_jk) * np.cos(alpha_ik + alpha_i) - np.sin(alpha_ik) * np.cos(alpha_jk + alpha_j)
        theta = np.arctan2(num, den)
        rho = r * np.sin(-alpha_ik - alpha_i + theta) / np.sin(alpha_ik)
        return (rho, theta), 4

    else:
        raise ValueError("角度关系不满足任何已知情况。请检查输入角度。")


# 测试用例
def test_location_cases():
    """测试四种情况下的定位计算"""
    r = 100.0  # 圆周半径
    # 无人机i和j的位置角度（弧度）
    alpha_i = np.pi / 4  # 45度
    alpha_j = np.pi / 3  # 60度

    # 情况1测试数据
    alpha_ij1 = 2.0  # 约114.6度
    alpha_ik1 = 0.8
    alpha_jk1 = 1.2
    print("情况1测试:")
    pos1, case1 = locate_drone(r, alpha_i, alpha_j, alpha_ij1, alpha_ik1, alpha_jk1)
    print(f"计算结果: ρ = {pos1[0]:.2f}, θ = {np.degrees(pos1[1]):.2f}°, 使用情况: {case1}")

    # 情况2测试数据
    alpha_ik2 = 0.6
    alpha_ij2 = 0.8
    alpha_jk2 = alpha_ik2 + alpha_ij2
    print("\n情况2测试:")
    pos2, case2 = locate_drone(r, alpha_i, alpha_j, alpha_ij2, alpha_ik2, alpha_jk2)
    print(f"计算结果: ρ = {pos2[0]:.2f}, θ = {np.degrees(pos2[1]):.2f}°, 使用情况: {case2}")

    # 情况3测试数据
    alpha_jk3 = 0.5
    alpha_ij3 = 0.7
    alpha_ik3 = alpha_jk3 + alpha_ij3
    print("\n情况3测试:")
    pos3, case3 = locate_drone(r, alpha_i, alpha_j, alpha_ij3, alpha_ik3, alpha_jk3)
    print(f"计算结果: ρ = {pos3[0]:.2f}, θ = {np.degrees(pos3[1]):.2f}°, 使用情况: {case3}")

    # 情况4测试数据
    alpha_ik4 = 0.4
    alpha_jk4 = 0.5
    alpha_ij4 = alpha_ik4 + alpha_jk4
    print("\n情况4测试:")
    pos4, case4 = locate_drone(r, alpha_i, alpha_j, alpha_ij4, alpha_ik4, alpha_jk4)
    print(f"计算结果: ρ = {pos4[0]:.2f}, θ = {np.degrees(pos4[1]):.2f}°, 使用情况: {case4}")


# 运行测试
if __name__ == "__main__":
    test_location_cases()
```