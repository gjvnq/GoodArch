# GoodArch CPU

## Core "wishlist"

  * Few instructions.
  * "Hidden registers" to help with virtual instructions.
  * No out of order execution or branch prediction.
  * Branch instructions have a field for the compiler to tell the CPU if the instruction will likely branch.
  * Large and numerous registers
    * Makes things easier and helps with using large IDs (such as UUIDs) for almost everything.
  * Stack protection against stupid software (or malware via plugins)
    * Probably two stacks: one for data and another for functions. This helps with exception handling and helps block jumps to other functions.
  * Probably use the most significnt bit to distinguish real addresses from virtual ones.
  * Automatic memory encryption?
  * Flags register shows:
    * Overflow for varios datatypes (u8, u16, u32, u64, u128, i8, i16, i32, i128). This can help computaion heavy software and emulation.
    * Which registers are zero and which are negative.
    * Current ring of protection.
  * Overflows don't necessairly trigger an interrupt.
  * OS can partially control the CPU cache. (will either prevent or agument things HeartBleed)
  * Probably no floating point nor integer division and multiplication for the first version.
  * Harware level ICP. Maybe something like ```sendmsg $pid $addr $size``` which copied the memory between ```$addr``` and ```$addr+$size``` to a special place on the recieving process (```$pid```) memory (maybe some memory pages specific to message recieving).
