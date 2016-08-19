## Open Source Collections

- [fuchsia-mirror/magenta](https://github.com/fuchsia-mirror/magenta)

	Magenta Kernel, Core Drivers, and Services https://fuchsia-review.googlesource.com/#/q/project:magenta
	
	Magenta is the **core platform** that powers the Fuchsia OS. Magenta is composed of a microkernel (source in kernel/...) as well as a small set of userspace services, drivers, and libraries (source in system/...) necessary for the system to boot, talk to hardware, load userspace processes and run them, etc. Fuchsia builds a much larger OS on top of this foundation.

	The Magenta Kernel provides **syscalls** to *manage processes*, threads, virtual memory, **inter-process communication**, waiting on object state changes, and locking (via futexes).

	Currently there are some temporary syscalls that have been used for early bringup work, which will be going away in the future as the long term syscall API/ABI surface is finalized. The expectation is that there will be 10s, not 100s of syscalls.

	Magenta syscalls are generally non-blocking. The wait (one, many, set) family of syscalls, ioport reads, and thread sleep being the notable exceptions.

- [tensorflow/magenta](https://github.com/tensorflow/magenta)

	Magenta: Music and Art Generation with Machine Intelligence



