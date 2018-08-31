# 状态管理

SDK 的有两个必须解决的问题：

1. 将调用方的输入都记录下来
2. 将记录下来的数据，编码成云端可识别的类型


在 LeanCloud SDK 中，开发者传递的都是语言内置的数据类型以及自定义的类型，而 SDK 需要将这些类型转化成 MongoDB 能识别的数据类型。首先我们来解决第一个问题：


## 将调用方的输入都记录下来

首先我们看下面一段代码：

```swift
public class RxAVObject {

    var localEstimatedData: [String: Any] = [String: Any]()
    public func get(key: String) -> Any? {
        if self.localEstimatedData.containsKey(key: key) {
            if let value = self.localEstimatedData[key] {
                return value
            }
        }
        return self.getProperty(key: key)
    }

    public func set(key: String, value: Any?) {
        if value == nil {
            self.performOperation(key: key, operation: AVDeleteOperation.sharedInstance)
        } else {
            let valid = AVCorePlugins.sharedInstance.avEncoder.isValidType(value: value!)
            if valid {
                self.performOperation(key: key, operation: AVSetOperation(value: value!))
            }
        }
    }
}
```
```typescript
```
```java
```


