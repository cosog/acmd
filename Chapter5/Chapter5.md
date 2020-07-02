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

| 代码                                       | 名称                       | 单位       | 类型     | 必填     | 备注          |
|--------------------------------------------|----------------------------|------------|----------|----------|---------------|
| AKString                                   | 应用密钥                   |            | string   |          | 预留字段      |
| WellName                                   | 井名                       |            | string   | *        |               |
| Date                                       | 汇总日期                   |            | string   | *        |               |
| **EveryTime**                              | **采集点参数**             |            |          |          |               |
| AcquisitionTime                            | 采集时间                   |            | string   | *        |               |
| CommStatus                                 | 通信状态                   |            | int      |          | 0-离线 1-在线 |
| CommTime                                   | 在线时间                   |            | float64  |          |               |
| CommTimeEfficiency                         | 在线时率                   |            | float64  |          |               |
| CommRange                                  | 在线区间                   |            | string   |          |               |
| RunStatus                                  | 运行状态                   |            | int      |          | 0-停止 1-运行 |
| RunTime                                    | 运行时间                   |            | float64  |          |               |
| RunTimeEfficiency                          | 运行时率                   | %          | float64  |          |               |
| RunRange                                   | 运行区间                   |            | string   |          |               |
| StopReason                                 | 停抽原因                   |            | int      |          |               |
| StartReason                                | 启抽原因                   |            | int      |          |               |
| TubingPressure                             | 油压                       | MPa        | float64  |          |               |
| CasingPressure                             | 套压                       | MPa        | float64  |          |               |
| WellHeadFluidTemperature                   | 井口油温                   | ℃         | float64  |          |               |
| ProductionGasOilRatio                      | 生产气油比                 | m^3/t      | float64  |          |               |
| FSResultCode                               | 功图工况代码               |            | int      | *        |               |
| Stroke                                     | 冲程                       | m          | float64  | *        |               |
| SPM                                        | 冲次                       | 1/min      | float64  | *        |               |
| UpperLoadLine                              | 理论上载荷线               | kN         | float64  | *        |               |
| LowerLoadLine                              | 理论下载荷线               | kN         | float64  | *        |               |
| UpperLoadLineOfExact                       | 考虑沉没压力的上载荷线     | kN         | float64  | *        |               |
| DeltaLoadLine                              | 理论液柱载荷               | kN         | float64  | *        |               |
| DeltaLoadLineOfExact                       | 考虑沉没压力的理论液柱载荷 | kN         | float64  | *        |               |
| FMax                                       | 最大载荷                   | kN         | float64  | *        |               |
| FMin                                       | 最小载荷                   | kN         | float64  | *        |               |
| DeltaF                                     | 载荷差                     | kN         | float64  | *        |               |
| Area                                       | 功图面积                   | kN·m       | float64  | *        |               |
| PlungerStroke                              | 柱塞冲程                   | m          | float64  | *        |               |
| AvailablePlungerStroke                     | 柱塞有效冲程               | m          | float64  | *        |               |
| FullnessCoefficient                        | 充满系数                   | 小数       | float64  | *        |               |
| LiquidVolumetricProduction                 | 产液量（方）               | m^3/d      | float64  |          |               |
| OilVolumetricProduction                    | 产油量（方）               | m^3/d      | float64  |          |               |
| WaterVolumetricProduction                  | 产水量（方）               | m^3/d      | float64  |          |               |
| AvailablePlungerStrokeVolumetricProduction | 柱塞有效冲程计算产量（方） | m^3/d      | float64  |          |               |
| PumpClearanceLeakVolumetricProduction      | 泵间隙漏失量（方）         | m^3/d      | float64  |          |               |
| TVLeakVolumetricProduction                 | 游动凡尔漏失量（方）       | m^3/d      | float64  |          |               |
| SVLeakVolumetricProduction                 | 固定凡尔漏失量（方）       | m^3/d      | float64  |          |               |
| GasInfluenceVolumetricProduction           | 气影响（方）               | m^3/d      | float64  |          |               |
| LiquidWeightProduction                     | 产液量（吨）               | t/d        | float64  | *        |               |
| OilWeightProduction                        | 产油量（吨）               | t/d        | float64  | *        |               |
| WaterWeightProduction                      | 产水量（吨）               | t/d        | float64  | *        |               |
| AvailablePlungerStrokeWeightProduction     | 柱塞有效冲程计算产量（吨） | t/d        | float64  |          |               |
| PumpClearanceLeakWeightProduction          | 泵间隙漏失量（吨）         | t/d        | float64  |          |               |
| TVLeakWeightProduction                     | 游动凡尔漏失量（吨）       | t/d        | float64  |          |               |
| SVLeakWeightProduction                     | 固定凡尔漏失量（吨）       | t/d        | float64  |          |               |
| GasInfluenceWeightProduction               | 气影响（吨）               | t/d        | float64  |          |               |
| VolumeWaterCut                             | 体积含水率                 | %          | float64  |          |               |
| WeightWaterCut                             | 重量含水率                 | %          | float64  | *        |               |
| PumpEff                                    | 泵效                       | %          | float64  |          |               |
| PumpEff1                                   | 冲程损失系数               | 小数       | float64  |          |               |
| RodFlexLength                              | 抽油杆伸长量               | m          | float64  |          |               |
| TubingFlexLength                           | 计算油管伸缩值             | m          | float64  |          |               |
| InertiaLength                              | 惯性载荷下冲程增量         | m          | float64  |          |               |
| PumpEff2                                   | 充满系数                   | 小数       | float64  |          |               |
| PumpEff3                                   | 间隙漏失系数               | 小数       | float64  |          |               |
| PumpEff4                                   | 液体收缩系数               | 小数       | float64  |          |               |
| PumpBoreDiameter                           | 泵径                       | m          | float64  |          |               |
| PumpSettingDepth                           | 泵挂                       | m          | float64  |          |               |
| ProducingfluidLevel                        | 动液面                     | m          | float64  |          |               |
| Submergence                                | 沉没度                     | m          | float64  |          |               |
| PumpIntakeP                                | 泵入口压力                 | MPa        | float64  |          |               |
| PumpIntakeT                                | 泵入口温度                 | ℃         | float64  |          |               |
| PumpIntakeGOL                              | 泵入口就地气液比           |            | float64  |          |               |
| PumpIntakeVisl                             | 泵入口粘度                 | mPa·s      | float64  |          |               |
| PumpIntakeBo                               | 泵入口原油体积系数         |            | float64  |          |               |
| PumpOutletP                                | 泵出口压力                 | MPa        | float64  |          |               |
| PumpOutletT                                | 泵出口温度                 | ℃         | float64  |          |               |
| PumpOutletGOL                              | 泵出口就地气液比           |            | float64  |          |               |
| PumpOutletVisl                             | 泵出口粘度                 | mPa·s      | float64  |          |               |
| PumpOutletBo                               | 泵出口原油体积系数         |            | float64  |          |               |
| ETResultCode                               | 电参工况代码               |            | int      |          |               |
| WattDegreeBalance                          | 功率平衡度                 | %          | float64  |          |               |
| UpStrokeWattMax                            | 上冲程功率最大值           | kW         | float64  |          |               |
| DownStrokeWattMax                          | 下冲程功率最大值           | kW         | float64  |          |               |
| IDegreeBalance                             | 电流平衡度                 | %          | float64  |          |               |
| UpStrokeIMax                               | 上冲程电流最大值           | A          | float64  |          |               |
| DownStrokeIMax                             | 下冲程电流最大值           | A          | float64  |          |               |
| DeltaRadius                                | 移动距离                   | m          | float64  |          |               |
| SurfaceSystemEfficiency                    | 地面效率                   | 小数       | float64  |          |               |
| WellDownSystemEfficiency                   | 井下效率                   | 小数       | float64  |          |               |
| SystemEfficiency                           | 系统效率                   | 小数       | float64  |          |               |
| PowerConsumptionPerTHM                     | 吨液百米耗电量             | kW·h/100·t | float64  |          |               |
| AvgWatt                                    | 平均有功功率               | kW         | float64  |          |               |
| PolishRodPower                             | 光杆功率                   | kW         | float64  |          |               |
| WaterPower                                 | 水功率                     | kW         | float64  |          |               |
| IA                                         | A相电流                    | A          | float64  |          |               |
| IB                                         | B相电流                    | A          | float64  |          |               |
| IC                                         | C相电流                    | A          | float64  |          |               |
| VA                                         | A相电压                    | V          | float64  |          |               |
| VB                                         | B相电压                    | V          | float64  |          |               |
| VC                                         | C相电压                    | V          | float64  |          |               |
| RunFrequency                               | 频率                       | HZ         | float64  |          |               |
| RPM                                        | 转速                       | r/min      | float64  |          |               |
| Signal                                     | 信号强度                   |            | float64  |          |               |
| WattSum                                    | 有功功率                   | kW         | float64  |          |               |
| VarSum                                     | 无功功率                   | kVar       | float64  |          |               |
| VASum                                      | 视在功率                   | kVA        | float64  |          |               |
| PFSum                                      | 功率因数                   | 小数       | float64  |          |               |

