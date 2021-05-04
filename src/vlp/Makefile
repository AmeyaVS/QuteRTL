PKGFLAG = -D_WITH_BDD_DEBUG
EXTHDRS = VLGlobe.h vlpBase.h vlpDefine.h vlpEnum.h vlpItoStr.h vlpOpNode.h vlpSubElement.h vlpCtrlNode.h vlpDesign.h vlpHierTree.h vlpModule.h vlpStack.h y.tab.hpp lib.tab.hpp parser.h vlpCmd.h vlpCU.h vlpFSM.h
 
LEX  = flex
YACC = bison
YFLAG = -d -v

CSRCS = lex.yy.cpp lex.lib.cpp
COBJS = lex.yy.o lex.lib.o

include ../Makefile.in
include ../Makefile.lib

cleanly:
	@rm -f lex.yy.cpp
	@rm -f lex.lib.cpp
	@rm -f y.tab.*
	@rm -f lib.tab.*

lex.yy.cpp : vlpLex.l y.tab.hpp
	@echo "> lex: $<"
	@$(LEX) -o lex.yy.cpp vlpLex.l

lex.lib.cpp : vlpLibLex.l lib.tab.hpp
	@echo "> lex: $<"
	@$(LEX) -Plib -o lex.lib.cpp vlpLibLex.l

y.tab.cpp y.tab.hpp &: vlpYacc.y
	@echo "> Yacc: $<"
	@$(YACC) $(YFLAG) -o y.tab.cpp vlpYacc.y

lib.tab.cpp lib.tab.hpp &: vlpLibYacc.y
	@echo "> Yacc: $<"
	@$(YACC) $(YFLAG) -p lib -o lib.tab.cpp vlpLibYacc.y

lex.yy.o : lex.yy.cpp

lex.lib.o : lex.lib.cpp
