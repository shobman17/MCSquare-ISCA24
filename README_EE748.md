Changes made:
1. We studied the number of destination reads that the CTT would get. 
2. We also studied the number of such entries in CTT that were misaligned.

What can we aim for?
1. When we get a destination read for a module that is not the same as the one we reached presently, we can simply reduce the CTT lookup latency for that case. OR add a negative thingy equal to the interconnect latency.
2. We increase the number of DRAM modules present in the design.

Interesting things I just realised : 
1. If we move the CTT to the LLC, we get some good benefits:
    a. We NEVER face the CTT lookup latency. This is because even if src and dest are in different modules, we just have to read the CTT once to make the decisions. In the current case, even if src and dest are in the same module, we waste time in invalidating the original request made. Sexam hogaya.
2. Obviously this comes at a small cost stil -- we will have some signals coming and going back. 