### 5.1.2 输入实例

```
{
	"AKString": "",
	"WellName": "J01-001",
	"Date":"2020-07-01",
	"EveryTime": [
		{
			"AcquisitionTime": "2020-07-01 10:00:00",
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
			"SPM": 4.1,
	 		"UpperLoadLine": 35.65,
	 		"LowerLoadLine": 21.69,
	 		"UpperLoadLineOfExact": 32.15,
	 		"DeltaLoadLine": 13.96,
	 		"DeltaLoadLineOfExact": 10.46,
	 		"FMax": 39.90,
	 		"FMin": 21.17,
	 		"DeltaF": 18.73,
	 		"Area": 19.21,
	 		"PlungerStroke": 2.25,
	 		"AvailablePlungerStroke": 1.76,
	 		"FullnessCoefficient": 0.78,
	 		"TheoreticalProduction": 9.12,
	 		"LiquidVolumetricProduction": 6,
	 		"OilVolumetricProduction": 1.2,
	 		"WaterVolumetricProduction": 4.8,
	 		"AvailablePlungerStrokeVolumetricProduction": 6.45,
	 		"PumpClearanceLeakVolumetricProduction": 0.12,
	 		"TVLeakVolumetricProduction": 0,
	 		"SVLeakVolumetricProduction": 0,
	 		"GasInfluenceVolumetricProduction": 0,
	 		"LiquidWeightProduction": 5.87,
	 		"OilWeightProduction": 1.2,
	 		"WaterWeightProduction": 4.8,
	 		"AvailablePlungerStrokeWeightProduction": 6.32,
	 		"PumpClearanceLeakWeightProduction": 0.12,
	 		"TVLeakWeightProduction": 0,
	 		"SVLeakWeightProduction": 0,
	 		"GasInfluenceWeightProduction": 0,
	 		"VolumeWaterCut": 80.2,
	 		"WeightWaterCut": 79.4,
	 		"PumpEff": 56.6,
	 		"PumpEff1": 0.78,
	 		"RodFlexLength": 0.187,
	 		"TubingFlexLength": 0.0373,
	 		"InertiaLength": 0.00853,
	 		"PumpEff2": 0.8,
	 		"PumpEff3": 0.912,
	 		"PumpEff4": 0.977,
	 		"PumpBoreDiameter": 0.032,
	 		"PumpSettingDepth": 1500,
	 		"ProducingfluidLevel": 1280,
	 		"Submergence": 220,
	 		"PumpIntakeP": 0.868,
	 		"PumpIntakeT": 59.88,
	 		"PumpIntakeGOL": 0.943,
	 		"PumpIntakeVisl": 1.01,
	 		"PumpIntakeBo": 1.04,
	 		"PumpOutletP": 11.69,
	 		"PumpOutletT": 59.74,
	 		"PumpOutletGOL": 0,
	 		"PumpOutletVisl": 0.687,
	 		"PumpOutletBo": 1.12,
	 		"ETResultCode": 1202,
	 		"WattDegreeBalance": 102,
	 		"UpStrokeWattMax": 5.6,
	 		"DownStrokeWattMax": 5.49,
	 		"IDegreeBalance": 108,
	 		"UpStrokeIMax": 22.2,
	 		"DownStrokeIMax": 20.56,
	 		"DeltaRadius": -0.1,
	 		"SurfaceSystemEfficiency": 0.343,
	 		"WellDownSystemEfficiency": 0.747,
	 		"SystemEfficiency": 0.36,
	 		"PowerConsumptionPerTHM": 1.5,
	 		"AvgWatt": 4.37,
	 		"PolishRodPower": 1.5,
	 		"WaterPower": 1.12,
	 		"IA": 20.7,
	 		"IB": 21.8,
			"IC": 22.4,
	 		"VA": 380,
	 		"VB": 380,
	 		"VC": 380,
	 		"RunFrequency": 50.5,
	 		"RPM": 0,
	 		"Signal": 18,
	 		"WattSum": 5.7,
	 		"VarSum": 2.4,
	 		"VASum": 8.6,
	 		"PFSum": 0.02
        },
		{
			"AcquisitionTime": "2020-07-01 14:00:00",
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
			"UpperLoadLine": 35.65,
	 		"LowerLoadLine": 21.69,
	 		"UpperLoadLineOfExact": 32.15,
	 		"DeltaLoadLine": 13.96,
	 		"DeltaLoadLineOfExact": 10.46,
	 		"FMax": 39.90,
	 		"FMin": 21.17,
	 		"DeltaF": 18.73,
	 		"Area": 19.21,
	 		"PlungerStroke": 2.25,
	 		"AvailablePlungerStroke": 1.76,
			"FullnessCoefficient": 0.82,
			"TheoreticalProduction": 9.12,
			"LiquidVolumetricProduction": 4.85,
			"OilVolumetricProduction": 1.02,
			"WaterVolumetricProduction": 3.75,
			"AvailablePlungerStrokeVolumetricProduction": 6.78,
	 		"PumpClearanceLeakVolumetricProduction": 0.12,
	 		"TVLeakVolumetricProduction": 0,
	 		"SVLeakVolumetricProduction": 0,
	 		"GasInfluenceVolumetricProduction": 0,
			"LiquidWeightProduction": 4.66,
			"OilWeightProduction": 0.91,
			"WaterWeightProduction": 3.81,
			"AvailablePlungerStrokeWeightProduction": 6.59,
	 		"PumpClearanceLeakWeightProduction": 0.12,
	 		"TVLeakWeightProduction": 0,
	 		"SVLeakWeightProduction": 0,
	 		"GasInfluenceWeightProduction": 0,
			"VolumeWaterCut": 80.2,
			"WeightWaterCut": 79.4,
			"PumpEff": 60,
			"PumpEff1": 0.821,
	 		"RodFlexLength": 0.187,
	 		"TubingFlexLength": 0.0373,
	 		"InertiaLength": 0.00853,
	 		"PumpEff2": 0.82,
	 		"PumpEff3": 0.912,
	 		"PumpEff4": 0.977,
			"PumpBoreDiameter": 0.032,
			"PumpSettingDepth": 1500,
			"ProducingfluidLevel": 1300,
			"Submergence": 200,
			"PumpIntakeP": 0.868,
	 		"PumpIntakeT": 59.88,
	 		"PumpIntakeGOL": 0.943,
	 		"PumpIntakeVisl": 1.01,
	 		"PumpIntakeBo": 1.04,
	 		"PumpOutletP": 11.69,
	 		"PumpOutletT": 59.74,
	 		"PumpOutletGOL": 0,
	 		"PumpOutletVisl": 0.687,
	 		"PumpOutletBo": 1.12,
			"ETResultCode": 1202,
			"WattDegreeBalance": 102,
			"UpStrokeWattMax": 5.42,
	 		"DownStrokeWattMax": 5.31,
			"IDegreeBalance": 104,
			"UpStrokeIMax": 21.7,
	 		"DownStrokeIMax": 20.87,
			"DeltaRadius": -0.2,
			"SurfaceSystemEfficiency": 0.408,
			"WellDownSystemEfficiency": 0.925,
			"SystemEfficiency": 0.377,
			"PowerConsumptionPerTHM": 0.5,
			"AvgWatt": 3.92,
	 		"PolishRodPower": 1.6,
	 		"WaterPower": 1.48,
			"IA": 22.5,
			"IB": 20.2,
			"IC": 21.7,
			"VA": 381.7,
			"VB": 379.2,
			"VC": 380.1,
			"RunFrequency": 50.1,
			"RPM": 0,
			"Signal": 20,
	 		"WattSum": 5.7,
	 		"VarSum": 2.4,
	 		"VASum": 8.6,
	 		"PFSum": 0.02
        },
		{
			"AcquisitionTime": "2020-07-01 20:00:00",
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
			"UpperLoadLine": 35.65,
	 		"LowerLoadLine": 21.69,
	 		"UpperLoadLineOfExact": 32.15,
	 		"DeltaLoadLine": 13.96,
	 		"DeltaLoadLineOfExact": 10.46,
	 		"FMax": 39.90,
	 		"FMin": 21.17,
	 		"DeltaF": 18.73,
	 		"Area": 19.21,
	 		"PlungerStroke": 2.25,
	 		"AvailablePlungerStroke": 1.76,
			"FullnessCoefficient": 0.85,
			"TheoreticalProduction": 9.12,
			"LiquidVolumetricProduction": 4.56,
			"OilVolumetricProduction": 0.91,
			"WaterVolumetricProduction": 3.65,
			"AvailablePlungerStrokeVolumetricProduction": 6.45,
	 		"PumpClearanceLeakVolumetricProduction": 0.12,
	 		"TVLeakVolumetricProduction": 0,
	 		"SVLeakVolumetricProduction": 0,
	 		"GasInfluenceVolumetricProduction": 0,
			"LiquidWeightProduction": 4.46,
			"OilWeightProduction": 0.81,
			"WaterWeightProduction": 3.65,
			"AvailablePlungerStrokeWeightProduction": 6.32,
	 		"PumpClearanceLeakWeightProduction": 0.12,
	 		"TVLeakWeightProduction": 0,
	 		"SVLeakWeightProduction": 0,
	 		"GasInfluenceWeightProduction": 0,
			"VolumeWaterCut": 80.8,
			"WeightWaterCut": 80.8,
			"PumpEff": 56.6,
			"PumpEff1": 0.815,
	 		"RodFlexLength": 0.187,
	 		"TubingFlexLength": 0.0373,
	 		"InertiaLength": 0.00853,
	 		"PumpEff2": 0.78,
	 		"PumpEff3": 0.912,
	 		"PumpEff4": 0.977,
			"PumpBoreDiameter": 0.032,
			"PumpSettingDepth": 1500,
			"ProducingfluidLevel": 1300,
			"Submergence": 200,
			"PumpIntakeP": 0.868,
	 		"PumpIntakeT": 59.88,
	 		"PumpIntakeGOL": 0.943,
	 		"PumpIntakeVisl": 1.01,
	 		"PumpIntakeBo": 1.04,
	 		"PumpOutletP": 11.69,
	 		"PumpOutletT": 59.74,
	 		"PumpOutletGOL": 0,
	 		"PumpOutletVisl": 0.687,
	 		"PumpOutletBo": 1.12,
			"ETResultCode": 1202,
			"WattDegreeBalance": 104,
			"UpStrokeWattMax": 5.6,
	 		"DownStrokeWattMax": 5.49,
			"IDegreeBalance": 105,
			"UpStrokeIMax": 22.2,
	 		"DownStrokeIMax": 20.56,
			"DeltaRadius": -0.2,
			"SurfaceSystemEfficiency": 0.365,
			"WellDownSystemEfficiency": 0.832,
			"SystemEfficiency": 0.304,
			"PowerConsumptionPerTHM": 0.77,
			"AvgWatt": 3.59,
	 		"PolishRodPower": 1.31,
	 		"WaterPower": 1.09,
			"IA": 22.8,
			"IB": 22.1,
			"IC": 23.2,
			"VA": 380.9,
			"VB": 378.2,
			"VC": 378.3,
			"RunFrequency": 50,
			"RPM": 0,
			"Signal": 18,
	 		"WattSum": 5.7,
	 		"VarSum": 2.4,
	 		"VASum": 8.6,
	 		"PFSum": 0.02
        }
    ]
}
```

