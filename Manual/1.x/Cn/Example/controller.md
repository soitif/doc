# 控制器
## URL解析规则
内置路由支持无限层级的路由,即Controller可以无限嵌套目录,如:

http://127.0.0.1:9501/api/auth/login

执行的方法为:\App\Controller\Api\Auth::login()

http://127.0.0.1:9501/a/b/c/d/f

如f为控制器名,执行的方法为:\App\Controller\A\B\C\D\F::index()
如F为方法名,执行的方法为:\App\Controllers\A\B\C\D::f()

## 示例代码
例如分别建立App\Controller\Api\Auth与App\Controller\Api\Index控制器。
```
namespace App\Controller\Api;


use Core\AbstractInterface\AbstractController;
use Core\Http\Message\Status;

class Auth extends AbstractController
{

    function index()
    {
        // TODO: Implement index() method.
        $this->response()->write("api auth index");
    }

    function onRequest($actionName)
    {
        // TODO: Implement onRequest() method.
    }

    function actionNotFound($actionName = null, $arguments = null)
    {
        // TODO: Implement actionNotFound() method.
        $this->response()->withStatus(Status::CODE_NOT_FOUND);
    }

    function afterAction()
    {
        // TODO: Implement afterAction() method.
    }
    function login(){
        /*
         * url is /api/auth/login/index.html
         */
        $this->response()->writeJson(Status::CODE_OK,null,'this is auth login ');
    }
}
```

```
namespace App\Controller\Api;


use Core\AbstractInterface\AbstractController;
use Core\Http\Message\Status;
use Core\Http\Message\UploadFile;

class Index extends AbstractController
{

    function index()
    {
        // TODO: Implement index() method.
        $this->response()->write("this is api index");/*  url:domain/api/index.html  domain/api/  */
    }

    function afterAction()
    {
        // TODO: Implement afterAction() method.
    }

    function onRequest($actionName)
    {
        // TODO: Implement onRequest() method.
    }

    function actionNotFound($actionName = null, $arguments = null)
    {
        // TODO: Implement actionNotFount() method.
        $this->response()->withStatus(Status::CODE_NOT_FOUND);
    }

    function afterResponse()
    {
        // TODO: Implement afterResponse() method.
    }
    function api(){
        $this->response()->write("this is api api");
    }
}
```
若想访问Auth::index,则URL为ip:port/api/auth/index.html

<script>
    var _hmt = _hmt || [];
    (function() {
        var hm = document.createElement("script");
        hm.src = "https://hm.baidu.com/hm.js?4c8d895ff3b25bddb6fa4185c8651cc3";
        var s = document.getElementsByTagName("script")[0];
        s.parentNode.insertBefore(hm, s);
    })();
</script>
<script>
(function(){
    var bp = document.createElement('script');
    var curProtocol = window.location.protocol.split(':')[0];
    if (curProtocol === 'https') {
        bp.src = 'https://zz.bdstatic.com/linksubmit/push.js';        
    }
    else {
        bp.src = 'http://push.zhanzhang.baidu.com/push.js';
    }
    var s = document.getElementsByTagName("script")[0];
    s.parentNode.insertBefore(bp, s);
})();
</script>
