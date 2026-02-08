<!--
 * @Author: lucky zhou_20006ee@163.com
 * @Date: 2026-02-07 22:36:52
 * @LastEditors: lucky zhou_20006ee@163.com
 * @LastEditTime: 2026-02-08 13:40:34
 * @FilePath: \Lucky.github.io\Core\Config\README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# 综述：

互斥锁（mutex，mutual exclusion 的缩写）是一种 **“谁抢到谁独占”** 的同步原语：

- 任意时刻最多 1 个线程持有锁；
    
- 其余线程再抢锁时只能阻塞（或超时返回）；
    
- 持有者用完必须解锁，否则别人永远进不来。
    

# mutex_t

除了构造函数你一无所有

用于创建一个互斥锁

# scoped_mutex_t

除了构造函数你一无所有

scoped_mutex_t _lock(get_lock());

scoped_mutex_t _lock(get_lock(),time_out);

用于获取锁，资源脱离生存周期（析构）时自动释放锁

# Warning:

1. 不要尝试将scope声明为static或全局变量，否则将会受到无法解锁的诅咒
    
2. 拷贝已被删除，请用引用或指针传递
    
3. 拿到锁后尽早离开作用域；长时间持有会阻塞高优先级任务