# sensitivity-analysis-model
分布式综合智慧能源系统模型——能源负荷敏感度分析模型


===========================<br>
### 项目简述
准确评估电压变化对敏感负荷的影响,有利于供电部门采取合理的供电方案,还有助于人们研究出提高敏感负荷电压耐受能力及降低电压暂降对其影响的可行性方案,制定出相应的电压补偿策略与方案,使负荷电压暂降经济损失降至最低。
### 环境依赖
Python 环境搭建<br>

### python第三方库
numpy>=1.9.0<br>
scipy<br>
matplotlib>=1.4.3<br>
pandas<br>
pre-commit<br>
pytest<br>
pytest-cov<br>
recommonmark<br>



### 输入参数要求
在参数文件中，以开头的#行将被视为注释并被忽略。<br>
P1 0.0 1.0<br>
P2 0.0 5.0<br>
P3 0.0 5.0<br>
...etc.<br>
如果参数名称或组名称包含空格，则参数文件也可以用逗号分隔。
### 命令行说明

生成样本（-p标志是参数文件）
```
salib sample saltelli \
     -n 1000 \
     -p ./src/SALib/test_functions/params/Ishigami.txt \
     -o model_input.txt
```

运行模型，默认为是用户定义的模型（可能为另一种语言）。只需保存输出即可。

运行分析
```
salib analyze sobol \
     -p ./src/SALib/test_functions/params/Ishigami.txt \
     -Y model_output.txt \
     -c 0
```

这会将索引和置信区间打印到命令行。您可以使用>运算符重定向到文件。

###并行索引计算（仅Sobol方法）
```python
Si = sobol.analyze(problem, Y, calc_second_order=True, conf_level=0.95,
                   print_to_console=False, parallel=True, n_processors=4)
```
其他方法包括Morris，FAST，Delta-MIM和DGSM。有关每种方法的所有命令行选项的说明，[请参见此处的示例](https://github.com/SALib/SALib/tree/master/examples).。

<br><br>





王波波，宋伟，李天昊，汤俊萱，孙奕程 <br>

东华大学，上海视易信息技术有限公司，2020


