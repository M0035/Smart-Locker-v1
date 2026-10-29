# 编译器
CC = gcc
# 编译选项：-Wall警告，-g gdb调试
CFLAGS = -Wall -g
# 链接库：sqlite3
LDFLAGS = -lsqlite3

# 目标程序名
TARGET = udpServer
# 源文件列表
SRCS = main.c server.c
# 自动生成目标文件列表 main.o server.o
OBJS = $(SRCS:.c=.o)

# 默认目标：make 就执行 all
all: $(TARGET)

# 链接规则：把 .o 合成可执行文件
$(TARGET): $(OBJS)
	$(CC) $(OBJS) -o $(TARGET) $(LDFLAGS)

# 编译规则：.c -> .o
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

# 清理：删除o文件和可执行程序
clean:
	rm -f $(OBJS) $(TARGET)

# 重新编译：先clean再all
rebuild: clean all

