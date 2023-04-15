====== The while-loop ======

===== Synopsis =====
&lt;code&gt;
while &lt;LIST1&gt; ; do
  &lt;LIST2&gt;
done
&lt;/code&gt;

===== Description =====
The while-loop is relatively simple in what it does: it executes the [[syntax:basicgrammar#lists | command list]] ''&lt;LIST1&gt;'' and if the exit code of it was 0 (TRUE) it executes ''&lt;LIST2&gt;''. This happens again and again until ''&lt;LIST1&gt;'' returns FALSE.

This is exactly the opposite of the [[syntax:ccmd:until_loop | until loop]].

:!: Like all loops (both ''for''-loops, ''while'' and ''until''), this loop can be
  * terminated (broken) by the ''break'' command, optionally as ''break N'' to break ''N'' levels of nested loops
  * forced to immediately do the next iteration using the ''continue'' command, optionally as ''continue N'' analog to ''break N''

==== Return status ====

The return status is the one of the last command executed in ''&lt;LIST2&gt;'', or ''0'' (''TRUE'') if none was executed.

===== Examples =====


===== Portability considerations =====


===== See also =====

  * Internal: [[syntax:ccmd:until_loop | The until loop]]
  * Internal: [[commands:builtin:read#code_examples|code examples of the read builtin command]] to see how you can loop over lines