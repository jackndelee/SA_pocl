# SA_pocl


This project is for POCL for ***"SA"***, not a ***general POCL.***

You can handle ***compile & runtime*** as you want.

</br>
FYI
</br>
Here is ***general POCL*** URL
http://portablecl.org/


------------
# How to compile ***SA POCL*** 
</br>

For compile changed device ***“vortex -> SA”***, 
</br>
you need to compile each ***build_vortex_cc (compiler)*** and ***build_vortex_rt (runtime)*** 

go to ***/SA_pocl/pocl ( my case is /opt/pocl )***

you can see two folders 
* build_vortex_cc 
* build_vortex_rt 

</br>
</br>


one more thing is the ***install*** folder. 

the ***New POCL (SA POCL)*** result will be stored in this folder.
</br>
</br>
![SA_POCL](https://github.com/jackndelee/SA_pocl/blob/main/POCL_build_device/doc/asset/POCL1.JPG)


------------
</br>


1. go to  ***build_vortex_cc*** for ***Vortex POCL*** compile



***step 1.***
 - cd build_vortex_cc



</br>

***step 2.***
- you should set install prefix on your’s path ***(home/XXX/XXXX)***


</br>
-cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/home/XXX/opt/pocl/install/compiler 
-DCMAKE_BUILD_TYPE=Debug 
-DOCS_AVAILABLE=ON 
-DWITH_LLVM_CONFIG=/opt/llvm-riscv/bin/llvm-config 

</br>
</br>
-DENABLE_VORTEX=ON 


***you have to change this command Vortex -> SA***


-DENABLE_SA=ON
</br>



</br>
-DBUILD_TESTS=OFF -DPOCL_DEBUG_MESSAGES=ON -DDEFAULT_ENABLE_ICD=OFF ..


</br>





</br>
</br>
</br>

***step 3.***



-cmake --build . --target install

</br>
</br>
</br>
</br>


-------------------
***2. go to build_vortex_rt for pocl vortex runtime***


</br>


***step 1.***




-cd build_vortex_rt


</br>


***step 2.***



- you should set install prefix on your’s path ***(home/XXX/XXXX)***

-cmake -G Ninja -DHOST_DEVICE_BUILD_HASH=riscv32-unknown-elf 
-DCMAKE_INSTALL_PREFIX=/home/XXX/opt/pocl/install/runtime 
-DCMAKE_BUILD_TYPE=Debug 
-DOCS_AVAILABLE=OFF 
-DVORTEX_DRIVER_INC=/home/XXX/vortex/driver/include 
-DVORTEX_DRIVER_LIB=/home/XXX/vortex/driver/stub/libvortex.so 


</br>


</br>
-DENABLE_VORTEX=ON 


***you have to change this command Vortex -> SA***


-DENABLE_SA=ON
</br>




</br>
</br>
 -DBUILD_TESTS=OFF
 -DPOCL_DEBUG_MESSAGES=ON -DDEFAULT_ENABLE_ICD=OFF ..
 
 

</br>
</br>
</br>


***step 3.***


-cmake --build . --target install



</br>


-----------
</br>




then when you go to ***/opt/pocl/install***


</br>


you can see the ***compiler & runtime*** which was set for ***the new device “SA”*** 
