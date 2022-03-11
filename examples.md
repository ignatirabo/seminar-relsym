# Examples

Notice that I am cheating because this is my analyzer, not Relational Symbolic Execution, but it's fairly similar.

 1. Without loops:
    - Insecure program: `./main.exe --dse-nodep code/if.11.code`
    - Secure program: `./main.exe --dse-nodep code/i_is_0_if.code`
 2. With loops:
    - Insecure program: `./main.exe --dse-nodep code/while.02.code` we found vulnerabilities.
    - Secure program with no crazy invariants added:
    `./main.exe --dse-nodep code/high2low.code` 
    - Cannot determine anything: `./main.exe --dse-nodep code/symbolic_dep.code`
    - Secure program: the first program can be proven secure, we just need more invariants (intervals domain).
    `./main.exe --dprod-nodep --dom box --thr "[ 100 + -1*i >= 0 ]" code/symbolic_dep.code`