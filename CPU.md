# GoodArch CPU

## Core "wishlist"

  * Few instructions.
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