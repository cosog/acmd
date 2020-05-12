# 第三章 能耗计算

- [第三章 能耗计算](Chapter3.md#第三章-能耗计算)
   - [3.1 输入文本](Chapter3.md#31-输入文本)
     - [3.1.1 输入参数说明](Chapter3.md#311-输入参数说明)
     - [3.1.2 输入实例](Chapter3.md#312-输入实例)
   - [3.2 输出文本](Chapter3.md#32-输出文本)
     - [3.2.1 输出参数说明](Chapter3.md#321-输出参数说明)
     - [3.2.2 输出实例](Chapter3.md#322-输出实例)


## 3.1 输入文本

### 3.1.1 输入参数说明

*表3-1 输入参数说明表*

| 代码             | 名称         | 单位   | 类型     | 必填     | 备注                       |
|------------------|--------------|--------|----------|----------|----------------------------|
| AKString         | 应用密钥     |        | string   |          |                            |
| WellName         | 井名         |        | string   | *        |                            |
| **Last**         | **上次电能** |        |          |          |                            |
| AcquisitionTime  | 采集时间     |        | string   | *        | 格式 "2020-01-18 15:00:00" |
| **Total**        | **累计电能** |        |          |          |                            |
| Watt             | 有功电能     | kW·h   | float64  | *        |                            |
| PWatt            | 正向有功电能 | kW·h   | float64  |          |                            |
| NWatt            | 反向有功电能 | kW·h   | float64  |          |                            |
| Var              | 无功电能     | kVar·h | float64  |          |                            |
| PVar             | 正向无功电能 | kVar·h | float64  |          |                            |
| NVar             | 反向无功电能 | kVar·h | float64  |          |                            |
| VA               | 视在电能     | kVA·h  | float64  |          |                            |
| **Today**        | **当日电能** |        |          |          |                            |
| Watt             | 有功电能     | kW·h   | float64  | *        |                            |
| PWatt            | 正向有功电能 | kW·h   | float64  |          |                            |
| NWatt            | 反向有功电能 | kW·h   | float64  |          |                            |
| Var              | 无功电能     | kVar·h | float64  |          |                            |
| PVar             | 正向无功电能 | kVar·h | float64  |          |                            |
| NVar             | 反向无功电能 | kVar·h | float64  |          |                            |
| VA               | 视在电能     | kVA    | float64  |          |                            |
| **Current**      | **本次电能** |        |          |          |                            |
| AcquisitionTime  | 采集时间     |        | string   | *        | 格式 "2020-03-18 15:00:00" |
| **Total**        | **累计电能** |        |          |          |                            |
| Watt             | 有功电能     | kW·h   | float64  | *        |                            |
| PWatt            | 正向有功电能 | kW·h   | float64  |          |                            |
| NWatt            | 反向有功电能 | kW·h   | float64  |          |                            |
| Var              | 无功电能     | kVar·h | float64  |          |                            |
| PVar             | 正向无功电能 | kVar·h | float64  |          |                            |
| NVar             | 反向无功电能 | kVar·h | float64  |          |                            |
| VA               | 视在电能     | kVA·h  | float64  |          |                            |
| **Today**        | **当日电能** |        |          |          |                            |
| Watt             | 有功电能     | kW·h   | float64  | *        |                            |
| PWatt            | 正向有功电能 | kW·h   | float64  |          |                            |
| NWatt            | 反向有功电能 | kW·h   | float64  |          |                            |
| Var              | 无功电能     | kVar·h | float64  |          |                            |
| PVar             | 正向无功电能 | kVar·h | float64  |          |                            |
| NVar             | 反向无功电能 | kVar·h | float64  |          |                            |
| VA               | 视在电能     | kVA·h  | float64  |          |                            |

### 3.1.2 输入实例

```
{
	"AKString": "",
	"WellName": "J01-001",
	"Last": {
		"AcquisitionTime": "2020-01-15 12:00:00",
		"Total": {
			"Watt": 4870.33,
			"PWatt": 4943.66,
			"NWatt": -73.33,
			"Var": 42087.63,
			"PVar": 42090.27,
			"NVar": -2.64,
			"VA": 16677.84
		},
		"Today": {
			"Watt": 33.73,
			"PWatt": 33.05,
			"NWatt": -1.26,
			"Var": 289.17,
			"PVar": 289.18,
			"NVar": 1,
			"VA": 113.13
		}
	},
	"Current": {
		"AcquisitionTime": "2020-01-16 01:00:00",
		"Total": {
			"Watt": 5203.74,
			"PWatt": 5280.07,
			"NWatt": -76.34,
			"Var": 45032.43,
			"PVar": 45035.09,
			"NVar": -2.66,
			"VA": 17835.27
		},
		"Today": {
			"Watt": 93.38,
			"PWatt": 94.1,
			"NWatt": -1.77,
			"Var": 818.53,
			"PVar": 818.54,
			"NVar": 1,
			"VA": 321.55
		}
	}
}
```

# 3.2 输出文本

### 3.2.1 输出参数说明

*表3-2 输出参数说明表*

| 代码                 | 名称             | 单位   | 类型     | 备注                                   |
|----------------------|------------------|--------|----------|----------------------------------------|
| WellName             | 井名             |        | string   |                                        |
| ResultStatus         | 计算结果状态     |        | int      | 详见表底注释[1]                        |
| **Verification**     | **数据校验**     |        |          |                                        |
| ErrorCounter         | 错误参数计数器   |        | int      | 错误参数个数                           |
| ErrorString          | 错误参数字符串   |        | string   | 数据错误，计算不成功                   |
| WarningCounter       | 报警计数器       |        | int      | 报警参数个数                           |
| WarningString        | 报警字符串       |        | string   | 报警参数（取默认值，计算正常进行）     |
| **Current**          | **本次电能**     |        |          |                                        |
| AcquisitionTime      | 采集时间         |        | string   |                                        |
| **Total**            | **累计电能**     |        |          |                                        |
| Watt                 | 有功电能         | kW·h   | float64  |                                        |
| PWatt                | 正向有功电能     | kW·h   | float64  |                                        |
| NWatt                | 反向有功电能     | kW·h   | float64  |                                        |
| Var                  | 无功电能         | kVar·h | float64  |                                        |
| PVar                 | 正向无功电能     | kVar·h | float64  |                                        |
| NVar                 | 反向无功电能     | kVar·h | float64  |                                        |
| VA                   | 视在电能         | kVA    | float64  |                                        |
| **Today**            | **当日电能**     |        |          |                                        |
| Watt                 | 有功电能         | kW·h   | float64  |                                        |
| PWatt                | 正向有功电能     | kW·h   | float64  |                                        |
| NWatt                | 反向有功电能     | kW·h   | float64  |                                        |
| Var                  | 无功电能         | kVar·h | float64  |                                        |
| PVar                 | 正向无功电能     | kVar·h | float64  |                                        |
| NVar                 | 反向无功电能     | kVar·h | float64  |                                        |
| VA                   | 视在电能         | kVA·h  | float64  |                                        |
| **Daily**            | **日数据**       |        |          |                                        |
| Date                 | 日期             |        | string   | 格式 "2017-03-18"，为空时说明未跨天    |
| Watt                 | 有功电能         | kW·h   | float64  |                                        |
| PWatt                | 正向有功电能     | kW·h   | float64  |                                        |
| NWatt                | 反向有功电能     | kW·h   | float64  |                                        |
| Var                  | 无功电能         | kVar·h | float64  |                                        |
| PVar                 | 正向无功电能     | kVar·h | float64  |                                        |
| NVar                 | 反向无功电能     | kVar·h | float64  |                                        |
| VA                   | 视在电能         | kVA·h  | float64  |                                        |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*

### 3.2.2 输出实例

```
{
    "WellName": "J01-001",
    "ResultStatus": 1,
    "Verification": {
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": ""
    },
    "Current": {
        "AcquisitionTime": "2020-01-16 01: 00: 00",
        "Total": {
            "Watt": 5203.74,
            "PWatt": 5280.07,
            "NWatt": -76.34,
            "Var": 45032.43,
            "PVar": 45035.09,
            "NVar": -2.66,
            "VA": 17835.27
        },"Today": {
            "Watt": 0,
            "PWatt": 0,
            "NWatt": 0,
            "Var": 0,
            "PVar": 0,
            "NVar": 0,
            "VA": 0
        } },
    "Daily": {
        "Date": "2020-01-15",
        "Watt": 367.14,
        "PWatt": 336.41,
        "NWatt": -3.01,
        "Var": 2944.8,
        "PVar": 2944.82,
        "NVar": -0.02,
        "VA": 1157.43
    }
}
```

----[第二章 时率计算](.././Chapter2/Chapter2.md)----[返回章节目录](.././README.md)----[第四章 通信计算](.././Chapter4/Chapter4.md)----