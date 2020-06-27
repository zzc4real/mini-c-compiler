JAVAC = javac
JAVA = java
CLASSPATH = .

init:
	$(JAVAC) JLex/*.java
	$(JAVAC) java_cup/runtime/*.java
	$(JAVAC) java_cup/*.java

parse: minic.cup
	$(JAVA) -classpath $(CLASSPATH) java_cup.Main minic.cup

lex: minic.lex
	$(JAVA) JLex.Main minic.lex
	mv minic.lex.java Yylex.java

build: sym.java parser.java Yylex.java
	$(JAVAC) absyn/*.java
	$(JAVAC) -d $(CLASSPATH) sym.java parser.java Yylex.java

all: init
	$(JAVA) -classpath $(CLASSPATH) java_cup.Main minic.cup
	$(JAVA) JLex.Main minic.lex
	mv minic.lex.java Yylex.java
	$(JAVAC) absyn/*.java
	$(JAVAC) -d $(CLASSPATH) sym.java parser.java Yylex.java

run:
	$(JAVA) -classpath $(CLASSPATH) Collect.parser

test:
	$(JAVA) -classpath $(CLASSPATH) Collect.parser < sample.c

vclean:
	-rm *~
	-rm *.out
	-rm *.txt
	-rm *.class
	-rm absyn/*.class
	-rm java_cup/*.class
	-rm Collect/*.class
	-rm Yylex.java
	-rm parser.java
	-rm sym.java
	-rm java_cup/runtime/*.class
	-rm -r Collect/
