
# files

EXE = senpai

OBJS = attack.o bit.o common.o eval.o fen.o game.o gen.o \
       hash.o libmy.o list.o main.o math.o move.o pawn.o \
       pos.o score.o search.o sort.o thread.o tt.o util.o var.o

# rules

all: $(EXE)

clean:
	$(RM) $(OBJS) .depend # keep exe

# general

CXX      = g++ # g++ if you must, but beware of NPS!
CXXFLAGS = -pthread
LDFLAGS  = -pthread

# warnings

CXXFLAGS += -ansi -pedantic -Wall -Wextra

# C++

CXXFLAGS += -std=c++11 -fno-rtti

# optimisation

#CXXFLAGS += -O3 -mcpu=cortex-a53 -mfloat-abi=hard -mfpu=neon-fp-armv8 -mneon-for-64bits -mtune=cortex-a53 ##Pi 3
#CXXFLAGS +=  -mcpu=cortex-a7 -mfpu=neon-vfpv4 -mneon-for-64bits ## Pi 2
##Pi 6
CXXFLAGS += -O3 -mcpu=arm1176jzf-s -mfpu=vfp -march=armv6
LDFLAGS  += -O3

CXXFLAGS += -flto
LDFLAGS  += -flto

# dependencies

$(EXE): $(OBJS)
	$(CXX) $(LDFLAGS) -o $@ $(OBJS)

.depend:
	$(CXX) $(CXXFLAGS) -MM $(OBJS:.o=.cpp) > $@

include .depend

