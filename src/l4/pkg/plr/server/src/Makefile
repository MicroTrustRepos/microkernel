PKGDIR      ?= ../..
L4DIR       ?= $(PKGDIR)/../..

TARGET      = romain

SYSTEMS     = x86-l4f

OBSERVERS = $(addprefix fault_handlers/, \
              debugger.cc \
              kiptime.cc \
			  lock_observer.cc \
              observer.cc \
              pagefault.cc \
              print_vcpu_state.cc \
              syscalls.cc \
              swifi.cc \
              trap_limit.cc \
              trap_observer.cc )

OBSERVERS += $(addprefix redundancy/, \
               dmr.cc)

ASMJIT = $(addprefix asmjit/, \
         Assembler.cc \
         AssemblerX86X64.cc \
         CodeGenerator.cc \
         Compiler.cc \
         CompilerX86X64.cc \
         CpuInfo.cc \
         Defs.cc \
         DefsX86X64.cc \
         Logger.cc \
         MemoryManager.cc \
         Operand.cc \
         OperandX86X64.cc \
         Platform.cc \
         Util.cc)

# list your .c or .cc files here
SRC_C       =
SRC_S       = instruction_length.S
SRC_CC      = main.cc \
              manager.cc \
              memory.cc \
              app_loading.cc \
              app_thread.cc \
              handler.cc \
              emulation.cc \
              $(OBSERVERS) \
              $(ASMJIT)

#SRC_CC += gdb_stub/gdb.cc \
#          gdb_stub/tcp_connection.cc \
#          gdb_stub/serial_connection.cc


# list requirements of your program here
REQUIRES_LIBS = libvcpu libstdc++ libloader libudis86 libiniparser libpthread \
                cxx_io libio-vbus
#REQUIRES_LIBS += lwip liblwip_netif_ankh

include $(L4DIR)/mk/prog.mk

DEFINES += -D__L4
CXXFLAGS += -Wno-parentheses -Wno-unused -Wno-reorder -Wno-missing-field-initializers \
            -Wno-sequence-point -Wno-sign-compare -Wno-missing-braces -Wno-uninitialized \
            -Wno-missing-declarations -Wno-format -Wno-write-strings
CXXFLAGS += $(call checkcxx,-std=c++11)
