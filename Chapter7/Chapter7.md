# 第七章 转速计产

- [第七章 转速计产](Chapter7.md#第七章-转速计产)
   - [7.1 输入文本](Chapter7.md#71-输入文本)
     - [7.1.1 输入参数说明](Chapter7.md#711-输入参数说明)
     - [7.1.2 输入实例](Chapter7.md#712-输入实例)
	 - [7.1.3 数据收集表](Chapter7.md#713-数据收集表)
   - [7.2 输出文本](Chapter7.md#72-输出文本)
     - [7.2.1 输出参数说明](Chapter7.md#721-输出参数说明)
     - [7.2.2 输出实例](Chapter7.md#722-输出实例)

## 7.1 输入文本 

### 7.1.1 输入参数说明

*表7-1 输入参数说明表*

| 代码                               | 名称             | 单位      | 类型     | 必填     | 备注                                           |
|------------------------------------|------------------|-----------|----------|----------|------------------------------------------------|
| AKString                           | 应用密钥         |           | string   |          | 预留字段                                       |
| WellName                           | 井名             |           | string   | *&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    |                |
| AcquisitionTime                    | 采集时间         |           | string   | *        |                                                |
| RPM                                | 转速             | r/min     | float64  | *        |                                                |
| **FluidPVT**                       | **流体PVT物性**  |           |          |          |                                                |
| CrudeOilDensity                    | 原油密度         | g/cm^3    | float64  | *        |                                                |
| WaterDensity                       | 水密度           | g/cm^3    | float64  | *        |                                                |
| NaturalGasRelativeDensity          | 天然气相对密度   |           | float64  | *        |                                                |
| SaturationPressure                 | 饱和压力         | MPa       | float64  | *        |                                                |
| **Reservoir**                      | **油层数据**   |           |          |          |                                                |
| Depth                              | 油层中部深度       | m         | float64  | *        | 油层中部（测量）深度                         |
| Temperature                        | 油层中部温度       | ℃        | float64  | *        |                                  |
| **WellboreTrajectory**             | **井身轨迹**     |           |          |          |                                                |
| MeasuringDepth                     | 测量深度         | m         | []float64  |          | 如直井可不填写，非直井按 实际数据填写          |
| DeviationAngle                     | 井斜角           | °         | []float64  |          |                                                |
| AzimuthAngle                       | 方位角           | °         | []float64  |          |                                                |
| **RodString**                      | **抽油杆参数**   |           |          |          |                                                |
| Type                               | 抽油杆类型       |           | int      |          | 1-实心抽油杆，2-空心抽油杆                     |
| Grade                              | 杆级别           |           | string   | *        | A,B,C,K,D,KD,HL,HY                             |
| Length                             | 杆长             | m         | float64  | *        | 不包含光杆和泵上拉杆                           |
| OutsideDiameter                    | 杆外径           | m         | float64  | *        |                                                |
| InsideDiameter                     | 杆内径           | m         | float64  |          | 为空心抽油杆预留                               |
| Density                            | 杆密度           | g/cm^3    | float64  |          | 默认值为7.85                                   |
| WeightPerMeter                     | 每米杆重         | kN/m      | float64  |          | 杆重（含节箍）                                 |
| **TubingString**                   | **油管参数**     |           |          |          |                                                |
| Grade                              | 油管钢级         |           | string   |          | 详见表底注释[1]                                |
| OutsideDiameter                    | 油管外径         | m         | float64  |          |                                                |
| InsideDiameter                     | 油管内径         | m         | float64  | *        | 默认0.062m                                     |
| Length                             | 油管长度         | m         | float64  |          |                                                |
| Density                            | 油管密度         | g/cm^3    | float64  |          |                                                |
| WeightPerMeter                     | 每米管重         | kN/m      | float64  |          |                                                |
| **Pump**                           | **螺杆泵参数**   |           |          |          |                                                |
| Manufacturer                       | 生产厂商         |           | string   |          |                                                |
| Model                              | 型号             |           | string   |          |                                                |
| BarrelLength                       | 泵筒长           | m         | float64  |          |                                                |
| BarrelSeries                       | 泵级数           |           | int      |          |                                                |
| RotorLength                        | 转子长           | m         | float64  |          |                                                |
| RotorDiameter                      | 转子直径         | m         | float64  |          |                                                |
| QPR                                | 每转公称排量     | m^3/r     | float64  | *        |                                                |
| **TailTubingString**               | **尾管参数**     |           |          |          |                                                |
| EquipmentType                      | 设备类型         |           | string   |          | 详见表底注释[2]                                |
| Grade                              | 尾管钢级         |           | string   |          | 详见表底注释[1]                                |
| OutsideDiameter                    | 尾管外径         | m         | float64  |          |                                                |
| InsideDiameter                     | 尾管内径         | m         | float64  |          |                                                |
| Length                             | 尾管长度         | m         | float64  |          |                                                |
| Density                            | 尾管密度         | g/cm^3    | float64  |          |                                                |
| WeightPerMeter                     | 每米管重         | kN/m      | float64  |          |                                                |
| GasAnchorEfficiency                | 气锚效率         | 小数      | float64  |          |                                                |
| **CasingString**                   | **生产套管参数** |           |          |          |                                                |
| Grade                              | 套管钢级         |           | string   |          |                                                |
| OutsideDiameter                    | 套管外径         | m         | float64  |          |                                                |
| InsideDiameter                     | 套管内径         | m         | float64  | *        | 默认0.127m                                     |
| Length                             | 套管长度         | m         | float64  |          |                                                |
| Density                            | 套管密度         | g/cm^3    | float64  |          |                                                |
| WeightPerMeter                     | 每米管重         | kN/m      | float64  |          |                                                |
| **Production**                     | **生产数据**     |           |          |          |                                                |
| WaterCut                           | 体积含水率       | %         | float64  | *        |                                                |
| ProductionGasOilRatio              | 生产气油比       | m^3/t     | float64  | *        |                                                |
| TubingPressure                     | 油压             | MPa       | float64  | *        | 如无油压数据，可录入回压数据                   |
| CasingPressure                     | 套压             | MPa       | float64  | *        |                                                |
| BackPressure                       | 回压             | MPa       | float64  |          | 如无油压数据，可录入回压数据                   |
| WellHeadFluidTemperature           | 井口油温         | ℃        | float64  |          |                                                |
| ProducingfluidLevel                | 动液面           | m         | float64  | *        |                                                |
| PumpSettingDepth                   | 泵挂             | m         | float64  | *        |                                                |
| **SystemEfficiency**               | **系统效率**     |           |          |          |                                                |
| MotorInputWatt                     | 电机输入有功功率 | kW        | float64  |          | 用于计算系统效率                               |
| **ManualIntervention**             | **人工干预**     |           |          |          |                                                |
| Code                               | 人工干预代码     |           | int      |          | 0-不干预，其他工况类型-干预                    |
| NetGrossRatio                      | 净毛比           | 小数      | float64  |          | 实际产量/软件计算产量，不标定产量直接填写1     |

**[1]** *钢级:H40,J55,K55,N80,M65,L80,C90,C95,T59,P110,Q125*  
**[2]** *尾管设备类型:TailTubing-尾管，FilterTubing-滤管（花管），Anchor-锚定器，GasAnchor-油气分离器*

### 7.1.2 输入实例

```
{
    "WellName": "03-033",
    "AcquisitionTime": "2018-10-21 09:00:00",
    "RPM": 90.15,
    "FluidPVT": {                                 //（1）流体PVT物性
        "CrudeOilDensity": 0.86,
        "WaterDensity": 1.00,
        "NaturalGasRelativeDensity": 0.7,
        "SaturationPressure": 9.6
    },
    "Reservoir": {                                //（2）油层数据
        "Depth": 1350.15,
        "Temperature": 66.15
    },
    "WellboreTrajectory": {                        //（3）井身轨迹
        "MeasuringDepth": [
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
    "RodString": {                                 //（4）抽油杆参数
        "EveryRod": [
            {
                "Type": 1,
                "Grade": "D",
                "Length": 246.8,
                "OutsideDiameter": 0.022,
                "InsideDiameter": 0.000,
                "Density": 7.85
            },
            {
                "Type": 1,
                "Grade": "D",
                "Length": 411.3,
                "OutsideDiameter": 0.019,
                "InsideDiameter": 0.000,
                "Density": 7.85
            }
        ]
    },
    "TubingString": {                              //（5）油管参数
        "EveryTubing": [
            {
                "Grade": "K55",
                "length": 1000.15,
                "OutsideDiameter": 0.073,
                "InsideDiameter": 0.062,
                "Density": 7.85,
                "WeightPerMeter": 0.00
            }
        ]
    },
    "Pump": {                                     //（6）螺杆泵参数
        "Manufacturer":"大庆",
		"Model":"GLB500-20",
		"BarrelLength": 10.15,
        "BarrelSeries": 20,
        "RotorLength": 8.15,
        "RotorDiameter": 0.059,
        "QPR": 0.0005

    },
    "CasingString": {                              （7）套管参数
        "EveryCasing": [
            {
                "Grade": "K55",
                "OutsideDiameter": 0.139,
                "InsideDiameter": 0.127,
                "Length": 3000.15,
                "Density": 7.85,
                "WeightPerMeter": 0
            }
        ]
    },
    "Production": {                               //（8）生产数据
        "WaterCut": 80.7,
        "ProductionGasOilRatio": 4.15,
        "TubingPressure": 0.7,
        "CasingPressure": 0.6,
		"BackPressure": 0,
        "WellHeadFluidTemperature": 35.15,
        "ProducingfluidLevel": 645.25,
        "PumpSettingDepth": 674.35
    },

    "SystemEfficiency": {                          //（9）系统效率
        "MotorInputWatt": 2.3
    },
    "ManualIntervention": {                        //（10）人工干预
        "Code": 0,
        "NetGrossRatio": 1.00
    }
}
```

### 7.1.3 数据收集表

*表7-2 区块数据*

| 序号      | 区块名称*  | 原油密度(g/cm^3)*   | 天然气相对密度*  | 饱和压力(MPa)*  | 中部深度(m)*  | 中部温度(℃) *|  
|:----------|:-----------|:--------------------|:-----------------|:----------------|:--------------|:---------------|
| 1         |            |                     |                  |                 |               |                |
| 2         |            |                     |                  |                 |               |                |


*表7-3 井身轨迹数据表*

| 序号      | 井名  | 测量深度 (m)  | 井斜角(°)  | 方位角(°)  |
|:----------|:------|:--------------|:-----------|:-----------|
| 1         |       |               |            |            |
| 2         |       |               |            |            |

*表7-4 生产数据*

| 序号      | 井名                 | 含水率(%)*           | 油压(回压)(MPa)*    | 套压(MPa)*          | 动液面(m)*          | 井口流温(℃)       | 生产气油比 *      |     
|:----------|:---------------------:|:----------------:|:------------------:|:--------------------:|:--------------------:|:-------------------:|:---------:|
| 1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |         |             |               |               |                    |                   |                  |
| 2        |                     |                     |                    |                    |                    |                   |                  |
| **序号** | **泵筒长(m)**         | **泵级数**        | **转子直径(mm)**   | **公称排量(ml/转)***    | **油管内径(m)*** | **一级杆级别*** | **一级杆外径(m)***  |
| 1        |                     |                     |                    |                    |                    |                   |                  |
| 2        |                     |                     |                    |                    |                    |                   |                  |
| **序号** | **一级杆长度(m)***  | **二级杆级别***  | **二级杆外径(m)***    |**二级杆长度(m)***  |**三级杆级别***  | **三级杆外径(m)***  | **三级杆长度(m)***            |
| 1        |                     |                     |                    |                    |                    |                   |                  |
| 2        |                     |                     |                    |                    |                    |                   |                  |


## 7.2 输出文本

### 7.2.1 输出参数说明

*表7-5 输出参数说明表*

| 代码                               | 名称               | 单位        | 类型     | 备注                                    |
|------------------------------------|--------------------|-------------|----------|-----------------------------------------|
| WellName                           | 井名               |             | string   |                                         |
| AcquisitionTime                    | 采集时间           |             | string   |                                         |
| RPM                                | 转速               | r/min       | float64  |                                         |
| RunStatus                          | 运行状态           |             | int      | 0-停止 1-运行                           |
| **CalculationStatus**              | **计算状态**       |             |          |                                         |
| ResultStatus                       | 计算结果状态       |             | int      | 详见表底注释[1]                         |
| ResultCode                         | 工况类型           |             | int      |                                         |
| **Verification**                   | **数据校验**       |             |          |                                         |
| ErrorCounter                       | 错误参数计数器     |             | int      | 错误参数个数                            |
| ErrorString                        | 错误参数字符串     |             | string   | 数据错误，计算不成功                    |
| WarningCounter                     | 报警计数器         |             | int      | 报警参数个数                            |
| WarningString                      | 报警字符串         |             | string   | 报警参数（取默认值，计算正常进行）      |
| **RodString**                      | **抽油杆参数**     |             |          |                                         |
| CNT                                | 杆数               |             | int      |                                         |
| LengthAll                          | 总杆长             | m           | float64  |                                         |
| WeightAll                          | 总杆重             | kN          | float64  |                                         |
| BuoyancyForceAll                   | 总浮力             | kN          | float64  |                                         |
| LengthString                       | 杆长字符串         |             | string   |                                         |
| GradeString                        | 杆级别字符串       |             | string   |                                         |
| OutsideDiameterString              | 杆外径字符串       |             | string   |                                         |
| InsideDiameterString               | 杆内径字符串       |             | string   |                                         |
| **EveryRod**                       | **每级杆参数**     |             |          |                                         |
| Type                               | 抽油杆类型         |             | int      | 1-实心抽油杆 2－空心抽油杆              |
| Grade                              | 杆级别             |             | string   | A,B,C,K,D,KD,HL,HY                      |
| Length                             | 杆长               | m           | float64  |                                         |
| OutsideDiameter                    | 杆外径             | m           | float64  |                                         |
| InsideDiameter                     | 杆内径             | m           | float64  |                                         |
| Area                               | 杆截面积           | m^2         | float64  |                                         |
| Weight                             | 杆重               | kN          | float64  |                                         |
| BuoyancyForce                      | 杆柱浮力           | kN          | float64  |                                         |
| Density                            | 杆柱密度           | g/cm^3      | float64  |                                         |
| WeightPerMeter                     | 每米杆重           | kN/m        | float64  |                                         |
| TE                                 | 抽油杆最小抗张强度 | MPa         | float64  |                                         |
| SF                                 | 抽油杆使用系数     | 小数        | float64  |                                         |
| DampingFactor                      | 每级杆的阻尼系数   |             | float64  |                                         |
| MaxStress                          | 各级杆最大应力     | MPa         | float64  |                                         |
| MinStress                          | 各级杆最小应力     | MPa         | float64  |                                         |
| AllowableStress                    | 各级杆许用应力     | MPa         | float64  |                                         |
| StressRatio                        | 应力范围比         | 小数        | float64  |                                         |
| **Production**                     | **生产参数**       |             |          |                                         |
| WaterCut                           | 体积含水率         | %           | float64  |                                         |
| ProductionGasOilRatio              | 生产气油比         | m^3/t     | float64  |                                         |
| TubingPressure                     | 油压               | MPa         | float64  |                                         |
| CasingPressure                     | 套压               | MPa         | float64  |                                         |
| BackPressure                       | 回压               | MPa         | float64  |                                         |
| WellHeadFluidTemperature           | 井口流温           | ℃          | float64  |                                         |
| ProducingfluidLevel                | 动液面             | m           | float64  |                                         |
| PumpSettingDepth                   | 泵挂               | m           | float64  |                                         |
| Submergence                        | 沉没度             | m           | float64  |                                         |
| PumpIntakeP                        | 泵入口压力         | MPa         | float64  |                                         |
| PumpIntakeT                        | 泵入口温度         | ℃          | float64  |                                         |
| PumpIntakeGOL                      | 泵入口就地气液比   | m^3/m^3      | float64  |                                         |
| PumpIntakeVisl                     | 泵入口粘度         | mPa·s       | float64  |                                         |
| PumpIntakeBo                       | 泵入口原油体积系数 | 小数        | float64  |                                         |
| PumpOutletP                        | 泵出口压力         | MPa         | float64  |                                         |
| PumpOutletT                        | 泵出口温度         | ℃          | float64  |                                         |
| PumpOutletGOL                      | 泵出口就地气液比   | m^3/m^3      | float64  |                                         |
| PumpOutletVisl                     | 泵出口粘度         | mPa·s       | float64  |                                         |
| PumpOutletBo                       | 泵出口原油体积系数 | 小数        | float64  |                                         |
| TheoreticalProduction              | 理论排量           | m^3/d       | float64  |                                         |
| LiquidVolumetricProduction         | 产液量（方）       | m^3/d       | float64  |                                         |
| OilVolumetricProduction            | 产油量（方）       | m^3/d       | float64  |                                         |
| WaterVolumetricProduction          | 产水量（方）       | m^3/d       | float64  |                                         |
| LiquidWeightProduction             | 产液量（吨）       | t/d         | float64  |                                         |
| OilWeightProduction                | 产油量（吨）       | t/d         | float64  |                                         |
| WaterWeightProduction              | 产水量（吨）       | t/d         | float64  |                                         |
| **PumpEfficiency**                 | **泵效**           |             |          |                                         |
| PumpEff1                           | 容积效率           | 小数        | float64  |                                         |
| PumpEff2                           | 液体收缩系数       | 小数        | float64  |                                         |
| PumpEff                            | 泵效               | 小数        | float64  |                                         |
| **SystemEfficiency**               | **系统效率分析**   |             |          |                                         |
| SystemEfficiency                   | 系统效率           | 小数        | float64  |                                         |
| MotorInputWatt                     | 电机输入有功功率   | kW          | float64  |                                         |
| WaterPower                         | 水功率             | kW          | float64  |                                         |

### 7.2.2 输出实例

```
{
    "WellName": "03-033",
    "AcquisitionTime": "2018-10-21 09: 00: 00",
    "RPM": 90.15,
    "RunStatus": 1,
    "CalculationStatus": {                         //（1）计算状态
        "ResultStatus": 1,
        "ResultCode": 0
    },
    "Verification": {                              //（2）数据校验
        "ErrorCounter": 0,
        "ErrorString": "",
        "WarningCounter": 0,
        "WarningString": ""
    },
    "RodString": {                                 //（3）抽油杆参数
        "CNT": 2,
        "LengthAll": 658.1,
        "WeightAll": 16.19,
        "BuoyancyForceAll": 2.01,
        "LengthString": "246.80/411.30",
        "GradeString": "D/D",
        "OutsideDiameterString": "0.022/0.019",
        "InsideDiameterString": "0.000/0.000",
        "EveryRod": [
            {
                "Type": 1,
                "Grade": "D",
                "Length": 246.8,
                "OutsideDiameter": 0.022,
                "InsideDiameter": 0,
                "Area": 0.00038,
                "Weight": 7.22,
                "WeightPerMeter": 0.0292,
                "BuoyancyForce": 0.895,
                "Density": 7.85,
                "TE": 793,
                "SF": 1,
                "DampingFactor": 0,
                "MaxStress": 0,
                "MinStress": 0,
                "AllowableStress": 0,
                "StressRatio": 0
            },
            {
                "Type": 1,
                "Grade": "D",
                "Length": 411.3,
                "OutsideDiameter": 0.019,
                "InsideDiameter": 0,
                "Area": 0.000284,
                "Weight": 8.97,
                "WeightPerMeter": 0.0218,
                "BuoyancyForce": 1.11,
                "Density": 7.85,
                "TE": 793,
                "SF": 1,
                "DampingFactor": 0,
                "MaxStress": 0,
                "MinStress": 0,
                "AllowableStress": 0,
                "StressRatio": 0
            }
        ]
    },
    "Production": {                                 //（4）生产数据
        "WaterCut": 80.7,
        "ProductionGasOilRatio": 4.15,
        "TubingPressure": 0.7,
        "CasingPressure": 0.6,
        "BackPressure": 0,
        "WellHeadFluidTemperature": 35.15,
        "ProducingfluidLevel": 645.25,
        "PumpSettingDepth": 674.35,
        "Submergence": 29.1,
        "PumpIntakeP": 0.996,
        "PumpIntakeT": 62.86,
        "PumpIntakeGOL": 0.00696,
        "PumpIntakeVisl": 0.935,
        "PumpIntakeBo": 1.05,
        "PumpOutletP": 7,
        "PumpOutletT": 62.76,
        "PumpOutletGOL": 0,
        "PumpOutletVisl": 0.932,
        "PumpOutletBo": 1.05,
        "TheoreticalProduction": 64.91,
        "LiquidVolumetricProduction": 63.9,
        "OilVolumetricProduction": 12.33,
        "WaterVolumetricProduction": 51.57,
        "LiquidWeightProduction": 62.17,
        "OilWeightProduction": 10.61,
        "WaterWeightProduction": 51.57
    },
    "PumpEfficiency": {                               //（5）泵效
        "PumpEff1": 0.993,
        "PumpEff2": 0.991,
        "PumpEff": 0.984
    },
    "SystemEfficiency": {                             //（6）系统效率
        "SystemEfficiency": 2.01,
        "MotorInputWatt": 2.3,
        "WaterPower": 4.62
    }
}
```

----[第六章 插件](.././Chapter6/Chapter6.md)----[返回章节目录](.././README.md)----[第八章 功图平衡](.././Chapter8/Chapter8.md)----