### Exercise 1:

We implemented C version for the code below

```python
do i =1 , N * i_stride , i_stride
   mean = mean + a ( i )
end do
```
and we compiled it with all optimization and vectorization disabled (-O0) and we run it for different strides
 we did the same thing, with (-O2) that activates some optimizations. We computed the cpu time and bandwith for different stride (1 to 20) and ploted the results below:

<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/caa2c79594c44f7f66e27b25d5012333b94aa509/day01/assignments/Stride_cputime.png?raw=true" alt="Sublime's custom image"/>
</p>






<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/8edc4ad637906d80b571746a576d17f7314df8c7/day01/assignments/Stride_bandwidth.png?raw=true" alt="Sublime's custom image"/>
</p>

According to the plots above, we notice that cpu time increases for different strides (1 to 20), however, the bandwidth descreases. We conclude that the penalty for not arranging the data so that the elements are accessed with unit (1) stride can be pretty severe.

### Exercise 2:

We implemented the NxN (N=200) multiplication using the block version in C. We ran it for different block size (b = 1, 2, 4, 5, 10, 20), we computed the cpu time and the bandwidth and ploted the results :  


<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/2fa38aff8b080a8013433abbbd0b4c79cc042956/day01/assignments/Block_cputime.png?raw=true" alt="Sublime's custom image"/>
</p>


<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/b931be91e72760dca7b1016f606ca7f6e776738a/day01/assignments/Block_bandwidth.png?raw=true" alt="Sublime's custom image"/>
</p>



According to the plots above, we note that the optimal block size is **4** because L2 cache memory was able to store this size (cache hit) , therefore, CPU avoids to look for the data in the RAM. 
