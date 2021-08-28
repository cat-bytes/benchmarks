It's very easy to make some words **bold** and other words *italic* with Markdown. You can even [link to Google!](http://google.com)

```
A block
```

Odroid HC-4 has 4 cores
 - MicroSD slot only

Odroid N2+ has 6 cores
 - eMMC socket
 - 4 3.0 USB ports
 - 12V/2A power supply recommend.  Did not work for me (blinking red light).  Worked with 15V/4A power supply.

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

real	79m56.965s
user	76m21.244s
sys	2m55.012s
```

Odroid N2+ and Seagate Ironwolf NAS SSD read benchmark
```
sudo hdparm -Ttv --direct /dev/sda

/dev/sda:
 multcount     = 16 (on)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 121601/255/63, sectors = 1953525168, start = 0
 Timing O_DIRECT cached reads:   550 MB in  2.00 seconds = 274.56 MB/sec
 Timing O_DIRECT disk reads: 826 MB in  3.01 seconds = 274.84 MB/sec
 ```
 
 Odroid N2+ and Seagate Ironwolf NAS SSD write benchmark
 ```
root@odroid:/mnt/ssd# sync
root@odroid:/mnt/ssd# echo 3 > /proc/sys/vm/drop_caches
root@odroid:/mnt/ssd# dd if=/dev/zero of=/mnt/ssd/temp oflag=direct bs=128k count=32k
32768+0 records in
32768+0 records out
4294967296 bytes (4.3 GB, 4.0 GiB) copied, 20.0062 s, 215 MB/s
```

HPE ProLiant MiroServer Gen10+ Xeon E-2224
```
real	19m56.431s
user	18m52.297s
sys	1m1.579s
```


Odroid HC-4
