SRC_PATH := src
SOURCES := $(wildcard $(SRC_PATH)/*.c)
PROGRAM := clock
EXE_PATH := exe
OBJ_PATH := obj
LIB_FILES :=
LIB_PATH :=
SDCC_MMCU = mmcs51
IRAM_SIZE := 0x100
CODE_LOC  := 0x0000
DATA_LOC  := 0x30
SDCC_LIBS := $(addprefix -l, $(LIB_FILES))
FULL_LIB_NAMES := $(join $(LIB_PATH), $(addprefix lib,$(addsuffix .a,$(LIB_FILES))))

SDCC_OBJECTS := $(addprefix $(OBJ_PATH)/, $(notdir $(SOURCES:%.c=%.rel)))
HEX := $(addprefix $(EXE_PATH)/, $(addsuffix .hex, $(PROGRAM)))
IHX := $(addprefix $(EXE_PATH)/, $(addsuffix .ihx, $(PROGRAM)))

CC := sdcc
OBJ := packihx

INCLUDES := $(addprefix -I,$(addsuffix src, $(LIB_PATH)))
LINKS := $(addprefix -L,$(LIB_PATH))

SDCC_CFLAGS := -$(SDCC_MMCU)
SDCC_LFLAGS := $(LINKS) -$(SDCC_MMCU) --iram-size $(IRAM_SIZE) --code-loc $(CODE_LOC) --data-loc $(DATA_LOC)

export SDCC_MMCU
export SDCC_CFLAGS

.PHONY: all SDCC_BUILD clean $(FULL_LIB_NAMES)

all: SDCC_BUILD

SDCC_BUILD: $(FULL_LIB_NAMES) $(HEX)

$(HEX): $(IHX)
	$(OBJ) $< > $@

$(FULL_LIB_NAMES):
	$(MAKE) -C $(@D) clean
	$(MAKE) -C $(@D)

$(IHX): $(SDCC_OBJECTS)
	mkdir -p $(EXE_PATH)
	$(CC) $(SDCC_LFLAGS) -o $@ $^ $(SDCC_LIBS)

$(OBJ_PATH)/%.rel: $(SRC_PATH)/%.c
	mkdir -p $(OBJ_PATH)
	$(CC) $(INCLUDES) $(SDCC_CFLAGS) -c $< -o $(OBJ_PATH)/

clean:
	rm -rf $(EXE_PATH) $(OBJ_PATH)
