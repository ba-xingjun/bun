# forkjointask 任务状态

NORMAL：表示任务“正常”完成的状态。

CANCELLED：表示任务“取消”完成的状态。

EXCEPTIONAL：表示任务“异常”完成的状态。注意，以上这三个状态都是“完成”的状态，只是完成的途径不一样。

SIGNAL：有其他任务依赖当前任务，任务结束前，通知其他任务join当前任务的结果。

0：任务初始状态（正在执行状态），不需要等待子任务完成。

# 子类
RecursiveAction：无返回值的任务。

RecursiveTask：有返回值的任务。

CountedCompleter：完成任务后将触发其他任务。
