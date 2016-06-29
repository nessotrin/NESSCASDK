PROJECT_NAME ?= Spassus2

PROJECT_FOLDER = ../Projects/$(PROJECT_NAME)

SRC_DIR = $(PROJECT_FOLDER)/src

AUTO_CPPS = $(shell find $(SRC_DIR) -type f -name "*.cpp")

AUTO_FOLDER = $(shell find $(SRC_DIR) -type d)

AUTO_INCLUDE = $(shell find $(SRC_DIR) -type d | sed 's;$(SRC_DIR);-I $(SRC_DIR);')

CXX = clang++
CXX_FLAGS = -O0 -fstack-protector-all -std=c++11 -Wfatal-errors -Wall -Wextra -Wpedantic -Wconversion -Wshadow -g 
BUILD_FLAGS = -I ../Calculib2/include $(AUTO_INCLUDE) -D CALCULIB
LINK_FLAGS = -lsfml-network -lsfml-graphics -lsfml-window -lsfml-system

# Final binary
BIN = addin
# Put all auto generated stuff to this build dir.
BUILD_DIR = $(PROJECT_FOLDER)/build



# List of all .cpp source files.
CPPS =  $(AUTO_CPPS)

# All .o files go to build dir.
OBJ = $(patsubst $(SRC_DIR)/%.cpp, $(BUILD_DIR)/%.o,$(CPPS))
# $(CPPS:$(PROJECT_FOLDER)/%.cpp=$(BUILD_DIR)/%.o)
# Gcc/Clang will create these .d files containing dependencies.
DEP = $(OBJ:%.o=%.d)


# Default target named after the binary.
$(BIN) : $(BUILD_DIR)/$(BIN)

# Actual target of the binary - depends on all .o files.
$(BUILD_DIR)/$(BIN) : $(OBJ)
	@# Create build directories - same structure as sources.
	@mkdir -p $(@D)
	@# Just link all the object files.
	$(CXX) $^ ../Calculib2/lib/Calculib2.a -o $@ $(CXX_FLAGS) $(LINK_FLAGS)

# Include all .d files
-include $(DEP)

# Build target for every single object file.
# The potential dependency on header files is covered
# by calling `-include $(DEP)`.
$(BUILD_DIR)/%.o : $(SRC_DIR)/%.cpp
	@mkdir -p $(@D)
	@# The -MMD flags additionaly creates a .d file with
	@# the same name as the .o file.
	$(CXX) -c $< -o $@ $(CXX_FLAGS) -MMD $(BUILD_FLAGS)

.PHONY : clean
clean :
	# This should remove all generated files.
	-@rm $(BUILD_DIR)/$(BIN) $(OBJ) $(DEP)
