# Password

A simple(?) shell script I wrote to generate passwords, since various things I need them for have ridiculous password
policies.

# DANGER!

> =========== DANGER DANGER DANGER! ===============

> This uses DICTIONARY WORDS which is considered BAD PRACTICE for passwords. Caveat passwordor!

## History

`password` started out as just to generate "easy typeable" passwords; which is to say, words that use letters on
alternating hands when touch-typing on a US QWERTY keyboard.

## Evolution

I've added functionality, mostly for shits and grins, to specify you want passwords that can be typed with just the
left, or just the right, hand.

And, a "tivo" password. The "tivo" password is one where each letter in the password is either the same as the current
letter, or next to it in an up/down/left/right direction. The idea here is that typing passwords into your Tivo with the
on-screen keyboard is so god damned irritating that I wanted to minimize the distance between letters to make it easier
to do so.

## Installation

Put this directory in your PATH. The `password.functions` file must live in the same PHYSICAL directory as `password`.

There are clever ways to determine what dir a script is actually in, even if you got to it via symlink (see:
http://stackoverflow.com/a/246128) but honestly I just didn't feel like screwing with it. See: caveats


## Usage

`/path/to/password -h` 

```
usage: password -s size_in_chars -r number_of_iterations [-d dictionary_file] [-{E|T|L|R}]
    -s <chars>: the minimum size in chars of the password.  Default: 3
    -r <reps>: The number of words to spit out.  Default: 1
    -d <dict_file>: File of words to choose from.  Default: /usr/share/dict/words
    -E: easily touch typeable (default, real words)
    -T: tivo style password - easily typable onscreen (no real words)
    -L: words that you can touchtype with your left hand only (real words)
    -R: words that you can touchtype with your right hand only (real words)
```

## Caveats

* I wrote this for me. It works for me. Nothing else is guaranteed, promised, nor hinted at.  It's not particularly well
  written code.
* This relies on `bash`'s idea of `$RANDOM` which is specifically called out as not being acceptable for cryptographic
  use.  (This may contribute to what appears to me the Tivo password generation being particularly fond of using the
  same letter rather than picking an adjacent one.)
