# This is a makefile that builds the Hindi morphological parser
# *****************************************************************


# Here we build the final generator , an inverted transducer of the analyzer.
# It is dependent upon hin.save

#ihin.fst: ../bin/ihin.fst
#../bin/ihin.fst: ../bin/hin.fst
#	@echo
#	@echo "*** Building the inverse ihin.fst ***"
#	@echo
#	@printf "load ../bin/hin.save \n\
#	invert net \n\
#	save stack ../bin/ihin.fst \n\
#	quit \n" > ../tmp/ihin-fst-script
#	@xfst  < ../tmp/ihin-fst-script
#	@rm -f ../tmp/ihin-fst-script




# Another goal is to build a preprocessor.This goal depends on tok.txt
#
#tok.fst: ../bin/tok.fst
#../bin/tok.fst: tok.txt
#	@echo
#	@echo "*** Building the tokenizer tok.fst ***" ;
#	@echo
#	@printf "source tok.txt \n\
#	save stack ../bin/tok.fst \n\
#	quit \n" > ../tmp/tok-script
#	@xfst  < ../tmp/tok-script
#	@rm -f ../tmp/tok-script


#hin.save: ../bin/hin.save
#../bin/hin.save: ../bin/xfst-hin.bin ../bin/hin-lex.save
#	@echo
#	@echo "*** Building the parser hin.save ***"
#	@echo
#	@printf "read regex [[@\"../bin/hin-lex.save\"] .o. \
#	[@\"../bin/xfst-hin.bin\"]] ; \n\
#	save stack ../bin/hin.save \n\
#	quit \n" > ../tmp/hin-save-script
#	@xfst  < ../tmp/hin-save-script
#	@rm -f ../tmp/hin-save-script

# The first goal is to build hin-lex.save
# This goal depends on a bunch of lexicon files

hin-lex.save: ../bin/hin-lex.save
../bin/hin-lex.save: hin-lex.txt noun-hin-lex.txt
	@echo
	@echo "*** Building hin-lex.save ***" ;
	@echo
	printf "compile-source hin-lex.txt noun-hin-lex.txt \n\
	save-source ../bin/hin-lex.save \n\
	quit \n" > ../tmp/hin-lex-save-script
	@lexc  < ../tmp/hin-lex-save-script
	rm -f ../tmp/hin-lex-save-script


# files above
#	noun-hin-morph.txt adj-hin-lex.txt \
#	verb-hin-lex.txt verb-hin-morph.txt pron-hin-lex.txt \
#	adv-hin-lex.txt pp-hin-lex.txt punct-hin-lex.txt \n\
#	punct-hin-lex.txt pp-hin-lex.txt

# The second goal is to build xfst-hin.bin
# This goal depends on xfst-hin.txt

#xfst-hin.bin: ../bin/xfst-hin.bin
#../bin/xfst-hin.bin: xfst-hin.txt
#	@echo
#	@echo "*** Building xfst-hin.bin ***" ;
#	@echo
#	@printf "source xfst-hin.txt \n\
#	save stack ../bin/xfst-hin.bin \n\
#	quit \n" > ../tmp/xfst-hin-script
#	@xfst  < ../tmp/xfst-hin-script
#	@rm -f ../tmp/xfst-hin-script

clean:
	@rm -f ../bin/*.bin ../bin/*.fst ../bin/*.save

