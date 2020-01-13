其实这个案例创建一个maven工程就可以了，一个发送消息的类，一个接受消息的类
使用的是默认账号，如果你需要自己创建账号也可以，只需要把代码中的账号换成你的就可以了
下面是创建新的用户的过程：

rabbitmqctl add_user username password

删除用户

rabbitmqctl delete_user guest

服务器该用户没有分配权限

rabbitmqctl set_permissions -p "/" username ".*" ".*" ".*"

 

创建用户并设置角色：
可以创建管理员用户，负责整个MQ的运维，例如：

$sudo rabbitmqctl add_user  user_admin  passwd_admin
赋予其administrator角色：

$sudo rabbitmqctl set_user_tags user_admin administrator

可以创建RabbitMQ监控用户，负责整个MQ的监控，例如：

$sudo rabbitmqctl add_user  user_monitoring  passwd_monitor
赋予其monitoring角色：

$sudo rabbitmqctl set_user_tags user_monitoring monitoring

可以创建某个项目的专用用户，只能访问项目自己的virtual hosts

$sudo rabbitmqctl  add_user  user_proj  passwd_proj
赋予其monitoring角色：

$sudo rabbitmqctl set_user_tags user_proj management
