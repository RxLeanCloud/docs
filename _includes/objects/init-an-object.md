# RxAVObject 基础用法

## 通过构造函数来构建 

```swift
var todo = RxAVObject(className: "RxTodo")

todo["title"] = "周报提醒"
todo["content"] = "每周五下午要提交周报"

todo.save().subscribe { (event) in
    print(event.element?.objectId)
}
```
```typescript
let todo: RxAVObject = new RxAVObject('RxTodo');

todo.set('title', '周报提醒');
todo.set('content', '每周五下午要提交周报');

todo.save().subscribe(() => {
    console.log('todo.title', todo.get('title'));
}});
```

## 通过已知的 className 和 objectId 来构建 

```swift
let todo = RxAVObject.createWithoutData(classnName: "RxSwiftTodo", objectId: "59fc0fd52f301e0069c76a67")
todo.fetch().subscribe(onNext: { (element) in
    let title = element.get(key: "title")
    print(title)
})
```

```typescript
let todo = RxAVObject.createWithoutData("RxTodo", "59fc0fd52f301e0069c76a67");
todo.fetch().subscribe(obj => {
    console.log('todo.title',todo.get('title'));
});
```

**注意**：上述代码在构建完成之后，主动的去服务端 fetch 了一下，这是常见的操作，这样一来客户端将获取到该对象在服务端最新的数据状态




