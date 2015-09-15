# Introduction #

Schmake will be a very lightweight build system that overcomes many of the short comings of make. It will not use /bin/sh for processing commands(unless explicitly told to). This makes it portable and also makes the resulting build script a bit more readable.

Everything in Schmake is meant to be fairly easy to figure out when reading a build script.

# Example #
#this is a comment
#build script for an example program composed of main.c and extra.c

objects{
  desribe: "builds the object files"
  input: src/*.c:
  output: obj/*.o;
  process:{
    $.each($file in $input){
      $out = replace ".c" with ".obj" in $file
      exec $CC $FLAGS -c $file -o $out
    }
  }
}

```