Print : 'Welcome to OurScheme!'
  
  repeat
  
    Print : '> '
    
    ReadSExp( inSExp ); 
    
    if no syntax error
    
      then 
      
        EvalSExp( inSExp, resultSExp ) ;
        
        if evaluation error
          then PrintEvaluationError() ;
          
        else // no evaluation error
          PrintSExp( resultSExp );
          
      end-then // no syntax error
      
    else // syntax error
      PrintSyntaxError() ;
    
  until user has just entered LEFT_PAREN "exit" RIGHT_PAREN
        or
        EOF encountered
  
  if ( END-OF-FILE encountered ) // and NOT 「user entered '(exit)'」
    Print 'ERROR (no more input) : END-OF-FILE encountered' 

  Print '\n'
  Print : 'Thanks for using OurScheme!'
  
  -------------------------------------------------------------------------------
  括號內的數字指的是這個function可接受的argument的數目 - i.e., the number of
 arguments that this function can take)
 
 
  1. Constructors

  cons (2)
  list (>= 0)

2. Bypassing the default evaluation

  quote (1)
  '     (1)

3. The binding of a symbol to an S-expression

  define (2)

  ; Once a symbol is defined (or "bound"), the user can enter 
  ; this symbol, and the system will return its binding.
  
  ; however, the user is not allowed to redefine symbols that happen
  ; to be system primitives such as 'cons' or 'car' or 'cdr', etc.

4. Part accessors

  car (1)
  cdr (1)

5. Primitive predicates (all functions below can only take 1 argument)

  atom?
  pair?
  list?
  null?
  integer?
  real?
  number? // in OurSchem, real? = number?, but not in Scheme (there are complex-numbers)
  string?
  boolean?
  symbol?

6. Basic arithmetic, logical and string operations

  + (>= 2)
  - (>= 2)
  * (>= 2)
  / (>= 2)
  
  ; in evaluating 'and' or 'or', it is possible that some "argument expr"
  ; does not get evaluated ; use Petite Scheme to see what this means
  ; e.g., (set! a 5) a (and (set! a 10) #f (set! a 100)) a (or #t (set! a 200)) a
  
  not (1)
  and (>= 2)
  or  (>= 2)
  
  ; all functions below can take 2 or more arguments
  
  >
  >=
  <
  <=
  =
  string-append
  string>?
  string<?
  string=?

7. Eqivalence tester

  eqv?    (2)
  equal?  (2)

8. Sequencing and functional composition

  begin   (>= 1)
  
  ; the user may also enter, e.g., >>(car (cdr '(1 2 3 4)))<<

9. Conditionals

  ; in evaluating 'if' or 'cond', it is possible that some "sub-expr"
  ; does not get evaluated (this is the meaning of conditional expressions) ;
  ; use Petite Scheme to check ;
  
  if     (2 or 3)
  cond   (>= 1)

10. clean-environment
