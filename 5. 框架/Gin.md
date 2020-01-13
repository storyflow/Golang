- [gin.Default()](https://gowalker.org/github.com/gin-gonic/gin#Default)：返回Gin的type Engine struct{...}，里面包含RouterGroup，相当于创建一个路由Handlers，可以后期绑定各类的路由规则和函数、中间件等
- [router.GET(...){...}](https://gowalker.org/github.com/gin-gonic/gin#IRoutes)：创建不同的HTTP方法绑定到Handlers中，也支持POST、PUT、DELETE、PATCH、OPTIONS、HEAD 等常用的Restful方法
- [gin.H{...}](https://gowalker.org/github.com/gin-gonic/gin#H)：就是一个map[string]interface{}
- [gin.Context](https://gowalker.org/github.com/gin-gonic/gin#Context)：Context是gin中的上下文，它允许我们在中间件之间传递变量、管理流、验证JSON请求、响应JSON请求等，在gin中包含大量Context的方法，例如我们常用的DefaultQuery、Query、DefaultPostForm、PostForm等等

