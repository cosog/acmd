# 第四章 电参诊断

- [第四章 电参诊断](Chapter4.md#第四章-电参诊断)
   - [4.1 输入文本](Chapter4.md#41-输入文本)
     - [4.1.1 输入参数说明](Chapter4.md#411-输入参数说明)
     - [4.1.2 输入实例](Chapter4.md#412-输入实例)
   - [4.2 输出文本](Chapter4.md#42-输出文本)
     - [4.2.1 输出参数说明](Chapter4.md#421-输出参数说明)
     - [4.2.2 输出实例](Chapter4.md#422-输出实例)
     - [4.2.3 工况类型代码](Chapter4.md#423-工况类型代码)

## 4.1 输入文本

### 4.1.1 输入参数说明

*表4-1 输入参数说明表*

| 代码                 | 名称             | 单位 | 类型     | 必填     | 备注     |
|----------------------|------------------|------|----------|----------|----------|
| AKString             | 应用密钥         |      | string   |          | 预留字段 |
| WellName             | 井名             |      | string   | *        |          |
| AcquisitionTime      | 采集时间         |      | string   | *        |          |
| CurrentA             | A相电流          | A    | float64  | *        |          |
| CurrentB             | B相电流          | A    | float64  | *        |          |
| CurrentC             | C相电流          | A    | float64  | *        |          |
| VoltageA             | A相电压          | V    | float64  | *        |          |
| VoltageB             | B相电压          | V    | float64  | *        |          |
| VoltageC             | C相电压          | V    | float64  | *        |          |
| ActivePowerSum       | 三相总有功功率   | kW   | float64  |          |          |
| ReactivePowerSum     | 三相总无功功率   | kVar | float64  |          |          |
| CompositePowerFactor | 三相综合功率因数 | cosΦ | float64  |          |          |

### 4.1.2 输入实例

```
{
    "AKString": "",
    "WellName": "J01-001",
    "AcquisitionTime": "2018-08-08 10:41:21",
    "CurrentA": 13.1,
    "CurrentB": 12.4,
    "CurrentC": 13.0,
    "VoltageA": 238.8,
    "VoltageB": 113.0,
    "VoltageC": 145.2,
    "ActivePowerSum": 45.9,
    "ReactivePowerSum": 45.9,
    "CompositePowerFactor": 0.7
}
```

## 4.2 输出文本

### 4.2.1 输出参数说明

*表4-2 输出参数说明表*

| 代码                          | 名称             | 单位 | 类型     | 备注            |
|-------------------------------|------------------|------|----------|-----------------|
| WellName                      | 井名             |      | string   |                 |
| ResultStatus                  | 计算结果状态     |      | int      | 详见表底注释[1] |
| AcquisitionTime               | 采集时间         |      | string   |                 |
| RunStatus                     | 运行状态         |      | int      | 0-停止 1-运行   |
| ResultCode                    | 结果代码         |      | int      | 代码详见表4-3   |
| Timer                         | 定时器           | 秒   | float64  |                 |
| **AlarmItems**                | **报警项**       |      |          |                 |
| **CurrentA**                  |   **A相电流**    |      |          |                 |
| MaxValueStatus                | 最大值报警状态   |      | int      | 1-报警 0-正常   |
| MinValueStatus                | 最小值报警状态   |      | int      | 1-报警 0-正常   |
| ZeroLevelStatus               | 零值报警状态     |      | int      | 1-报警 0-正常   |
| BalacneStatus                 | 数据均衡报警状态 |      | int      | 1-报警 0-正常   |
| **CurrentB**                  | **B相电流**      |      |          |                 |
| MaxValueStatus                | 最大值报警状态   |      | int      | 1-报警 0-正常   |
| MinValueStatus                | 最小值报警状态   |      | int      | 1-报警 0-正常   |
| ZeroLevelStatus               | 零值报警状态     |      | int      | 1-报警 0-正常   |
| BalacneStatus                 | 数据均衡报警状态 |      | int      | 1-报警 0-正常   |
| **CurrentC**                  | **C相电流**      |      |          |                 |
| MaxValueStatus                | 最大值报警状态   |      | int      | 1-报警 0-正常   |
| MinValueStatus                | 最小值报警状态   |      | int      | 1-报警 0-正常   |
| ZeroLevelStatus               | 零值报警状态     |      | int      | 1-报警 0-正常   |
| BalacneStatus                 | 数据均衡报警状态 |      | int      | 1-报警 0-正常   |
| **VoltageA**                  | **A相电压**      |      |          |                 |
| MaxValueStatus                | 最大值报警状态   |      | int      | 1-报警 0-正常   |
| MinValueStatus                | 最小值报警状态   |      | int      | 1-报警 0-正常   |
| ZeroLevelStatus               | 零值报警状态     |      | int      | 1-报警 0-正常   |
| BalacneStatus                 | 数据均衡报警状态 |      | int      | 1-报警 0-正常   |
| **VoltageB**                  | **B相电压**      |      |          |                 |
| MaxValueStatus                | 最大值报警状态   |      | int      | 1-报警 0-正常   |
| MinValueStatus                | 最小值报警状态   |      | int      | 1-报警 0-正常   |
| ZeroLevelStatus               | 零值报警状态     |      | int      | 1-报警 0-正常   |
| BalacneStatus                 | 数据均衡报警状态 |      | int      | 1-报警 0-正常   |
| **VoltageC**                  | **C相电压**      |      |          |                 |
| MaxValueStatus                | 最大值报警状态   |      | int      | 1-报警 0-正常   |
| MinValueStatus                | 最小值报警状态   |      | int      | 1-报警 0-正常   |
| ZeroLevelStatus               | 零值报警状态     |      | int      | 1-报警 0-正常   |
| BalacneStatus                 | 数据均衡报警状态 |      | int      | 1-报警 0-正常   |
| **ElectricLimit**             | **报警界限值**   |      |          |                 |
| **CurrentA**                  | **A相电流**      |      |          |                 |
| Max                           | 最大值界限       | A    | float64  |                 |
| Min                           | 最小值界限       | A    | float64  |                 |
| **CurrentB**                  | **B相电流**      |      |          |                 |
| Max                           | 最大值界限       | A    | float64  |                 |
| Min                           | 最小值界限       | A    | float64  |                 |
| **CurrentC**                  | **C相电流**      |      |          |                 |
| Max                           | 最大值界限       | A    | float64  |                 |
| Min                           | 最小值界限       | A    | float64  |                 |
| **VoltageA**                  | **A相电压**      |      |          |                 |
| Max                           | 最大值界限       | V    | float64  |                 |
| Min                           | 最小值界限       | V    | float64  |                 |
| **VoltageB**                  | **B相电压**      |      |          |                 |
| Max                           | 最大值界限       | V    | float64  |                 |
| Min                           | 最小值界限       | V    | float64  |                 |
| **VoltageC**                  | **C相电压**      |      |          |                 |
| Max                           | 最大值界限       | V    | float64  |                 |
| Min                           | 最小值界限       | V    | float64  |                 |
| ETResultString                | 电参工况综合     |      | string   |                 |
| CurrentString                 | 电流综合         | A    | string   |                 |
| VoltageString                 | 电压综合         | V    | string   |                 |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*

### 4.2.2 输出实例

```
{
    "WellName": "J01-001",
    "ResultStatus": 1,
    "AcquisitionTime": "2018-08-08 10:41:21",
    "RunStatus": 1,
    "ResultCode": 1323,
    "AlarmItems": {                          //（1）报警项
        "CurrentA": {
        },
        "CurrentB": {
        },
        "CurrentC": {
        },
        "VoltageA": {
            "BalacneStatus": 1
        },
        "VoltageB": {
            "BalacneStatus": 1
        },
        "VoltageC": {
            "BalacneStatus": 1
        }
    },
    "ElectricLimit": {                       //（2）报警界限值
        "CurrentA": {
            "Max": 15.72,
            "Min": 10.48
        },
        "CurrentB": {
            "Max": 14.88,
            "Min": 9.92
        },
        "CurrentC": {
            "Max": 15.6,
            "Min": 10.4
        },
        "VoltageA": {
            "Max": 262.68,
            "Min": 214.92
        },
        "VoltageB": {
            "Max": 124.3,
            "Min": 101.7
        },
        "VoltageC": {
            "Max": 159.72,
            "Min": 130.68
        }
    },
    "ETResultString":"",
    "CurrentString": "13.10/12.40/13.00",
    "VoltageString": "238.80/113.00/145.20"
}
```
### 4.2.3 工况类型代码

*表4-3 代码表*

| 序号 | 代码     | 名称                                                         | 
|------|----------|--------------------------------------------------------------|
| 1    | 1202     | 正常                                                         | 
| 2    | 1311     | 缺相                                                         | 
| 3    | 1313     | 过载（螺杆泵：井卡，抽油机：井卡、杆断脱）                   | 
| 4    | 1314     | 欠载（螺杆泵：杆断脱、皮带断，抽油机：井卡、杆断脱、皮带断） | 
| 5    | 1321     | 过电压                                                       | 
| 6    | 1322     | 欠电压                                                       |
| 7    | 1323     | 三相电压不均衡                                               |
| 8    | 1324     | 三相电流不均衡（防盗电）                                     |
| 9    | 0        | 空（停止时对应的响应工况）                                   |

----[第三章 功图平衡](.././Chapter3/Chapter3.md)----[返回章节目录](.././README.md)----[第五章 电参平衡](.././Chapter5/Chapter5.md)----
