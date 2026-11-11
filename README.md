# 非均匀客流样本的校准估计与不确定性

本项目保存百货多业态经营研究的合成资料及输入读取工具。当前程序只解析文件并显示输入类型与记录数量，不进行统计分析、模型训练、优化求解或业务推荐。所有记录均为虚构，不能用于陈述真实商场经营结果。

## 输入约定

probability 是基础纳入概率，空 duration/intent 为结果变量缺失。cluster_id 为重采样单位，floor/time_band 为校准维度。controls 中边际为固定目标量。

fixtures 为资料目录，src/sample_reader.py 为读取器，tests 为格式读取测试。输入在运行中保持不变；研究计算结果可写入独立的 .workspace-output 目录。

## 本地操作

Python 3.11 及以上版本，现有读取工具只依赖标准库，不需要下载第三方包。进入项目根目录：

    python -m src.sample_reader fixtures/sample.csv

编译检查：

    python -m compileall -q src tests

格式读取测试：

    python -m unittest discover -s tests -v

## 固定运行环境

    docker build -t footfall-calibration:local .
    docker run --rm footfall-calibration:local

容器默认运行输入测试。镜像使用完整内容摘要固定，研究输入随项目一起复制。
