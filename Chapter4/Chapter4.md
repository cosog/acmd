# 第四章 通信计算

- [第四章 通信计算](Chapter4.md#第四章-通信计算)
   - [4.1 输入文本](Chapter4.md#41-输入文本)
     - [4.1.1 输入参数说明](Chapter4.md#411-输入参数说明)
     - [4.1.2 输入实例](Chapter4.md#412-输入实例)
   - [4.2 输出文本](Chapter4.md#42-输出文本)
     - [4.2.1 输出参数说明](Chapter4.md#421-输出参数说明)
     - [4.2.2 输出实例](Chapter4.md#422-输出实例)

## 4.1 输入文本

### 4.1.1 输入参数说明

*表4-1 输入参数说明表*

| 代码                    | 名称            | 单位 | 类型     | 必填     | 备注                           |
|-------------------------|-----------------|------|----------|----------|--------------------------------|
| AKString                | 应用密钥        |      | string   |          |                                |
| WellName                | 井名            |      | string   | *        |                                |
| **Last**                | **上次通信**    |      |          |          |                                |
| AcquisitionTime         | 采集时间        |      | string   | *        | 格式 "2020-01-18 15:00:00"     |
| CommStatus              | 通信状态        |      | bool     | *        | true-在线 false-离线           |
| **CommEfficiency**      | **通信时率**    |      |          |          |                                |
| **Range**               | **实时区间**    |      |          |          |                                |
| StartTime               | 开始时间        |      | string   | *        | 详见表底注释[1]                |
| EndTime                 | 结束时间        |      | string   | *        | 详见表底注释[1]                |
| Time                    | 实时时间        | h    | float64  | *        |                                |
| Efficiency              | 实时时率        | 小数 | float64  | *        |                                |
| **Current**             | **本次通信**    |      |          |          |                                |
| AcquisitionTime         | 采集时间        |      | string   | *        | 格式 "2020-03-18 15:00:00"     |
| CommStatus              | 通信状态        |      | bool     | *        | true-在线 false-离线           |

**[1]** *开始时间/结束时间:1、 StartTime="" EndTime=""-全天运行 2、 StartTime="00:00" EndTime="00:00"-全天停止 3、其他-按区间段运行*

### 4.1.2 输入实例

```
{
	"AKString": "",
	"WellName": "J01-001",
	"Last": {
		"AcquisitionTime": "2020-01-15 12:00:00",
		"CommStatus": true,
		"CommEfficiency": {
			"Range": [
				{
					"StartTime": "00:00",
					"EndTime": "05:00"
				},
				{
					"StartTime": "07:00",
					"EndTime": "12:00"
				}
			],
			"Time": 10,
			"Efficiency": 0.417
		}
	},
	"Current": {
		"AcquisitionTime": "2020-01-16 01:00:00",
		"CommStatus": true
	}
}
```

## 4.2 输出文本

### 4.2.1 输出参数说明

*表4-2 输出参数说明表*

| 代码                    | 名称               | 单位 | 类型     | 备注                                      |
|-------------------------|--------------------|------|----------|-------------------------------------------|
| WellName                | 井名               |      | string   |                                           |
| ResultStatus            | 计算结果状态       |      | int      | 详见表底注释[1]                           |
| **Verification**        | **数据校验**       |      |          |                                           |
| ErrorCounter            | 错误参数计数器     |      | int      | 错误参数个数                              |
| ErrorString             | 错误参数字符串     |      | string   | 数据错误，计算不成功                      |
| WarningCounter          | 报警计数器         |      | int      | 报警参数个数                              |
| WarningString           | 报警字符串         |      | string   | 报警参数（取默认值，计算正常进行）        |
| **Current**             | **本次数据**       |      |          |                                           |
| AcquisitionTime         | 采集时间           |      | string   |                                           |
| CommStatus              | 通信状态           |      | bool     | true-在线 false-离线                      |
| **CommEfficiency**      | **通信时率**       |      |          |                                           |
| **Range**               | **实时区间**       |      |          |                                           |
| StartTime               | 开始时间           |      | string   | 详见表底注释[2]                           |
| EndTime                 | 结束时间           |      | string   | 详见表底注释[2]                           |
| Time                    | 实时在线时间       | h    | float64  |                                           |
| Efficiency              | 实时在线时率       | 小数 | float64  |                                           |
| RangeString             | 实时在线区间字符串 |      | string   | 00:00-8:00;10:00-00:00                    |
| **Daily**               | **日数据**         |      |          |                                           |
| Date                    | 日期               |      | string   | 格式 "2017-03-18"，为空时说明未跨天       |
| CommStatus              | 通信状态           |      | bool     | true-在线 false-离线                      |
| **CommEfficiency**      | **通信时率**       |      |          |                                           |
| **Range**               | **日区间**         |      |          |                                           |
| StartTime               | 开始时间           |      | string   |                                           |
| EndTime                 | 结束时间           |      | string   |                                           |
| Time                    | 日在线时间         | h    | float64  |                                           |
| Efficiency              | 日在线时率         | 小数 | float64  |                                           |
| RangeString             | 日在线区间字符串   |      | string   |                                           |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*  
**[2]** *开始时间/结束时间:1、 StartTime="" EndTime=""-全天运行 2、 StartTime="00:00" EndTime="00:00"-全天停止 3、其他-按区间段运行*

### 4.2.2 输出实例

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
		"CommStatus": true,
		"CommEfficiency": {
			"Range": [
				{
					"StartTime": "00: 00",
					"EndTime": "01: 00"
                }
            ],
			"Time": 1,
			"Efficiency": 1,
			"RangeString": "00: 00-01: 00"
		}
	},
	"Daily": {
		"Date": "2020-01-15",
		"CommStatus": true,
		"CommEfficiency": {
			"Range": [
				{
					"StartTime": "00: 00",
					"EndTime": "05: 00"
                },
				{
					"StartTime": "07: 00",
					"EndTime": "00: 00"
                }
            ],
			"Time": 22,
			"Efficiency": 0.917,
			"RangeString": "00: 00-05: 00;07: 00-00: 00"
		}
	}
}
```

----[第三章 能耗计算](.././Chapter3/Chapter3.md)----[返回章节目录](.././README.md)----[第五章 全井汇总](.././Chapter5/Chapter5.md)----