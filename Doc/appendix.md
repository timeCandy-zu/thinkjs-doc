## 附录

### 默认配置
```js
/**
 * 框架默认配置
 * 可以在App/Conf/config.js里修改下面的配置值
 * @type {Object}
 */
module.exports = {
  port: 8360, //监听端口
  use_proxy: false, //是否使用代理访问，如：nginx。开启后不能通过ip+端口直接访问
  encoding: 'utf8', //输出数据的编码
  url_pathname_prefix: '',  //不解析的pathname前缀
  url_pathname_suffix: '.html', //不解析的pathname后缀，这样利于seo
  app_tag_on: true, //是否支持标签功能
  url_resource_on: true,  //是否监听静态资源类请求
  url_resource_reg: /^(resource\/|static\/|favicon\.ico)/, //判断是否是静态资源的正则
  url_route_on: true, //是否开启自定义路由功能

  post_json_content_type: ['application/json'], //post数据为json时的content-type
  post_max_file_size: 1024 * 1024 * 1024, //上传文件大小限制，默认1G
  post_max_fields: 1000, //最大表单数
  post_max_fields_size: 2 * 1024, //单个表单最大值
  
  app_group_list: ['Home', 'Admin'], //分组列表
  default_group: 'Home', //默认分组
  default_controller: 'Index', //默认模块
  default_action: 'index',  //默认Action
  call_controller: 'Home:Index:_404', //controller不存在时执行方法，此配置表示调用Home分组下IndexController的_404Action方法
  call_method: '__call', //当找不到方法时调用什么方法，这个方法存在时才有效
  before_action: '__before', //调用一个action前调用的方法，会将action名传递进去
  after_action: '__after', //调用一个action之后调用的方法，会将action名传递进去
  url_params_bind: true, //方法参数绑定,将URL参数值绑定到action的参数上
  action_suffix: 'Action', //action后缀
  url_callback_name: 'callback', //jsonp格式的callback名字
  json_content_type: 'application/json', //发送json时的content-type
  auto_send_content_type: true, //是否自动发送Content-Type,默认值为`tpl_content_type`配置值
  log_process_pid: true, //记录进程的id,方便其他脚本处理。
  use_cluster: false, //是否使用cluster，默认不使用，0：为cpu的数量，可以自定义值
  autoload_path: {}, //autoload查找的path，用于thinkRequire加载自定义库的时候查找
  create_server_fn: '', //自定义create server全局函数名，可以在Common/common.js里实现

  load_ext_config: [], //加载额外的配置文件 CONF_PATH
  load_ext_file: [], //加载额外的文件 COMMON_PATH

  use_websocket: false, //是否使用websocket
  websocket_allow_origin: '', //允许从那里发送过来的websocket，可以是字符串、数组、回调函数，为空表示不检测
  websocket_sub_protocal: '', //websocket子协议，可以是个字符串也可以是回调函数
  websocket_message_handle: undefined, //websocket消息处理函数

  error_tpl_path: THINK_PATH + '/View/error.html', //错误页模版
  error_no_key: 'errno', //错误number的key
  error_no_default_value: 1000, //错误号默认值
  error_msg_key: 'errmsg', //错误消息的key

  cookie_domain: '', //cookie有效域名
  cookie_path: '/',   //cookie路径
  cookie_timeout: 0, //cookie失效时间，0为浏览器关闭，单位：秒

  session_name: 'thinkjs', //session对应的cookie名称
  session_type: 'File', //session存储类型, 空为内存，还可以为File
  session_path: '', //File类型下文件存储位置，默认为系统的tmp目录
  session_options: {}, //session对应的cookie选项
  session_sign: '', //session对应的cookie使用签名
  session_timeout: 24 * 3600, //session失效时间，单位：秒

  db_type: 'mysql', // 数据库类型
  db_host: 'localhost', // 服务器地址
  db_port: '', // 端口
  db_name: '', // 数据库名
  db_user: 'root', // 用户名
  db_pwd: '', // 密码
  db_prefix: 'think_', // 数据库表前缀
  db_fieldtype_check: false, // 是否进行字段类型检查
  db_fields_cache: true, // 启用字段缓存
  db_charset: 'utf8', // 数据库编码默认采用utf8
  db_nums_per_page: 20, //默认每页显示的条数
  db_like_fields: [], //自动进行模糊查询，如: ['title', 'content']
  db_cache_on: true, //是否启用查询缓存，如果关闭那么cache方法则无效
  db_cache_type: '', //缓存类型，默认为内存缓存
  db_cache_path: CACHE_PATH + '/db', //缓存路径，File类型下有效
  db_cache_timeout: 3600, //缓存时间，默认为1个小时

  tpl_content_type: 'text/html', //模版输出类型
  tpl_file_suffix: '.html', //模版文件名后缀
  tpl_file_depr: '_', //controller和action之间的分隔符
  tpl_engine_type: 'ejs', //模版引擎名称
  tpl_engine_config: {}, 

  cache_type: 'File', //数据缓存类型
  cache_timeout: 6 * 3600, //数据缓存有效期，单位: 秒
  cache_path: CACHE_PATH,  //缓存路径设置 (File缓存方式有效)
  cache_file_suffix: '.json', //File缓存方式下文件后缀名
  cache_gc_hour: [4], //缓存清除的时间点，数据为小时

  html_cache_on: false, //HTML静态缓存
  html_cache_timeout: 3600, //缓存时间，单位为秒
  html_cache_rules: {}, //缓存规则
  html_cache_path: CACHE_PATH + '/html',
  html_cache_file_callback: undefined, //生成缓存文件的回调函数
  html_cache_file_suffix: '.html', //缓存文件后缀名

  memcache_host: '127.0.0.1', //memcache host
  memcache_port: 11211, //memecache端口
};
```

这些配置的值都可以在App/Conf/config.js文件里重新设置。

### 系统常量

系统里定义很多系统常量，方便在项目中使用。

* `APP_DEBUG` 开启调试，开发中使用，上线后需要关闭
* `APP_MODE` 运行模式
* `THINK_PATH` thinkjs库的目录
* `THINK_VERSION` 当前thinkjs的版本
* `THINK_LIB_PATH` thinkjs的lib路径
* `THINK_EXTEND_PATH` thinkjs的扩展路径
* `APP_PATH` 项目App路径，如:`/home/welefen/www.test.com/App`
* `COMMON_PATH` Common路径，对应为`App/Common`
* `LIB_PATH` Lib路径，对应为`App/Lib`
* `CONF_PATH` 配置路径，对应为`App/Conf`
* `VIEW_PATH` 模版路径，对应为`App/View`
* `RUNTIME_PATH` runtime路径，对应为`App/Runtime`
* `DATA_PATH` 临时数据路径，对应为`App/Runtime/Data`
* `CACHE_PATH` 缓存路径，对应为`App/Runtime/Cache`