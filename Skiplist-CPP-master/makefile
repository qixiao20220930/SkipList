/*
 * @Author: qixiao20220930 2457119625@qq.com
 * @Date: 2022-10-01 07:19:29
 * @LastEditors: qixiao20220930 2457119625@qq.com
 * @LastEditTime: 2022-10-16 10:26:03
 * @FilePath: \Skiplist-CPP-master\makefile
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
 */
CC=g++  
CXXFLAGS = -std=c++0x
CFLAGS=-I
skiplist: main.o 
	$(CC) -o ./bin/main main.o --std=c++11 -pthread 
	rm -f ./*.o

clean: 
	rm -f ./*.o
