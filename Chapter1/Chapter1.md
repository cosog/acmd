# Chapter1 采集处理

- [Chapter1 采集处理](Chapter1.md#Chapter1-采集处理)
    - [1.1 输入文本](Chapter1.md##1.1-输入文本)
      - [1.1.1 输入参数说明](Chapter1.md###1.1.1-输入参数说明)
      - [1.1.2 输入实例](Chapter1.md###1.1.2-输入实例)
    - [1.2 输出文本](Chapter1.md##1.2-输出文本)
      - [1.2.1 输出参数说明](Chapter1.md###1.2.1-输出参数说明)
      - [1.2.2 输出实例](Chapter1.md###1.2.2-输出实例)

## 1.1 输入文本

### 1.1.1 输入参数说明

*表1 采集处理输入参数说明表*

| 字段代码                 | 字段名        | 单位 | 字段类型 | 是否必填 | 备注                 |
|-------------------------|--------------|------|----------|----------|----------------------|
| WellName                | 井名          |      | string   | 是       |                      |
| NameplateStroke         | 铭牌冲程       | m    | float64  | 是       | 与前臂长二选一填写      |
| ForearmLength           | 前臂长        | m    | float64  | 否       | 与铭牌冲程二选一填写     |
| Interval                | 采样间隔       | ms   | float64  | 否       |                      |
| **FADiagram**           | 载荷-角度数据   |      |          |          |                      |
| AcquisitionTime         | 采集时间       |      | string   | 是       |                      |
| F                       | 载荷           | kN   | float64  | 是       |                      |
| A                       | 角度           | °    | float64  | 是       |                      |

### 1.1.2 输入实例

```
{
"WellName": "01-020",       //（1）井名
"NameplateStroke": 4.35,    //（2）铭牌冲程
"ForearmLength": 4.2,       //（3）前臂长
"Interval": 66,             //（4）采集间隔
"FADiagram": {              //（5）载荷-角度参数
"AcquisitionTime": "2018-03-07 16:38:24", //（5-1）采集时间
"F": [    //（5-2）载荷
        62.14,
        61.93,
        61.71,
        61.71,
        61.32,
        ...
        62.63,
        62.68,
        62.68,
        62.79,
        62.79
    ],
"A": [    //（5-3）角度
        17.81,
        18.76,
        19.72,
        19.72,
        20.67,
        ...
        8.53,
        9.75,
        11.12,
        11.12,
        12.21,
        13.44
        ]
    }
}
```
## 1.2 输出文本

### 1.2.1 输出参数说明

*表2 采集处理输出参数说明表*
| 字段代码           | 字段名           | 单位  | 字段类型 | 备注                              |
|-------------------|-----------------|-------|----------|----------------------------------|
| WellName          | 井名             |       | string   |                                  |
| **CalculationStatus** | 计算状态         |       |          |                                   |
| ResultStatus      | 计算结果状态      |       | int      | 不同值代表不同状态，详见表底注释[1]     |
| ResultCode        | 诊断结果         |       | int      |                                   |
| **Verification**      | 数据校验         |       |          |                                   |
| ErrorCounter      | 错误参数计数器    |       | int      | 错误参数个数                        |
| ErrorString       | 错误参数字符串    |       | string   | 数据错误，计算不成功                 |
| WarningCounter    | 报警计数器       |       | int      | 报警参数个数                        |
| WarningString     | 报警字符串       |       | string   | 报警参数（取默认值，计算正常进行）      |
| SDKPlusCounter    | Plus版报警计数器 |       | int      | 预留                               |
| SDKPlusString     | Plus版报警字符串 |       | string   | 预留                               |
|                   |                |       |          |                                   |
| NameplateStroke   | 铭牌冲程        | m     | float64  |                                   |
| ForearmLength     | 前臂长          | m     | float64  |                                   |
| OptimizedInterval | 优化采集间隔     | ms    | float64  |                                   |
| OptimizedCount    | 优化采集点数     |       | int      |                                   |
| **FSDiagram**     |  功图数据       |       |          |                                   |
| AcquisitionTime   | 采集时间        |       | string   |                                   |
| Stroke            | 功图冲程        | m     | float64  |                                   |
| SPM               | 功图冲次        | 1/min | float64  |                                   |
| CNT               | 点数           |       | int      |                                    |
| F                 | 载荷           | kN    | float64  |                                    |
| S                 | 位移           | m     | float64  |                                    |

[1]***1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*** 

*表3 诊断结果代码说明表*
| 序号  | 诊断结果代码   | 诊断结果说明                            |
|------|--------------|---------------------------------------|
| 1    | 1102         | 正常                                   |
| 2    | 1104         | 检查仪表                               |
| 3    | 1106         | 少于半个周期，优化重新采集                |
| 4    | 1107         | 少于1个周期，大于半个周期，优化重新采集     |
| 5    | 1108         | 功图点数少于目标点数下限，优化重新采集      |
| 6    | 1109         | 功图点数多于目标上限，优化重新采集         |
| 7    | 1362         | 停抽                                  |

### 1.2.2 输出实例

```
{
    "WellName": "01-020",       //（1）井名
    "CalculationStatus": {      //（2）计算状态
        "ResultStatus": 1,
        "ResultCode": 1102
    },
    "Verification": {           //（3）数据校验
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": "",
        "SDKPlusCounter": 0,
        "SDKPlusString": ""
    },
    "NameplateStroke": 4.35,    //（4）铭牌冲程
    "ForearmLength": 4.2,       //（5）前臂长
    "OptimizedInterval": 66,    //（6）优化采集间隔
    "OptimizedCount": 1200,     //（7）优化采集点数
    "FSDiagram": {              //（8）功图数据
        "AcquisitionTime": "2016-02-01 16:38:24", //（8-1）采集时间
        "Stroke": 4.35,             //（8-2）冲程
        "SPM": 4.5,                 //（8-3）冲次
        "CNT": 202,                 //（8-4）点数
        "F": [                      //（8-5）载荷
            37.5,
            37.5,
            37.5,
            38.27,
            38.27,
            38.86,
            39.07,
            ...
            37.48,
            37.48,
            37.17,
            37.43,
            37.43,
            37.82,
            38.09
        ],
        "S": [                       //（8-6）位移
            0,
            0,
            0,
            0,
            0,
            0,
            0.0103,
            ...
            0.13,
            0.13,
            0.0902,
            0.0601,
            0.0601,
            0.0301,
            0.0103
        ]
    }
}
```
----[返回章节目录](https://github.com/cosog-chentr/acmd/blob/master/README.md)----[Chapter2 功图诊断&计产](https://github.com/cosog-chentr/acmd/blob/master/Chapter2/Chapter2.md)----