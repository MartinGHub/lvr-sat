LVR SAT solver
=======

**Authors:** _Martin Jakomin_ & _Mateja Rojko_

SAT solver created as a project work at course LVR (Logic in Computer Science).
It contains the structures for boolean operators and expressions, various functions for expression manipulation
and simplification, SAT solver based on DPLL algorithm and methods for conversion of some known problems
to Boolean expressions, such as graph coloring and sudoku.

___


## Algorithm
The implementation of our sat solver is based on DPLL algorithm (http://en.wikipedia.org/wiki/DPLL_algorithm),
with various improvements, such as loop simplification and sorting the clauses by their length.


## Project structure
 * `SAT/` contains the source code:
   * `SAT/bool.py` contains the classes for Boolean constructs (operators) and expressions, and functions for expression
   manipulation and simplification
   * `SAT/sat.py` contains the sat solver (modified DPLL algorithm)
   * `SAT/sat_converter.py` contains the methods for converting the graph coloring problem and Sudoku to Boolean expressions
   * `SAT/examples.py` contains some examples for usage of Boolean constructs, expressions, functions and SAT
   * `SAT/test.py` contains te unit tests for the project


## Instructions
 * **Building the expression:** By using constructs such as Var, Neg, Or, And and Const, found in `bool.py` you can build any Boolean expression.
 Variables are defined with: **Var**("Variable name"), Negation with **Neg**(_expression_), constant with **Const**(_True_/_False_),
 And clause with **And**([_List of literals or expressions_]) and similar Or clause with **Or**([_List of literals or expressions_]).

 * **Expression manipulation and simplification:** In `bool.py` you can find various functions, such as nnf, simplify, cnf, solve and simplify_cnf.
 For conversion to Negation normal form you can use **nnf**(_expression_), similar you can use **cnf**(_expression_) for conversion
  to Conjunctive normal form. You can simplify the expression with **simplify**(_expression_) or **simplify_cnf**(_expression_,_dictionary of set literals_)
  which will simplify the expression using the set variables and convert it to CNF form (some kind of partial solve). For
  complete solving of an expression you must provide full variable setting in a dictionary of form {"variable name": _True_/_False_}
  and then call the function **solve**(_expression_,_variable setting_).

 * **SAT:** For Boolean satisfiability problem (SAT) you can use the function sat() found in `sat.py`. It comes with two
 possible options: sat(_expression_, {}) or sat(_expression_, _variable setting_) if you want to set initial variables.
 The output is either (False, {}) if expression is not satisfiable or (True, v) if expression is satisfiable (where v is
  the dictionary of variable setting, such that expression is satisfiable under those settings).

 * **Conversion of known problems:** In `sat_converter.py` you can find methods for converting the n-coloring of a
  graph problem and Sudoku solvability problem to Boolean expressions. The example calls can be found in `sat_converter.py`.
    * n-coloring of a graph: For converting the n-coloring of a graph problem to Boolean expressions you can use the
    **Graph2SAT**(_list of vertices_, _dictionary of edges_,_n_).
    * Sudoku: For converting the solvability problem to Boolean expressions you can use the **sudoku2SAT**(_list of lists of rows_). The rows
    must be represented with a list of "" (for empty cells) and numbers (occupied cells).

 * **For more information see: `examples.py`.**
