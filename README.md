LPEG/J
======

This is a straight port of the LPEG compiler and virtual machine
to Java. It also includes a binding to LuaJ, so Lua scripts running
under LuaJ can use it as if it were LPEG 0.10.1
(with `require "lpegj.luaj.lpeg"`), with the caveats below.

Caveats
-------

* LuaJ does not have a 100% faithful implementation of arithmetic
  metamethods, so things like `1 - p` where p is a pattern do
  not work; use `lpeg.P(1) - p`. Things like `p + 1` work, though.
  The file `test.lua` has been adjusted accordingly.

* Almost no optimizations yet in the generated patterns, just the
  simplest identities

* NO VERIFIER, so you may write patterns that hang and the compiler
  will not detect it

* A lot of sanity checking that LPEG does to detect erroneous
  patterns and captures is missing

As a rule of thumb, if it works in LPEG it should work in LPEG/J, and
if it does not work in LPEG it may give a spurious result in LPEG/J.
Plans are to do the verifier first, then sanity checking, and the funky
optimizations last.

License
-------

The license is the same as Lua.
