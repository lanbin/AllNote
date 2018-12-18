LinkedList链表是LeetCode中经常出现的数据结构。

其节点基本模型可以写成

```javascript
// 链表节点
class ListNode {
    constructor(val = '', next = null) {
        this.val = val
        this.next = next
    }
}
```

通过不断创造新的节点，并且按照源数据的顺序将节点前后链接，便获得了一个链表。

在LeetCode中，对于链表的使用主要是

- 将给到的数组转成链表
- 将链表的所有的值进行打印
- 对比两个链表是否相似

```javascript
const List = {}

// 从数组转换成链表
List.from = data => {
  let current = null
  let next = null

  // 从后往前，因为next的值需要是先确定后一个节点
  if (Array.isArray(data)) {
    for (var index = data.length - 1; index >= 0; index--){
      current = new ListNode(data[index], current)
    }
  }
  return current
}

// 循环拿出节点的值，并使用符号连接起来输出
List.display = node => {
  let val = []
  while (node) {
    val.push(node.val)
    node = node.next
  }
  console.log(val.join('->'))
}

// 对比两个链表在相同位置节点的值是否一样
List.compareValue = (l1, l2) => {
  while (l1) {
    // 如果l2没有了 则false
    if (!l2) return false
    // 如果值不一样 则false
    if (l1.val !== l2.val) return false

    l1 = l1.next
    l2 = l2.next
  }

  // l1匹配结束之后 l2也应该结束
  return !l1 && !l2
}
```

以上方法，基本可以满足在测试用例中， 对于解题结果的使用。