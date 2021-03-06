# superpin
Super-fast Arduino pin-manipulation macros

``` C
struct Pin {
  uint8_t bit;
  uint8_t *reg;
};

struct Pin pin_output(uint8_t n) {
  struct Pin pin = { digitalPinToBitMask(n), portOutputRegister(digitalPinToPort(n)) };
  return pin;
}

struct Pin pin_input(uint8_t n) {
  struct Pin pin = { digitalPinToBitMask(n), portInputRegister(digitalPinToPort(n)) };
  return pin;
}

#define pin_high(p) (*p.reg |= p.bit)
#define pin_low(p) (*p.reg &= ~p.bit)
#define pin_read(p) (*p.reg & p.bit)
```
