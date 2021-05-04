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
	@$(LEX) vlpLex.l
	@mv lex.yy.c lex.yy.cpp

lex.lib.cpp : vlpLibLex.l lib.tab.hpp
	@echo "> lex: $<"
	@$(LEX) -Plib vlpLibLex.l
	@mv lex.lib.c lex.lib.cpp

y.tab.cpp y.tab.hpp &: vlpYacc.y
	@echo "> Yacc: $<"
	@$(YACC) $(YFLAG) vlpYacc.y
	@mv vlpYacc.tab.c y.tab.cpp
	@mv vlpYacc.tab.h y.tab.hpp

lib.tab.cpp lib.tab.hpp &: vlpLibYacc.y
	@echo "> Yacc: $<"
	@$(YACC) $(YFLAG) -p lib vlpLibYacc.y
	@mv vlpLibYacc.tab.c lib.tab.cpp
	@mv vlpLibYacc.tab.h lib.tab.hpp

lex.yy.o : lex.yy.cpp

lex.lib.o : lex.lib.cpp
