# 1 Windows设置定时任务
## 1.1 目标：每隔两小时重启python程序
## 1.2 bat文件
目的：关闭所有夜神模拟器进程和python进程，重新启动python程序
```
@echo off  
taskkill /f /im "nox*" /t  
taskkill /f /im "python*" /t  
  
cd /d D:\sandalwood\projects\Emulator    
D:\sandalwood\virtualenv\common\Scripts\python.exe D:\sandalwood\projects\Emulator\jd\eid.py
```
## 1.3 创建定时任务
1. 鼠标右击我的电脑》管理》任务计划程序》任务计划程序库》，随便选一个定时任务，如果红框框出的地方显示历史记录（已禁用）则点击步骤三箭头指出的启动所有任务历史记录，点击创建任务
![[Pasted image 20230925173657.png]]
2. 任务计划程序》创建任务
![[Pasted image 20230925170351.png]]
3. 默认进入常规界面，填写任务名称，选择电脑Windows版本 
![[Pasted image 20230925170625.png]]
4. 点击触发器》新建，进入新建触发器窗口，选择“每天”》选择任务开始时间》选择重复任务间隔》选择两小时（如果没有两小时的选项可以手动输入）》持续时间改为无限期》点击确认
![[Pasted image 20230925171014.png]]
5. 点击操作》新建，进入新建操作窗口，点击浏览》选择执行文件位置，点击确认
![[Pasted image 20230925172154.png]]
6. 点击设置，其他设置按照需求勾选，注意步骤2中默认是请勿启动新实例，我的bat文件执行的python程序在下一次触发器触发时并不会停止，所以会报“实例已创建”之类的警告然后定时任务不执行，所以选择并发执行，然后点击确认
![[Pasted image 20230925172812.png]]
## 1.4 报错
### 1.4.1 注意：
如果未打开历史任务记录则看不到报错返回信息，详见1.3步骤一
![[Pasted image 20230925175135.png]]
### 1.4.2  win10定时任务报错：操作员或系统管理员拒绝了请求
- 在企业版Windows发现这个报错
- [win10定时任务报错：操作员或系统管理员拒绝了请求_会spark的篮球少年的博客-CSDN博客](https://blog.csdn.net/qq_15230053/article/details/88817019?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522169563524416800185861994%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=169563524416800185861994&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~first_rank_ecpm_v1~rank_v31_ecpm-1-88817019-null-null.nonecase&utm_term=%E5%AE%9A%E6%97%B6%E4%BB%BB%E5%8A%A1&spm=1018.2226.3001.4450)
1.4.2 已存在任务实例
- 详见1.3最后一个步骤