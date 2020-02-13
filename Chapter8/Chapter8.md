# 第八章 电参反演

- [第八章 电参反演](Chapter8.md#第八章-电参反演)
   - [8.1 输入文本](Chapter8.md#81-输入文本)
     - [8.1.1 输入参数说明](Chapter8.md#811-输入参数说明)
     - [8.1.2 输入实例](Chapter8.md#812-输入实例)
   - [8.2 输出文本](Chapter8.md#82-输出文本)
     - [8.2.1 输出参数说明](Chapter8.md#821-输出参数说明)
     - [8.2.2 输出实例](Chapter8.md#822-输出实例)
     - [8.2.3 数据收集表](Chapter8.md#823-数据收集表) 

## 8.1 输入文本

### 8.1.1 输入参数说明

*表8-1 输入参数说明表*

| 代码                          | 名称               | 单位  | 类型     | 必填     | 备注                                                           |
|-------------------------------|--------------------|-------|----------|----------|----------------------------------------------------------------|
| AKString                      | 应用密钥           |       | string   |          |                                                                |
| WellName                      | 井名               |       | string   | *&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|                                   |
| AcquisitionTime               | 采集时间           |       | string   | *        |                                                                |
| SPM                           | 冲次               | 1/min | float64  | *        |                                                                |
| Watt                          | 有功功率           | kW    | float64  | *        |                                                                |
| I                             | 电流               | A     | float64  | *        |                                                                |
| RPM                           | 转速               | r/min | float64  | *        |                                                                |
| **PumpingUnit**               | **抽油机数据**     |       |          |          |                                                                |
| Manufacturer                  | 厂商               |       | string   | *        |                                                                |
| Model                         | 型号               |       | string   | *        |                                                                |
| Stroke                        | 冲程               | m     | float64  | *        |                                                                |
| CrankRotationDirection        | 曲柄旋转方向       |       | string   | *        | Clockwise－顺时针 Anticlockwise－逆时针 立式抽油机无           |
| OffsetAngleOfCrank            | 曲柄偏置角         | °     | float64  | *        | 非异相型抽油机填0                                              |
| OffsetAngleOfCrankPS          | 曲柄位置开关偏置角 | °     | float64  |          |                                                                |
| CrankGravityRadius            | 曲柄重心半径       | m     | float64  | *        |                                                                |
| SingleCrankWeight             | 单块曲柄重量       | kN    | float64  | *        |                                                                |
| StructuralUnbalance           | 结构不平衡重       | kN    | float64  | *        | 复合平衡尾平衡按角度档位可调的                                 |
| **Balance**                   | **平衡块**         |       |          |          |                                                                |
| **EveryBalance**              | **平衡块参数**     |       |          |          |                                                                |
| Position                      | 位置               | m     | float64  | *        |                                                                |
| Weight                        | 重量               | kN    | float64  | *        |                                                                |
| **PRTF**                      | **光杆位置因数**   |       |          |          |                                                                |
| CrankAngle                    | 曲柄转角           | °     | float64  | *        |                                                                |
| PR                            | 光杆位置因数       | %     | float64  | *        |                                                                |
| TF                            | 扭矩因数           | m     | float64  | *        |                                                                |
| SurfaceSystemEfficiency       | 地面效率           | 小数  | float64  | *        |                                                                |
| WattAngle                     | 功率滤波角度       | °     | float64  | *        |                                                                |
| WattTimes                     | 功率滤波次数       |       | int      | *        |                                                                |
| ITimes                        | 电流滤波次数       |       | int      | *        |                                                                |
| RPMTimes                      | 转速滤波次数       |       | int      | *        |                                                                |
| FSDiagramTimes                | 功图滤波次数       |       | int      | *        |                                                                |
| FSDiagramLeftTimes            | 功图左侧滤波次数   |       | int      | *        |                                                                |
| FSDiagramRightTimes           | 功图右侧滤波次数   |       | int      | *        |                                                                |
| LeftPercent                   | 左侧截取百分比     | %     | float64  | *        |                                                                |
| RightPercent                  | 右侧截取百分比     | %     | float64  | *        |                                                                |

### 8.1.2 输入实例

```
{
    "AKString": "",
    "WellName": "Z363-X18",
    "AcquisitionTime": "2019-09-17 18:32:53",
    "SPM": 6.33,
    "Watt": [
        8.59,
        8.52,
        8.15,
        8.01,
        ...
        8.11,
        8.42,
        8.92,
        8.51
    ],
    "I": [
        13.11,
        13.09,
        12.99,
        12.89,
        ...
        12.89,
        12.93,
        13.08,
        13.1
    ],
    "RPM": [
        964.67,
        962.66,
        961.89,
        973.03,
        ...
        962.49,
        966.34,
        965.42,
        960.99
    ],
    "PumpingUnit": {
        "Manufacturer": "大庆",
        "Model": "CYJY8-3-37HB",
        "Stroke": 3,
        "CrankRotationDirection": "Clockwise",
        "OffsetAngleOfCrank": -8,
        "OffsetAngleOfCrankPS": -4,
        "CrankGravityRadius": 0.77,
        "SingleCrankWeight": 12.706,
        "StructuralUnbalance": -0.5,
        "Balance": {
            "EveryBalance": [
                {
                    "Position": 0.62,
                    "Weight": 12.6
                },
                {
                    "Position": 0.6,
                    "Weight": 11.25
                }
            ]
        },
        "PRTF": {
            "CrankAngle": [
                0,
                15,
                30,
                45,
                60,
                75,
                90,
                105,
                120,
                135,
                150,
                165,
                180,
                195,
                210,
                225,
                240,
                255,
                270,
                285,
                300,
                315,
                330,
                345,
                360
            ],
            "PR": [
                1.01,
                0.18,
                3.46,
                10.56,
                20.57,
                32.21,
                44.3,
                56,
                66.8,
                76.48,
                84.88,
                91.84,
                97.02,
                99.78,
                99.18,
                94.49,
                85.9,
                74.55,
                61.72,
                48.45,
                35.52,
                23.62,
                13.42,
                5.63,
                1.01
            ],
            "TF": [
                -0.3231,
                0.1397,
                0.6076,
                1.0041,
                1.2671,
                1.3817,
                1.3768,
                1.297,
                1.1781,
                1.0399,
                0.8859,
                0.7051,
                0.4706,
                0.1434,
                -0.2953,
                -0.7773,
                -1.1702,
                -1.4098,
                -1.5142,
                -1.5166,
                -1.4371,
                -1.2812,
                -1.046,
                -0.726,
                -0.3231
            ]
        }
    },
    "SurfaceSystemEfficiency": 0.9,
    "WattAngle": 89,
    "WattTimes": 3,
    "ITimes": 3,
    "RPMTimes": 0,
    "FSDiagramTimes": 3,
    "FSDiagramLeftTimes": 100,
    "FSDiagramRightTimes": 0,
    "LeftPercent": 1,
    "RightPercent": 4.5
}
```

## 8.2 输出文本

### 8.2.1 输出参数说明

*表8-2 输出参数说明表*

| 代码                       | 名称               | 单位  | 类型     | 备注                                         |
|----------------------------|--------------------|-------|----------|----------------------------------------------|
| WellName                   | 井名               |       | string   |                                              |
| ResultStatus               | 计算结果状态       |       | int      | 详见表底注释[1]                              |
| **Verification**           | **数据校验**       |       |          |                                              |
| ErrorCounter               | Error计数器        |       | int      | 错误参数个数                                 |
| ErrorString                | Error字符串        |       | string   | 数据错误，计算不成功                         |
| WarningCounter             | Warning计数器      |       | int      | 报警参数个数                                 |
| WarningString              | Warning字符串      |       | string   | 报警参数（取默认值，计算正常进行）           |
| SDKPlusCounter             | Plus版报警计数器   |       | int      | 预留                                         |
| SDKPlusString              | Plus版报警字符串   |       | string   | 预留                                         |
| AcquisitionTime            | 采集时间           |       | string   |                                              |
| Stroke                     | 冲程               | m     | float64  |                                              |
| SPM                        | 冲次               | 1/min | float64  |                                              |
| CNT                        | 点数               |       | int      |                                              |
| F                          | 载荷               | kN    | float64  |                                              |
| S                          | 位移               | m     | float64  |                                              |
| Watt                       | 有功功率           | kW    | float64  |                                              |
| I                          | 电流               | A     | float64  |                                              |
| RPM                        | 转速               | r/min | float64  |                                              |
| UpstrokeIMax               | 上冲程最大电流     | A     | float64  |                                              |
| DownstrokeIMax             | 下冲程最大电流     | A     | float64  |                                              |
| UpstrokeWattMax            | 上冲程最大有功功率 | kW    | float64  |                                              |
| DownstrokeWattMax          | 下冲程最大有功功率 | kW    | float64  |                                              |
| IDegreeBalance             | 电流平衡度         | %     | float64  |                                              |
| WattDegreeBalance          | 功率平衡度         | %     | float64  |                                              |
| MotorInputAvgWatt          | 电机输入有功功率   | kW    | float64  |                                              |
| MaxF                       | 最大载荷           | kN    | float64  |                                              |
| MinF                       | 最小载荷           | kN    | float64  |                                              |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*

### 8.2.2 输出实例

```
{
    "WellName": "J01-001",
    "ResultStatus": 1,
    "Verification": {
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": "",
        "SDKPlusCounter": 0,
        "SDKPlusString": ""
    },
    "AcquisitionTime": "2019-09-17 18:32:53",
    "Stroke": 3,
    "SPM": 6.33,
    "CNT": 156,
    "F": [
        31.62,
        31.58,
        31.55,
        31.54,
		...
        32.36,
        32.08,
        31.88,
        31.75
    ],
    "S": [
        3,
        3,
        3,
        3,
		...
        3,
        3,
        3,
        3
    ],
    "F360": [
        23.79,
        24.07,
        24.35,
        24.65,
        ...
        22.82,
        23.03,
        23.28,
        23.52
    ],
    "S360": [
        0,
        0,
        0,
        0,
        ...
        0.0333,
        0.0234,
        0.0136,
        0.00378
    ],
    "A360": [
        0,
        1,
        2,
        3,
        ...
        356,
        357,
        358,
        359
    ],
    "Watt": [
        8.39,
        8.26,
        8.08,
        7.87,
        ...
        8.36,
        8.43,
        8.45,
        8.42
    ],
    "I": [
        13.02,
        12.98,
        12.92,
        12.82,
        ...
        12.9,
        12.96,
        13,
        13.01
    ],
    "RPM": [
        964.67,
        962.66,
        961.89,
        973.03,
        ...
        962.49,
        966.34,
        965.42,
        960.99
    ],
    "UpstrokeIMax": 15.21,
    "DownstrokeIMax": 13.02,
    "UpstrokeWattMax": 12.02,
    "DownstrokeWattMax": 8.39,
    "IDegreeBalance": 85.62,
    "WattDegreeBalance": 69.77,
    "MotorInputAvgWatt": 4.74,
    "MaxF": 33.53,
    "MinF": 16.51,
    "MaxF360": 36.13,
    "MinF360": 16.52
}
```

### 8.2.3 数据收集表

*表8-3 数据收集表*

| 数据                 | 备注                     |                                                                                                          |
|----------------------|--------------------------|----------------------------------------------------------------------------------------------------------|
| 井名                 |                          |                                                                                                          |
| 冲程（m）            | 可以通过曲柄孔销位置确定 |                                                                                                          |
| 抽油机基础数据       | 厂家                     | 该项数据可在抽油机说明书中寻找。对于大庆油田装备制造集团生产的抽油机，注明厂家型号，大部分型号已有说明书 |
|                      | 型号                     |                                                                                                          |
|                      | 旋转方向                 |                                                                                                          |
|                      | 曲柄偏置角(°)            |                                                                                                          |
|                      | 曲柄重心半径(m)          |                                                                                                          |
|                      | 单块曲柄重量(kN)         |                                                                                                          |
|                      | 结构不平衡重(kN)         |                                                                                                          |
|                      | 平衡块重量(kN)           |                                                                                                          |
| 抽油机位置扭矩因数表 | 曲柄转角(°)              |                                                                                                          |
|                      | 光杆位置因数PR(%)        |                                                                                                          |
|                      | 扭矩因数TF(m)            |                                                                                                          |
| 平衡块位置           | 平衡块1位置(m)           | 平衡块数以实际为准，当平衡块大小不一致时，需注明大小                                                     |
|                      | 平衡块2位置(m)           |                                                                                                          |
|                      | 平衡块3位置(m)           |                                                                                                          |
|                      | 平衡块4位置(m)           |                                                                                                          |

----[第七章 电参能耗](https://github.com/cosog/acmd/blob/master/Chapter7/Chapter7.md)----[返回章节目录](https://github.com/cosog/acmd/blob/master/README.md)----[第九章 转速计产](https://github.com/cosog/acmd/blob/master/Chapter9/Chapter9.md)----