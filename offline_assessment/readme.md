# 前言

为了尽量减少沟通上的障碍，特此编写本文档。

# 语言

我擅长的语言是`C++`和`Python`，你可以从中选一门语言让我作答。但是，根据题目的一些特殊性质，我可能会请求你更换语言编写。比如以下原因：

1. 一些数据结构上的性能开销，`Python`比`C++`慢得多，这时如果我发现这道题使用`Python`有超时（时间超限，Time Limited Exceed）的风险，我会告诉你我**建议**选择`C++`解答。
2. 一些题目处理输入输出比较麻烦，这时我会告诉你我**建议**选择`Python`解答。

注：

1. 我不会`Java`，一般这种情况我只会使用GPT将写出的`C++`或`Python`代码转成`Java`代码。这种转换可能会对代码造成一些潜在的影响，包括但不限于：将有序集转换成无序集，最终导致代码出错，这种情况我无法注意到。
2. 如果选择使用`Python`提交，那么选择使用`pypy3`提交（一般OJ上都会有），`pypy3`性能上比`Python3`更加优秀，发生诸如时间超限的概率也会降低。

# 面试进行前

本章将介绍面试进行前的工作。如果有额外的需求，请提前跟我说。

## 预约

请提前一些时间预约，在[这里](https://docs.qq.com/form/page/DYlpzRFhVSXR0QlNx)填写你的预约信息。

## 选定代码共享的方式

我将在以下3种通道之一，注册一个专属的实时通道，并且发送给你。我将在上面直接写所需要的内容。我一边写，你会一边看到。

1. [codeshare](https://codeshare.io/)
2. 飞书
3. Google Docs

这个由你进行选择。如果选择的是第2-3种，我开通完文档后，会向你发送链接，请你向我【申请编辑权限】。

## 选定题目传达的方式

支持以下3种通道：

1. 拍照
2. 腾讯会议（共享屏幕）
3. Zoom（共享屏幕）

这个由你进行选择。如果选择的是第2-3种，为了节约时间，**由你**提前开通一个会议，告诉我会议的链接，并且共享你的屏幕。

## 选定你的语言

目前只支持以下2种语言：

1. `C++`
2. `Python`

# 面试进行中

本章将介绍面试进行中的工作。

## 题目传达

如果你选择的是第1种共享方式，那么发送的图片需要注意如下内容：需要**讲清楚题目**的意思，然后把对应的内容发送图片即可，例如只包含以下文字的图片：

```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
```

### *注意*

如果题意不清晰，我会提供一个输入样例给你，由你去询问面试官这个输入样例应该给出什么结果。

示例：面试官的题意模糊不清，只提供了以下内容：

```
all subsets
```

那么我会让你问面试官，以下输入样例会给出什么结果？

```
[1,2,3]
```

那么面试官告诉你，应该返回以下内容，我这边就明白了，原来他是要求出给定输入数组的幂集：

```
[[],[1],[2],[3],[1,2],[1,3],[2,3],[1,2,3]]
```

## 回复

在专属的通道上回复，我会分为如下的几个步骤（假设使用的语言是`Python`）。

1. 收到题目后，我首先会用简单的几句话写思路。以上面的题目为例，我会写：

```py
# 由于字符最多只有26个，因此字符串的长度至多为26。我们只需要枚举每个字符作为左端点，然后逐渐向右扩展，遇到第一个遇到过的字符停下即可。
```

2. 开始编写代码。

```py
def solve(s)
    n = len(s)
    ans = 0
    for i in range(n):
        st = set()
        for j in range(i, n):
            if s[j] in st:
                break
            st.add(s[j])
        ans = max(ans, len(st))
    return ans
```

3. 生成注释。如果生成的注释不清晰，我还会进一步修正。

```py
def solve(s):
    # 获取输入字符串的长度
    n = len(s)
    # 初始化答案为0
    ans = 0
    # 外层循环，从字符串的每一个字符开始
    for i in range(n):
        # 创建一个空集合用于存储不重复的字符
        st = set()
        # 内层循环，从当前字符开始，遍历到字符串的末尾
        for j in range(i, n):
            # 如果字符已经在集合中，结束内层循环
            if s[j] in st:
                break
            # 如果字符不在集合中，将其添加到集合
            st.add(s[j])
        # 更新答案为目前找到的最大不重复子串的长度
        ans = max(ans, len(st))
    # 返回最长无重复字符子串的长度
    return ans
```

4. 如果有样例，我会编写测试样例代码。

```py
print(solve("abcabcbb"))
print(solve("pwwkew"))
print(solve("bbbbb"))
```

因此，最终页面看起来如下：

```py
# 由于字符最多只有26个，因此字符串的长度至多为26。我们只需要枚举每个字符作为左端点，然后逐渐向右扩展，遇到第一个遇到过的字符停下即可。

def solve(s):
    # 获取输入字符串的长度
    n = len(s)
    # 初始化答案为0
    ans = 0
    # 外层循环，从字符串的每一个字符开始
    for i in range(n):
        # 创建一个空集合用于存储不重复的字符
        st = set()
        # 内层循环，从当前字符开始，遍历到字符串的末尾
        for j in range(i, n):
            # 如果字符已经在集合中，结束内层循环
            if s[j] in st:
                break
            # 如果字符不在集合中，将其添加到集合
            st.add(s[j])
        # 更新答案为目前找到的最大不重复子串的长度
        ans = max(ans, len(st))
    # 返回最长无重复字符子串的长度
    return ans

print(solve("abcabcbb"))
print(solve("pwwkew"))
print(solve("bbbbb"))
```

###

如果你写错了，我会进行提醒。以上面为例，你在第7行将`s[j]`写成了`s[i]`，如下：

```py
def solve(s)
    n = len(s)
    ans = 0
    for i in range(n):
        st = set()
        for j in range(i, n):
            if s[i] in st:
                break
            st.add(s[j])
        ans = max(ans, len(st))
    return ans
```

我会这样子输入很多个字符`v`提醒你下一行有错，比如：

```py
def solve(s)
    n = len(s)
    ans = 0
    for i in range(n):
        st = set()
        for j in range(i, n):
            vvvvvvvvvvv抄错了
            if s[i] in st:
                break
            st.add(s[j])
        ans = max(ans, len(st))
    return ans
```

# 关于等待

如果选择的是第1种题目传达方式，我会在预约的开始时间内**45分钟关注消息（因为通常45分钟内就开始写代码）**，如果超过45分钟我会认为你这场面试不需要写代码，从而不会太关注消息。如果超过了这个时间仍然需要写代码，请通过拨打电话/视频提醒我，谢谢！
