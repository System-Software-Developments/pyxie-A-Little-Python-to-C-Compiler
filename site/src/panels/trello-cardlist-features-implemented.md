---
template: mainpanel
source_form: markdown
name: Trello Cardlist Features Implemented
updated: August 2015
title: Trello Cardlist Features Implemented
---
### Features Implemented

* 3\. Arduino LEONARDO compatible compilation profile.
* 3\.3 Code generation outputs code targetting "setup" instead of "main"
* 3\.4 Makefile uses the arduino makefile #arduino leonardo
* 4\.1 compilation profiles support removal of elements of the clib
* 3\.2 Code generation is called with this switch toggled
* 3\.1 Detect that we are in a profile mode from a command line switch
* 2\. Function calls that do not require arguments are tested
* 61\. Make Release Script
* 62\. build_release_script.py
* 63\. Documentation in /docs is generated from website source documentation
* 64\. Docs on usage #docs
* 65\. Man page for pyxie
* 66\. Docs in README.md, setup.py and docs/ are generated from website.
* 67\. Support for for statements
* 0\.0.15 = = = = = = = = = =
* 71\. BUG: clibs can only be used on development machine...
* 0\.0.14 = = = = = = = = = =
* 74\. BUG: Putting the for loop at the end of the program causes compilation to fail
* 75\. BUG: statement_block at EOF not emitting dedents correctly #fixed
* 76\. Simple for...range loops
* 77\. Function call code supports simplified type definitions for builtins (such as range)
* 78\. Compile phase is split into "codegen" and "compile"
* 79\. Implement a simple iterator protocol for C++ objects - to allow implementation of something like range functions and generators.
* 80\. Implementation of a simple C Library to include into user generated code as necessary.
* 0\.0.13 = = = = = = = = = =
* 82\. Parsing bracketed full expressions
* 83\. Chained boolean expressions and chained mixtures of boolean expressions work as expected
* 84\. Boolean expression support: NOT
* 85\. Boolean expression support: AND
* 86\. Boolean expression support: OR
* 87\. Support for if/elif/else statements
* 88\. Support for if statements
* 0\.0.12 = = = = = = = = = =
* 92\. Release tasks: 0.0.12
* 93\. Comparison operators
* 94\. Can now handle loops that count towards zero and do something with them...
* 95\. support for while statements
* 96\. While Loop conditional is a expression
* 97\. Continue works in a While loop
* 98\. Break works with With True
* 99\. While works with While True:
* 100\. Define basic principles for Pyxie
* 0\.0.11 = = = = = = = = = =
* 108\. Function call code generation supports Print as special case
* 109\. Code generation function calls
* 110\. Support python comments so we can CHEAT and do things like #include <arduino.h> :-D (What a *neat* idea :-) )
* 111\. Parsing function calls
* 0\.0.10 = = = = = = = = = =
* 115\. Pyxie will now compile files outside the pyxie code tree
* 116\. Code generation of expression statements.
* 117\. Test suite checks that programs that should fail to compile do so
* 118\. Test suite uses new analysis hook
* 119\. PARSING USES STANDARD TREE MODEL, BUT ALSO USES CUSTOM TRAVERSALS FOR FLEXIBILITY
* 120\. Type inference code changes are refactored and cleaned up
* 121\. Strategy for managing variables needs defining
* 122\. New strategy for type inference - lexical scope friendly
* 123\. Analysis through tree for identifiers doesn't work as expected. Needs fixing/resolving
* 124\. Now, before we analyse types, all identifiers are guaranteed to be in the global context. We don't need to stuff in a new version, just update it.
* 125\. Contexts themselves are kinda wrong, need a rethink
* 126\. Analysis Phase adds context
* 127\. Pynodes are tree nodes (and hence trees)
* 128\. Analyse is an explicit phase internally, initially focussed on types
* 129\. Results of analyse phase can be made visible.
* 130\. Docs added to pyxie/__init__.py
* 0\.0.9 = = = = = = = = = =
* 139\. Pyxie harness supports parsing random files
* 140\. Pyxie harness supports compiling random files
* 141\. Pyxie harness has a testing mode
* 142\. Bracket negative literal values in expressions to avoid confusing C++
* 145\. Pyxie is now left recursive not right recursive
* 146\. conversion of expression statements
* 147\. BUG: 10-1-2 gives 9 not 11
* 0\.0.8 = = = = = = = = = =
* 151\. Replace python AST list style representation with a nodal representation - to simplify type decoration etc
* 152\. Type inference for expressions
* 153\. assignment where the rvalue is a simple integer expression
* 154\. Variable types are looked upin/stored to  a global context.
* 155\. Testcase added for assignments where the rvalue is an expression
* 156\. BUGFIX: Should only include iostream once, if at all.
* 157\. Printing of op_func blocks
* 158\. Conversion of core "operator functions" for integers
* 159\. Code generation for INTEGER core expressions
* 160\. BUGFIX: Precedence for operators is inverted for some reason.  +- binding tighter than */
* 161\. BUG - When the parser is reused, line numbers in lexer do not reset for new files
* 162\.Parsing core expressions - times, divide, power, plus, minus  - NOT function call, not parenthesised
* 163\. Parsing blocks generates block tokens
* 164\. Lexical Analysis matches initial language spec
* 165\. Print handles mixed literals
* 166\. Code generation for atomic literals
* 167\. "models" contains an initial baseline model mapping python-CST to CPP-CST
* 168\. Generation of decorated CPP-CST from parsed assignment statements
* 169\. C++ Code can be generated from the baseline CPP-CST for libc based testing
* 170\. Parsing assignment statements
* 171\. Parsing identifiers
* 172\. Parsing of value literals
* 173\. Baseline parser/lexer infrastructure for parser build/testing
* 174\. Long description on PyPI