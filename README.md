# I2C SLG Library

This is a library of GreenPAK SLG46826.

## Support Devices

- [SLG46826](https://www.renesas.com/us/en/products/programmable-mixed-signal-asic-ip-products/greenpak-programmable-mixed-signal-products/greenpak-system-programmability/slg46826-greenpak-programmable-mixed-signal-matrix-system-programmability)

## Usage
```c
#include "I2C_SLG46826.h"

I2C_SLG46826 slg(Wire);

#define SLG46826_I2C_SDA 32
#define SLG46826_I2C_SCL 33

void setup() {
  // Init Serial
  Serial.begin(115200);
  delay(500);

  // Init I2C
  Wire.begin(SLG46826_I2C_SDA, SLG46826_I2C_SCL);
}

void loop() {
  Serial.printf("SLG46826 SCAN\n");
  for (int i = 0; i < 16; i++) {
    if (slg.scanSlg(i)) {
      Serial.printf(" Control Code = %d\n", i);
    }
  }
  Serial.println();

  delay(5000);
}
```
