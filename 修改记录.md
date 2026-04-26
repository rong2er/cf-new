
### 一、 删掉节点名称后缀
这一步把类似 `-443-Trojan-WS-TLS` 这种尾巴全删掉了。

**修改前：**
```javascript
const nodeName = `${nodeNameBase}-${port}${suffix}`;
```

**修改后：**
```javascript
const nodeName = nodeNameBase;
```
> **说明**：此修改应用到了代码中所有出现此行的地方（共 5 处）。

---

### 二、 优化 ALPN 设置
这一步是为了增加节点的稳定性。

**修改前：**
```javascript
'h3'
// 或者
'h3,h2'
```

**修改后：**
```javascript
'h3,h2,http/1.1'
```
> **说明**：所有涉及 `alpn` 的地方都统一改成了这个，这样你的节点兼容性会更好。

---

### 三、 禁用原生地址
确认以下这两行代码前面有 `//`，表示它们已经不生效了。

**状态：**
```javascript
//const nativeList = [{ ip: workerDomain, isp: '原生地址' }];
//await addNodesFromList(nativeList);
```
### 一、 删掉节点名称后缀

