SRC=src
INC=include
OBJ=obj
BIN=bin
CXX=g++
LIB=lib
CPPFLAGS=-Wall -g -I$(INC) -c


all:$(BIN)/pruebatraductor
# ************ Generación de documentación ******************
documentacion:
	@echo Creando documentacion...
	@doxygen doc/doxys/Doxyfile

	
# ************ Compilación de módulos ************
$(BIN)/pruebatraductor:$(OBJ)/pruebatraductor.o $(LIB)/libtraductor.a
	@echo Creando el ejecutable bin/pruebatraductor...
	@$(CXX) -o $(BIN)/pruebatraductor $(OBJ)/pruebatraductor.o -I$(INC) -L$(LIB) -ltraductor

$(LIB)/libtraductor.a:$(OBJ)/palabra.o $(OBJ)/diccionario.o $(OBJ)/traductor.o
	@echo Creando la libreria...
	@ar rvs $(LIB)/libtraductor.a $(OBJ)/palabra.o $(OBJ)/diccionario.o $(OBJ)/traductor.o 

$(OBJ)/palabra.o:$(SRC)/palabra.cpp
	@echo Creando el modulo objeto obj/palabra.o ...
	@$(CXX) $(CPPFLAGS)  -o $(OBJ)/palabra.o $(SRC)/palabra.cpp -I$(INC)

$(OBJ)/diccionario.o:$(SRC)/diccionario.cpp
	@echo Creando el modulo objeto obj/diccionario.o ...
	@$(CXX) $(CPPFLAGS)  -o $(OBJ)/diccionario.o $(SRC)/diccionario.cpp -I$(INC)

$(OBJ)/traductor.o:$(SRC)/traductor.cpp
	@echo Creando el modulo objeto obj/traductor.o ...
	@$(CXX) $(CPPFLAGS)  -o $(OBJ)/traductor.o $(SRC)/traductor.cpp -I$(INC)

$(OBJ)/pruebatraductor.o:$(SRC)/pruebatraductor.cpp
	@echo Creando el modulo objeto obj/pruebatraductor.o
	@$(CXX) $(CPPFLAGS)  -o $(OBJ)/pruebatraductor.o $(SRC)/pruebatraductor.cpp -I$(INC) 


# ************ Limpieza ************
clean:
	@echo Limpiando...
	@-rm $(OBJ)/*.o $(LIB)/*.a $(BIN)/*
#

mrproper:clean
	@-rm -dfr doc/html/