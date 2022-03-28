# MM32_LD

MM32 Linker Description Files for GNU Linker at Link Phase.

```powershell
memory/MM32_4K_32K.ld ----> RAM=4K, ROM=32K
```

## Usage

**`memory/*.ld` IS FISRT**

@Command:

```bash
arm-none-eabi-gcc XXX.o ... -Tmemory/MM32_4K_32K.ld -Tcommon/sections.ld -Tlibs/libs.ld
```

@Makefile:

```makefile
...

LDSCRIPT = \
-Tld/memory/MM32_4K_32K.ld \
-Tld/common/sections.ld \
-Tld/libs/libs.ld 

...

LDFLAGS = $(MCU) --specs=nano.specs $(LDSCRIPT) $(LIBDIR) $(LIBS) -Wl,-Map=$(BUILD_DIR)/$(TARGET).map,--cref -Wl,--gc-sections

...
```

## Tree List

```bash
│ README.md
│  
├─common            # Common party
│  └─ sections.ld        
│
├─libs              # Libs/Third-party 
│  └─ libs.ld      
│
└─memory            # Chip Memory
   ├─ MM32_2K_16K.ld
   ├─ ...
   └─ MM32_128K_512K.ld
```