## 5.2 输出文本

### 5.2.1 输出参数说明

*表5-2 输出参数说明表*

| 代码                                            | 名称                              | 单位       | 类型     | 备注                                 |
|-------------------------------------------------|-----------------------------------|------------|----------|--------------------------------------|
| WellName                                        | 井名                              |            | string   |                                      |
| ResultStatus                                    | 计算结果状态                      |            | int      | 详见表底注释[1]                      |
| **Verification**                                | **数据校验**                      |            |          |                                      |
| ErrorCounter                                    | 错误参数计数器                    |            | int      |                                      |
| ErrorString                                     | 错误参数字符串                    |            | string   |                                      |
| WarningCounter                                  | 报警计数器                        |            | int      |                                      |
| WarningString                                   | 报警字符串                        |            | string   |                                      |
| CommStatus                                      | 通信状态                          |            | int      |                                      |
| CommTime                                        | 在线时间                          |            | float64  |                                      |
| CommTimeEfficiency                              | 在线时率                          |            | float64  |                                      |
| CommRange                                       | 在线区间                          |            | string   |                                      |
| RunStatus                                       | 运行状态                          |            | int      |                                      |
| RunTime                                         | 运行时间                          |            | float64  |                                      |
| RunTimeEfficiency                               | 运行时率                          |            | float64  |                                      |
| RunRange                                        | 运行区间                          |            | string   |                                      |
| StopReason                                      | 停抽原因                          |            | int      |                                      |
| StartReason                                     | 启抽原因                          |            | int      |                                      |
| FSResultCode                                    | 功图工况代码                      |            | int      |                                      |
| FSResultString                                  | 功图工况综合                      |            | string   |                                      |
| ExtendedDays                                    | 功图延用天数                      |            | int      |                                      |
| **Stroke**                                      | **冲程**                          |            |          |                                      |
| Value                                           | 值                                | m          | float64  |                                      |
| Max                                             | 最大值                            | m          | float64  |                                      |
| Min                                             | 最小值                            | m          | float64  |                                      |
| **SPM**                                         | **冲次**                          |            |          |                                      |
| Value                                           | 值                                | 1/min      | float64  |                                      |
| Max                                             | 最大值                            | 1/min      | float64  |                                      |
| Min                                             | 最小值                            | 1/min      | float64  |                                      |
| **TubingPressure**                              | **油压**                          |            |          |                                      |
| Value                                           | 值                                | MPa        | float64  |                                      |
| Max                                             | 最大值                            | MPa        | float64  |                                      |
| Min                                             | 最小值                            | MPa        | float64  |                                      |
| **CasingPressure**                              | **套压**                          |            |          |                                      |
| Value                                           | 值                                | MPa        | float64  |                                      |
| Max                                             | 最大值                            | MPa        | float64  |                                      |
| Min                                             | 最小值                            | MPa        | float64  |                                      |
| **WellHeadFluidTemperature**                    | **井口油温**                     |            |          |                                      |
| Value                                           | 值                                | ℃         | float64  |                                      |
| Max                                             | 最大值                            | ℃         | float64  |                                      |
| Min                                             | 最小值                            | ℃         | float64  |                                      |
| **ProductionGasOilRatio**                       | **生产气油比**                   |            |          |                                      |
| Value                                           | 值                                | m^3/t      | float64  |                                      |
| Max                                             | 最大值                            | m^3/t      | float64  |                                      |
| Min                                             | 最小值                            | m^3/t      | float64  |                                      |
| **UpperLoadLine**                               | **理论上载荷线**                 |            |          |                                      |
| Value                                           | 值                                | kN         | float64  |                                      |
| Max                                             | 最大值                            | kN         | float64  |                                      |
| Min                                             | 最小值                            | kN         | float64  |                                      |
| **LowerLoadLine**                               | **理论下载荷线**                 |            |          |                                      |
| Value                                           | 值                                | kN         | float64  |                                      |
| Max                                             | 最大值                            | kN         | float64  |                                      |
| Min                                             | 最小值                            | kN         | float64  |                                      |
| **UpperLoadLineOfExact**                        | **考虑沉没压力的上载荷线**       |            |          |                                      |
| Value                                           | 值                                | kN         | float64  |                                      |
| Max                                             | 最大值                            | kN         | float64  |                                      |
| Min                                             | 最小值                            | kN         | float64  |                                      |
| **DeltaLoadLine**                               | **理论液柱载荷**                 |            |          |                                      |
| Value                                           | 值                                | kN         | float64  |                                      |
| Max                                             | 最大值                            | kN         | float64  |                                      |
| Min                                             | 最小值                            | kN         | float64  |                                      |
| **DeltaLoadLineOfExact**                        | **考虑沉没压力的理论液柱载荷**  |            |          |                                       |
| Value                                           | 值                               | kN         | float64  |                                       |
| Max                                             | 最大值                           | kN         | float64  |                                       |
| Min                                             | 最小值                           | kN         | float64  |                                       |
| **Fmax**                                        | **最大载荷**                     |            |          |                                       |
| Value                                           | 值                               | kN         | float64  |                                       |
| Max                                             | 最大值                           | kN         | float64  |                                       |
| Min                                             | 最小值                           | kN         | float64  |                                       |
| **Fmin**                                        | **最小载荷**                     |            |          |                                       |
| Value                                           | 值                               | kN         | float64  |                                       |
| Max                                             | 最大值                           | kN         | float64  |                                       |
| Min                                             | 最小值                           | kN         | float64  |                                       |
| **DeltaF**                                      | **载荷差**                       |            |          |                                       |
| Value                                           | 值                               | kN         | float64  |                                       |
| Max                                             | 最大值                           | kN         | float64  |                                       |
| Min                                             | 最小值                           | kN         | float64  |                                       |
| **Area**                                        | **功图面积**                     |            |          |                                       |
| Value                                           | 值                               | kN·m       | float64  |                                       |
| Max                                             | 最大值                           | kN·m       | float64  |                                       |
| Min                                             | 最小值                           | kN·m       | float64  |                                       |
| **PlungerStroke**                               | **柱塞冲程**                     |            |          |                                       |
| Value                                           | 值                               | m          | float64  |                                       |
| Max                                             | 最大值                           | m          | float64  |                                       |
| Min                                             | 最小值                           | m          | float64  |                                       |
| **AvailablePlungerStroke**                      | **柱塞有效冲程**                 |            |          |                                       |
| Value                                           | 值                               | m          | float64  |                                       |
| Max                                             | 最大值                           | m          | float64  |                                       |
| Min                                             | 最小值                           | m          | float64  |                                       |
| **FullnessCoefficient**                         | **充满系数**                     |            |          |                                      |
| Value                                           | 值                               | 小数       | float64  |                                      |
| Max                                             | 最大值                           | 小数       | float64  |                                      |
| Min                                             | 最小值                           | 小数       | float64  |                                      |
| **LiquidVolumetricProduction**                  | **日产液量(方)**                 |            |          |                                      |
| Value                                           | 值                               | m^3/d      | float64  |                                      |
| Max                                             | 最大值                           | m^3/d      | float64  |                                      |
| Min                                             | 最小值                           | m^3/d      | float64  |                                      |
| **OilVolumetricProduction**                     | **日产油量(方)**                 |            |          |                                      |
| Value                                           | 值                               | m^3/d      | float64  |                                      |
| Max                                             | 最大值                           | m^3/d      | float64  |                                      |
| Min                                             | 最小值                           | m^3/d      | float64  |                                      |
| **WaterVolumetricProduction**                   | **日产水量(方)**                 |            |          |                                      |
| Value                                           | 值                               | m^3/d      | float64  |                                      |
| Max                                             | 最大值                           | m^3/d      | float64  |                                      |
| Min                                             | 最小值                           | m^3/d      | float64  |                                      |
| **AvailablePlungerStrokeVolumetricProduction**  | **柱塞有效冲程计算产量(方)**    |            |          |                                     |
| Value                                           | 值                               | m^3/d      | float64  |                                     |
| Max                                             | 最大值                           | m^3/d      | float64  |                                        |
| Min                                             | 最小值                           | m^3/d      | float64  |                                        |
| **PumpClearanceLeakVolumetricProduction**       | **泵间隙漏失量(方)**             |             |          |                                        |
| Value                                           | 值                               | m^3/d      | float64  |                                        |
| Max                                             | 最大值                           | m^3/d      | float64  |                                        |
| Min                                             | 最小值                           | m^3/d      | float64  |                                         |
| **TVLeakVolumetricProduction**                  | **游动凡尔漏失量(方)**           |            |          |                                         |
| Value                                           | 值                               | m^3/d      | float64  |                                         |
| Max                                             | 最大值                           | m^3/d      | float64  |                                         |
| Min                                             | 最小值                           | m^3/d      | float64  |                                         |
| **SVLeakVolumetricProduction**                  | **固定凡尔漏失量(方)**           |            |          |                                         |
| Value                                           | 值                               | m^3/d      | float64  |                                         |
| Max                                             | 最大值                           | m^3/d      | float64  |                                         |
| Min                                             | 最小值                           | m^3/d      | float64  |                                         |
| **GasInfluenceVolumetricProduction**            | **气影响(方)**                   |            |          |                                         |
| Value                                           | 值                               | m^3/d      | float64  |                                         |
| Max                                             | 最大值                           | m^3/d      | float64  |                                         |
| Min                                             | 最小值                           | m^3/d      | float64  |                                         |
| **LiquidWeightProduction**                      | **日产液量(吨)**                 |             |          |                                      |
| Value                                           | 值                               | t/d         | float64  |                                      |
| Max                                             | 最大值                           | t/d         | float64  |                                      |
| Min                                             | 最小值                           | t/d         | float64  |                                      |
| **OilWeightProduction**                         | **日产油量(吨)**                 |             |          |                                      |
| Value                                           | 值                               | t/d         | float64  |                                      |
| Max                                             | 最大值                           | t/d         | float64  |                                      |
| Min                                             | 最小值                           | t/d         | float64  |                                      |
| **WaterWeightProduction**                       | **日产水量(吨)**                 |             |          |                                      |
| Value                                           | 值                               | t/d         | float64  |                                      |
| Max                                             | 最大值                           | t/d         | float64  |                                      |
| Min                                             | 最小值                           | t/d         | float64  |                                      |
| **AvailablePlungerStrokeWeightProduction**      | **柱塞有效冲程计算产量(吨)**    |            |          |                                      |
| Value                                           | 值                               | t/d        | float64  |                                      |
| Max                                             | 最大值                           | t/d        | float64  |                                       |
| Min                                             | 最小值                           | t/d        | float64  |                                       |
| **PumpClearanceLeakWeightProduction**           | **泵间隙漏失量(吨)**             |            |          |                                       |
| Value                                           | 值                               | t/d        | float64  |                                       |
| Max                                             | 最大值                           | t/d        | float64  |                                       |
| Min                                             | 最小值                           | t/d        | float64  |                                       |
| **TVLeakWeightProduction**                      | **游动凡尔漏失量(吨)**           |            |          |                                       |
| Value                                           | 值                               | t/d        | float64  |                                       |
| Max                                             | 最大值                           | t/d        | float64  |                                       |
| Min                                             | 最小值                           | t/d        | float64  |                                       |
| **SVLeakWeightProduction**                      | **固定凡尔漏失量(吨)**           |            |          |                                      |
| Value                                           | 值                               | t/d        | float64  |                                       |
| Max                                             | 最大值                           | t/d        | float64  |                                       |
| Min                                             | 最小值                           | t/d        | float64  |                                       |
| **GasInfluenceWeightProduction**                | **气影响(吨)**                   |            |          |                                       |
| Value                                           | 值                               | t/d        | float64  |                                       |
| Max                                             | 最大值                           | t/d        | float64  |                                       |
| Min                                             | 最小值                           | t/d        | float64  |                                       |
| **VolumeWaterCut**                              | **体积含水率**                   |            |          |                                      |
| Value                                           | 值                               | %          | float64  |                                      |
| Max                                             | 最大值                           | %          | float64  |                                      |
| Min                                             | 最小值                           | %          | float64  |                                      |
| **WeightWaterCut**                              | **重量含水率**                   |            |          |                                      |
| Value                                           | 值                               | %          | float64  |                                      |
| Max                                             | 最大值                           | %          | float64  |                                      |
| Min                                             | 最小值                           | %          | float64  |                                      |
| **PumpEff**                                     | **泵效**                         |            |          |                                      |
| Value                                           | 值                               | %          | float64  |                                      |
| Max                                             | 最大值                           | %          | float64  |                                      |
| Min                                             | 最小值                           | %          | float64  |                                      |
| **PumpEff1**                                    | **冲程损失系数**                 |            |          |                                    |
| Value                                           | 值                               | %          | float64  |                                      |
| Max                                             | 最大值                           | %          | float64  |                                       |
| Min                                             | 最小值                           | %          | float64  |                                       |
| **RodFlexLength**                               | **抽油杆伸长量**                 |            |          |                                       |
| Value                                           | 值                               | m          | float64  |                                       |
| Max                                             | 最大值                           | m          | float64  |                                        |
| Min                                             | 最小值                           | m          | float64  |                                        |
| **TubingFlexLength**                            | **计算油管伸缩值**              |            |          |                                        |
| Value                                           | 值                               | m          | float64  |                                       |
| Max                                             | 最大值                           | m          | float64  |                                       |
| Min                                             | 最小值                           | m          | float64  |                                      |
| **InertiaLength**                               | **惯性载荷下冲程增量**          |            |          |                                        |
| Value                                           | 值                               | m          | float64  |                                        |
| Max                                             | 最大值                           | m          | float64  |                                        |
| Min                                             | 最小值                           | m          | float64  |                                        |
| **PumpEff2**                                    | **充满系数**                     |            |          |                                       |
| Value                                           | 值                               | %          | float64  |                                        |
| Max                                             | 最大值                           | %          | float64  |                                        |
| Min                                             | 最小值                           | %          | float64  |                                        |
| **PumpEff3**                                    | **间隙漏失系数**                 |            |          |                                        |
| Value                                           | 值                               | %          | float64  |                                        |
| Max                                             | 最大值                           | %          | float64  |                                        |
| Min                                             | 最小值                           | %          | float64  |                                        |
| **PumpEff4**                                    | **液体收缩系数**                 |            |          |                                       |
| Value                                           | 值                               | %          | float64  |                                       |
| Max                                             | 最大值                           | %          | float64  |                                       |
| Min                                             | 最小值                           | %          | float64  |                                       |
| **PumpBoreDiameter**                            | **泵径**                         |            |          |                                      |
| Value                                           | 值                               | m          | float64  |                                      |
| Max                                             | 最大值                           | m          | float64  |                                      |
| Min                                             | 最小值                           | m          | float64  |                                      |
| **PumpSettingDepth**                            | **泵挂**                         |            |          |                                      |
| Value                                           | 值                               | m          | float64  |                                      |
| Max                                             | 最大值                           | m          | float64  |                                      |
| Min                                             | 最小值                           | m          | float64  |                                      |
| **ProducingfluidLevel**                         | **动液面**                       |            |          |                                      |
| Value                                           | 值                               | m          | float64  |                                      |
| Max                                             | 最大值                           | m          | float64  |                                      |
| Min                                             | 最小值                           | m          | float64  |                                      |
| **Submergence**                                 | **沉没度**                       |            |          |                                      |
| Value                                           | 值                               | m          | float64  |                                      |
| Max                                             | 最大值                           | m          | float64  |                                      |
| Min                                             | 最小值                           | m          | float64  |                                      |
| **PumpIntakeP**                                 | **泵入口压力**                   |            |          |                                     |
| Value                                           | 值                               | MPa        | float64  |                                       |
| Max                                             | 最大值                           | MPa        | float64  |                                       |
| Min                                             | 最小值                           | MPa        | float64  |                                        |
| **PumpIntakeT**                                 | **泵入口温度**                   |            |          |                                      |
| Value                                           | 值                               | ℃          | float64  |                                       |
| Max                                             | 最大值                           | ℃          | float64  |                                       |
| Min                                             | 最小值                           | ℃          | float64  |                                       |
| **PumpIntakeGOL**                               | **泵入口就地气液比**             |            |          |                                       |
| Value                                           | 值                               |            | float64  |                                       |
| Max                                             | 最大值                           |            | float64  |                                       |
| Min                                             | 最小值                           |            | float64  |                                       |
| **PumpIntakeVisl**                              | **泵入口粘度**                   |            |          |                                      |
| Value                                           | 值                               | mPa·s      | float64  |                                       |
| Max                                             | 最大值                           | mPa·s      | float64  |                                       |
| Min                                             | 最小值                           | mPa·s      | float64  |                                       |
| **PumpIntakeBo**                                | **泵入口原油体积系数**           |            |          |                                       |
| Value                                           | 值                               |            | float64  |                                      |
| Max                                             | 最大值                           |            | float64  |                                       |
| Min                                             | 最小值                           |            | float64  |                                       |
| **PumpOutletP**                                 | **泵出口压力**                   |            |          |                                      |
| Value                                           | 值                               | MPa        | float64  |                                      |
| Max                                             | 最大值                           | MPa        | float64  |                                      |
| Min                                             | 最小值                           | MPa        | float64  |                                      |
| **PumpOutletT**                                 | **泵出口温度**                   |            |          |                                     |
| Value                                           | 值                               | ℃          | float64  |                                     |
| Max                                             | 最大值                           | ℃          | float64  |                                      |
| Min                                             | 最小值                           | ℃          | float64  |                                      |
| **PumpOutletGOL**                               | **泵出口就地气液比**             |            |          |                                      |
| Value                                           | 值                               |            | float64  |                                      |
| Max                                             | 最大值                           |            | float64  |                                      |
| Min                                             | 最小值                           |            | float64  |                                      |
| **PumpOutletVisl**                              | **泵出口粘度**                   |            |          |                                     |
| Value                                           | 值                               | mPa·s      | float64  |                                      |
| Max                                             | 最大值                           | mPa·s      | float64  |                                      |
| Min                                             | 最小值                           | mPa·s      | float64  |                                      |
| **PumpOutletBo**                                | **泵出口原油体积系数**           |            |          |                                      |
| Value                                           | 值                               |            | float64  |                                      |
| Max                                             | 最大值                           |            | float64  |                                      |
| Min                                             | 最小值                           |            | float64  |                                     |
| ETResultCode                                    | 电参工况代码                     |            | int      |                                      |
| ETResultString                                  | 电参工况综合                     |            | string   |                                      |
| **WattDegreeBalance**                           | **功率平衡度**                   |            |          |                                      |
| Value                                           | 值                               | %          | float64  |                                      |
| Max                                             | 最大值                           | %          | float64  |                                      |
| Min                                             | 最小值                           | %          | float64  |                                      |
| **UpStrokeWattMax**                             | **上冲程功率最大值**             |            |          |                                     |
| Value                                           | 值                               | kW         | float64  |                                      |
| Max                                             | 最大值                           | kW         | float64  |                                       |
| Min                                             | 最小值                           | kW         | float64  |                                       |
| **DownStrokeWattMax**                           | **下冲程功率最大值**             |            |          |                                       |
| Value                                           | 值                               | kW         | float64  |                                       |
| Max                                             | 最大值                           | kW         | float64  |                                       |
| Min                                             | 最小值                           | kW         | float64  |                                       |
| **IdegreeBalance**                              | **电流平衡度**                   |            |          |                                      |
| Value                                           | 值                               | %          | float64  |                                      |
| Max                                             | 最大值                           | %          | float64  |                                      |
| Min                                             | 最小值                           | %          | float64  |                                      |
| **UpStrokeIMax**                                | **上冲程电流最大值**             |            |          |                                     |
| Value                                           | 值                               | A          | float64  |                                      |
| Max                                             | 最大值                           | A          | float64  |                                      |
| Min                                             | 最小值                           | A          | float64  |                                      |
| **DownStrokeIMax**                              | **下冲程电流最大值**             |            |          |                                     |
| Value                                           | 值                               | A          | float64  |                                      |
| Max                                             | 最大值                           | A          | float64  |                                      |
| Min                                             | 最小值                           | A          | float64  |                                      |
| **DeltaRadius**                                 | **移动距离**                     |            |          |                                      |
| Value                                           | 值                               | m          | float64  | + 代表向外移 -代表向内移             |
| Max                                             | 最大值                           | m          | float64  | + 代表向外移 -代表向内移             |
| Min                                             | 最小值                           | m          | float64  | + 代表向外移 -代表向内移             |
| **SurfaceSystemEfficiency**                     | **地面效率**                     |            |          |                                      |
| Value                                           | 值                               | 小数       | float64  |                                      |
| Max                                             | 最大值                           | 小数       | float64  |                                      |
| Min                                             | 最小值                           | 小数       | float64  |                                      |
| **WellDownSystemEfficiency**                    | **井下效率**                     |            |          |                                      |
| Value                                           | 值                               | 小数       | float64  |                                      |
| Max                                             | 最大值                           | 小数       | float64  |                                      |
| Min                                             | 最小值                           | 小数       | float64  |                                      |
| **SystemEfficiency**                            | **系统效率**                     |            |          |                                      |
| Value                                           | 值                               | 小数       | float64  |                                      |
| Max                                             | 最大值                           | 小数       | float64  |                                      |
| Min                                             | 最小值                           | 小数       | float64  |                                      |
| **PowerConsumptionPerTHM**                      | **吨液百米耗电量**               |            |          |                                      |
| Value                                           | 值                               | kW·h/100·t | float64  |                                      |
| Max                                             | 最大值                           | kW·h/100·t | float64  |                                      |
| Min                                             | 最小值                           | kW·h/100·t | float64  |                                      |
| **AvgWatt**                                     | **平均有功功率**                 |            |          |                                   |
| Value                                           | 值                               | kW         | float64  |                                     |
| Max                                             | 最大值                           | kW         | float64  |                                      |
| Min                                             | 最小值                           | kW         | float64  |                                       |
| **PolishRodPower**                              | **光杆功率**                     |            |          |                                      |
| Value                                           | 值                               | kW         | float64  |                                      |
| Max                                             | 最大值                           | kW         | float64  |                                      |
| Min                                             | 最小值                           | kW         | float64  |                                       |
| **WaterPower**                                  | **水功率**                       |            |          |                                     |
| Value                                           | 值                               | kW         | float64  |                                      |
| Max                                             | 最大值                           | kW         | float64  |                                      |
| Min                                             | 最小值                           | kW         | float64  |                                       |
| **IA**                                          | **A相电流**                      |            |          |                                      |
| Value                                           | 值                               | A          | float64  |                                      |
| Max                                             | 最大值                           | A          | float64  |                                      |
| Min                                             | 最小值                           | A          | float64  |                                      |
| **IB**                                          | **B相电流**                      |            |          |                                      |
| Value                                           | 值                               | A          | float64  |                                      |
| Max                                             | 最大值                           | A          | float64  |                                      |
| Min                                             | 最小值                           | A          | float64  |                                      |
| **IC**                                          | **C相电流**                      |            |          |                                      |
| Value                                           | 值                               | A          | float64  |                                      |
| Max                                             | 最大值                           | A          | float64  |                                      |
| Min                                             | 最小值                           | A          | float64  |                                      |
| IMaxString                                      | 电流最大值字符串                 | A          | string   |                                      |
| IMinString                                      | 电流最小值字符串                 | A          | string   |                                      |
| **VA**                                          | **A相电压**                      |            |          |                                      |
| Value                                           | 值                               | V          | float64  |                                      |
| Max                                             | 最大值                           | V          | float64  |                                      |
| Min                                             | 最小值                           | V          | float64  |                                      |
| **VB**                                          | **B相电压**                      |            |          |                                      |
| Value                                           | 值                               | V          | float64  |                                      |
| Max                                             | 最大值                           | V          | float64  |                                      |
| Min                                             | 最小值                           | V          | float64  |                                      |
| **VC**                                          | **C相电压**                      |            |          |                                      |
| Value                                           | 值                               | V          | float64  |                                      |
| Max                                             | 最大值                           | V          | float64  |                                      |
| Min                                             | 最小值                           | V          | float64  |                                      |
| VMaxString                                      | 电压最大值字符串                 | V          | string   |                                      |
| VMinString                                      | 电压最小值字符串                 | V          | string   |                                      |
| **RunFrequency**                                | **频率**                         |            |          |                                      |
| Value                                           | 值                               | HZ         | float64  |                                      |
| Max                                             | 最大值                           | HZ         | float64  |                                      |
| Min                                             | 最小值                           | HZ         | float64  |                                      |
| **RPM**                                         | **转速**                         |            |          |                                      |
| Value                                           | 值                               | r/min      | float64  |                                      |
| Max                                             | 最大值                           | r/min      | float64  |                                      |
| Min                                             | 最小值                           | r/min      | float64  |                                      |
| **Signal**                                      | **信号强度**                     |            |          |                                     |
| Value                                           | 值                               |            | float64  |                                       |
| Max                                             | 最大值                           |            | float64  |                                       |
| Min                                             | 最小值                           |            | float64  |                                       |
| **WattSum**                                     | **有功功率**                     |            |          |                                       |
| Value                                           | 值                               | kW         | float64  |                                       |
| Max                                             | 最大值                           | kW         | float64  |                                      |
| Min                                             | 最小值                           | kW         | float64  |                                       |
| **VarSum**                                      | **无功功率**                     |            |          |                                      |
| Value                                           | 值                               | kVar       | float64  |                                      |
| Max                                             | 最大值                           | kVar       | float64  |                                       |
| Min                                             | 最小值                           | kVar       | float64  |                                       |
| **VASum**                                       | **视在功率**                     |            |          |                                       |
| Value                                           | 值                               | kVA        | float64  |                                      |
| Max                                             | 最大值                           | kVA        | float64  |                                      |
| Min                                             | 最小值                           | kVA        | float64  |                                      |
| **PFSum**                                       | **功率因数**                     |            |          |                                       |
| Value                                           | 值                               | 小数       | float64  |                                       |
| Max                                             | 最大值                           | 小数       | float64  |                                       |
| Min                                             | 最小值                           | 小数       | float64  |                                       |

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
    "CommRange": "00: 00-21: 00",
    "RunStatus": 1,
    "RunTime": 21,
    "RunTimeEfficiency": 0.875,
    "RunRange": "00: 00-21: 00",
    "StopReason": 1,
    "StartReason": 1,
    "TubingPressure": {
        "Value": 1.6,
        "Max": 2.1,
        "Min": 1.5
    },
    "CasingPressure": {
        "Value": 1.62,
        "Max": 2.2,
        "Min": 1.5
    },
    "WellHeadFluidTemperature": {
        "Value": 17.5,
        "Max": 30,
        "Min": 15
    },
    "ProductionGasOilRatio": {
        "Value": 58.33,
        "Max": 75,
        "Min": 55
    },
    "FSResultCode": 1202,
    "FSResultString": "20: 00: 00  正常",
    "ExtendedDays": 0,
    "Stroke": {
        "Value": 2.52,
        "Max": 2.6,
        "Min": 2.5
    },
    "SPM": {
        "Value": 4.1,
        "Max": 4.1,
        "Min": 4.1
    },
    "UpperLoadLine": {
        "Value": 35.65,
        "Max": 35.65,
        "Min": 35.65
    },
    "LowerLoadLine": {
        "Value": 21.69,
        "Max": 21.69,
        "Min": 21.69
    },
    "UpperLoadLineOfExact": {
        "Value": 32.15,
        "Max": 32.15,
        "Min": 32.15
    },
    "DeltaLoadLine": {
        "Value": 13.96,
        "Max": 13.96,
        "Min": 13.96
    },
    "DeltaLoadLineOfExact": {
        "Value": 10.46,
        "Max": 10.46,
        "Min": 10.46
    },
    "FMax": {
        "Value": 39.9,
        "Max": 39.9,
        "Min": 39.9
    },
    "FMin": {
        "Value": 21.17,
        "Max": 21.17,
        "Min": 21.17
    },
    "DeltaF": {
        "Value": 18.73,
        "Max": 18.73,
        "Min": 18.73
    },
    "Area": {
        "Value": 19.21,
        "Max": 19.21,
        "Min": 19.21
    },
    "PlungerStroke": {
        "Value": 2.25,
        "Max": 2.25,
        "Min": 2.25
    },
    "AvailablePlungerStroke": {
        "Value": 1.76,
        "Max": 1.76,
        "Min": 1.76
    },
    "FullnessCoefficient": {
        "Value": 0.785,
        "Max": 0.85,
        "Min": 0.78
    },
    "TheoreticalProduction": {
        "Value": 9.12,
        "Max": 9.12,
        "Min": 9.12
    },
    "LiquidVolumetricProduction": {
        "Value": 5.09,
        "Max": 5.25,
        "Min": 3.99
    },
    "OilVolumetricProduction": {
        "Value": 1.01,
        "Max": 1.05,
        "Min": 0.796
    },
    "WaterVolumetricProduction": {
        "Value": 4.08,
        "Max": 4.2,
        "Min": 3.19
    },
    "AvailablePlungerStrokeVolumetricProduction": {
        "Value": 5.7,
        "Max": 5.93,
        "Min": 5.64
    },
    "PumpClearanceLeakVolumetricProduction": {
        "Value": 0.105,
        "Max": 0.105,
        "Min": 0.105
    },
    "TVLeakVolumetricProduction": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "SVLeakVolumetricProduction": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "GasInfluenceVolumetricProduction": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "LiquidWeightProduction": {
        "Value": 4.97,
        "Max": 5.14,
        "Min": 3.9
    },
    "OilWeightProduction": {
        "Value": 1.03,
        "Max": 1.05,
        "Min": 0.709
    },
    "WaterWeightProduction": {
        "Value": 3.94,
        "Max": 4.2,
        "Min": 3.19
    },
    "AvailablePlungerStrokeWeightProduction": {
        "Value": 5.58,
        "Max": 5.77,
        "Min": 5.53
    },
    "PumpClearanceLeakWeightProduction": {
        "Value": 0.105,
        "Max": 0.105,
        "Min": 0.105
    },
    "TVLeakWeightProduction": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "SVLeakWeightProduction": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "GasInfluenceWeightProduction": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "VolumeWaterCut": {
        "Value": 80.17,
        "Max": 80.8,
        "Min": 80.2
    },
    "WeightWaterCut": {
        "Value": 79.34,
        "Max": 80.8,
        "Min": 79.4
    },
    "PumpEff": {
        "Value": 57.31,
        "Max": 60,
        "Min": 56.6
    },
    "PumpEff1": {
        "Value": 0.787,
        "Max": 0.821,
        "Min": 0.78
    },
    "RodFlexLength": {
        "Value": 0.187,
        "Max": 0.187,
        "Min": 0.187
    },
    "TubingFlexLength": {
        "Value": 0.0373,
        "Max": 0.0373,
        "Min": 0.0373
    },
    "InertiaLength": {
        "Value": 0.00853,
        "Max": 0.00853,
        "Min": 0.00853
    },
    "PumpEff2": {
        "Value": 0.805,
        "Max": 0.82,
        "Min": 0.78
    },
    "PumpEff3": {
        "Value": 0.912,
        "Max": 0.912,
        "Min": 0.912
    },
    "PumpEff4": {
        "Value": 0.977,
        "Max": 0.977,
        "Min": 0.977
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
        "Value": 1283.33,
        "Max": 1300,
        "Min": 1280
    },
    "Submergence": {
        "Value": 216.67,
        "Max": 220,
        "Min": 200
    },
    "PumpIntakeP": {
        "Value": 0.868,
        "Max": 0.868,
        "Min": 0.868
    },
    "PumpIntakeT": {
        "Value": 59.88,
        "Max": 59.88,
        "Min": 59.88
    },
    "PumpIntakeGOL": {
        "Value": 0.943,
        "Max": 0.943,
        "Min": 0.943
    },
    "PumpIntakeVisl": {
        "Value": 1.01,
        "Max": 1.01,
        "Min": 1.01
    },
    "PumpIntakeBo": {
        "Value": 1.04,
        "Max": 1.04,
        "Min": 1.04
    },
    "PumpOutletP": {
        "Value": 11.69,
        "Max": 11.69,
        "Min": 11.69
    },
    "PumpOutletT": {
        "Value": 59.74,
        "Max": 59.74,
        "Min": 59.74
    },
    "PumpOutletGOL": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "PumpOutletVisl": {
        "Value": 0.687,
        "Max": 0.687,
        "Min": 0.687
    },
    "PumpOutletBo": {
        "Value": 1.12,
        "Max": 1.12,
        "Min": 1.12
    },
    "ETResultCode": 1202,
    "ETResultString": "20: 00: 00  正常",
    "WattDegreeBalance": {
        "Value": 101.92,
        "Max": 104,
        "Min": 102
    },
    "UpStrokeWattMax": {
        "Value": 5.56,
        "Max": 5.6,
        "Min": 5.42
    },
    "DownStrokeWattMax": {
        "Value": 5.45,
        "Max": 5.49,
        "Min": 5.31
    },
    "IDegreeBalance": {
        "Value": 107.29,
        "Max": 108,
        "Min": 104
    },
    "UpStrokeIMax": {
        "Value": 22.1,
        "Max": 22.2,
        "Min": 21.7
    },
    "DownStrokeIMax": {
        "Value": 20.62,
        "Max": 20.87,
        "Min": 20.56
    },
    "DeltaRadius": {
        "Value": -0.117,
        "Max": -0.1,
        "Min": -0.2
    },
    "SurfaceSystemEfficiency": {
        "Value": 0.356,
        "Max": 0.408,
        "Min": 0.343
    },
    "WellDownSystemEfficiency": {
        "Value": 0.781,
        "Max": 0.925,
        "Min": 0.747
    },
    "SystemEfficiency": {
        "Value": 0.278,
        "Max": 0.377,
        "Min": 0.304
    },
    "PowerConsumptionPerTHM": {
        "Value": 1.32,
        "Max": 1.5,
        "Min": 0.5
    },
    "AvgWatt": {
        "Value": 4.31,
        "Max": 4.37,
        "Min": 3.59
    },
    "PolishRodPower": {
        "Value": 1.53,
        "Max": 1.6,
        "Min": 1.31
    },
    "WaterPower": {
        "Value": 1.2,
        "Max": 1.48,
        "Min": 1.09
    },
    "IA": {
        "Value": 20.99,
        "Max": 22.8,
        "Min": 20.7
    },
    "IB": {
        "Value": 21.45,
        "Max": 22.1,
        "Min": 20.2
    },
    "IC": {
        "Value": 22.22,
        "Max": 23.2,
        "Min": 21.7
    },
    "IMaxString": "22.80/22.10/23.20",
    "IMinString": "20.70/20.20/21.70",
    "VA": {
        "Value": 380.32,
        "Max": 381.7,
        "Min": 380
    },
    "VB": {
        "Value": 379.91,
        "Max": 380,
        "Min": 378.2
    },
    "VC": {
        "Value": 380.09,
        "Max": 380.1,
        "Min": 378.3
    },
    "VMaxString": "381.70/380.00/380.10",
    "VMinString": "380.00/378.20/378.30",
    "RunFrequency": {
        "Value": 50.44,
        "Max": 50.5,
        "Min": 50
    },
    "RPM": {
        "Value": 0,
        "Max": 0,
        "Min": 0
    },
    "Signal": {
        "Value": 18.42,
        "Max": 20,
        "Min": 18
    },
    "WattSum": {
        "Value": 5.7,
        "Max": 5.7,
        "Min": 5.7
    },
    "VarSum": {
        "Value": 2.4,
        "Max": 2.4,
        "Min": 2.4
    },
    "VASum": {
        "Value": 8.6,
        "Max": 8.6,
        "Min": 8.6
    },
    "PFSum": {
        "Value": 0.02,
        "Max": 0.02,
        "Min": 0.02
    }
}
```

----[第四章 通信计算](.././Chapter4/Chapter4.md)----[返回章节目录](.././README.md)----[第六章 插件](.././Chapter6/Chapter6.md)----