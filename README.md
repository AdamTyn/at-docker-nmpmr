### AT-Docker/nmpmr

1. [2020-12-05] 更新 *master* 分支为 `php7.4.13` 版本，合并 *php74-mac* 分支到 *master*

2. [2020-12-04] 更新 `php扩展`，升级 `composer` 到最新版本

   |  Upgrade List  |
   | :------------: |
   | composer-2.0.8 |
   |   zip-1.19.2   |
   |  xdebug-3.0.0  |
   |  swoole-4.5.9  |
   |  redis-5.3.2   |
   | mongodb-1.9.0  |
   |  mcrypt-1.0.4  |

3. [2020-12-03] 移除部分 `php扩展`

   | Deprecated List |
   | :-------------: |
   |   php-rdkafka   |
   |    php-event    |
   |     php-nsq     |

4. [2020-09-14] 更新 `php扩展`，升级 `composer` 和 `phpunit` 到最新版本

   |   Upgrade List   |
   | :--------------: |
   | composer-1.10.13 |
   |  phpunit-9.3.9   |
   |   swoole-4.5.3   |
   |   event-2.5.7    |
   |   redis-5.3.1    |
   |  mongodb-1.8.0   |

5. [2020-06-22] 新增 `php-xlswriter` 扩展

6. [2020-06-17] 更新 `php扩展`，升级 `composer` 和 `phpunit` 到最新版本

   |  Upgrade List   |
   | :-------------: |
   | composer-1.10.7 |
   |  phpunit-9.2.3  |
   |  swoole-4.5.2   |
   |  xdebug-2.9.6   |
   |   redis-5.2.2   |
   |  rdkafka-4.0.3  |
   |    nsq-3.5.0    |
   |  mongodb-1.7.4  |
   |   event-2.5.6   |
   |   zip-1.19.0    |

7. [2020-04-25] 新增 `php7.4` 版本，切换分支到 *php74* ，重新编译容器即可

8. [2020-04-24] 所有分支均添加了 `xdebug` 扩展（如果使用 `swoole` 出现冲突，可以在 */usr/etc/php/conf.d* 目录下 **重命名 *docker-ext-xdebug.ini* 文件** 即可禁用此扩展）