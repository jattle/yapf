## 简介

yapf是一种程序逻辑流程控制框架，其思路是使用DAG描述程序业务逻辑中的本来关系，
通过拓扑排序调度业务逻辑的并发执行，解决promise/future、协程等流程控制原语
在实现逻辑的串行并行组合上实现比较繁琐或可读性差的问题。
    
使用者通过配置文件声明各流程定义以及流程间关系，编写各独立流程实现代码，
不需要关心流程的执行顺序，由框架统一调度。
    
框架支持多种流程调度线程，默认使用std::thread，使用者可以提供自己的调度线程，
比如将RPC框架的协程能力封装为一种调度线程，目前提供了taf_co_thread调度线程，
其底层使用了TAF/TARS协程来执行流程，必须运行在TAF/TARS框架上。

本流程框架是RPC框架无关的，其基础能力不依赖任何框架实现，适用于任何程序的内部流程组织。

注意：框架依赖C++17以上语言标准。

## 目录说明

- yapf/base 
  
源码实现。包括DAG表示、流程调度器、流控等。

- yapf/flow_control
框架用到的流控实现以及一些工具类。

- TODO
提供一些常规的例子。
