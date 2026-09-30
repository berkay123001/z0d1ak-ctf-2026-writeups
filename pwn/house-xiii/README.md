# House XIII · Pwn

**Core idea:** a stale object reference survived a type change, enabling a protected call target to be forged after recovering its secret-dependent integrity value.

## What made the heap state useful

The service's `transmute` operation could leave an old table entry pointing at a freed object. A normal allocation did not reliably reclaim that chunk: this path used `calloc`, which bypassed the expected tcache behavior. Filling the 0x190-size tcache bin forced the freed object into the unsorted bin, after which `calloc` could overlap the old `STARGMTR` and new `ORBITAL` views.

The bytecode inspection operation supplied a PIE and heap leak. A `status:` response then acted as a comparison oracle for the process secret; a 64-step binary search recovered the value needed to satisfy the protected function-pointer check.

## Turning overlap into a call

An edit path wrote fields inside the overlapped object without enforcing the object's magic. The forged structure needed a masked function pointer and a hash that included the object pointer itself. The call operation dereferenced a *slot containing* the target function pointer; pointing directly at the function was the wrong shape and failed validation.

The useful function was already in the binary: with object field `+0x7c` set to `13` and a nonnegative descriptor at `+0x78`, it called `sendfile(1, fd, ..., 0x400)`. The challenge had left the flag open on descriptor `13`, so a shell or `openat` was unnecessary—and seccomp would have blocked `openat` anyway.

## Evidence and limits

The archived exploit and final audit record a live flag. Its heap grooming, pointer encoding, and descriptor number are challenge-specific. On the original timed instance, pipelining setup commands mattered because menu round trips consumed the session budget.

**Flag:** `zdk{HOUs3_XL11_opEn5_wh3N_thE_s74l3_4uD17_r3coRd_R3wRl7ES_THE_r0UT3}`
