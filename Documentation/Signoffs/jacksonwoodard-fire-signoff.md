# Fire Module Signoff

## Subsystem Function
The function of the fire module subsystem is to detect if a fire has ever occured in a specific room in a house. The system will work by using a IR Temperature Sensor that is installed on the ceiling of a room with a piece of copper that will be the source for the temperature sensor to aim at to recieve the temperature.

![firemodule](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/e768ff15-9812-4a0a-b979-6f65d493c14f)

## Constraints
| No. | Constraints | Origin |
| --- | ----------- | ------ |
|  1  | Shall be able to detect the temperature of the senosr and send the data to the head unit. | Project Team |
|  2  | Sensor shall not be a distraction to the homeowner | All External Stakeholders, Ethics, & Team Supervisor |

## Buildable Schematic

![BlockDiagram](https://github.com/jacksonrwoodard/HouseHealthMonitoring/assets/142913669/af28eb34-ada7-40e6-9d11-8862e578e8f3)

The picture shown above is the detailed block diagram of the MLX90614 IR Temperature Sensor. The MLX90614 is controlled by an internal state machine that controls the measurements and calculations of the object and ambient temperatures and does the post-processing to output the data [1].
## Analysis

## Bill of Materials (BOM)
| DEVICE | Quantity | Price Per Unit | Total Price |
| ------ | -------- | -------------- | ----------- |
|

## References

[1] DigiKey, “MLX90614ESF-BAA-000-SP Melexis Technologies NV - DigiKey,” Melexis Technologies NV MLX90614ESF-BAA-000-SP, https://www.digikey.com/en/products/detail/melexis-technologies-nv/MLX90614ESF-BAA-000-SP/5414793 (accessed Oct. 24, 2023). 
