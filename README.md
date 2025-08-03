# for_internship
# MPU6050 Manual I2C Interface (Without Wire.h)

## 📌 Overview
This project demonstrates **manual I2C (bit-banging)** communication between an **Arduino** and the **MPU6050 IMU sensor**, without using any libraries such as `Wire.h` or sensor-specific drivers.  
The code manually implements the I2C protocol by toggling SDA and SCL pins, writes configuration values to the MPU6050, and reads raw accelerometer and gyroscope data.

---

## 🛠 Hardware Setup
| MPU6050 Pin | Arduino Pin |
|-------------|-------------|
| VCC         | 5V (or 3.3V) |
| GND         | GND         |
| SDA         | D4          |
| SCL         | D5          |

⚠ **Pull-up resistors (4.7kΩ)** are required on SDA and SCL lines.

---

## 📜 Code Features
✅ Manual bit-banging I2C implementation  
✅ Functions for `start`, `stop`, `write_byte`, `read_byte`  
✅ MPU6050 initialization (`PWR_MGMT_1` register write)  
✅ Burst read of 14 bytes (accel, temp, gyro data)  
✅ Prints raw values to Serial Monitor  

---

## ▶️ Expected Serial Output
Once uploaded and running on hardware, the **Serial Monitor (9600 baud)** will show output like:
MPU6050 Initialized
AX: 1234 AY: -456 AZ: 16789 | GX: 120 GY: -230 GZ: 45
AX: 1250 AY: -440 AZ: 16810 | GX: 110 GY: -220 GZ: 60
AX: 1240 AY: -450 AZ: 16795 | GX: 115 GY: -225 GZ: 50


Values will change as you move/rotate the sensor.

---

## 📝 Approach
1. **I2C Bit-Banging:**  
   - Manually toggled SDA and SCL pins to generate start, stop, ACK/NACK, and data bits.  
2. **MPU6050 Initialization:**  
   - Wrote `0x00` to `PWR_MGMT_1` register (0x6B) to wake up the sensor.  
3. **Burst Data Read:**  
   - Performed a multi-byte read starting from register `0x3B` to get 14 bytes (Accel + Temp + Gyro).  
4. **Data Parsing:**  
   - Combined high and low bytes into signed 16-bit integers.  
5. **Serial Output:**  
   - Printed raw values at 500 ms intervals.

---

## ⚠ Limitations
- Without real hardware, this code cannot be fully tested.  
- I2C timing (`i2c_delay`) may need slight tuning on real hardware.  
- Logic analyzer/oscilloscope is useful for debugging ACK/NACK issues.

---

## 📧 Submission Info
- **Files Included:**  
  - `codee.txt` (source code)  
  - `README.md` (this file)  




