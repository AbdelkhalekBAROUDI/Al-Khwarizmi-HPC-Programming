### Exercise 1:

- Implement C or Fortran version for the code below

```python
do i =1 , N * i_stride , i_stride
   mean = mean + a ( i )
end do
```
- Compute the cpu time and bandwith for different stride (1 to 20) and plot the results
- We compile the above Fortran code with all optimization and vectorization disabled (-O0) and we run it for different strides
- We do the same thing, with (-O2) that activates some optimizations
- What is the conclusion?

- Expected output (Not necessary the same result):
<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/caa2c79594c44f7f66e27b25d5012333b94aa509/day01/assignments/Stride_cputime.png?raw=true" alt="Sublime's custom image"/>
</p>




<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/8edc4ad637906d80b571746a576d17f7314df8c7/day01/assignments/Stride_bandwidth.png?raw=true" alt="Sublime's custom image"/>
</p>



### Exercise 2:

- Implement the MxM multiplication using the block version
- Naive version:
```fortran
program main
implicit none
integer, parameter :: N = 1000
integer, parameter :: SIZE_OF = 8 ! for double precision
integer,parameter :: SEED = 86456
real(8), dimension(N,N) :: x,y,z,tx
integer :: i,j,k
real(8) :: msec, rate
real(8) :: start, finish

call srand(SEED)

z(:,:) = 0.0
do i=1, N
  do j=1, N
    x(i,j) = rand() + 1.0
    y(i,j) = rand() + 1.0
  end do
end do

! .......................................................
do i=1, N
  do j=1, N
    do k=1, N
      z(i,j) = z(i,j) + x(i,k) * y(k,j)  
    end do
  end do
end do
```
- Compute the cpu time and bandwith for different block size, which block size is the optimal one ? Why ?

- Expected output (Not necessary the same result):

<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/2fa38aff8b080a8013433abbbd0b4c79cc042956/day01/assignments/Block_cputime.png?raw=true" alt="Sublime's custom image"/>
</p>


<p align="center">
  <img src="https://github.com/AbdelkhalekBAROUDI/Al-Khwarizmi-HPC-Programming/blob/b931be91e72760dca7b1016f606ca7f6e776738a/day01/assignments/Block_bandwidth.png?raw=true" alt="Sublime's custom image"/>
</p>
