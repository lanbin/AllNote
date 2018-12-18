最近开始接触LeetCode. 它提供了一个非常不错的在线编辑和调试的IDE。

但是毕竟存在网络交互时间，而且还限制提交的频次。对于前端这种，改完就要马上得结果的工作习惯还是有点点影响。那么就在想能不能在本地也创造一个类似的编写、调试、验证的环境，将足够的测试用例通过后再提交上去。

本地的做题编写主要目的是进行快速的验证，那么其实这个过程就和单元测试很类似。每个文件提供一个方法，单元测试调用这个方法去和已知的结果进行比对，如果通过了所有的测试情况那么说明答案基本没问题，最多就是性能的优化了。

项目地址：[leetcode-environment-js](https://github.com/lanbin/leetcode-environment-js)

## 单元测试

单元测试分为

- TDD Test-Driven Development 测试驱动开发，关注结果
- BDD Behavior-Driven Development 行为驱动开发，关注逻辑

## 工具

NodeJs中的单元测试肯定就跑不开：Mocha+Chai

Mocha是一个测试框架，运行测试的工具。

Chai是一个断言库，他支持很多类似人类语言的方法调用来做结果的判断。断言库用来判断源码的执行结果和预期结果是否一致。

断言主要可以用来判断：

```javascript
// 是否相等
expect(x).to.be(.not).equal(x)

// 布尔值
expect(x).to(.not).be.ok

// typeof
expect(x).to.be.a(an)('string')

// include
expect(x).to.include(contain)(2)

// empty
expect(x).to.be.empty

// match
expect(x).to.match(new Reg())
```

__describe__为一个“测试Suite”，包含一组相关测试

__it__为一个“测试用例”，包含一个单独的测试

## 结合LeetCode

将LeetCode的解题文件放在**/src**下，测试文件放在**/test**下。测试文件中加入官方提供示例中的结果作为单元测试的初始测试用例，如果提交之后出现未通过的例子可以再手动在增加进来。

配置__package.json__

```json
{
  ...
  scripts: {
     "test": "mocha --compilers js:@babel/register --watch"
  }
}
```

使用@babel/register 可以使得Mocha编译执行ES6的文件。

```shell
$ npm test testFilePath
```

这样就可以针对某一个文件进行Watch，当解题文件或者测试文件出现修改的时候，单元测试将重新执行。这样就可以保存即得结果，快速的查看解题是否正确。

## 参考

- [http://www.dengzhr.com/node-js/1282](http://www.dengzhr.com/node-js/1282)
- [http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html](http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html)