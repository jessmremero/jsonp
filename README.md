# jsonp
jsonp跨域
简单来讲，就是把要传递的数据包裹在callback函数里面，这样其他的跨域网站在加载你的js文件时，就会收到你响应的数据，
同时它可以重新定义callback函数，最终实现把这些数据放到页面里的目的
例：
else if(path === '/main.js'){  
    var string = fs.readFileSync('./main.js', 'utf8')   
	var functionName = query.callback
    response.end(functionName + '(2)')//服务设置好，HTML调用main.js最终返回的形式是（假设?callback=xxx）xxx(1).只需要在HTML中定义好xxx函数就好
  }
  例如：服务器设置好想要传递的数据是2，但是该数据是包裹在一个动态的查询参数里面的
  <script >
  function ccc(x){
    document.write(x)
  }
</script>
<script src="http://localhost:8888/main.js?callback=ccc"></script>
其他跨域网站在加载该js文件时，控制台打出ccc(2)，然后可以随意定义这个ccc，最终达到输入到页面里的目的
