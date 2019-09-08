# Bean的作用域（scope）

- singleton

> 默认scope，容器创建时就初始化了，并且在容器中只存在这一个实例。

- prototype

> 原型，每次都重新生成一个新的对象，对象的生命周期也交给请求方管理。

- request

> 用于web程序，每个request都对应一个实例。可以看做prototype的特例

- session

> 类似request

- global session

> session只有应用在基于porlet的web应用程序中才有意义

# Bean的加载过程