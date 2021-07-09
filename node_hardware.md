It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)

```
A block
```

Odroid HC-4 has 4 cores

Odroid N2+ has 6 cores

Build bitcoin core:
```
./autogen.sh
./configure BDB_LIBS="-L${BDB_PREFIX}/lib -ldb_cxx-4.8" BDB_CFLAGS="-I${BDB_PREFIX}/include" --without-gui --with-zmq
time make
```
Results from Odroid N2+
```
real	95m43.794s
user	76m56.428s
sys	4m45.648s
```
