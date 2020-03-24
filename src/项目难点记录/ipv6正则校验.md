# IPv6校验

提到校验，第一反应使用正则，于是

根据 IPv6 地址格式：

- 冒分16进制
- 8组最多4个

于是得到

```javascript
const IPv6Reg = /^([0-9a-fA-F]{1,4}:){7}([0-9a-fA-F]{1,4}){1}$/
```

但是IPv6有简写形式，如果ip单元中出现全是0的项，可以用双冒号省略(::), 一组中出现多出可以简写的地方只能简写最右边的一组

在简写约束下，在使用正则就比较复杂，正面解决比较麻烦，于是我通过反面处理，基于规则用函数方式校验

通过分析得规则如下：

- 标准IPv6格式符合要求
- 简写方式必然会出现有且只有一次双冒号分隔符 (::)
- 简写的ip单元总数不超过7，最多等于7
- 简写分割的右面部分不能出现可以简写的ip单元
- 高位零按严格书写标准限制

```javascript
function IPv6UnitTest(unitArr, callback) {
    unitArr.every((unit, index) => {

        // 高位0检验
        if (/^0+\d$/.test(unit)) {
            callback('填写错误，IPv6单元禁止高位0')
        }

        if (!(/^[0-9a-fA-F]{1,4}$/.test(unit))) {
            callback(`填写错误，第${index + 1}单元不符合4位16进制要求`);
        }
        return /^[0-9a-fA-F]{1,4}$/.test(unit);
    });
}

export const IPv6SimpleValidateFunc = (rule, value, callback) => {
    console.log(value)
    if (fullIPv6Reg.test(value)) {
        callback()
    }

    const simpleSplit = value.split('::');
    if (simpleSplit.length > 2) {
        callback("ipv6中只能有一次简写")
    }

    if (simpleSplit.length !== 2) {
        callback("请正确输入IPv6地址")
    }

    console.log(simpleSplit)

    let totalGroup = []
    simpleSplit.forEach((current, index) => {
        console.log(1, current)
        totalGroup = totalGroup.concat(current.split(":"))

        if (index === 1 && current.length > 0) {
            // 这里面不能有可简写的存在
            current.split(":").every(item => {
                if (item === '0') {
                    callback('简写方式不正确，请优先对右边单元简写')
                } else {
                    return true
                }
            })
        } else {
            // 处理 aaaa:: (::)双冒号结尾的情况
            totalGroup.pop()
        }
    })

    console.log(totalGroup)
    if (totalGroup.length > 7) {
        callback('IPv6简写地址单元数不能超过7')
    }

    IPv6UnitTest(totalGroup, callback)

    callback()
}
```
