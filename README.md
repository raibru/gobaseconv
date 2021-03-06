gobc - GO BASE CONVERTER
========================

Introduction
------------

For my work I need an easy way to display a base values in diffrent convertions. You can also use the bc tool like the following command line below. But I like to have a small tool which display me the converted values I need in a simple way. I also need this in the linux and windows world.

Used with tool bc in linux world. The tool bc can do much more than convert only to other bases:

```shell
$ echo "obase=16; ibase=10; 42" |bc
$ echo "obase=10; ibase=10; 42" |bc
$ echo "obase=8; ibase=10; 42" |bc
$ echo "obase=2; ibase=10; 42" |bc
```

The tool gobc converts from one base into another base and print the result on stdout. The tool accept following base value types:

* hexadecimal (hex, x)
* decimal (dec, d)
* octal (oct, o)
* binary (bin, b)

The output prints all converted values in one line with/without base prefix

```shell
$ gobc -h
Exchange a given base-x number to hex, dec, oct, bin

Usage:
  gobc [flags]

Flags:
  -b, --bin string         convert string number from binary.
                           Read from pipe use '.' as parameter
  -d, --dec string         convert string number from decimal.
                           Read from pipe use '.' as parameter
  -h, --help               help for gobc
  -x, --hex string         convert string number from hexadecimal.
                           Read from pipe use '.' as parameter
      --lead-zero string   Print data with leading zeros
                           defined by a string and separated by ','
                           e.g 'x:4,d:2,o:3,b:8'
                             hex: x:4 -> 4 leading zeros
                             dec: d:2 -> 2 leading zeros
                             oct: o:3 -> 3 leading zeros
                             bin: b:8 -> 8 leading zeros
  -o, --oct string         convert string number from octal.
                           Read from pipe use '.' as parameter
  -p, --prefix             display converted values with base prefix
  -v, --version            display gobc version
```

```shell
$ gobc -d 42
2a 42 52 101010
```

```shell
$ gobc -d 42 -p
0x2a 0d42 0o52 0b101010
```

Leading zeros
-------------

If the output value shall have a length of 8 but is less then this the leading zero parameter fill up to given lenght with leading zeros, e.g:

```shell
$ gobc -d 1 --lead-zero x:4,b:8
0001 1 1 00000001
```

Build
-----

Use go1.12 or higher to build the tool gobc

Build the linux binaries run

```shell
$ make build_lin
```

Build the windows binaries run

```shell
$ make build_win
```
