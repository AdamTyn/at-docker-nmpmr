### AT-Docker/nmpmr

1. *master* 分支为 `php7.2` 版本
2. [2020-4-24] 所有分支均添加了 `xdebug` 扩展（如果使用 `swoole` 出现冲突，可以在 */usr/etc/php/conf.d* 目录下 **重命名 *docker-ext-xdebug.ini* 文件** 即可禁用此扩展）
3. [2020-4-25] 新增 `php7.4` 版本，切换分支到 *php74* ，重新编译容器即可
4. [2020-6-17] 更新 `php扩展`，升级 `composer` 和 `phpunit` 到最新版本

|         Upgrade List          |
| :---------------------------: |
|        composer-1.10.7        |
| phpunit-8.5.6 & phpunit-9.2.3 |
|         swoole-4.5.2          |
|         xdebug-2.9.6          |
|          redis-5.2.2          |
|         rdkafka-4.0.3         |
|           nsq-3.5.0           |
|         mongodb-1.7.4         |
|          event-2.5.6          |
|          zip-1.19.0           |

5. [2020-6-22] 新增 `xlswriter` 扩展