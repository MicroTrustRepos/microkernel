PKGDIR ?=	../../..
L4DIR ?=	$(PKGDIR)/..

SYSTEMS = x86-l4f

TARGET                = pthread_mutex
SRC_C = main.c

include $(L4DIR)/mk/prog.mk

LDFLAGS += -lpthread_rep -luc_c
