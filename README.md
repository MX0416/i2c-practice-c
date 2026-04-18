### This project is a quick practice of the I2C serial protocol. 

This project is a quick practice for myself of the I2C protocol by writing and reading from a BMP180 temperature and pressure sensor



This block of code is a quick way of going through all possible I2C addresses and seeing which slave addresses are ready

```c
  printf("\nScan I2C1\n");
  // 2^7 = 128, total number of possible combinations for 7 bit slave address
  for (uint8_t i = 0; i < 128; i++) {
      // reminder that we need to shift the address left by 1 because the 8th bit is the r/w bit
      if (HAL_I2C_IsDeviceReady(&hi2c1, (uint16_t) (i << 1), 3, 5) == HAL_OK) {
          // We got an ack
          printf("%2x ", i);
      } else {
          printf("-- ");
      }
      if (i > 0 && (i + 1) % 16 == 0)
          printf("\n");
  }
```
