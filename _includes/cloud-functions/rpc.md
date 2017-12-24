## <a name="use-rpc-another-way"></a> RPC 远程调用的新用法 {#use-rpc-another-way} 

首先，定义一个处理器，它的职责的是将传入的参数打包成一个 json 格式的参数字典，交给本地的 RPC 函数，并且它还需要处理返回的结果，将返回结果为 json 格式的字典正确的反序列化为用户定义的对象。

我们的需求是，我有一个云函数，它接收一个 字符串参数 id，这个 id 指的是电影的 id，然后它在云端查询打分表，然后算出一个结果，这个结果不只是包含了分数，还包含了电影的基本信息，比如导演，电影名称等关键数据，返回给客户端，客户端的调用结果是想拿到一个具体的 Movie 对象，Movie 对象代码如下：



```swift
class Movie {
    
    public var stars: Int = 0
    public var name: String = ""
    public var diretor: String = ""
    public var id: String = ""
}

```
然后，我定义一个 Id 处理器，他将 id 包装成参数字典，然后它也承担的将返回的 json 数据重新封装成一个全新的 Movie 对象，代码如下：

```swift
class MovieIdProcessor: RxAVRPCFunctionConvertible {

    func encode(entity: String) -> [String: Any] {
        return ["id": entity];
    }

    func decode(resultDictionary: [String: Any]) -> Movie {
        let movie = Movie()
        movie.diretor = resultDictionary["diretor"] as! String
        movie.stars = resultDictionary["stars"] as! Int
        movie.name = resultDictionary["name"] as! String
        return movie
    }

    typealias ParameterType = String

    typealias ResultType = Movie
}
```

然后我们需要定义一个 RPC 函数，他有 2 个必要的属性：

- 云函数名称 functionName，比如 `getStars`，对应的是你部署的云函数代码里面对应的函数名称

- 处理器 processor，我们前面已经实现了一个这样根据 id 然后获取电影对象的处理器

它的代码如下：

```swift
class GetMovieRPC: RxAVRPCFunction {
    var processor: MovieIdProcessor
    var functionName: String = ""
    init(funtionName: String, idProcessor: MovieIdProcessor) {
        self.functionName = funtionName
        self.processor = idProcessor
    }
}
```

最后就是我们调用一下：

```swift
let cloudFunction = GetMovieRPC(funtionName: "getStars", idProcessor: MovieIdProcessor())
cloudFunction.execute(parameter: "1008").subscribe { (done) in
    let movie = done.element
    print("\(movie?.stars)")
}
```