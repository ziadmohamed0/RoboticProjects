# Makefile for STM32F103C8T6 Robot Arm Project

# Compiler and tools
CC = arm-none-eabi-gcc
OBJCOPY = arm-none-eabi-objcopy
SIZE = arm-none-eabi-size

# Project name and directories
PROJECT = robot_arm
SRC_DIR = src
BUILD_DIR = build
INCLUDE_DIR = include

# Source files
SRCS = $(wildcard $(SRC_DIR)/*.c)
OBJS = $(SRCS:$(SRC_DIR)/%.c=$(BUILD_DIR)/%.o)

# MCU and toolchain flags
MCU = cortex-m3
LD_SCRIPT = stm32f103c8t6.ld
CFLAGS = -mcpu=$(MCU) -mthumb -Wall -O2 -ffunction-sections -fdata-sections \
         -I$(INCLUDE_DIR) -DSTM32F103xB
LDFLAGS = -T$(LD_SCRIPT) -Wl,--gc-sections

# Targets
all: $(BUILD_DIR)/$(PROJECT).elf

$(BUILD_DIR)/$(PROJECT).elf: $(OBJS)
	@mkdir -p $(BUILD_DIR)
	$(CC) $(CFLAGS) $(LDFLAGS) $^ -o $@
	$(OBJCOPY) -O ihex $@ $(BUILD_DIR)/$(PROJECT).hex
	$(OBJCOPY) -O binary $@ $(BUILD_DIR)/$(PROJECT).bin
	$(SIZE) $@

$(BUILD_DIR)/%.o: $(SRC_DIR)/%.c
	@mkdir -p $(BUILD_DIR)
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -rf $(BUILD_DIR)

flash: $(BUILD_DIR)/$(PROJECT).bin
	st-flash write $< 0x8000000

.PHONY: all clean flash
