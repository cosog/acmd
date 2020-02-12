# 第二章 功图诊断&计产

- [第二章 功图诊断&计产](Chapter2.md#第二章-功图诊断计产)
   - [2.1 输入文本（完整版）](Chapter2.md#21-输入文本完整版)
     - [2.1.1 输入参数说明](Chapter2.md#211-输入参数说明)
     - [2.1.2 输入实例（无尾管）](Chapter2.md#212-输入实例无尾管)
     - [2.1.3 输入实例（有尾管、滤管）](Chapter2.md#213-输入实例有尾管滤管)
     - [2.1.4 数据收集表](Chapter2.md#214-数据收集表)
        - [2.1.4.1 油井数据收集表](Chapter2.md#2141-油井数据收集表)
        - [2.1.4.2 煤层气井数据收集表](Chapter2.md#2142-煤层气井数据收集表)
   - [2.2 输出文本（完整版）](Chapter2.md#22-输出文本完整版)
     - [2.2.1 输出参数说明](Chapter2.md#221-输出参数说明)
     - [2.2.2 输出实例](Chapter2.md#222-输出实例)
     - [2.2.3 工况类型代码](Chapter2.md#223-工况类型代码)
   - [2.3 输入文本（精简版）](Chapter2.md#23-输入文本精简版)
     - [2.3.1 输入参数说明](Chapter2.md#231-输入参数说明)
     - [2.3.2 输入实例](Chapter2.md#232-输入实例)
   - [2.4 输出文本（精简版）](Chapter2.md#24-输出文本精简版)
     - [2.4.1 输出参数说明](Chapter2.md#241-输出参数说明)
     - [2.4.2 输出实例](Chapter2.md#242-输出实例)
     - [2.4.3 工况类型代码](Chapter2.md#243-工况类型代码)

## 2.1 输入文本(完整版)

### 2.1.1 输入参数说明

*表2-1 输入参数说明表*

| 代码                                | 名称                    | 单位      | 类型     | 必填     | 备注                                    |
|-------------------------------------|-------------------------|-----------|----------|----------|-----------------------------------------|
| AKString                            | 应用密钥                |           | string   |          | 预留字段                                |
| WellName                            | 井名                    |           | string   | *        |                                         |
| **FluidPVT**                        | **流体PVT物性**         |           |          |          |                                         |
| CrudeOilDensity                     | 原油密度                | g/cm\^3   | float64  | *        | 煤层气井不填写                          |
| WaterDensity                        | 水密度                  | g/cm\^3   | float64  | *        |                                         |
| NaturalGasRelativeDensity           | 天然气相对密度          |           | float64  | *        |                                         |
| SaturationPressure                  | 饱和压力                | MPa       | float64  | *        | 煤层气井不填写                          |
| **Reservoir**                       | **油气藏物性**          |           |          |          |                                         |
| Depth                               | 油气藏深度              | m         | float64  | *        | 油气藏中部（测量）深度                  |
| Temperature                         | 油气藏温度              | ℃        | float64  | *        | 油气藏中部温度                          |
| **WellboreTrajectory**              | **井身轨迹**            |           |          |          |                                         |
| MeasuringDepth                      | 测量深度                | m         | float64  |          | 如直井可不填写，非直井按 实际数据填写   |
| VerticalDepth                       | 垂直深度                | m         | float64  |          |                                         |
| DeviationAngle                      | 井斜角                  | °         | float64  |          |                                         |
| AzimuthAngle                        | 方位角                  | °         | float64  |          |                                         |
| **RodString**                       | **抽油杆参数**          |           |          |          |                                         |
| Type                                | 抽油杆类型              |           | int      |          | 1-实心抽油杆，2-空心抽油杆              |
| Grade                               | 杆级别                  |           | string   | *        | A，B，C，K，D，KD，HL，HY               |
| Length                              | 杆长                    | m         | float64  | *        | 不包含光杆和泵上拉杆                    |
| OutsideDiameter                     | 杆外径                  | m         | float64  | *        |                                         |
| InsideDiameter                      | 杆内径                  | m         | float64  |          | 为空心抽油杆预留                        |
| Density                             | 杆密度                  | g/cm\^3   | float64  |          | 默认值为7.85                            |
| WeightPerMeter                      | 每米杆重                | kN/m      | float64  |          | 杆重（含节箍）                          |
| **TubingString**                    | **油管参数**            |           |          |          |                                         |
| Grade                               | 油管钢级                |           | string   |          | 详见表底注释[1]                         |
| OutsideDiameter                     | 油管外径                | m         | float64  |          |                                         |
| InsideDiameter                      | 油管内径                | m         | float64  | *        | 默认0.062m                              |
| Length                              | 油管长度                | m         | float64  |          |                                         |
| Density                             | 油管密度                | g/cm\^3   | float64  |          |                                         |
| WeightPerMeter                      | 每米管重                | kN/m      | float64  |          |                                         |
| **Pump**                            | **抽油泵参数**          |           |          |          |                                         |
| PumpType                            | 泵类型                  |           | string   |          | R-杆式泵 T-管式泵                       |
| BarrelType                          | 泵筒类型                |           | string   |          | 详见表底注释[2]                         |
| PumpGrade                           | 泵级别                  |           | int      |          | 详见表底注释[3]                         |
| BarrelLength                        | 泵筒长                  | m         | float64  |          |                                         |
| PlungerLength                       | 柱塞长                  | m         | float64  |          | 默认1.2m                                |
| PumpBoreDiameter                    | 泵径                    | m         | float64  | *        | 详见表底注释[4]                         |
| Clearance                           | 柱塞与缸套配合单边间隙  | m         | float64  |          | 组合泵默认按1级间隙,整筒泵默认按2级间隙 |
| AntiImpactStroke                    | 防冲距                  | m         | float64  |          | 默认值取0.1                             |
| **TailTubingString**                | **尾管参数**            |           |          |          |                                         |
| EquipmentType                       | 设备类型                |           | string   |          | 详见表底注释[4]                         |
| Grade                               | 尾管钢级                |           | string   |          | 详见表底注释[1]                         |
| OutsideDiameter                     | 尾管外径                | m         | float64  |          |                                         |
| InsideDiameter                      | 尾管内径                | m         | float64  |          |                                         |
| Length                              | 尾管长度                | m         | float64  |          |                                         |
| Density                             | 尾管密度                | g/cm\^3   | float64  |          |                                         |
| WeightPerMeter                      | 每米管重                | kN/m      | float64  |          |                                         |
| GasAnchorEfficiency                 | 气锚效率                | 小数      | float64  |          | 无气锚填0                               |
| **CasingString**                    | **生产套管参数**        |           |          |          |                                         |
| Grade                               | 套管钢级                |           | string   |          | 详见表底注释[1]                         |
| OutsideDiameter                     | 套管外径                | m         | float64  |          |                                         |
| InsideDiameter                      | 套管内径                | m         | float64  | *        | 默认0.127m                              |
| Length                              | 套管长度                | m         | float64  |          |                                         |
| Density                             | 套管密度                | g/cm\^3   | float64  |          |                                         |
| WeightPerMeter                      | 每米管重                | kN/m      | float64  |          |                                         |
| **ProductionParameter**             | **生产数据**            |           |          |          |                                         |
| WaterCut                            | 体积含水率              | %         | float64  | *        | 煤层气井填100                           |
| ProductionGasOilRatio               | 生产气油比              | m\^3/m\^3 | float64  | *        | 煤层气井不填                            |
| TubingPressure                      | 油压（回压）            | MPa       | float64  | *        | 如无油压，可录入回压                    |
| CasingPressure                      | 套压                    | MPa       | float64  | *        |                                         |
| WellHeadFluidTemperature            | 井口油温                | ℃        | float64  |          |                                         |
| ProducingfluidLevel                 | 动液面                  | m         | float64  | *        |                                         |
| PumpSettingDepth                    | 泵挂                    | m         | float64  | *        |                                         |
| Submergence                         | 沉没度                  | m         | float64  |          |                                         |
| **FSDiagram**                       | **功图数据**            |           |          |          |                                         |
| AcquisitionTime                     | 采集时间                |           | string   |          | "YYYY-MM-DD HH:NN:SS"                    |
| Stroke                              | 冲程                    | m         | float64  |          |                                         |
| SPM                                 | 冲次                    | 1/min     | float64  | *        |                                         |
| F                                   | 载荷                    | kN        | float64  | *        |                                         |
| S                                   | 位移                    | m         | float64  | *        |                                         |
| P                                   | 三相总有功功率          | kW        | float64  |          |                                         |
| A                                   | 三相平均电流            | A         | float64  |          |                                         |
| **SystemEfficiency**                | **系统效率**            |           |          |          |                                         |
| MotorInputActivePower               | 电机输入有功功率        | kW        | float64  |          | 用于计算系统效率                        |
| **ManualIntervention**              | **人工干预**            |           |          |          |                                         |
| Code                                | 人工干预                |           | int      |          | 0-不干预，其他工况类型-干预             |
| NetGrossRatio                       | 净毛比                  | 小数      | float64  |          | 实际产量/软件计算产量，默认1            |

**[1]** *钢级:H40,J55,K55,N80,M65,L80,C90,C95,T59,P110,Q125*  
**[2]** *泵筒类型:H-厚壁筒,用于金属柱塞; W-薄壁筒,用于金属柱塞; L-组合泵筒,用于金属柱塞; P-厚壁筒,用于软密封柱塞; S-薄壁筒,用于软密封柱塞; X-厚壁筒,用于金属柱塞,薄壁形螺纹构形*  
**[3]** *泵类型:整筒泵：1-一级泵 2-二级泵 3-三级泵 4-四级泵 5-五级泵 组合泵：1-一级泵 2-二级泵 3-三级泵*  
**[4]** *泵径:组合泵筒：0.028，0.032，0.038，0.044，0.051，0.057，0.063，0.070，0.083，0.095 整筒泵：0.02699，0.0318，0.0381，0.0445，0.0452， 0.0508，0.0572，0.0635，0.0699，0.0953*  
**[5]** *尾管设备类型:TailTubing-尾管，FilterTubing-滤管（花管），Anchor-锚定器，GasAnchor-油气分离器*


### 2.1.2 输入实例（无尾管）

```
{
	"AKString": "",                   //（1） 应用密钥
	"WellName": "1-1",                //（2） 井名
	"FluidPVT": {                     //（3） 流体PVT物性
		"CrudeOilDensity": 0.86,
		"WaterDensity": 1,
		"NaturalGasRelativeDensity": 0.7,
		"SaturationPressure": 9.6
	},
	"Reservoir": {                    //（4） 油气藏物性 
		"Depth": 1350,
		"Temperature": 66
	},
	"WellboreTrajectory": {           //（5） 井身轨迹，各项参数按顺序依次输入
		"MeasuringDepth": [
			100,
			200
				],
		"VerticalDepth": [
			100,
			200
			],
		"DeviationAngle": [
			0,
			0
			],
		"AzimuthAngle": [
			0,
			0
			]
	},

	"RodString": {                    //（6）抽油杆参数，每级杆柱参数对应一组结构体，多级杆柱按结构体依次输入
		"EveryRod": [
			{
				"Type": 1,
				"Grade": “D”,
				"Length": 329.86,
				"OutsideDiameter": 0.022,
				"InsideDiameter": 0,
				"Density": 7.85,
				"WeightPerMeter": 0
				},
			{
				"Type": 1,
				"Grade": “D”,
				"Length": 668.52,
				"OutsideDiameter": 0.019,
				"InsideDiameter": 0,
				"Density": 7.85,
				"WeightPerMeter": 0
				}
				]
	},
	"TubingString": {                //（7） 油管参数，多级油管按结构体依次输入
		"EveryTubing": [
			{
				"Grade": "K55",
				"length": 1000,
				"OutsideDiameter": 0.073,
				"InsideDiameter": 0.062,
				"Density": 7.85,
				"WeightPerMeter": 0
				}
				]
	},
	"Pump": {                        //（8） 泵参数
		"PumpType ": ”T”,
		"BarrelType": “L”,
		"PumpGrade": 1,
		"BarrelLength": 8,
		"PlungerLength": 1.3,
		"PumpBoreDiameter": 0.044,
		"Clearance": 0.00002,
		"AntiImpactStroke": 0.1
	},
	"CasingString": {                //（9） 套管参数，多级套管按结构体依次输入
		"EveryCasing": [
			{
				"Grade": "K55",
				"OutsideDiameter": 0.139,
				"InsideDiameter": 0.127,
				"Length": 3000,
				"Density": 7.85,
				"WeightPerMeter": 0
				}
				]
	},
	"ProductionParameter": {         //（10） 生产参数
		"WaterCut": 73.1,
		"ProductionGasOilRatio": 7,
		"TubingPressure": 0.5,
		"CasingPressure": 0.6,
		"WellHeadFluidTemperature": 35,
		"ProducingfluidLevel": 975,
		"PumpSettingDepth": 1012.36,
		"Submergence": 37.36
	},
	"FSDiagram": {                   //（11） 功图数据
		"AcquisitionTime": "2016-02-01 16:38:24",
		"Stroke": 2.11,
		"SPM": 2.6,
		"F": [
			[26.53],
			[27.69],
			[28.86],
			[30.16],
			[31.26],
			[32.54],
			...
			[23.24],
			[23.61],
			[23.83],
			[24.08],
			[24.6]
			],
		"S": [
			[0],
			[0.01],
			[0.01],
			[0.02],
			[0.03],
			...
			[0.04],
			[0.01],
			[0]
			],
		"P": [
			0.3,
			0.6,
			0.3,
			0.6,
			0.6,
			...
			3.0,
			1.2,
			0.0,
			0.9,
			1.8
			],
		"A": [
			17.54,
			17.52,
			17.48,
			17.33,
			17.2,
			...
			17.69,
			17.64,
			17.56,
			17.67,
			17.79
			]
	},
	"SystemEfficiency": {            //（12） 系统效率
		"MotorInputActivePower": 2.3
	},
	"ManualIntervention": {          //（13） 人工干预
		"Code": 0,
		"NetGrossRatio": 1
	}
}
```

### 2.1.3 输入实例（有尾管、滤管）
```
{
	"AKString": "",                 //（1） 应用密钥
	"WellName": "1-1",              //（2） 井名
	"FluidPVT": {                   //（3） 流体PVT物性
		"CrudeOilDensity": 0.86,
		"WaterDensity": 1,
		"NaturalGasRelativeDensity": 0.7,
		"SaturationPressure": 9.6
	},
	"Reservoir": {                  //（4） 油藏物性 
		"Depth": 1350,
		"Temperature": 66
	},
	"WellboreTrajectory": {         //（5） 井身轨迹，各项参数按顺序依次输入
		"MeasuringDepth": [
			100,
			200
			],
		"VerticalDepth": [
			100,
			200
			],
		"DeviationAngle": [
			0,
			0
			],
		"AzimuthAngle": [
			0,
			0
			]
	},
	"RodString": {                  //（6）抽油杆参数，每级杆柱参数对应一组结构体，多级杆柱按结构体依次输入
		"EveryRod": [
			{
				"Type": 1,
				"Grade": "D",
				"Length": 329.86,
				"OutsideDiameter": 0.022,
				"InsideDiameter": 0,
				"Density": 7.85,
				"WeightPerMeter": 0
				},
			{
				"Type": 1,
				"Grade": "D",
				"Length": 668.52,
				"OutsideDiameter": 0.019,
				"InsideDiameter": 0,
				"Density": 7.85,
				"WeightPerMeter": 0
				}
				]
	},
	"TubingString": {               //（7） 油管参数，多级油管按结构体依次输入
		"EveryTubing": [
			{
				"Grade": "K55",
				"length": 1000,
				"OutsideDiameter": 0.073,
				"InsideDiameter": 0.062,
				"Density": 7.85,
				"WeightPerMeter": 0
				}
				]
	},
	"Pump": {                       //（8） 泵参数
		"PumpType": "T",
		"BarrelType": "L",
		"PumpGrade": 1,
		"BarrelLength": 8,
		"PlungerLength": 1.3,
		"PumpBoreDiameter": 0.044,
		"Clearance": 0.00002,
		"AntiImpactStroke": 0.1
	},
	"TailTubingString": {           //（9）尾管（含滤管）
		"EveryEquipment": [
			{
				"EquipmentType": "TailTubing",
				"Grade": "K55",
				"Length": 25,
				"OutsideDiameter": 0.073,
				"InsideDiameter": 0.062,
				"Density": 7.85
				},
			{
				"EquipmentType": "FilterTubing",
				"Grade": "K55",
				"Length": 5,
				"OutsideDiameter": 0.073,
				"InsideDiameter": 0.062,
				"Density": 7.85
				},
			{
				"EquipmentType": "TailTubing",
				"Grade": "K55",
				"Length": 25,
				"OutsideDiameter": 0.073,
				"InsideDiameter": 0.062,
				"Density": 7.85
				}
				]
	},
	"CasingString": {             //（10） 套管参数，多级套管按结构体依次输入
		"EveryCasing": [
			{
				"Grade": "K55",
				"OutsideDiameter": 0.139,
				"InsideDiameter": 0.127,
				"Length": 3000,
				"Density": 7.85,
				"WeightPerMeter": 0
				}
				]
	},
	"ProductionParameter": {       //（11） 生产参数
		"WaterCut": 73.1,
		"ProductionGasOilRatio": 7,
		"TubingPressure": 0.5,
		"CasingPressure": 0.6,
		"WellHeadFluidTemperature": 35,
		"ProducingfluidLevel": 975,
		"PumpSettingDepth": 1012.36,
		"Submergence": 37.36
	},
	"FSDiagram": {                 //（12） 功图数据
		"AcquisitionTime": "2016-02-01 16:38:24",
		"Stroke": 2.11,
		"SPM": 2.6,
		"F": [
			[26.53],
			[27.69],
			[28.86],
			[30.16],
			[31.26],
			[32.54],
			…
			[23.24],
			[23.61],
			[23.83],
			[24.08],
			[24.6]
			],
		"S": [
			[0],
			[0.01],
			[0.01],
			[0.02],
			[0.03],
			...
			[0.04],
			[0.02],
			[0.01],
			[0.01],
			[0]
			],
		"P": [
			0.3,
			0.6,
			0.3,
			0.6,
			0.6,
			...
			3.0,
			1.2,
			0.0,
			0.9,
			1.8
			],
		"A": [
			17.54,
			17.52,
			17.48,
			17.33,
			17.2,
			...
			17.69,
			17.64,
			17.56,
			17.67,
			17.79
			]
	},
	"SystemEfficiency": {             //（13） 系统效率
		"MotorInputActivePower": 2.3
	},
	"ManualIntervention": {           //（14）人工干预
		"Code": 0,
		"NetGrossRatio": 1
	}
}
```

### 2.1.4 数据收集表

#### 2.1.4.1 油井数据收集表

*表2-2 区块数据* *

| 序号     | 区块名称* | 原油密度(g/cm\^3)* | 水密度(g/cm\^3)* | 天然气相对密度* | 饱和压力(MPa)* | 中部深度(m)* | 中部温度(℃) *|
|----------|-----------|--------------------|------------------|-----------------|----------------|--------------|---------------|
| 1        |           |                    |                  |                 |                |              |               |
| 2        |           |                    |                  |                 |                |              |               |
| 3        |           |                    |                  |                 |                |              |               |


*表2-3 井身轨迹数据表*

| 序号     | 井名 | 测量深度 (m) | 垂直深度 (m) | 井斜角(°) | 方位角(°) |
|----------|------|--------------|--------------|-----------|-----------|
| 1        |      |              |              |           |           |
| 2        |      |              |              |           |           |
| 3        |      |              |              |           |           |

*表2-4 生产数据1*

| 序号     | 井名 | 含水率(%)* | 油压（回压）(MPa)* | 套压(MPa)* | 动液面(m)* | 井口流温(℃) | 生产气油比 *| 净毛比 *|
|----------|------|------------|--------------------|------------|------------|--------------|-------------|---------|
| 1        |      |            |                    |            |            |              |             |         |
| 2        |      |            |                    |            |            |              |             |         |
| 3        |      |            |                    |            |            |              |             |         |

*表2-5生产数据2*

| 序号     | 井名*          | 泵类型          | 泵级别*    | 泵径(m) *   | 柱塞长(m)      | 泵筒类型        | 油管内径(m)*| 生产套管内径(m) | 一级杆类型     | 一级杆级别*    |
|----------|----------------|-----------------|------------|-------------|----------------|-----------------|-------------|-----------------|----------------|----------------|
| 1        |                |                 |            |             |                |                 |             |                 |                |                |
| 2        |                |                 |            |             |                |                 |             |                 |                |                |
| 序号     | 一级杆外径(m) *| 一级杆长度(m)*  | 二级杆类型 | 二级杆级别* | 二级杆外径(m)* | 二级杆长度(m)*  | 三级杆类型  | 三级杆级别*     | 三级杆外径(m)* | 三级杆长度(m)* |
| 1        |                |                 |            |             |                |                 |             |                 |                |                |
| 2        |                |                 |            |             |                |                 |             |                 |                |                |

#### 2.1.4.2 煤层气井数据收集表

*表2-6 区块数据*

| 序号     | 井名*| 水密度(g/cm\^3)* | 煤层气相对密度* | 中部深度(m)*   | 中部温度(℃) *|
|----------|------|------------------|-----------------|----------------|---------------|
| 1        |      |                  |                 |                |               |
| 2        |      |                  |                 |                |               |
| 3        |      |                  |                 |                |               |

*表2-7 井身轨迹数据表*

| 序号     | 井名 | 测量深度 (m) | 垂直深度 (m) | 井斜角(°) | 方位角(°) |
|----------|------|--------------|--------------|-----------|-----------|
| 1        |      |              |              |           |           |
| 2        |      |              |              |           |           |
| 3        |      |              |              |           |           |

*表2-8 生产数据1*

| 序号     | 井名* | 油压(回压)(MPa)* | 套压(MPa)* | 动液面(m)* | 井口流温(℃) | 净毛比 *|
|----------|------|-------------------|------------|--------------|-------------|--------|
| 1        |      |                   |            |              |             |        |
| 2        |      |                   |            |              |             |        |
| 3        |      |                   |            |              |             |        |

*表2-9 生产数据2*

| 序号     | 井名*          | 泵类型          | 泵级别*    | 泵径(m)*    | 柱塞长(m)      | 泵筒类型       | 油管内径(m)* | 生产套管内径(m) | 一级杆类型     | 一级杆级别*    |
|----------|----------------|-----------------|------------|-------------|----------------|----------------|--------------|-----------------|----------------|----------------|
| 1        |                |                 |            |             |                |                |              |                 |                |                |
| 2        |                |                 |            |             |                |                |              |                 |                |                |
| 序号     | 一级杆外径(m)* | 一级杆长度(m)*  | 二级杆类型 | 二级杆级别* | 二级杆外径(m)* | 二级杆长度(m)* | 三级杆类型   | 三级杆级别*     | 三级杆外径(m)* | 三级杆长度(m)* |
| 1        |                |                 |            |             |                |                |              |                 |                |                |
| 2        |                |                 |            |             |                |                |              |                 |                |                |

## 2.2 输出文本（完整版）

### 2.2.1 输出参数说明

*表2-10 输出参数说明表*

| 代码                                       | 名称                       | 单位        | 类型     | 备注                              |
|--------------------------------------------|----------------------------|-------------|----------|-----------------------------------|
| WellName                                   | 井名                       |             | string   |                                   |
| **CalculationStatus**                      | **计算状态**               |             |          |                                   |
| ResultStatus                               | 计算结果状态               |             | int      | 详见表底注释[1]                   |
| ResultCode                                 | 工况类型                   |             | int      | 详见工况类型代码表                |
| **Verification**                           | **数据校验**               |             |          |                                   |
| ErrorCounter                               | 错误参数计数器             |             | int      | 错误参数个数                      |
| ErrorString                                | 错误参数字符串             |             | string   | 数据错误，计算不成功              |
| WarningCounter                             | 报警计数器                 |             | int      | 报警参数个数                      |
| WarningString                              | 报警字符串                 |             | string   | 报警参数（取默认值，计算正常进行）|
| SDKPlusCounter                             | Plus版报警计数器           |             | int      | 预留                              |
| SDKPlusString                              | Plus版报警字符串           |             | string   | 预留                              |
| **RodString**                              | **抽油杆参数**             |             |          |                                   |
| CNT                                        | 杆数                       |             | int      |                                   |
| LengthAll                                  | 总杆长                     | m           | float64  |                                   |
| WeightAll                                  | 总杆重                     | kN          | float64  |                                   |
| BuoyancyForceAll                           | 总浮力                     | kN          | float64  |                                   |
| LengthString                               | 杆长字符串                 |             | string   |                                   |
| GradeString                                | 杆级别字符串               |             | string   |                                   |
| OutsideDiameterString                      | 杆外径字符串               |             | string   |                                   |
| InsideDiameterString                       | 杆内径字符串               |             | string   |                                   |
| **EveryRod**                               | **每级杆参数**             |             |          |                                   |
| Type                                       | 抽油杆类型                 |             | int      | 1-实心抽油杆 2－空心抽油杆        |
| Grade                                      | 杆级别                     |             | string   | A，B，C，K，D，KD，HL，HY         |
| Length                                     | 杆长                       | m           | float64  |                                   |
| OutsideDiameter                            | 杆外径                     | m           | float64  |                                   |
| InsideDiameter                             | 杆内径                     | m           | float64  |                                   |
| Area                                       | 杆截面积                   | m\^2        | float64  |                                   |
| Weight                                     | 杆重                       | kN          | float64  |                                   |
| BuoyancyForce                              | 杆柱浮力                   | kN          | float64  |                                   |
| Density                                    | 杆柱密度                   | g/cm\^3     | float64  |                                   |
| WeightPerMeter                             | 每米杆重                   | kN/m        | float64  |                                   |
| TE                                         | 抽油杆最小抗张强度         | MPa         | float64  |                                   |
| SF                                         | 抽油杆使用系数             | 小数        | float64  |                                   |
| DampingFactor                              | 每级杆的阻尼系数           |             | float64  |                                   |
| MaxStress                                  | 各级杆最大应力             | MPa         | float64  |                                   |
| MinStress                                  | 各级杆最小应力             | MPa         | float64  |                                   |
| AllowableStress                            | 各级杆许用应力             | MPa         | float64  |                                   |
| StressRatio                                | 应力范围比                 | 小数        | float64  |                                   |
| **ProductionParameter**                    | **生产参数**               |             |          |                                   |
| WaterCut                                   | 体积含水率                 | %           | float64  | 煤层气井为100                     |
| ProductionGasOilRatio                      | 生产气油比                 | m\^3/m\^3   | float64  |                                   |
| TubingPressure                             | 油压（回压）               | MPa         | float64  |                                   |
| CasingPressure                             | 套压                       | MPa         | float64  |                                   |
| WellHeadFluidTemperature                   | 井口流温                   | ℃          | float64  |                                   |
| ProducingfluidLevel                        | 动液面                     | m           | float64  |                                   |
| PumpSettingDepth                           | 泵挂                       | m           | float64  |                                   |
| Submergence                                | 沉没度                     | m           | float64  |                                   |
| PumpIntakeP                                | 泵入口压力                 | MPa         | float64  |                                   |
| PumpIntakeT                                | 泵入口温度                 | ℃          | float64  |                                   |
| PumpIntakeGOL                              | 泵入口就地气液比           |             | float64  |                                   |
| PumpInletVisl                              | 泵入口粘度                 | mPa·s       | float64  |                                   |
| PumpInletBo                                | 泵入口原油体积系数         | 小数        | float64  |                                   |
| PumpOutletP                                | 泵出口压力                 | MPa         | float64  |                                   |
| PumpOutletT                                | 泵出口温度                 | ℃          | float64  |                                   |
| PumpOutletGOL                              | 泵出口就地气液比           |             | float64  |                                   |
| PumpOutletVisl                             | 泵出口粘度                 | mPa·s       | float64  |                                   |
| PumpOutletBo                               | 泵出口原油体积系数         | 小数        | float64  |                                   |
| NetGrossRatio                              | 净毛比                     | 小数        | float64  |                                   |
| TheoreticalProduction                      | 理论排量                   | m\^3/d      | float64  |                                   |
| LiquidVolumetricProduction                 | 产液量（方）               | m\^3/d      | float64  | 煤层气井取产液量                  |
| OilVolumetricProduction                    | 产油量（方）               | m\^3/d      | float64  |                                   |
| WaterVolumetricProduction                  | 产水量（方）               | m\^3/d      | float64  |                                   |
| AvailablePlungerStrokeVolumetricProduction | 柱塞有效冲程计算产量（方） | m\^3/d      | float64  |                                   |
| PumpClearanceLeakVolumetricProduction      | 泵间隙漏失量（方）         | m\^3/d      | float64  |                                   |
| TVLeakVolumetricProduction                 | 游动凡尔漏失量（方）       | m\^3/d      | float64  |                                   |
| SVLeakVolumetricProduction                 | 固定凡尔漏失量（方）       | m\^3/d      | float64  |                                   |
| GasInfluenceVolumetricProduction           | 气影响（方）               | m\^3/d      | float64  |                                   |
| LiquidWeightProduction                     | 产液量（吨）               | t/d         | float64  | 煤层气井取产液量                  |
| OilWeightProduction                        | 产油量（吨）               | t/d         | float64  |                                   |
| WaterWeightProduction                      | 产水量（吨）               | t/d         | float64  |                                   |
| AvailablePlungerStrokeWeightProduction     | 柱塞有效冲程计算产量（吨） | t/d         | float64  |                                   |
| PumpClearanceLeakWeightProduction          | 泵间隙漏失量（吨）         | t/d         | float64  |                                   |
| TVLeakWeightProduction                     | 游动凡尔漏失量（吨）       | t/d         | float64  |                                   |
| SVLeakWeightProduction                     | 固定凡尔漏失量（吨）       | t/d         | float64  |                                   |
| GasInfluenceWeightProduction               | 气影响（吨）               | t/d         | float64  |                                   |
| **FSDiagram**                              | **功图数据**               |             |          |                                   |
| AcquisitionTime                            | 采集时间                   |             | string   |                                   |
| Stroke                                     | 功图冲程                   | m           | float64  |                                   |
| SPM                                        | 功图冲次                   | 1/min       | float64  |                                   |
| CNT                                        | 点数                       |             | int      |                                   |
| Area                                       | 功图面积                   |             | float64  |                                   |
| UpperLoadLine                              | 理论上载荷                 | kN          | float64  |                                   |
| LowerLoadLine                              | 理论下载荷                 | kN          | float64  |                                   |
| FullnessCoefficient                        | 功图充满系数               | 小数        | float64  |                                   |
| PlungerStroke                              | 柱塞冲程                   | m           | float64  |                                   |
| AvailablePlungerStroke                     | 柱塞有效冲程               | m           | float64  |                                   |
| F                                          | 载荷                       | kN          | float64  | 功图载荷                          |
| S                                          | 位移                       | m           | float64  | 功图位移                          |
| P                                          | 三相总有功功率             | kW          | float64  |                                   |
| A                                          | 三相平均电流               | A           | float64  |                                   |
| FMax                                       | 最大载荷                   | kN          | float64  | 各级功图最大载荷                  |
| FMin                                       | 最小载荷                   | kN          | float64  | 各级功图最小载荷                  |
| SMaxIndex                                  | 位移最大值索引             |             | int      |                                   |
| SMinIndex                                  | 位移最小值索引             |             | int      |                                   |
| UpStrokePMax                               | 上冲程功率最大值           | kW          | float64  |                                   |
| DownStrokePMax                             | 下冲程功率最大值           | kW          | float64  |                                   |
| PDegreeOfBalance                           | 功率平衡度                 | %           | float64  |                                   |
| PMaxRatioString                            | 功率比字符串               |             | string   |                                   |
| AverageP                                   | 平均总有功功率             | kW          | float64  |                                   |
| UpStrokeAMax                               | 上冲程电流最大值           | A           | float64  |                                   |
| DownStrokeAMax                             | 下冲程电流最大值           | A           | float64  |                                   |
| ADegreeOfBalance                           | 电流平衡度                 | %           | float64  |                                   |
| AMaxRatioString                            | 电流比字符串               |             | string   |                                   |
| **PumpEfficiency**                         | **泵效**                   |             |          |                                   |
| RodFlexLength                              | 抽油杆伸长量               | m           | float64  |                                   |
| TubingFlexLength                           | 油管伸缩值                 | m           | float64  |                                   |
| InertiaLength                              | 惯性载荷增量               | m           | float64  |                                   |
| PumpEff1                                   | 冲程损失系数               | 小数        | float64  |                                   |
| PumpEff2                                   | 充满系数                   | 小数        | float64  |                                   |
| PumpEff3                                   | 间隙漏失系数               | 小数        | float64  |                                   |
| PumpEff4                                   | 液体收缩系数               | 小数        | float64  |                                   |
| PumpEff                                    | 总泵效                     | 小数        | float64  |                                   |
| **SystemEfficiency**                       | **系统效率分析**           |             |          |                                   |
| SurfaceSystemEfficiency                    | 地面效率                   | 小数        | float64  |                                   |
| WellDownSystemEfficiency                   | 井下效率                   | 小数        | float64  |                                   |
| SystemEfficiency                           | 系统效率                   | 小数        | float64  |                                   |
| MotorInputActivePower                      | 电机输入有功功率           | kW          | float64  |                                   |
| PolishRodPower                             | 光杆功率                   | kW          | float64  |                                   |
| WaterPower                                 | 水功率                     | kW          | float64  |                                   |
| PowerConsumptionPerTHM                     | 吨液百米耗电量             | kW·h/100m·t | float64  |                                   |

**[1]** *计算结果状态:1:计算成功，-44:请求数据读取失败，-55:请求数据json解码失败， -66:井数许可超限，-77:计算异常， -88:响应数据json编码失败， -99:数据校验错误*

### 2.2.2 输出实例

```
{
    "WellName": "1-1",                     //（1）井名
    "CalculationStatus": {                 //（2）计算状态
        "ResultStatus": 1,
        "ResultCode": 1205
    },
    "Verification": {                      //（3）数据校验
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": "",
        "SDKPlusCounter": 0,
        "SDKPlusString": ""
    },
    "RodString": {                         //（4）抽油杆参数
        "CNT": 2,
        "LengthAll": 1000,
        "WeightAll": 24.78,
        "BuoyancyForceAll": 3.08,
        "LengthString": "246.80/411.30",
        "GradeString": "D/D",
        "OutsideDiameterString": "0.022/0.019",
        "InsideDiameterString": "0.000/0.000",
        "EveryRod": [
            {
                "Type": 1,
                "Grade": "D",
                "Length": 400,
                "OutsideDiameter": 0.022,
                "InsideDiameter": 0,
                "Area": 0.000380,
                "Weight": 11.69,
                "BuoyancyForce": 1.45,
                "Density": 7.85,
                "TE": 620,
                "SF": 1,
                "DampingFactor": 0.10,
                "MaxStress": 104.96,
                "MinStress": 55.69,
                "AllowableStress": 186.32,
                "StressRatio": 0.56
            },
            {
                "Type": 1,
                "Grade": "D",
                "Length": 600,
                "OutsideDiameter": 0.019,
                "InsideDiameter": 0,
                "Area": 0.000283,
                "Weight": 13.08,
                "BuoyancyForce": 1.63,
                "Density": 7.85,
                "TE": 620,
                "SF": 1,
                "DampingFactor": 0.0944,
                "MaxStress": 99.45,
                "MinStress": 33.82,
                "AllowableStress": 174.02,
                "StressRatio": 0.57
            }
        ]
    },
    "ProductionParameter": {                               //（5）生产数据
        "WaterCut": 80,
        "ProductionGasOilRatio": 50,
        "TubingPressure": 0.5,
        "CasingPressure": 0.3,
        "WellHeadFluidTemperature": 40,
        "ProducingfluidLevel": 800,
        "PumpSettingDepth": 1000,
        "PumpIntakeP": 2.21,
        "PumpIntakeT": 70.01,
        "PumpIntakeGOL": 0.43,
        "PumpOutletP": 9.98,
        "PumpOutletT": 68.98,
        "PumpOutletGOL": 0.012,
        "PumpOutletVisl": 0.75,
        "PumpOutletBo": 1.13,
		"NetGrossRatio": 1,
		"TheoreticalProduction": 15.16,
        "LiquidVolumetricProduction": 4.56,
        "OilVolumetricProduction": 0.91,
        "WaterVolumetricProduction": 3.65,
        "AvailablePlungerStrokeVolumetricProduction": 4.68,
        "PumpClearanceLeakVolumetricProduction": 0,
        "TVLeakVolumetricProduction": 0,
        "SVLeakVolumetricProduction": 0,
        "GasInfluenceVolumetricProduction": 0,
        "LiquidWeightProduction": 4.46,
        "OilWeightProduction": 0.81,
        "WaterWeightProduction": 3.65,
        "AvailablePlungerStrokeWeightProduction": 4.58,
        "PumpClearanceLeakWeightProduction": 0,
        "TVLeakWeightProduction": 0,
        "SVLeakWeightProduction": 0,
        "GasInfluenceWeightProduction": 0
    },
    "FSDiagram": {                                       //（6）功图数据
        "AcquisitionTime": "2016-02-01 16:38:24",
        "Stroke": 3.02,
        "SPM": 3.5,
        "CNT": 143,
        "Area": 19.21,
        "UpperLoadLine": 35.65,
        "LowerLoadLine": 21.69,
        "FullnessCoefficient": 0.30,
        "PlungerStroke": 2.7,
        "AvailablePlungerStroke": 0.82,
        "F": [
            [                  ==//各项值代表意义：光杆功图载荷、各级杆顶端功图载荷，按实际杆数依次填写，泵顶端载荷即为泵功图载荷==
				26.53,         ==//光杆功图载荷（一级杆顶端功图载荷）==
				14.33,         ==//二级杆顶端功图载荷==
				1.06           ==//泵功图载荷==
				],
            [
                27.69,
                15.49,
                2.20
            ],
            …
            [
                24.08,
                12.45,
                -0.78
            ],
            [
                24.6,
                13.31,
                0.06
            ]
        ],
        "S": [
            [               ==//各项值代表意义：光杆功图位移、各级杆顶端功图位移，按实际杆数依次填写，泵顶端位移即为泵功图位移==
				0,          ==//光杆功图位移（一级杆顶端功图位移）==
				-0.0054     ==//二级杆柱顶端功图位移==
				-0.0174     ==//泵功图位移==
				],
            [
                0.01,
                -0.0084,
                -0.0325
            ],
            …
            [
                0.01,
                0.0089,
                0.0164
            ],
            [
                0,
                0.0003,
                -0.0010
            ]
        ],
		"P": [
				0.3, 
				0.6, 
				0.3, 
				0.6, 
				0.6, 
	 			...
				3.0, 
				1.2, 
				0.0, 
				0.9, 
				1.8
		],
		"A": [
				17.54, 
				17.52, 
				17.48, 
				17.33, 
				17.2, 
				...
				17.69, 
				17.64, 
				17.56, 
				17.67, 
				17.79
			],
        "FMax": [
            39.90,
            28.19,
            14.89
        ],
        "FMin": [
            21.17,
            9.59,
            -3.53
        ],
        "SMaxIndex": 99,
        "SMinIndex": 0,
        "UpStrokePMax": 93,
        "DownStrokePMax": 84.6,
        "PDegreeOfBalance": 90.97,
        "PMaxRatioString": 20.1/22.09,
        "AverageP": 28.14,
        "UpStrokeAMax": 58.1,
        "DownStrokeAMax": 51.04,
        "ADegreeOfBalance": 87.85,
        "AMaxRatioString": 18.4/20.94
    },
    "PumpEfficiency": {                          //（7）泵效
        "PumpEff1": 0,
        "RodFlexLength": 0,
        "TubingFlexLength": 0,
        "InertiaLength": 0,
        "PumpEff2": 0,
        "PumpEff3": 0,
        "PumpEff4": 0,
        "PumpEff": 0
    },
    "SystemEfficiency": {                       //（8）系统效率
        "SurfaceSystemEfficiency": 0,
        "WellDownSystemEfficiency": 0,
        "SystemEfficiency": 0,
        "PowerConsumptionPerTHM": 26.93,
        "MotorInputActivePower": 0,
        "PolishRodPower": 2.23,
        "WaterPower": 0 
    }
   }
```

### 2.2.3 工况类型代码

*表2-11 油井代码表*

| 序号 | 代码         | 名称             | 优化建议           |
|------|--------------|------------------|--------------------|
| 1    | 1201         | 抽喷             |                    |
| 2    | 1202         | 正常             |                    |
| 3    | 1203         | 充满不足         |                    |
| 4    | 1204         | 供液不足         | 间抽或降低冲次     |
| 5    | 1205         | 供液极差         | 间抽或降低冲次     |
| 6    | 1206         | 抽空             | 间抽或降低冲次     |
| 7    | 1207         | 泵堵             | 热洗或加药         |
| 8    | 1208         | 气锁             | 合理控制气体       |
| 9    | 1209         | 气影响           | 合理控制气体       |
| 10   | 1210         | 间隙漏           | 检泵               |
| 11   | 1211         | 油管漏           | 油管打压试验       |
| 12   | 1212         | 游动凡尔漏失     | 热洗或检泵         |
| 13   | 1213         | 固定凡尔漏失     | 热洗或检泵         |
| 14   | 1214         | 双凡尔漏失       | 热洗或检泵         |
| 15   | 1215         | 游动凡尔失灵     | 检泵               |
| 16   | 1216         | 固定凡尔失灵     | 检泵               |
| 17   | 1217         | 双凡尔失灵       | 检泵               |
| 18   | 1218         | 上死点别、碰     | 校正井口设备       |
| 19   | 1219         | 碰泵             | 上提（增大）防冲距 |
| 20   | 1220         | 柱塞未下入工作筒 | 下放（缩小）防冲距 |
| 21   | 1221         | 柱塞脱出工作筒   | 下放（缩小）防冲距 |
| 22   | 1222         | 杆断脱           | 替换抽油杆         |
| 23   | 1223         | 杆（泵）卡       | 热洗或检泵         |
| 24   | 1224         | 轻微结蜡         | 热洗或加药         |
| 25   | 1225         | 严重结蜡         | 热洗或加药         |
| 26   | 1226         | 轻微出砂         | 防砂               |
| 27   | 1227         | 严重出砂         | 防砂               |
| 28   | 1230         | 惯性载荷大       | 降低冲次           |
| 29   | 1231         | 应力超标         | 优化抽油杆柱组合   |
| 30   | 1232         | 采集异常         | 检查采集仪表       |
| 31   | 1302         | 停抽             |                    |

*表2-12 煤层气代码表*

| 序号 | 代码         | 名称             | 优化建议           |
|------|--------------|------------------|--------------------|
| 1    | 1201         | 抽喷             |                    |
| 2    | 1202         | 正常             |                    |
| 3    | 1203         | 充满不足         |                    |
| 4    | 1204         | 供液不足         | 间抽或降低冲次     |
| 5    | 1205         | 供液极差         | 间抽或降低冲次     |
| 6    | 1206         | 抽空             | 间抽或降低冲次     |
| 7    | 1207         | 泵堵             | 洗井或检泵         |
| 8    | 1208         | 气锁             | 合理控制气体       |
| 9    | 1209         | 气影响           | 合理控制气体       |
| 10   | 1210         | 间隙漏           | 检泵               |
| 11   | 1211         | 油管漏           | 油管打压试验       |
| 12   | 1212         | 游动凡尔漏失     | 洗井或检泵         |
| 13   | 1213         | 固定凡尔漏失     | 洗井或检泵         |
| 14   | 1214         | 双凡尔漏失       | 洗井或检泵         |
| 15   | 1215         | 游动凡尔失灵     | 检泵               |
| 16   | 1216         | 固定凡尔失灵     | 检泵               |
| 17   | 1217         | 双凡尔失灵       | 检泵               |
| 18   | 1218         | 上死点别、碰     | 校正井口设备       |
| 19   | 1219         | 碰泵             | 上提（增大）防冲距 |
| 20   | 1220         | 柱塞未下入工作筒 | 下放（缩小）防冲距 |
| 21   | 1221         | 柱塞脱出工作筒   | 下放（缩小）防冲距 |
| 22   | 1222         | 杆断脱           | 替换抽油杆         |
| 23   | 1223         | 杆（泵）卡       | 洗井或检泵         |
| 24   | 1226         | 出煤渣           | 防煤渣             |
| 25   | 1227         | 严重出煤渣       | 防煤渣             |
| 26   | 1230         | 惯性载荷大       | 降低冲次           |
| 27   | 1231         | 应力超标         | 优化抽油杆柱组合   |
| 28   | 1232         | 采集异常         | 检查采集仪表       |
| 29   | 1302         | 停抽             |                    |

## 2.3 输入文本（精简版）

### 2.3.1 输入参数说明

*表2-13 输入参数说明表*

| 代码            | 名称     | 单位  | 类型     | 必填    | 备注                            |
|-----------------|----------|-------|----------|---------|---------------------------------|
| AKString        | 应用密钥 |       | string   |         | 预留字段                        |
| WellName        | 井名     |       | string   | *       |                                 |
| AcquisitionTime | 采集时间 |       | string   | *       | YYYY-MM-DD HH:NN:SS"            |
| SPM             | 冲次     | 1/min | float64  | *       |                                 |
| S               | 位移     | m     | float64  | *       |                                 |
| F               | 载荷     | kN    | float64  | *       |                                 |
| UpperLoadLine   | 上载荷线 | kN    | float64  | *       | 取非故障情况下功图上载荷平均值  |
| LowerLoadLine   | 下载荷线 | kN    | float64  | *       | 取非故障情况下功图下载荷平均值  |

### 2.3.2 输入实例

```
{
    "AKString": "",
    "WellName": "新01-010",
    "AcquisitionTime": "2016-02-01 16:38:24",
    "SPM": 3.72,
    "UpperLoadLine": 44.01,
    "LowerLoadLine": 25.14,
    "F": [
        25.21,
        26.45,
        26.79,
        26.89,
        ......
        23.63,
        23.86,
        24.06,
        24.17,
        24.10
    ],
    "S": [
        0.0,
        0.0,
        0.0,
        0.01,
        ......
        0.01,
        0.01,
        0.0,
        0.0,
        0.0
    ]
}
```

## 2.4 输出文本（精简版）

### 2.4.1 输出参数说明

*表2-14 输出参数说明表*

| 代码                   | 名称             | 单位 | 类型     | 备注                               |
|------------------------|------------------|------|----------|------------------------------------|
| WellName               | 井名             |      | string   |                                    |
| ResultStatus           | 计算结果状态     |      | int      |                                    |
| ResultCode             | 工况类型         |      | int      | 见工况类型代码表                   |
| CNT                    | 点数             |      | int      |                                    |
| Stroke                 | 功图冲程         | m    | float64  |                                    |
| FullnessCoefficient    | 功图充满系数     | 小数 | float64  |                                    |
| PlungerStroke          | 柱塞冲程         | m    | float64  |                                    |
| AvailablePlungerStroke | 柱塞有效冲程     | m    | float64  |                                    |
| FMax                   | 最大载荷         | kN   | float64  | 功图最大载荷                       |
| FMin                   | 最小载荷         | kN   | float64  | 功图最小载荷                       |
| SMaxIndex              | 位移最大值索引   |      | int      | 详见表底注释[1]                    |
| SMinIndex              | 位移最小值索引   |      | int      | 详见表底注释[2]                    |
| Area                   | 功图面积         |      | float64  |                                    |
| PolishRodPower         | 光杆功率         | kW   | float64  |                                    |
| **Verification**       | **数据校验**     |      |          |                                    |
| ErrorCounter           | 错误参数计数器   |      | int      | 错误参数个数                       |
| ErrorString            | 错误参数字符串   |      | string   | 数据错误，计算不成功               |
| WarningCounter         | 报警计数器       |      | int      | 报警参数个数                       |
| WarningString          | 报警字符串       |      | string   | 报警参数（取默认值，计算正常进行） |
| SDKPlusCounter         | Plus版报警计数器 |      | int      | 预留                               |
| SDKPlusString          | Plus版报警字符串 |      | string   | 预留                               |

**[1]** *位移最大值索引:位移最大值所在的点数，从最小值到最大值为上冲程，从最大值再返回最小值为下冲程，界面展示时可以将上下冲程画成两种不同颜色*  
**[2]** *位移最小值索引:位移最小值所在的点数，从最小值到最大值为上冲程，从最大值再返回最小值为下冲程，界面展示时可以将上下冲程画成两种不同颜色*

### 2.4.2 输出实例

```
{
    "WellName": "新01-010",
    "AcquisitionTime": "2016-02-01 16: 38: 24",
    "ResultStatus": 1,
    "ResultCode": 1203,
    "CNT": 200,
    "Stroke": 2.94,
    "FullnessCoefficient": 0.374,
    "PlungerStroke": 2.54,
    "AvailablePlungerStroke": 0.95,
    "FMax": 44.62,
    "FMin": 20.62,
    "SMaxIndex": 103,
    "SMinIndex": 197,
    "Area": 32.21,
    "PolishRodPower": 2,
    "Verification": {
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": "",
        "SDKPlusCounter": 0,
        "SDKPlusString": ""
    }
}
```

### 2.4.3 工况类型代码

*表2-15 油井代码表*

| 序号 | 代码         | 名称             | 优化建议           |
|------|--------------|------------------|--------------------|
| 1    | 1202         | 正常             |                    |
| 2    | 1203         | 充满不足         |                    |
| 3    | 1204         | 供液不足         | 间抽或降低冲次     |
| 4    | 1205         | 供液极差         | 间抽或降低冲次     |
| 5    | 1206         | 抽空             | 间抽或降低冲次     |
| 6    | 1208         | 气锁             | 合理控制气体       |
| 7    | 1209         | 气影响           | 合理控制气体       |
| 8    | 1210         | 间隙漏           | 检泵               |
| 9    | 1211         | 油管漏           | 油管打压试验       |
| 10   | 1212         | 游动凡尔漏失     | 热洗或检泵         |
| 11   | 1213         | 固定凡尔漏失     | 热洗或检泵         |
| 12   | 1214         | 双凡尔漏失       | 热洗或检泵         |
| 13   | 1215         | 游动凡尔失灵     | 检泵               |
| 14   | 1216         | 固定凡尔失灵     | 检泵               |
| 15   | 1217         | 双凡尔失灵       | 检泵               |
| 16   | 1218         | 上死点别、碰     | 校正井口设备       |
| 17   | 1219         | 碰泵             | 上提（增大）防冲距 |
| 18   | 1220         | 柱塞未下入工作筒 | 下放（缩小）防冲距 |
| 19   | 1221         | 柱塞脱出工作筒   | 下放（缩小）防冲距 |
| 20   | 1222         | 杆断脱           | 替换抽油杆         |
| 21   | 1223         | 杆（泵）卡       | 热洗或检泵         |
| 22   | 1224         | 轻微结蜡         | 热洗或加药         |
| 23   | 1225         | 严重结蜡         | 热洗或加药         |
| 24   | 1226         | 轻微出砂         | 防砂               |
| 25   | 1227         | 严重出砂         | 防砂               |
| 26   | 1230         | 惯性载荷大       | 降低冲次           |
| 27   | 1232         | 采集异常         | 检查采集仪表       |
| 28   | 1302         | 停抽             |                    |

*表2-16 煤层气井代码表*

| 序号 | 代码         | 名称             | 优化建议           |
|------|--------------|------------------|--------------------|
| 1    | 1202         | 正常             |                    |
| 2    | 1203         | 充满不足         |                    |
| 3    | 1204         | 供液不足         | 间抽或降低冲次     |
| 4    | 1205         | 供液极差         | 间抽或降低冲次     |
| 5    | 1206         | 抽空             | 间抽或降低冲次     |
| 6    | 1208         | 气锁             | 合理控制气体       |
| 7    | 1209         | 气影响           | 合理控制气体       |
| 8    | 1210         | 间隙漏           | 检泵               |
| 9    | 1211         | 油管漏           | 油管打压试验       |
| 10   | 1212         | 游动凡尔漏失     | 洗井或检泵         |
| 11   | 1213         | 固定凡尔漏失     | 洗井或检泵         |
| 12   | 1214         | 双凡尔漏失       | 洗井或检泵         |
| 13   | 1215         | 游动凡尔失灵     | 检泵               |
| 14   | 1216         | 固定凡尔失灵     | 检泵               |
| 15   | 1217         | 双凡尔失灵       | 检泵               |
| 16   | 1218         | 上死点别、碰     | 校正井口设备       |
| 17   | 1219         | 碰泵             | 上提（增大）防冲距 |
| 18   | 1220         | 柱塞未下入工作筒 | 下放（缩小）防冲距 |
| 19   | 1221         | 柱塞脱出工作筒   | 下放（缩小）防冲距 |
| 20   | 1222         | 杆断脱           | 替换抽油杆         |
| 21   | 1223         | 杆（泵）卡       | 洗井或检泵         |
| 22   | 1226         | 出煤渣           | 防煤渣             |
| 23   | 1227         | 严重出煤渣       | 防煤渣             |
| 24   | 1230         | 惯性载荷大       | 降低冲次           |
| 25   | 1232         | 采集异常         | 检查采集仪表       |
| 26   | 1302         | 停抽             |                    |

----[第一章 采集处理](https://github.com/cosog/acmd/blob/master/Chapter1/Chapter1.md)----[返回章节目录](https://github.com/cosog/acmd/blob/master/README.md)----[第三章 功图平衡](https://github.com/cosog/acmd/blob/master/Chapter3/Chapter3.md)----