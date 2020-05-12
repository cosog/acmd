# 第五章 全井汇总

- [第五章 全井汇总](Chapter5.md#第五章-全井汇总)
   - [5.1 输入文本](Chapter5.md#51-输入文本)
     - [5.1.1 输入参数说明](Chapter5.md#511-输入参数说明)
     - [5.1.2 输入实例](Chapter5.md#512-输入实例)
   - [5.2 输出文本](Chapter5.md#52-输出文本)
     - [5.2.1 输出参数说明](Chapter5.md#521-输出参数说明)
     - [5.2.2 输出实例](Chapter5.md#522-输出实例)

## 5.1 输入文本

### 5.1.1 输入参数说明

*表5-1 输入参数说明表*

| 代码                       | 名称           | 单位       | 类型     | 必填     | 备注          |
|----------------------------|----------------|------------|----------|----------|---------------|
| AKString                   | 应用密钥       |            | string   |          | 预留字段      |
| WellName                   | 井名           |            | string   | *        |               |
| **EveryTime**              | **采集点参数** |            |          |          |               |
| AcquisitionTime            | 采集时间       |            | string   | *        |               |
| CommStatus                 | 通信状态       |            | int      |          | 0-离线 1-在线 |
| CommTime                   | 在线时间       |            | float64  |          |               |
| CommTimeEfficiency         | 在线时率       |            | float64  |          |               |
| CommRange                  | 在线区间       |            | string   |          |               |
| RunStatus                  | 运行状态       |            | int      |          | 0-停止 1-运行 |
| RunTime                    | 运行时间       |            | float64  |          |               |
| RunTimeEfficiency          | 运行时率       | %          | float64  |          |               |
| RunRange                   | 运行区间       |            | string   |          |               |
| StopReason                 | 停抽原因       |            | int      |          |               |
| StartReason                | 启抽原因       |            | int      |          |               |
| TubingPressure             | 油压           | MPa        | float64  |          |               |
| CasingPressure             | 套压           | MPa        | float64  |          |               |
| WellHeadFluidTemperature   | 井口油温       | ℃         | float64  |          |               |
| ProductionGasOilRatio      | 生产气油比     | m^3/t      | float64  | *        |               |
| FSResultCode               | 功图工况代码   |            | int      | *        |               |
| Stroke                     | 功图冲程       | m          | float64  | *        |               |
| SPM                        | 功图冲次       | 1/min      | float64  | *        |               |
| FullnessCoefficient        | 充满系数       | 小数       | float64  | *        |               |
| LiquidVolumetricProduction | 产液量（方）   | m^3/d      | float64  |          |               |
| OilVolumetricProduction    | 产油量（方）   | m^3/d      | float64  |          |               |
| WaterVolumetricProduction  | 产水量（方）   | m^3/d      | float64  |          |               |
| LiquidWeightProduction     | 产液量（吨）   | t/d        | float64  | *        |               |
| OilWeightProduction        | 产油量（吨）   | t/d        | float64  | *        |               |
| WaterWeightProduction      | 产水量（吨）   | t/d        | float64  | *        |               |
| VolumeWaterCut             | 体积含水率     | %          | float64  |          |               |
| WeightWaterCut             | 重量含水率     | %          | float64  | *        |               |
| PumpEff                    | 泵效           | %          | float64  |          |               |
| PumpBoreDiameter           | 泵径           | m          | float64  |          |               |
| PumpSettingDepth           | 泵挂           | m          | float64  |          |               |
| ProducingfluidLevel        | 动液面         | m          | float64  |          |               |
| Submergence                | 沉没度         | m          | float64  |          |               |
| ETResultCode               | 电参工况代码   |            | int      |          |               |
| WattDegreeBalance          | 功率平衡度     | %          | float64  |          |               |
| IDegreeBalance             | 电流平衡度     | %          | float64  |          |               |
| DeltaRadius                | 移动距离       | m          | float64  |          |               |
| SurfaceSystemEfficiency    | 地面效率       | 小数       | float64  |          |               |
| WellDownSystemEfficiency   | 井下效率       | 小数       | float64  |          |               |
| SystemEfficiency           | 系统效率       | 小数       | float64  |          |               |
| PowerConsumptionPerTHM     | 吨液百米耗电量 | kW·h/100·t | float64  |          |               |
| IA                         | A相电流        | A          | float64  |          |               |
| IB                         | B相电流        | A          | float64  |          |               |
| IC                         | C相电流        | A          | float64  |          |               |
| VA                         | A相电压        | V          | float64  |          |               |
| VB                         | B相电压        | V          | float64  |          |               |
| VC                         | C相电压        | V          | float64  |          |               |
| RunFrequency               | 频率           | HZ         | float64  |          |               |
| RPM                        | 转速           | r/min      | float64  |          |               |

### 5.1.2 输入实例

```
{
	"AKString": "",
	"WellName": "J01-001",
	"EveryTime": [
		{
			"AcquisitionTime": "2020-01-15 10:00:00",
			"CommStatus": 1,
			"CommTime": 10,
			"CommTimeEfficiency": 0.42,
			"CommRange": "00:00-10:00",
			"RunStatus": 1,
			"RunTime": 10,
			"RunTimeEfficiency": 0.42,
			"RunRange": "00:00-10:00",
			"StopReason": 1,
			"StartReason": 1,
			"TubingPressure": 1.5,
			"CasingPressure": 1.5,
			"WellHeadFluidTemperature": 15,
			"ProductionGasOilRatio": 55,
			"FSResultCode": 1202,
			"Stroke": 2.5,
			"SPM": 3.9,
			"FullnessCoefficient": 0.7,
			"LiquidVolumetricProduction": 6,
			"OilVolumetricProduction": 1.2,
			"WaterVolumetricProduction": 4.8,
			"LiquidWeightProduction": 6,
			"OilWeightProduction": 1.2,
			"WaterWeightProduction": 4.8,
			"VolumeWaterCut": 80,
			"WeightWaterCut": 80,
			"PumpEff": 80,
			"PumpBoreDiameter": 0.032,
			"PumpSettingDepth": 1500,
			"ProducingfluidLevel": 1280,
			"Submergence": 220,
			"ETResultCode": 1202,
			"WattDegreeBalance": 100,
			"IDegreeBalance": 100,
			"DeltaRadius": 0,
			"SurfaceSystemEfficiency": 60,
			"WellDownSystemEfficiency": 60,
			"SystemEfficiency": 36,
			"PowerConsumptionPerTHM": 1.5,
			"IA": 15,
			"IB": 15,
			"IC": 15,
			"VA": 380,
			"VB": 380,
			"VC": 380,
			"RunFrequency": 50.5,
			"RPM": 0
        },
		{
			"AcquisitionTime": "2020-01-15 14:00:00",
			"CommStatus": 1,
			"CommTime": 14,
			"CommTimeEfficiency": 0.58,
			"CommRange": "00:00-14:00",
			"RunStatus": 1,
			"RunTime": 14,
			"RunTimeEfficiency": 0.58,
			"RunRange": "00:00-14:00",
			"StopReason": 1,
			"StartReason": 1,
			"TubingPressure": 2.1,
			"CasingPressure": 2.2,
			"WellHeadFluidTemperature": 30,
			"ProductionGasOilRatio": 75,
			"FSResultCode": 1202,
			"Stroke": 2.6,
			"SPM": 4.1,
			"FullnessCoefficient": 0.85,
			"LiquidVolumetricProduction": 4.56,
			"OilVolumetricProduction": 0.91,
			"WaterVolumetricProduction": 3.65,
			"LiquidWeightProduction": 4.46,
			"OilWeightProduction": 0.81,
			"WaterWeightProduction": 3.65,
			"VolumeWaterCut": 80,
			"WeightWaterCut": 80,
			"PumpEff": 85,
			"PumpBoreDiameter": 0.032,
			"PumpSettingDepth": 1500,
			"ProducingfluidLevel": 1300,
			"Submergence": 200,
			"ETResultCode": 1202,
			"WattDegreeBalance": 104,
			"IDegreeBalance": 105,
			"DeltaRadius": -0.2,
			"SurfaceSystemEfficiency": 70,
			"WellDownSystemEfficiency": 70,
			"SystemEfficiency": 40,
			"PowerConsumptionPerTHM": 0.5,
			"IA": 11,
			"IB": 11,
			"IC": 11,
			"VA": 360,
			"VB": 360,
			"VC": 360,
			"RunFrequency": 50,
			"RPM": 0
        },
		{
			"AcquisitionTime": "2020-01-15 20:00:00",
			"CommStatus": 1,
			"CommTime": 21,
			"CommTimeEfficiency": 0.875,
			"CommRange": "00:00-21:00",
			"RunStatus": 1,
			"RunTime": 21,
			"RunTimeEfficiency": 0.875,
			"RunRange": "00:00-21:00",
			"StopReason": 1,
			"StartReason": 1,
			"TubingPressure": 2.1,
			"CasingPressure": 2.2,
			"WellHeadFluidTemperature": 30,
			"ProductionGasOilRatio": 75,
			"FSResultCode": 1202,
			"Stroke": 2.6,
			"SPM": 4.1,
			"FullnessCoefficient": 0.85,
			"LiquidVolumetricProduction": 4.56,
			"OilVolumetricProduction": 0.91,
			"WaterVolumetricProduction": 3.65,
			"LiquidWeightProduction": 4.46,
			"OilWeightProduction": 0.81,
			"WaterWeightProduction": 3.65,
			"VolumeWaterCut": 80.8,
			"WeightWaterCut": 80.8,
			"PumpEff": 85,
			"PumpBoreDiameter": 0.032,
			"PumpSettingDepth": 1500,
			"ProducingfluidLevel": 1300,
			"Submergence": 200,
			"ETResultCode": 1202,
			"WattDegreeBalance": 104,
			"IDegreeBalance": 105,
			"DeltaRadius": -0.2,
			"SurfaceSystemEfficiency": 70,
			"WellDownSystemEfficiency": 70,
			"SystemEfficiency": 40,
			"PowerConsumptionPerTHM": 0.5,
			"IA": 12,
			"IB": 12,
			"IC": 12,
			"VA": 360,
			"VB": 360,
			"VC": 360,
			"RunFrequency": 50,
			"RPM": 0
        }
    ]
}
```

## 5.2 输出文本

### 5.2.1 输出参数说明

*表5-2 输出参数说明表*

| 代码                             | 名称              | 单位       | 类型     | 备注                                 |
|----------------------------------|-------------------|------------|----------|--------------------------------------|
| WellName                         | 井名              |            | string   |                                      |
| ResultStatus                     | 计算结果状态      |            | int      | 详见表底注释[1]                      |
| **Verification**                 | **数据校验**      |            |          |                                      |
| ErrorCounter                     | 错误参数计数器    |            | int      |                                      |
| ErrorString                      | 错误参数字符串    |            | string   |                                      |
| WarningCounter                   | 报警计数器        |            | int      |                                      |
| WarningString                    | 报警字符串        |            | string   |                                      |
| CommStatus                       | 通信状态          |            | int      |                                      |
| CommTime                         | 在线时间          |            | float64  |                                      |
| CommTimeEfficiency               | 在线时率          |            | float64  |                                      |
| CommRange                        | 在线区间          |            | string   |                                      |
| RunStatus                        | 运行状态          |            | int      |                                      |
| RunTime                          | 运行时间          |            | float64  |                                      |
| RunTimeEfficiency                | 运行时率          |            | float64  |                                      |
| RunRange                         | 运行区间          |            | string   |                                      |
| StopReason                       | 停抽原因          |            | int      |                                      |
| StartReason                      | 启抽原因          |            | int      |                                      |
| FSResultCode                     | 功图工况代码      |            | int      |                                      |
| FSResultString                   | 功图工况综合      |            | string   |                                      |
| ExtendedDays                     | 功图延用天数      |            | int      |                                      |
| **Stroke**                       | **功图冲程**      |            |          |                                      |
| Value                            | 值                | m          | float64  |                                      |
| Max                              | 最大值            | m          | float64  |                                      |
| Min                              | 最小值            | m          | float64  |                                      |
| **SPM**                          | **功图冲次**      |            |          |                                      |
| Value                            | 值                | 1/min      | float64  |                                      |
| Max                              | 最大值            | 1/min      | float64  |                                      |
| Min                              | 最小值            | 1/min      | float64  |                                      |
| **TubingPressure**               | **油压**          |            |          |                                      |
| Value                            | 值                | MPa        | float64  |                                      |
| Max                              | 最大值            | MPa        | float64  |                                      |
| Min                              | 最小值            | MPa        | float64  |                                      |
| **CasingPressure**               | **套压**          |            |          |                                      |
| Value                            | 值                | MPa        | float64  |                                      |
| Max                              | 最大值            | MPa        | float64  |                                      |
| Min                              | 最小值            | MPa        | float64  |                                      |
| **WellHeadFluidTemperature**     | **井口油温**      |            |          |                                      |
| Value                            | 值                | ℃         | float64  |                                      |
| Max                              | 最大值            | ℃         | float64  |                                      |
| Min                              | 最小值            | ℃         | float64  |                                      |
| **ProductionGasOilRatio**        | **生产气油比**    |            |          |                                      |
| Value                            | 值                | m^3/t      | float64  |                                      |
| Max                              | 最大值            | m^3/t      | float64  |                                      |
| Min                              | 最小值            | m^3/t      | float64  |                                      |
| **FullnessCoefficient**          | **充满系数**      |            |          |                                      |
| Value                            | 值                | 小数       | float64  |                                      |
| Max                              | 最大值            | 小数       | float64  |                                      |
| Min                              | 最小值            | 小数       | float64  |                                      |
| **LiquidVolumetricProduction**   | **日产液量**      |            |          |                                      |
| Value                            | 值                | m^3/d      | float64  |                                      |
| Max                              | 最大值            | m^3/d      | float64  |                                      |
| Min                              | 最小值            | m^3/d      | float64  |                                      |
| **OilVolumetricProduction**      | **日产油量**      |            |          |                                      |
| Value                            | 值                | m^3/d      | float64  |                                      |
| Max                              | 最大值            | m^3/d      | float64  |                                      |
| Min                              | 最小值            | m^3/d      | float64  |                                      |
| **WaterVolumetricProduction**    | **日产水量**      |            |          |                                      |
| Value                            | 值                | m^3/d      | float64  |                                      |
| Max                              | 最大值            | m^3/d      | float64  |                                      |
| Min                              | 最小值            | m^3/d      | float64  |                                      |
| **LiquidWeightProduction**       | **日产液量**      |            |          |                                      |
| Value                            | 值                | t/d        | float64  |                                      |
| Max                              | 最大值            | t/d        | float64  |                                      |
| Min                              | 最小值            | t/d        | float64  |                                      |
| **OilWeightProduction**          | **日产油量**      |            |          |                                      |
| Value                            | 值                | t/d        | float64  |                                      |
| Max                              | 最大值            | t/d        | float64  |                                      |
| Min                              | 最小值            | t/d        | float64  |                                      |
| **WaterWeightProduction**        | **日产水量**      |            |          |                                      |
| Value                            | 值                | t/d        | float64  |                                      |
| Max                              | 最大值            | t/d        | float64  |                                      |
| Min                              | 最小值            | t/d        | float64  |                                      |
| **VolumeWaterCut**               | **体积含水率**    |            |          |                                      |
| Value                            | 值                | %          | float64  |                                      |
| Max                              | 最大值            | %          | float64  |                                      |
| Min                              | 最小值            | %          | float64  |                                      |
| **WeightWaterCut**               | **重量含水率**    |            |          |                                      |
| Value                            | 值                | %          | float64  |                                      |
| Max                              | 最大值            | %          | float64  |                                      |
| Min                              | 最小值            | %          | float64  |                                      |
| **PumpEff**                      | **泵效**          |            |          |                                      |
| Value                            | 值                | %          | float64  |                                      |
| Max                              | 最大值            | %          | float64  |                                      |
| Min                              | 最小值            | %          | float64  |                                      |
| **PumpBoreDiameter**             | **泵径**          |            |          |                                      |
| Value                            | 值                | m          | float64  |                                      |
| Max                              | 最大值            | m          | float64  |                                      |
| Min                              | 最小值            | m          | float64  |                                      |
| **PumpSettingDepth**             | **泵挂**          |            |          |                                      |
| Value                            | 值                | m          | float64  |                                      |
| Max                              | 最大值            | m          | float64  |                                      |
| Min                              | 最小值            | m          | float64  |                                      |
| **ProducingfluidLevel**          | **动液面**        |            |          |                                      |
| Value                            | 值                | m          | float64  |                                      |
| Max                              | 最大值            | m          | float64  |                                      |
| Min                              | 最小值            | m          | float64  |                                      |
| **Submergence**                  | **沉没度**        |            |          |                                      |
| Value                            | 值                | m          | float64  |                                      |
| Max                              | 最大值            | m          | float64  |                                      |
| Min                              | 最小值            | m          | float64  |                                      |
| ETResultCode                     | 电参工况代码      |            | int      |                                      |
| ETResultString                   | 电参工况综合      |            | string   |                                      |
| **WattDegreeBalance**            | **功率平衡度**    |            |          |                                      |
| Value                            | 值                | %          | float64  |                                      |
| Max                              | 最大值            | %          | float64  |                                      |
| Min                              | 最小值            | %          | float64  |                                      |
| **IdegreeBalance**               | **电流平衡度**    |            |          |                                      |
| Value                            | 值                | %          | float64  |                                      |
| Max                              | 最大值            | %          | float64  |                                      |
| Min                              | 最小值            | %          | float64  |                                      |
| **DeltaRadius**                  | **移动距离**      |            |          |                                      |
| Value                            | 值                | m          | float64  | + 代表向外移 -代表向内移            |
| Max                              | 最大值            | m          | float64  | + 代表向外移 -代表向内移            |
| Min                              | 最小值            | m          | float64  | + 代表向外移 -代表向内移            |
| **SurfaceSystemEfficiency**      | **地面效率**      |            |          |                                      |
| Value                            | 值                | 小数       | float64  |                                      |
| Max                              | 最大值            | 小数       | float64  |                                      |
| Min                              | 最小值            | 小数       | float64  |                                      |
| **WellDownSystemEfficiency**     | **井下效率**      |            |          |                                      |
| Value                            | 值                | 小数       | float64  |                                      |
| Max                              | 最大值            | 小数       | float64  |                                      |
| Min                              | 最小值            | 小数       | float64  |                                      |
| **SystemEfficiency**             | **系统效率**      |            |          |                                      |
| Value                            | 值                | 小数       | float64  |                                      |
| Max                              | 最大值            | 小数       | float64  |                                      |
| Min                              | 最小值            | 小数       | float64  |                                      |
| **PowerConsumptionPerTHM**       | **吨液百米耗电量**|            |          |                                      |
| Value                            | 值                | kW·h/100·t | float64  |                                      |
| Max                              | 最大值            | kW·h/100·t | float64  |                                      |
| Min                              | 最小值            | kW·h/100·t | float64  |                                      |
| DailyAPC                         | 日有功功耗        | kW·h       | float64  |                                      |
| DailyRPC                         | 日无功功耗        | kVar·h     | float64  |                                      |
| **IA**                           | **A相电流**       |            |          |                                      |
| Value                            | 值                | A          | float64  |                                      |
| Max                              | 最大值            | A          | float64  |                                      |
| Min                              | 最小值            | A          | float64  |                                      |
| **IB**                           | **B相电流**       |            |          |                                      |
| Value                            | 值                | A          | float64  |                                      |
| Max                              | 最大值            | A          | float64  |                                      |
| Min                              | 最小值            | A          | float64  |                                      |
| **IC**                           | **C相电流**       |            |          |                                      |
| Value                            | 值                | A          | float64  |                                      |
| Max                              | 最大值            | A          | float64  |                                      |
| Min                              | 最小值            | A          | float64  |                                      |
| IMaxString                       | 电流最大值字符串  | A          | string   |                                      |
| IMinString                       | 电流最小值字符串  | A          | string   |                                      |
| **VA**                           | **A相电压**       |            |          |                                      |
| Value                            | 值                | V          | float64  |                                      |
| Max                              | 最大值            | V          | float64  |                                      |
| Min                              | 最小值            | V          | float64  |                                      |
| **VB**                           | **B相电压**       |            |          |                                      |
| Value                            | 值                | V          | float64  |                                      |
| Max                              | 最大值            | V          | float64  |                                      |
| Min                              | 最小值            | V          | float64  |                                      |
| **VC**                           | **C相电压**       |            |          |                                      |
| Value                            | 值                | V          | float64  |                                      |
| Max                              | 最大值            | V          | float64  |                                      |
| Min                              | 最小值            | V          | float64  |                                      |
| VMaxString                       | 电压最大值字符串  | V          | string   |                                      |
| VMinString                       | 电压最小值字符串  | V          | string   |                                      |
| **RunFrequency**                 | **频率**          |            |          |                                      |
| Value                            | 值                | HZ         | float64  |                                      |
| Max                              | 最大值            | HZ         | float64  |                                      |
| Min                              | 最小值            | HZ         | float64  |                                      |
| **RPM**                          | **转速**          |            |          |                                      |
| Value                            | 值                | r/min      | float64  |                                      |
| Max                              | 最大值            | r/min      | float64  |                                      |
| Min                              | 最小值            | r/min      | float64  |                                      |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误* 

### 5.2.2 输出实例

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
	"CommStatus": 1,
	"CommTime": 21,
	"CommTimeEfficiency": 0.875,
	"CommRange": "00:00-21:00",
	"RunStatus": 1,
	"RunTime": 21,
	"RunTimeEfficiency": 0.875,
	"RunRange": "00:00-21:00",
	"StopReason": 1,
	"StartReason": 1,
	"TubingPressure": {
		"Value": 1.8,
		"Max": 2.1,
		"Min": 1.5
	},
	"CasingPressure": {
		"Value": 1.85,
		"Max": 2.2,
		"Min": 1.5
	},
	"WellHeadFluidTemperature": {
		"Value": 22.5,
		"Max": 30,
		"Min": 15
	},
	"ProductionGasOilRatio": {
		"Value": 65,
		"Max": 75,
		"Min": 55
	},
	"FSResultCode": 1202,
	"FSResultString": "20:00:00  正常",
	"ExtendedDays": 1,
	"Stroke": {
		"Value": 2.55,
		"Max": 2.6,
		"Min": 2.5
	},
	"SPM": {
		"Value": 4,
		"Max": 4.1,
		"Min": 3.9
	},
	"FullnessCoefficient": {
		"Value": 0.775,
		"Max": 0.85,
		"Min": 0.7
	},
	"LiquidVolumetricProduction": {
		"Value": 4.62,
		"Max": 5.25,
		"Min": 3.99
	},
	"OilVolumetricProduction": {
		"Value": 0.913,
		"Max": 1.05,
		"Min": 0.796
	},
	"WaterVolumetricProduction": {
		"Value": 3.71,
		"Max": 4.2,
		"Min": 3.19
	},
	"LiquidWeightProduction": {
		"Value": 4.58,
		"Max": 5.25,
		"Min": 3.9
	},
	"OilWeightProduction": {
		"Value": 0.905,
		"Max": 1.05,
		"Min": 0.709
	},
	"WaterWeightProduction": {
		"Value": 3.67,
		"Max": 4.2,
		"Min": 3.19
	},
	"VolumeWaterCut": {
		"Value": 80.23,
		"Max": 80.8,
		"Min": 80
	},
	"WeightWaterCut": {
		"Value": 80.23,
		"Max": 80.8,
		"Min": 80
	},
	"PumpEff": {
		"Value": 82.5,
		"Max": 85,
		"Min": 80
	},
	"PumpBoreDiameter": {
		"Value": 0.032,
		"Max": 0.032,
		"Min": 0.032
	},
	"PumpSettingDepth": {
		"Value": 1500,
		"Max": 1500,
		"Min": 1500
	},
	"ProducingfluidLevel": {
		"Value": 1290,
		"Max": 1300,
		"Min": 1280
	},
	"Submergence": {
		"Value": 210,
		"Max": 220,
		"Min": 200
	},
	"ETResultCode": 1202,
	"ETResultString": "20:00:00  正常",
	"WattDegreeBalance": {
		"Value": 102,
		"Max": 104,
		"Min": 100
	},
	"IDegreeBalance": {
		"Value": 102.5,
		"Max": 105,
		"Min": 100
	},
	"DeltaRadius": {
		"Value": -0.1,
		"Max": 0,
		"Min": -0.2
	},
	"SurfaceSystemEfficiency": {
		"Value": 65,
		"Max": 70,
		"Min": 60
	},
	"WellDownSystemEfficiency": {
		"Value": 65,
		"Max": 70,
		"Min": 60
	},
	"SystemEfficiency": {
		"Value": 38,
		"Max": 40,
		"Min": 36
	},
	"PowerConsumptionPerTHM": {
		"Value": 1,
		"Max": 1.5,
		"Min": 0.5
	},
	"IA": {
		"Value": 13.29,
		"Max": 15,
		"Min": 11
	},
	"IB": {
		"Value": 13.29,
		"Max": 15,
		"Min": 11
	},
	"IC": {
		"Value": 13.29,
		"Max": 15,
		"Min": 11
	},
	"IMaxString": "15.00/15.00/15.00",
	"IMinString": "11.00/11.00/11.00",
	"VA": {
		"Value": 370,
		"Max": 380,
		"Min": 360
	},
	"VB": {
		"Value": 370,
		"Max": 380,
		"Min": 360
	},
	"VC": {
		"Value": 370,
		"Max": 380,
		"Min": 360
	},
	"VMaxString": "380.00/380.00/380.00",
	"VMinString": "360.00/360.00/360.00",
	"RunFrequency": {
		"Value": 50.25,
		"Max": 50.5,
		"Min": 50
	},
	"RPM": {
		"Value": 0,
		"Max": 0,
		"Min": 0
	}
}
```

----[第四章 通信计算](.././Chapter4/Chapter4.md)----[返回章节目录](.././README.md)----[第六章 插件](.././Chapter6/Chapter6.md)----