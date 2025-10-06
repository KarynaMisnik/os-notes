# os-notes

- [What is Operating System](#what-is-operating-system)
- [History of Operating Systems](#history-of-operating-systems)
  - [Multithreaded and Multicore Chips](#multithreaded-and-multicore-chips)
- [Operating System Variants](#operating-system-variants)
- [Operating Systems Concepts](#operating-systems-concepts)
  - [Ontogeny Recapitulates Phylogeny](#ontogeny-recapitulates-phylogeny)
- [System Calls](#system-calls)
- [Operating System Structure](#operating-system-structure)
  - [Monotholic Systems](#monotholic-systems)
  - [Layered Systems](#layered-systems)
- [Virtual Machines](#virtual-machines)
- [Review Questions](#review-questions)
- [Computer Hardware](#computer-hardware)
- [Von Neumann Machine](#von-neumann-machine)
- [Hypervisors](#hypervisors)
- [Processor Architecture](#processor-architecture)
- [Kernel](#kernel)
- [Memory Management](#memory-management)
- [Processes](#processes)
- [Concurrency, Parallelism, Threads & Interrupts](#concurrency-parallelism-threads-interrupts)
- [File systems & partitioning](#file-systems-partitioning)

🌐 Operating System — Key Concepts ❗

1. Definition of Operating System

An Operating System (OS) is the most fundamental system software that controls a computer’s hardware and provides services for applications.
It acts as the interface between the user, applications, and hardware.

Without an OS, users would need to directly program hardware devices (like writing raw instructions for disk I/O or memory management), which is extremely complex and error-prone.

👉 Think of the OS as both a translator and a manager.

2. Roles of an Operating System

An OS has two classic and complementary views:

(A) OS as an Extended Machine (Abstraction Layer)

Hardware is complex and inconvenient to program directly.

The OS hides hardware details and provides abstractions that are easier for programmers.

Example:

Instead of writing instructions to move a disk arm to a track → OS provides a simple command like read(file).

Instead of handling I/O with raw binary codes → OS provides devices as if they are files/streams.

✅ Purpose: Make the computer easier to use.

Examples of abstractions:

Files instead of raw disk blocks.

Processes instead of raw CPU instruction sequences.

Virtual memory instead of raw RAM addresses.

System calls / APIs instead of direct device programming.

(B) OS as a Resource Manager

A computer has finite resources: CPU, memory, storage, I/O devices, network, etc.

The OS manages and allocates resources fairly and efficiently among competing programs and users.

It decides:

Who gets the CPU (scheduling).

How memory is divided and protected.

Which files a process can access.

How I/O devices are shared.

✅ Purpose: Optimize performance and prevent conflicts.

Examples:

CPU scheduling → OS decides which process runs next.

Memory allocation → OS prevents one process from overwriting another’s memory.

Disk management → OS organizes data in file systems.

I/O management → OS coordinates printers, network, USB devices, etc.

3. Dual Nature of the OS

As Extended Machine → OS provides a user-friendly environment for programmers and users.

As Resource Manager → OS ensures safe, fair, and efficient use of hardware.

You can think of it like this:

For users/programmers → it’s a convenience (hide hardware details).

For the system → it’s a control center (manages limited resources).

4. Core Functions of an OS

Process Management (creating, scheduling, terminating processes).

Memory Management (allocating, protecting, virtual memory).

File System Management (files, directories, permissions).

Device Management (drivers, I/O control).

Security and Protection (authentication, isolation).

Networking (communication protocols, sockets).

User Interface (CLI, GUI, system calls).

## History of Operating Systems ❗

1️⃣ First Generation (1940s – early 1950s) – <ins>Vacuum Tubes</ins>

**Hardware:** Plugboards and switches

**OS:** no operating systems.

Programmers configured the machine by manually wiring plugboards or flipping switches.

Input/output was done with paper tape or very primitive punched cards, but those carried data, not really “programs” in the modern sense.

<ins>Characteristic:</ins> Programs were hard-wired into the machine.

**Examples:** ENIAC (1945), UNIVAC I (1951) – purely batch processing by humans.

2️⃣ Second Generation (**mid-1950s – 1960s**) – <ins>Transistors</ins>

**Hardware:** Code was punched into cards, which were fed into a card reader.

**OS:** The OS (actually a simple “monitor program”) read jobs from punch cards one by one → batch processing. This eliminated the need to rewire the computer for every program.

Programming method: Punch cards for batch processing

Programs were written in assembly language or early high-level languages (FORTRAN, COBOL).

<ins>Characteristic:</ins> Punch cards allowed more flexible and automated program input.

**Examples:** IBM 7090 series, IBM 1401 with early monitor programs.

3️⃣ Third Generation (**1960s – 1970s**) – <ins>Integrated Circuits</ins>

**Hardware:** Integrated circuits, more reliable, faster.

**OS:** Multiprogramming and time-sharing systems emerged.

<ins>Characteristics:</ins>

🔹 OS could run multiple programs concurrently, sharing CPU and I/O.

🔹 Introduction of spooling for I/O devices (like printers).

🔹 Basic resource management – memory, CPU scheduling.

🔹 Users could interact with the computer via terminals.

**Examples:** IBM System/360 with OS/360, DEC PDP series with RT-11.

#### Spooling

**Spooling** stands for Simultaneous Peripheral Operations On-Line. It’s a technique used by operating systems to manage slow I/O devices (like printers) efficiently while letting the CPU continue processing other tasks.

🔹 How it works

Output/input data is temporarily stored in a buffer (usually on disk or memory).

The CPU doesn’t wait for the slow device to finish; it keeps executing other instructions.

The OS or a separate program then feeds the data to the device at its own pace.

4️⃣ Fourth Generation (**1970s – 1990s**) – <ins>Microprocessors</ins>

**Hardware:** Microprocessors and personal computers became common.

**OS:** PC operating systems and GUI-based OS started.

<ins>Characteristics:</ins>

🔹 Introduction of graphical user interfaces (GUI) – more user-friendly.

🔹 Support for personal computing and networking.

🔹 Advanced multiprocessing, file systems, and security features.

**Examples:** Microsoft DOS, Windows 3.x, Apple Macintosh System Software, UNIX variants (BSD, System V)

5️⃣ Fifth Generation (**1990s – Present**) – <ins>Modern Computing</ins>

**Hardware:** Powerful microprocessors, multi-core CPUs, Internet connectivity.

**OS:** Modern operating systems supporting multimedia, networking, mobility, and distributed computing.

<ins>Characteristics:</ins>

🔹 Fully graphical OS with multitasking and multi-user support.

🔹 Support for mobile devices, cloud computing, and virtualization.

🔹 Security, scalability, and real-time capabilities are emphasized.

**Examples:** Windows 10/11, macOS, Linux distributions (Ubuntu, Fedora), Android, iOS (for mobile platforms)

## Review Questions

❓ For what reason an OS is a resource manager?

> Modern OS are multi-tasking. Applications have to share some resources/hardware.

🔹 An Operating System (OS) manages the computer’s resources: CPU, memory, storage, I/O devices, etc.

🔹 In a multi-tasking environment, multiple programs run **concurrently**.

🔹 The OS allocates resources fairly, prevents conflicts, and ensures each application can access the hardware safely.

This is why we call the OS a resource manager.

❓ What is POSIX?

**POSIX (Portable Operating System Interface)** is a set of standards defined by IEEE.

<ins>Its goal:</ins> make programs portable across different UNIX-like operating systems.

POSIX defines:

🔹 APIs (system calls);

🔹 Command-line shells and utilities;

🔹 File system behavior, process control, signals, etc.;

> POSIX is the IEEE standard that defines a portable UNIX interface.

❓ Which kernel is running in Android OS?

Android OS is based on the **Linux kernel**, although the user space and application framework are customized by Google.

The Linux kernel in Android handles:

🔹 Process and memory management

🔹 File system access

🔹 Hardware drivers and device control

🔹 Networking

## Computer Hardware

The **CPU (Central Processing Unit)** is the “brain” of the computer, fetching and executing instructions in a cycle until a program finishes. Each CPU has its own instruction set (e.g., x86 vs. ARM), making them incompatible. To speed up execution, CPUs use registers to store variables, results, and instructions. Special registers, like the program counter, track the address of the next instruction.

The **Program Status Word (PSW)** register stores condition codes, CPU priority, mode (user/kernel), and control bits, playing a key role in system calls and I/O. When switching tasks, the operating system must save and restore all registers. Modern CPUs use pipelining, allowing multiple instructions to be fetched, decoded, and executed simultaneously for better performance.

A superscalar CPU has multiple execution units (e.g., integer, floating-point, Boolean) and can fetch and execute several instructions simultaneously, often out of order, with hardware ensuring correct results. CPUs also support two modes: kernel mode, with full hardware access (used by the OS), and user mode, with restricted access (used by applications or parts of embedded systems).

User programs run in user mode, with restricted instructions (no I/O or memory protection). To access OS services, they make system calls via the TRAP instruction, which switches execution to kernel mode. The OS performs the request, then returns control to the program. Other traps may occur due to hardware exceptions (e.g., divide by zero, underflow), and the OS decides whether to terminate, ignore, or pass control back to the program.

#### Multithreaded and Multicore Chips

Moore’s law observes that transistor counts on chips double about every 18 months, though physical limits will eventually stop this trend. Extra transistors enable designs like superscalar CPUs and larger caches, but diminishing returns push further innovations. One major advance is multithreading (hyperthreading), which allows a CPU to keep the state of multiple threads and switch between them rapidly. While not true parallelism, it reduces idle time and improves efficiency.

Multithreading makes each thread look like a separate CPU to the OS, which can lead to inefficient scheduling if threads share one CPU while others sit idle. Modern CPUs now use multicore designs, with many independent cores (some chips exceeding 60), requiring multiprocessor-capable operating systems. GPUs, with thousands of small cores, excel at parallel tasks (like graphics or encryption) but are poorly suited for general OS execution.

#### Memory

Memory must balance speed, size, and cost, so computers use a hierarchy. At the top are CPU registers—extremely fast but tiny (<1 KB). Below that is cache memory, which stores frequently used data in small, fast storage near the CPU. Accessing cache is quick (a few cycles), but a cache miss forces slower main memory access. Modern systems often use multiple cache levels (L1, L2, L3) with decreasing speed and increasing size.

Caching improves performance whenever some data is used more often than others. Operating systems use it for files, path lookups, and even network addresses. Key design issues include: when to add items to the cache, where to place them, which items to evict, and where to store evicted items.

In CPU caches, new items are typically added on a cache miss, with placement determined by memory address bits. Modified data is written back to its original memory location. Modern CPUs use multiple caches: small, very fast L1 caches (for instructions and data, ~16 KB each) and larger, slower L2 caches (several MB), which reduce memory access delays.

On multicore chips, caches can be shared among cores (Intel) or private to each core (AMD), each approach having trade-offs in complexity and consistency. Main memory (RAM) is the primary storage for CPU requests not in cache, typically ranging from hundreds of MB to several GB. Some systems also include non-volatile memory like ROM, which retains data without power and is used for bootloaders or low-level device control.

EEPROM and flash memory are non-volatile and rewritable, though slower than RAM, making them useful for firmware updates and portable devices. Flash is intermediate in speed between RAM and disk but wears out after many erase cycles. CMOS memory is volatile and powered by a small battery, storing system time, date, and configuration settings with minimal power consumption.

#### Disks

Magnetic disks (hard drives) are much cheaper and larger than RAM but far slower. Data is stored on spinning platters in tracks and sectors, accessed by a mechanical arm. Average access times include 1–10 ms for arm movement and 5–10 ms for rotation, with transfer rates ranging from 50 MB/s to 160 MB/s.

SSDs (Solid State Drives) store data in flash memory without moving parts, offering non-volatile storage like disks but faster access. Virtual memory allows programs larger than physical RAM by storing parts on disk and using RAM as a cache, with address translation handled by the MMU. Context switches in multiprogramming systems may require flushing caches and updating MMU mappings, which can be costly for performance.

#### I/O Devices

I/O devices consist of a controller and the device itself. The controller, often a small embedded computer, translates OS commands (e.g., read sector 11,206) into device-specific operations, handling complex details like disk geometry, bad sectors, and data assembly. The device presents a simple, standardized interface (e.g., SATA disks) so any compatible controller can operate it.

Device drivers are software that allow the OS to communicate with controllers. Each controller requires a specific driver, usually running in kernel mode. Drivers can be installed by relinking the kernel, loading at boot, or dynamically while the system runs—the last method is common for hot-pluggable devices like USB and IEEE 1394.

Device registers allow drivers to communicate with controllers, either mapped into the OS address space or accessed via a special I/O port space using IN/OUT instructions. I/O methods include busy waiting, where the driver polls the device until the operation completes, which ties up the CPU.

A second I/O method uses interrupts. The driver starts the device and returns, allowing the OS to do other work. When the device finishes, it signals the interrupt controller, which notifies the CPU. The CPU reads the device number to identify which device completed the operation, enabling efficient multitasking without busy waiting.

When an interrupt occurs, the CPU saves the program counter and PSW, switches to kernel mode, and uses the interrupt vector to find the device’s handler. The handler queries the device, completes the I/O, and returns control to the interrupted program. A third I/O method uses DMA (Direct Memory Access), allowing data transfer without CPU intervention; the DMA signals an interrupt when done. Interrupts can be temporarily disabled to handle timing conflicts, with the controller prioritizing multiple pending interrupts.

#### Buses

As CPUs and memory became faster, single-bus architectures became a bottleneck, leading to multiple buses (cache, memory, PCIe, PCI, USB, SATA, DMI) with different speeds and purposes. The PCIe bus is the main high-speed bus, using serial point-to-point connections instead of older shared parallel buses, supporting multiple lanes for parallel data transfer. PCIe is continually upgraded (e.g., 2.0 → 3.0 → 4.0) to match the speed of modern peripherals.

Legacy PCI devices connect through separate hub processors, forming a tree of buses. Modern systems use multiple buses: DDR3 for memory, PCIe for graphics, DMI for hubs, USB for peripherals, and SATA for disks. Each CPU core has dedicated and shared caches, adding additional bus traffic. USB allows hot-pluggable connections of slower I/O devices, with speeds increasing from 12 Mbps (USB 1.0) to 5 Gbps (USB 3.0).

SCSI buses provide high-performance connections for disks and other bandwidth-heavy devices, mainly in servers and workstations (up to 640 MB/s). The OS must detect and configure peripherals, a task simplified by Plug and Play, which automatically assigns interrupts and I/O addresses, replacing the old manual DIP-switch setup that often caused conflicts.

#### Booting the Computer

The boot process begins with the BIOS on the motherboard, which performs basic I/O, checks RAM and devices, and scans buses to detect peripherals. It then selects a boot device (from CMOS settings) and loads the bootloader from its first sector, which in turn loads the operating system. The OS then queries the BIOS for device configuration and loads necessary device drivers.
After loading device drivers into the kernel, the operating system initializes tables, starts background processes, and launches the login program or GUI.

## Operating System Variants

#### Mainframe Operating Systems

Mainframe operating systems handle massive I/O and multiple jobs simultaneously. They provide batch processing (non-interactive jobs), transaction processing (many small requests per second), and timesharing (multiple remote users). Examples include OS/390, though UNIX variants like Linux are increasingly replacing them.

#### Server Operaring Systems

Server operating systems run on powerful computers to serve multiple users over a network, providing services like printing, file sharing, and web hosting. Examples include Solaris, FreeBSD, Linux, and Windows Server 201x.

#### Multiprocessor Operating Systems

Multiprocessor and parallel systems connect multiple CPUs into a single system, requiring specialized operating systems for communication, connectivity, and consistency. Modern multicore personal computers also need OS support for multiple cores. Many popular OSes, including Windows and Linux, support multiprocessor environments.

#### Personal Computer Operating Systems

Personal computer operating systems focus on supporting a single user with multiprogramming, handling dozens of programs at once. They are widely used for tasks like word processing, spreadsheets, games, and Internet access. Examples include Linux, FreeBSD, Windows 7/8, and macOS.

#### Handheld Operating Systems

Handheld computers—including tablets, smartphones, and PDAs—feature multicore CPUs, sensors, and significant memory, running sophisticated operating systems. The market is dominated by Android and iOS, with a large ecosystem of third-party applications.

#### Embedded Operating Systems

Embedded systems run on the computers that control devices that are not generally thought of as computers and which do not accept user-installed software.
Typical examples are microwave ovens, TV sets, cars, DVD recorders, traditional
phones, and MP3 players.

The main property which distinguishes embedded systems from handhelds is the certainty that no untrusted software will ever run on it. You cannot download new applications to your microwave oven — all the software
is in ROM. This means that there is no need for protection between applications,
leading to design simplification. Systems such as Embedded Linux, QNX and VxWorks are popular in this domain.

#### Sensor-Node Operating Systems

Networks of tiny sensor nodes are being deployed for numerous purposes. These nodes are tiny computers that communicate with each other and with a base station using wireless communication. Sensor networks are used to protect the perimeters of buildings, guard national borders, detect fires in forests, measure temperature and precipitation for weather forecasting, glean information about
enemy movements on battlefields, and much more.

The sensors are small battery-powered computers with built-in radios. They have limited power and must work for long periods of time unattended outdoors, frequently in environmentally harsh conditions. The network must be robust enough to tolerate failures of individual nodes, which happen with ever-increasing frequency as the batteries begin to run down.

Each sensor node is a real computer, with a CPU, RAM, ROM, and one or more environmental sensors. It runs a small, but real operating system, usually one that is event driven, responding to external events or making measurements periodically based on an internal clock. The operating system has to be small and simple
because the nodes have little RAM and battery lifetime is a major issue. Also, as with embedded systems, all the programs are loaded in advance; users do not suddenly start programs they downloaded from the Internet, which makes the design much simpler. TinyOS is a well-known operating system for a sensor node.

#### Real-time Operating Systems

Real-time operating systems (RTOS) prioritize meeting time-sensitive deadlines. Hard real-time systems guarantee actions occur at precise times (e.g., industrial process control, avionics), while soft real-time systems tolerate occasional deadline misses (e.g., digital audio, smartphones). RTOS may be implemented as tightly coupled libraries without full protection (e.g., eCos). Handheld, embedded, and real-time systems often overlap, with soft real-time aspects and preloaded software only.

#### Smart Card Operating Systems

Smart card operating systems run on tiny, credit-card-sized devices with severe CPU and memory constraints. Some handle a single function (e.g., payments), while others support Java applets, requiring multiprogramming, scheduling, and resource protection within a minimal OS.

## Operating Systems Concepts ❗

#### Processes

Processes are programs in execution, each with an address space (executable code, data, stack) and associated resources like registers, open files, and related processes. In multiprogramming systems, the OS switches between processes, saving their state so they can resume exactly where they left off. Most OSes store process information in a process table, while the address space is called the core image.

Process-management system calls handle creation, termination, memory management, and waiting for child processes. Processes can form process trees, with parent and child processes cooperating via interprocess communication (IPC). Processes can also set timers or notifications to handle asynchronous events, such as network message timeouts.

Signals are software interrupts (like timers or hardware traps). When a signal arrives the OS saves the process’s state, runs a signal handler (e.g., to retransmit a message), then restores the process.
Users and protection: each user has a UID (and belongs to groups with GIDs). Processes inherit the UID of their creator. One special UID — the superuser/Administrator — can bypass many protection rules.

> A UID (User Identifier) is a unique number assigned to each user on a Linux
> or UNIX system. It is used by the operating system to identify users
> and manage permissions, ownership of files, and access control. The root
> user always has UID 0, while regular users have UIDs starting from 1000
> (or 500 on older systems). UIDs are essential for system security and
> user management.

#### Address Spaces

Main memory holds executing programs. Simple OSs run one program at a time, while sophisticated OSs allow multiple programs simultaneously, using hardware-enforced protection to prevent interference. Each process has its own address space, which may exceed physical memory. Virtual memory lets the OS keep part of a process in RAM and part on disk, creating the illusion of a large contiguous address space. Managing memory and address spaces is a core OS function.

#### Files

A file system is a <ins>core</ins> OS feature that provides a consistent, device-independent way to manage data. The OS offers system calls to **create**, **remove**, **read**, and **write** files. Files are organized into directories (folders) to group related files together. Additional system calls allow creating and deleting directories, as well as adding or removing files from them. Directories can contain both files and other directories.

Both processes and files are organized hierarchically as trees, but they differ in depth, lifetime, and access control:

🔸 Process trees are shallow (usually ≤3 levels), short-lived (minutes), and only parents can control/access child processes.

🔸 File/directory trees are often deeper (4–5+ levels), long-lived (years), and can be accessed by a wider group beyond the owner.

**Files are identified by their path names:**

🔸 Absolute path: starts from the root directory <code>/</code>

```bash
/Faculty/Prof.Brown/Courses/CS101
```

🔸 Relative path: starts from the process’s current working directory

```bash
Courses/CS101 if the working directory is /Faculty/Prof.Brown
```

Processes can change their current working directory via a **system call**.

**File opening and permissions:**

Before a file can be read or written, it must be opened.

The OS checks permissions; if allowed, it returns a file descriptor (a small integer) for subsequent operations.

If access is denied, an error code is returned.

**Mounted file systems in UNIX:**

UNIX allows different file systems (e.g., hard disk, CD-ROM, USB drive) to be attached (“mounted”) into a single directory tree.

Before mounting: separate file systems cannot be accessed together.

After mounting: the external file system appears under a chosen directory in the root tree, allowing unified access (e.g., files on a CD-ROM mounted at /b can be accessed as /b/x and /b/y).

Mounting usually occurs on empty directories, because existing files at the mount point become inaccessible while the external system is mounted.

Multiple disks can all be mounted into a single tree, maintaining device independence.

**Special files in UNIX:**

UNIX treats I/O devices as files so they can be read/written with the same system calls as regular files.

Two kinds of special files:

Block special files – for devices with randomly addressable blocks (e.g., disks). Programs can read/write specific blocks directly.

Character special files – for devices that handle character streams (e.g., printers, modems).

Special files are conventionally located in the <code>/dev directory</code

```bash
/dev/lp for the printer
```

**Pipes:**

Pipes are pseudofiles used to connect processes for communication.

One process writes to the pipe as if it were an output file; another reads from it like an input file.

The implementation of pipes is similar to files, making interprocess communication look like ordinary file I/O.

The only way to detect that a file is actually a pipe is via a special system call.

#### Input/Output

I/O in Computers and Operating Systems:

All computers need input devices (keyboards, sensors, etc.) and output devices (monitors, printers, etc.) to interact with users.

The operating system is responsible for managing these devices.

Every OS includes an I/O subsystem to handle this management.

Some I/O software is device-independent, meaning it works with many devices in the same way.

Other parts, such as device drivers, are device-specific, tailored to control particular hardware.

#### Protection

Operating System Security

Computers store sensitive information, such as emails, business plans, and tax returns.

The operating system manages security to ensure that only authorized users can access files and resources.

**Example – UNIX File Permissions:**

Each file has a 9-bit protection code, divided into three 3-bit fields:

**Owner** – permissions for the file’s owner

**Group** – permissions for users in the owner’s group

**Others** – permissions for everyone else

Each 3-bit field uses the rwx convention:

🟡 <code>r</code> = read

🔵 <code>w</code> = write

🟣 <code>x</code> = execute

Example:

```bash
rwxr-x--x
```

Owner: read, write, execute

Group: read, execute

Others: execute only

For directories, <code>x</code> means search permission, and - indicates the absence of a permission.

**Additional Security Considerations:**

Protecting the system from unauthorized users, viruses, and other threats is also a key responsibility of the operating system.

#### The Shell

The Operating System vs. Programs That Use It

Operating system (OS): The code that executes system calls and manages hardware and resources.

Programs like editors, compilers, linkers, and shells are not part of the OS, even though they heavily use OS features.

**Example** – The UNIX Shell

The shell (e.g., <code>sh</code>, <code>csh</code>, <code>ksh</code>, <code>bash</code>) is a command interpreter that serves as the main
interface between the user and the OS (unless using a GUI).

**When a user logs in:**

The shell starts with the terminal as standard input and output.

It displays a prompt (e.g., <code>$</code>) to signal it is ready for commands.

When the user types a command, e.g., <code>date:</code>

The shell creates a child process to run the program.

The shell waits for the child process to finish.

Once finished, the shell displays the prompt again for the next command.

1. Redirection of Input and Output

Standard output (stdout) redirection:

```bash
date > file
```

ends the output of the date command into the file instead of the terminal.

Standard input (stdin) redirection:

```bash
sort < file1 > file2
```

Reads input from <code>file1</code>, sorts it, and writes the output to <code>file2</code>.

2. Pipes

Using output from one program as input to another:

```bash
cat file1 file2 file3 | sort > /dev/lp
```

<code>cat</code> concatenates three files.

<code>sort</code> organizes all lines alphabetically.

Output is sent to <code>/dev/lp</code>, usually the printer.

3. Background Execution

Ampersand (**&**) runs a command in the background:

```bash
cat file1 file2 file3 | sort > /dev/lp &
```

The shell immediately returns a prompt.

User can continue other work while the command runs.

4. Graphical User Interfaces (GUIs)

GUI is just a program running on top of the OS, similar to a shell.

Linux: Users can choose GUIs like Gnome or KDE, or even run no GUI (terminal only).

Windows: The default GUI (Explorer) can be replaced by another program, though few users do this.

#### Ontogeny Recapitulates Phylogeny

**Key Ideas:**

Haeckel’s concept:

Ontogeny recapitulates phylogeny → Embryo development (ontogeny) mirrors the evolutionary
stages of the species (phylogeny).

**Example** (simplified/incorrect for humans): a human embryo passes through
“fish” and “pig” stages before becoming human.

**Analogy to computers:**

Each new class of computers (mainframe → minicomputer → personal computer → handheld → embedded → smart card)
seems to repeat stages its ancestors went through, in both hardware and software.

Innovations build on what came before, much like evolution.

**Technology drives adoption:**

Just as the Romans lacked cars because the technology didn’t exist,
computers exist because we can now build them cheaply, not because there was a
long-standing human desire.

Technological capability shapes what systems appear and how they evolve.

**Takeaway:**

The evolution of computing isn’t just market demand—it’s largely technology-driven,
and each new type of system often retraces steps its predecessors took,
incorporating lessons and limitations along the way.

**Key Points:**

Technology can make ideas obsolete, then revive them:

Unlike biology, where extinction is permanent, in computing an “extinct” idea may
reappear if technological conditions change.

**Example:** Cache memory appeared when CPUs became faster than memory,
might vanish if memory surpasses CPU, then reappear if CPU speeds outpace memory again.

**Obsolete concepts still matter:**

Understanding why an idea became obsolete helps predict if it might become useful again in the future.

Execution paradigms illustrate the **pendulum effect**:

Early computers: hardwired instruction sets → fastest but inflexible.

Microprogramming (IBM 360): interpreted “hardware instructions” → flexible, made hardwired execution obsolete.

RISC computers: direct execution faster → microprogramming becomes obsolete.

Modern interpretation (Java applets): network delays make execution speed less critical → interpretation resurges.

Takeaway:
Computing ideas are not permanently extinct; they resurface depending on relative performance trade-offs in hardware and software. Understanding the “why” behind obsolescence is crucial to predicting future relevance.

> RISC stands for **Reduced Instruction Set Computer**, a type of computer architecture that focuses on
> a simplified set of instructions. The primary goal of RISC architecture is to execute instructions quickly by using a smaller,
> highly optimized set of instructions that can be executed in a single clock cycle. This contrasts with **CISC** (Complex Instruction Set Computer) architectures, which use a larger set of more complex instructions.
> The design philosophy behind RISC is to streamline the hardware by reducing the complexity of the instruction set. This allows for faster instruction execution, simpler hardware design, and improved performance for certain types of workloads. RISC architectures typically rely on software (compilers) to handle complex operations by breaking them down into multiple simpler instructions.
> Examples of RISC-based processors include ARM, MIPS, and RISC-V. These architectures are widely used in embedded systems, mobile devices, and other performance-critical applications due to their efficiency and power-saving capabilities.

#### Large Memories

**Key Points:**

Memory constraints drove low-level programming:

IBM 7090/7094 (late 1950s–1964): ~128 KB memory → assembly language for both programs and operating systems to conserve memory.
High-level languages emerged when resources improved:
FORTRAN, COBOL compilers became good → assembly language declined.

Minicomputers (e.g., PDP-1, 4 KB memory) → assembly language resurged due to tight memory.
Microcomputers and embedded systems repeated this pattern:
Early 1980s microcomputers: 4 KB memory → assembly language dominant.
Embedded computers (same CPUs as microcomputers) → assembly used initially.
Modern trend toward high-level languages as resources grow:
Personal computers: abundant memory → C, C++, Java, etc.
Smart cards: small memory → sometimes Java interpreted, not compiled.

Takeaway:
The hardware limits of memory and CPU power repeatedly dictate the software approach. When resources are limited, low-level programming dominates;
when resources expand, high-level languages flourish. This cyclical pattern mirrors the earlier discussion about obsolescence and revival of ideas.

#### Protection Hardware

**Key Points:**

<ins>Early mainframes (IBM 7090/7094):</ins>

No protection hardware → monoprogramming only.
A buggy program could crash the OS or entire machine.

IBM 360:

Introduced primitive protection hardware → allowed multiprogramming (multiple programs in memory, taking turns running).
Monoprogramming became obsolete… temporarily.
Early minicomputers (PDP-1, PDP-8):
No protection hardware → back to monoprogramming.
Later, PDP-11 added protection hardware → multiprogramming and eventually UNIX.

<ins>Early microcomputers (Intel 8080):</ins>

Again, no protection hardware → single-program operation.

Multiprogramming possible only with Intel 80286 and newer CPUs.

<ins>Embedded systems today:</ins>

Often lack protection hardware, so typically run only one program at a time.

Takeaway:

Just like the earlier memory constraints affecting programming languages, the presence or
absence of hardware protection repeatedly dictated whether multiprogramming could be supported.
Concepts like multiprogramming become “obsolete” and then resurface depending on hardware evolution.

**Key Points:**

<ins>Mainframes:</ins>

Initially: No protection hardware → single-program operation, simple OS.
Later: Added protection hardware → multiprogramming → full timesharing.

<ins>Minicomputers:</ins>

Initially: No protection hardware → ran one program at a time.
Later: Gained protection hardware → ran multiple programs.

<ins>Microcomputers (early PCs):</ins>

Initially: Very small memory (≈4 KB) → could not support high-level languages or multiprogramming.

Later: Memory and hardware improvements → multiprogramming, modern OS features.

<ins>Handhelds and smart cards:</ins>

Followed the same pattern → started simple, gradually gained more advanced OS capabilities as hardware improved.

<ins>Underlying Principle:</ins>

Software development is dictated by technology.
Limitations in memory or protection hardware forced simpler OS design; improvements enabled more complex functionality.

**Takeaway:**

The evolution of operating systems is cyclical and technology-driven. Hardware dictates what software can do,
and as hardware evolves, software features like multiprogramming, high-level languages,
and timesharing are reincarnated across generations of computing devices.

#### Disks

**Key Points:**

<ins>Early Mainframes (1950s–1960s):</ins>

Primarily magnetic-tape based: programs read from tape, compiled, run, and results written back to tape.
No disks, no file system initially.
IBM RAMAC (1956): First hard disk, 5 million 7-bit characters (~medium-res photo), occupied ~4 m², very expensive (~$35,000/year).
Led to primitive file systems.

CDC 6600 (1964):
Fastest computer of its time.
Allowed “permanent files” with user-assigned names, creating a single-level directory.
Mainframes eventually evolved to complex hierarchical file systems, e.g., MULTICS.

<ins>Minicomputers (e.g., PDP-11, 1970):</ins>

Standard disk: RK05, 2.5 MB, compact compared to RAMAC.
Initially had single-level directories.
Microcomputers (early PCs, CP/M):
Floppy disks, single-level directory system.
File system concepts were still simple, mirroring early minicomputers.

**Takeaway:**

File systems evolved alongside storage technology: from no disks → single-level directories → hierarchical directories.
Early computers were constrained by capacity and cost, limiting the complexity of storage management.

#### Virtual memory

**Key Points:**

<ins>Virtual Memory:</ins>

Allows programs larger than physical RAM to run by swapping pages between RAM and disk.
First appeared on mainframes, then adopted by minicomputers and later microcomputers.
Enabled dynamic linking: programs could load libraries at runtime instead of compiling them in.
MULTICS was the first system to support this feature.

<ins>Recycling of Ideas:</ins>

Many concepts originate in one context, become obsolete, then reappear in new contexts:
Assembly language → revived in early microcomputers
Monoprogramming → reappears in tiny embedded systems
Single-level directories → reused in early PCs
This demonstrates the technological pendulum: ideas are dependent on hardware capabilities and system requirements.

**Broader Insight:**

Studying older concepts and algorithms is valuable because they may resurface in modern contexts like embedded systems or smart cards.
Essentially, virtual memory is an example of a concept that started in high-end systems and trickled down over time, while older “obsolete” ideas often re-emerge in constrained environments.

## System Calls

1. What Are System Calls?

A system call (syscall) is a controlled entry point into the operating system kernel. It allows a user program to request a service from the OS that cannot be performed in user mode, such as accessing hardware, creating processes, or performing I/O.
Key idea: User programs cannot directly access hardware for safety and protection; they must go through the OS using system calls.

2. Why System Calls Exist

Protection: Prevents user programs from crashing the system or accessing other processes’ memory.
Abstraction: Hides hardware complexity (e.g., disk layout, device registers) behind clean APIs.
Resource management: Allows the OS to manage CPU, memory, and I/O devices efficiently.

3. How System Calls Work

User program executes a library function (e.g., open(), read())
Library code triggers a software interrupt or trap
CPU switches to kernel mode
OS executes the requested service
Result is returned to the user program
CPU switches back to user mode
Think of it as a door between user mode and kernel mode, controlled and secure.

4. Categories of System Calls

System calls can be broadly classified into several categories:
a. Process Control
Purpose: Manage processes (creation, execution, termination, scheduling).

Examples:
fork() → create a new process
exec() → replace process memory with a new program
exit() → terminate a process
wait() → wait for a child process to finish

b. File Management
Purpose: Access, create, manipulate files and directories.

Examples:
open(), close() → open/close a file
read(), write() → read from/write to a file
unlink() → delete a file
mkdir(), rmdir() → create/remove directories

c. Device Management
Purpose: Communicate with I/O devices through device drivers.

Examples:
ioctl() → device-specific operations
read(), write() → on special files representing devices

d. Information Maintenance
Purpose: Obtain system or process information, or modify it.

Examples:
getpid() → get process ID
alarm() → set a timer
time() → get current time

e. Communication
Purpose: Enable interprocess communication (IPC).

Examples:
pipe() → create a pipe between processes
shmget() → allocate shared memory
msgget() → create message queues
socket() → network communication

5. Mechanism Details
   System Call Invocation: Usually via a software interrupt, trap, or a special CPU instruction (syscall in x86-64).
   Kernel Mode: System calls execute in privileged kernel mode, which can directly access hardware.
   Return Values: Typically indicate success or failure, with -1 or an error code on failure.
   Libraries: C standard library (libc) often wraps system calls for easier usage (e.g., printf() calls write() internally).

6. Examples

```c
#include <stdio.h>
#include <unistd.h>
#include <fcntl.h>

int main() {
    int fd = open("file.txt", O_RDONLY);  // system call
    if (fd == -1) {
        perror("open failed");
        return 1;
    }

    char buffer[100];
    ssize_t n = read(fd, buffer, 100);   // system call
    write(1, buffer, n);                 // system call (stdout)
    close(fd);                            // system call

    return 0;
}
```

Here, open(), read(), write(), close() are direct system calls handled by the kernel.

7. Important Concepts Related to System Calls

Blocking vs Non-blocking: Some system calls may block the process until completion (e.g., read()), others return immediately (e.g., fcntl() with O_NONBLOCK).
Signals and Interrupts: Certain system calls can be interrupted by signals (e.g., timers, I/O events).
File Descriptors: Numeric handles returned by the OS to identify files, sockets, or devices.
Context Switching: When a syscall occurs, CPU switches from user to kernel mode, saving the process state.

8. Practical Considerations
   System calls are slower than library functions because of the user-to-kernel mode switch.
   Minimizing syscalls in performance-critical applications is often desirable.
   Security: Only kernel can enforce access permissions, so system calls are the gatekeepers for protected resources.

## Operating System Structure ❗

#### Monolithic Systems

1. Definition
   A monolithic OS is one in which the entire operating system runs as a single program in kernel mode.
   All the services—process management, memory management, file systems, device drivers, and system calls—
   are compiled into one large executable.

**Key idea:** Everything lives in kernel space and can directly call any other part of the OS.

2. Structure and Organization
   The OS is a collection of procedures (functions or modules).
   Each procedure can freely call any other procedure if needed.
   No inherent restrictions on access or communication between procedures.

<code>Implication:</code>

**Efficiency:** Calls are simple and fast since they are just normal function calls within the same address space.

**Complexity:** Thousands of procedures calling each other can make the system hard to understand, maintain, or extend.

3. Compilation and Linking

Compile each procedure (or file) into object code.

Link all object files into a single kernel executable.

The OS now runs as one big binary in kernel mode.

Note: Unlike modular or microkernel approaches, there’s no strict encapsulation; every function can access all data and functions of the OS.

4. Pros of Monolithic Design

High performance: Direct function calls within a single address space are faster than inter-process communication.

Simple execution model: Only one program (the OS kernel) is running in kernel mode.

Full access to hardware: Since everything is in kernel mode, all procedures can manipulate hardware or resources directly.

5. Cons of Monolithic Design

Reliability: A bug in any procedure can crash the entire OS.

Maintainability: Hard to isolate, modify, or debug parts of the OS.

Lack of information hiding: All procedures can access all other procedures and internal data structures.

6. Examples

UNIX (traditional versions like early BSD)

Linux kernel

MS-DOS (early versions)

Summary Table

<table>
  <thead>
    <tr>
      <th>Aspect</th>
      <th>Details</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Definition</td>
      <td>Entire OS runs as a single program in kernel mode, with all services compiled into one executable.</td>
    </tr>
    <tr>
      <td>Structure</td>
      <td>Procedures can freely call each other without restrictions, leading to high efficiency but complexity.</td>
    </tr>
    <tr>
      <td>Advantages</td>
      <td>High performance, simple execution model, full hardware access.</td>
    </tr>
    <tr>
      <td>Disadvantages</td>
      <td>Low reliability, difficult to maintain, lack of modularity.</td>
    </tr>
    <tr>
      <td>Examples</td>
      <td>UNIX, Linux kernel, MS-DOS.</td>
    </tr>
  </tbody>
</table>

Key Insight: The monolithic design trades safety and modularity for speed and simplicity. Modern operating systems (like Linux) mitigate some of the risks with modular kernels, where some components can be loaded/unloaded dynamically, but the basic monolithic principle still applies.

**System Calls in Monolithic Systems**

Even in a monolithic OS, there is structure behind how user programs access OS services.

**How a system call works**

User program sets up parameters for the system call (usually on the stack or in registers).
Trap instruction is executed.
This switches the CPU from user mode to kernel mode.
It also transfers control to a predefined entry point in the OS.
Operating system fetches parameters and identifies which system call was requested.

System call table lookup:

The OS has a table of pointers, where each entry corresponds to a system call.
Slot **k** points to the procedure that implements system call **k**.
The service procedure executes, performs the operation, and returns control to the user program.

> This mechanism provides a controlled way for user programs to access
> privileged OS functions safely, even in a monolithic kernel.

<ins>Suggested OS Structure</ins>

Even though the kernel is monolithic, it can be organized into layers or components:
Main program / dispatcher
Receives requests (system calls) and invokes the correct service procedure.
Service procedures
One for each system call.

Example: <code>read()</code>, <code>write()</code>, <code>fork()</code>, <code>exec()</code> in UNIX.

Utility procedures
Helper routines used by many service procedures.
Example: routines for copying data between user and kernel memory, managing common data structures, or validating parameters.

Diagrammatically:

```bash
User Program
      |
  Trap Instruction
      |
  Main OS Dispatcher
      |
 -------------------
| Service Procedures |
 -------------------
      |
 -------------------
| Utility Procedures |
 -------------------
```

**Loadable Extensions**

Many monolithic OSes still support dynamically loadable modules, which lets you extend functionality without rebooting the OS:
UNIX/Linux: Shared libraries (.so files)
Windows: Dynamic-Link Libraries (.dll files)

These often include:
Device drivers
File system modules
Network protocols

**Example:** <code>C:\Windows\system32</code> on Windows contains thousands of <code>.dll</code> files that the OS and programs can use dynamically.

**Key Points to Remember**

System calls are the interface between user programs and kernel services.
Trap instruction ensures safety by switching to kernel mode.
Monolithic OS can still be modular internally, with service procedures and utility routines.
Loadable extensions provide flexibility without redesigning or rebooting the kernel.

#### Layered Systems

**Concept of Layered OS**

A layered operating system is structured as a hierarchy of layers, each built upon the layer below it:

<ins>Lowest layer:</ins> Handles the most fundamental functions, usually very close to the hardware.
<ins>Higher layers:</ins> Use services provided by the layers below, adding more sophisticated functionality.
Each layer only interacts directly with the layer immediately beneath it.

**Advantages:**

Easier to understand, design, and debug, since each layer is relatively independent.
Crashes or bugs in higher layers are less likely to corrupt lower layers.
Clear information hiding: higher layers do not need to know the internal workings of lower layers.

**Disadvantages:**

Slightly less efficient than monolithic systems, because service calls may have to pass through multiple layers.

**The THE System**

Developed by **E. W. Dijkstra (1968)** at Technische Hogeschool Eindhoven.
Implemented on an Electrologica X8 computer with 32K of 27-bit words.
It was a simple batch system, but very influential for OS design.

<ins>Layer Structure of THE System</ins>

The THE system had 6 layers:

**Layer 0** – CPU Scheduling and Multiprogramming

Allocates the processor among processes.
Handles interrupts and timer expiration.
Provides basic multiprogramming, so that higher layers can run sequential processes without worrying about concurrent execution.

**Layers 1–5** – Higher-Level Services

Sequential processes built on top of layer 0.

Each layer provided more sophisticated services, such as:

File management
I/O device management
Interprocess communication
User interface and job control
Each layer only interacts with the layer immediately below it.
Layered design ensures modularity, abstraction, and a clear separation of concerns.

**Key Takeaways**

Layered OSes generalize the idea of modularity in monolithic systems.
Each layer offers a well-defined interface to the layer above.
THE system demonstrated that complex OS functionality could be structured in layers, simplifying development and debugging.
Modern OS designs often combine monolithic kernels with layered concepts to balance efficiency and modularity.

```bash
Layer 5: User-level job control and batch processing
        - Provides interface for submitting and controlling jobs
        - Uses services from lower layers for I/O and file access

Layer 4: I/O management
        - Handles input/output devices
        - Provides abstraction to upper layers

Layer 3: Interprocess communication
        - Manages communication between processes
        - Ensures synchronization and data transfer

Layer 2: Memory management
        - Allocates and protects memory for processes
        - Provides virtual memory abstractions

Layer 1: Device drivers and low-level routines
        - Provides basic access to hardware devices
        - Called by higher-level services

Layer 0: CPU scheduling and multiprogramming
        - Allocates CPU to processes
        - Handles interrupts and timer events
        - Provides basic multiprogramming capabilities
```

**How it works:**

Each layer uses only the services of the layer directly below it.
Layer 0 is closest to the hardware; Layer 5 is closest to the user.
This design provides modularity, abstraction, and better maintainability compared to a purely monolithic system.

#### Client-Server Model

The client-server model distinguishes between servers, which provide services, and clients, which use them. Clients request services by sending messages, and servers respond. This works whether the processes run on the same machine or on different machines connected via a network. Many modern systems, including the Web, use this model: a PC (client) requests a webpage from a server, which then sends it back.

1. Message Passing

Communication between clients and servers usually occurs via message passing, not direct procedure calls.
Messages contain requests and may include parameters; responses carry the results or status.
Message passing allows the location transparency: clients don’t need to know if the server is local or remote.

2. Synchronous vs Asynchronous Communication

Synchronous: the client waits for the server to respond (blocking).
Asynchronous: the client sends a request and continues processing; the server responds later (non-blocking).

3. Advantages of the Model

Modularity: Services are encapsulated in servers, making maintenance easier.
Scalability: Multiple clients can access a server simultaneously.
Network transparency: The same model works for single machines or distributed systems.
Flexibility: Servers can be upgraded or replaced independently of clients.

4. Disadvantages / Challenges

Performance overhead: Message passing is slower than direct function calls.
Reliability: Server failures affect all clients relying on that service.
Complexity: Handling network delays, concurrency, and failures adds complexity.

5. Examples

Web browsing: Browser (client) ↔ Web server.
Email: Email client ↔ Mail server.
Databases: Application ↔ Database server.
Microkernels: Core OS services as servers; user processes as clients.

```bash
Single Machine:
   +---------+          +---------+
   | Client  | <----->  | Server  |
   +---------+          +---------+
       |                     |
       |   Message Passing    |
       +---------------------+

Networked Machines:
   +---------+                 +---------+
   | Client  |  ----Message-->  | Server  |
   +---------+  <---Reply----   +---------+
       |                             |
   Local/Remote                     Local/Remote
      Machine                        Machine

```

#### Virtual Machines

The initial OS/360 was a batch system, but users wanted interactive terminals.
IBM’s official timesharing system, TSS/360, arrived late, was large and slow,
and was eventually abandoned. Meanwhile, IBM’s Cambridge group created
VM/370 (originally CP/CMS), later evolving into z/VM, widely used on IBM mainframes.

VM/370 separates multiprogramming from providing a convenient interface.
Its virtual machine monitor runs on the bare hardware, offering multiple
virtual machines that are exact copies of the physical machine, including
kernel/user modes, I/O, and interrupts.

Each VM/370 virtual machine is identical to the real hardware, so it can run
any OS that runs on the physical machine. Different VMs often run different OSes;
originally, some ran OS/360 while others ran **CMS** (Conversational Monitor System)
for interactive timesharing.

When a CMS program makes a system call, it is handled by the OS in its VM, not by
VM/370. The OS then issues normal hardware I/O instructions, which are trapped by
VM/370 and executed as part of the virtual hardware simulation.

This separation of multiprogramming and extended machine functions makes each
component simpler, flexible, and easier to maintain. Modern z/VM runs multiple
full OSes simultaneously, such as Linux alongside traditional IBM systems.

Although IBM and some other companies have offered virtual-machine products for
decades, virtualization in PCs was largely ignored until recently. New needs and
technologies have made it popular:

Server consolidation: Companies can run multiple servers (mail, web, FTP, etc.)
on a single machine without one crash affecting the others.

Web hosting: Virtual machines allow hosting providers to offer each customer a
full “virtual server” on a shared physical machine. This gives flexibility like a
dedicated server at the cost of shared hosting.

<ins>Virtualization for End Users:</ins>

Users can run multiple OSes simultaneously (e.g., Windows and Linux) on one machine.

Type 1 hypervisor (formerly “virtual machine monitor”) manages the virtual machines.

Challenge: CPUs must be virtualizable. Early x86 CPUs ignored privileged
instructions in user mode, making virtualization inefficient.

Solution: Academic projects like Disco (Stanford) and Xen (Cambridge) solved these
problems.

Modern hypervisors: VMware Workstation, Xen, KVM (Linux), VirtualBox (Oracle),
Hyper-V (Microsoft).

Improving Virtual Machine Performance:

**Binary Translation / Machine Simulators**

Early research projects improved interpreters (e.g., Bochs) by translating blocks
of code on the fly and caching them.

Performance improved, but still insufficient for commercial use.

**Hybrid Approach / Type 2 Hypervisors**

Add a kernel module to handle heavy tasks (e.g., VMware Workstation).
Use the host OS and file system to create virtual disks and processes.
Guest OS runs as if on real hardware, with GUI and background processes.
Type 1 vs. Type 2 Hypervisors
Type 1: No host OS, manages storage and processes directly.
Type 2: Relies on a host OS for storage, process creation, and file management.

**Paravirtualization**

Modifies the guest OS to remove privileged instructions.
Not true virtualization, but improves performance in certain setups.

#### Java Virtual Machine (JVM):

<ins>Purpose:</ins>

JVM is a virtual machine architecture designed to run Java programs anywhere.

**How it works:**

Java source code → compiled into JVM bytecode → executed by a software JVM interpreter.
JVM abstracts away the underlying hardware, making Java programs portable.

**Advantages:**

Platform independence: Same JVM bytecode can run on any machine with a JVM interpreter.
Safety & security: Properly implemented JVM interpreters can check incoming programs
and execute them in a protected environment.
Simplicity: Easier to interpret than producing native binaries for multiple architectures.

#### Exokernels

<ins>Concept:</ins>

Instead of fully emulating hardware like traditional virtual machines,
an exokernel partitions resources and allocates them to user-level virtual machines.

<ins>How it works:</ins>

Runs in kernel mode.
Allocates CPU, memory, and disk blocks to each virtual machine.
Checks that each VM only uses its assigned resources.
User-level VMs can run their own operating systems.

**Advantages:**

Less overhead: No need for address remapping for virtualized resources.
Separation of concerns: Multiprogramming handled by exokernel; OS code runs in user space.
Efficiency: Each VM accesses resources directly within its allocation.
Here’s a simple diagram comparing traditional virtual machines and the exokernel approach:

```bash
Traditional Virtual Machines (VM/370, Type 1 Hypervisor)
--------------------------------------------------------
          User OS (Guest 1)
          ----------------
          User OS (Guest 2)
          ----------------
        Virtual Machine Monitor / Hypervisor
        -----------------------------
        Physical Hardware (CPU, Memory, Disk, I/O)

Notes:
- Each guest OS thinks it has the full machine.
- Hypervisor remaps all resources (CPU, memory, disk) to avoid conflicts.
- Full emulation overhead.

--------------------------------------------------------

Exokernel
---------
          User-level OS / VM (1)
          ----------------------
          User-level OS / VM (2)
          ----------------------
                   Exokernel
                   -------------
                   Physical Hardware (CPU, Memory, Disk, I/O)
```

Notes:

- Exokernel only allocates resources and enforces protection.
- No emulation or remapping of resources.
- OS runs in user space directly on allocated resources.
- Lower overhead, more efficient.

## Von Neumann Machine

1. The Von Neumann architecture (1945, John von Neumann) is the basic design model of almost all modern computers.
   It defines how a computer system should be organized:

One memory stores both instructions (programs) and data.
A CPU (Central Processing Unit) fetches instructions, decodes them, and executes them.
Input/output devices let the user interact with the machine.
It’s also called the stored-program concept → programs are stored in memory just like data.

2. The Components
   Here’s the basic structure:

```bash
           +-------------------+
Input ---> |                   |
           |                   | ---> Output
           |   Memory          |
           | (data+programs)   |
           +---------+---------+
                     |
            +--------+--------+
            |                 |
            |   CPU           |
            |                 |
   +--------+--------+  +-----+-----+
   | Control Unit    |  | Arithmetic|
   | (fetch/decode)  |  | Logic Unit|
   +-----------------+  +-----------+
```

Key parts:

Memory: stores instructions & data.
Control Unit (CU): fetches an instruction, decodes it, and tells ALU what to do.
Arithmetic Logic Unit (ALU): performs calculations and logical operations.
Registers: tiny, very fast storage inside CPU (e.g., accumulator, instruction register, program counter).
Input/Output: communication with outside world.

3. The Von Neumann Cycle (Fetch–Decode–Execute)

Every program runs in this endless loop:
Fetch: Control Unit fetches the next instruction from memory (address stored in the Program Counter).
Decode: Instruction is interpreted (e.g., ADD, LOAD, STORE).
Execute: ALU or I/O unit carries out the instruction.
Update PC: Program Counter moves to the next instruction.
This is the instruction cycle.

4. Simple Example in Von Neumann "code"

Let’s say you want to compute:

```bash
Z = X + Y
```

In pseudo-machine code:

```bash
1. LOAD X        ; load value of X into Accumulator
2. ADD Y         ; add value of Y to Accumulator
3. STORE Z       ; store result into memory location Z
4. HALT          ; stop program
```

What happens:

CPU fetches instruction 1, decodes it (LOAD), executes it → Accumulator = X.
CPU fetches instruction 2, executes ADD → Accumulator = X+Y.
CPU fetches instruction 3, executes STORE → Z = Accumulator.
Instruction 4 halts program.

5. Why it Matters

Foundation of all modern computers (PCs, laptops, smartphones all follow this model).
Introduced stored programs → programs are just data, so computers can load & run new software easily.

Limitations:

Von Neumann bottleneck = CPU speed limited by memory bandwidth (fetching instructions/data one at a time).
But still forms the backbone of computer science.
Most common commands:

<!-- Von Neumann / Simple Machine Commands — Cheatsheet -->
<section>
  <h2>Von Neumann — Simple Machine Commands (Cheatsheet)</h2>

  <p><strong>Registers (common)</strong>: <code>PC</code> (Program Counter), <code>IR</code> (Instruction Register),
  <code>ACC</code> (Accumulator), <code>SP</code> (Stack Pointer), general registers <code>R0..Rn</code>.</p>

  <table>
    <thead>
      <tr>
        <th>Command</th>
        <th>Meaning</th>
        <th>Example / Notes</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>LOAD X</code></td>
        <td>Load value at memory address <code>X</code> into <code>ACC</code> (or a register)</td>
        <td><code>ACC ← M[X]</code></td>
      </tr>
      <tr>
        <td><code>STORE X</code></td>
        <td>Store value from <code>ACC</code> (or a register) into memory address <code>X</code></td>
        <td><code>M[X] ← ACC</code></td>
      </tr>
      <tr>
        <td><code>MOVE R1, R2</code></td>
        <td>Copy value from <code>R2</code> to <code>R1</code></td>
        <td>Register-to-register transfer</td>
      </tr>
      <tr>
        <td><code>ADD X</code></td>
        <td>Add value at <code>X</code> to <code>ACC</code></td>
        <td><code>ACC ← ACC + M[X]</code></td>
      </tr>
      <tr>
        <td><code>SUB X</code></td>
        <td>Subtract value at <code>X</code> from <code>ACC</code></td>
        <td><code>ACC ← ACC - M[X]</code></td>
      </tr>
      <tr>
        <td><code>MUL X</code></td>
        <td>Multiply <code>ACC</code> by value at <code>X</code></td>
        <td><code>ACC ← ACC * M[X]</code></td>
      </tr>
      <tr>
        <td><code>DIV X</code></td>
        <td>Divide <code>ACC</code> by value at <code>X</code></td>
        <td>Be careful of divide-by-zero</td>
      </tr>
      <tr>
        <td><code>INC R</code></td>
        <td>Increment register <code>R</code> by 1</td>
        <td><code>R ← R + 1</code></td>
      </tr>
      <tr>
        <td><code>DEC R</code></td>
        <td>Decrement register <code>R</code> by 1</td>
        <td><code>R ← R - 1</code></td>
      </tr>
      <tr>
        <td><code>JMP LABEL</code></td>
        <td>Unconditional jump — set <code>PC</code> to <code>LABEL</code></td>
        <td>Flow control</td>
      </tr>
      <tr>
        <td><code>JZ LABEL</code></td>
        <td>Jump if zero — jump when <code>ACC</code> == 0</td>
        <td>Conditional branch</td>
      </tr>
      <tr>
        <td><code>JNZ LABEL</code></td>
        <td>Jump if not zero — jump when <code>ACC</code> ≠ 0</td>
        <td>Conditional branch</td>
      </tr>
      <tr>
        <td><code>CALL LABEL</code></td>
        <td>Call subroutine — push return address, set <code>PC</code> to <code>LABEL</code></td>
        <td>Use <code>RET</code> to return</td>
      </tr>
      <tr>
        <td><code>RET</code></td>
        <td>Return from subroutine — pop return address into <code>PC</code></td>
        <td></td>
      </tr>
      <tr>
        <td><code>PUSH R</code></td>
        <td>Push register <code>R</code> onto stack</td>
        <td><code>SP ← SP - 1; M[SP] ← R</code></td>
      </tr>
      <tr>
        <td><code>POP R</code></td>
        <td>Pop top of stack into register <code>R</code></td>
        <td><code>R ← M[SP]; SP ← SP + 1</code></td>
      </tr>
      <tr>
        <td><code>IN</code></td>
        <td>Read a value from an input device into <code>ACC</code></td>
        <td>Device I/O (simplified)</td>
      </tr>
      <tr>
        <td><code>OUT</code></td>
        <td>Write <code>ACC</code> (or register) to an output device</td>
        <td>Device I/O</td>
      </tr>
      <tr>
        <td><code>NOP</code></td>
        <td>No operation — does nothing for one cycle</td>
        <td>Useful for timing / alignment</td>
      </tr>
      <tr>
        <td><code>HALT</code></td>
        <td>Stop program execution</td>
        <td>End of program</td>
      </tr>
    </tbody>
  </table>

  <h3>Tiny example: Z = X + Y</h3>
  <pre><code>
    ; assume X, Y, Z are memory addresses
    LOAD X    ; ACC = M[X]
    ADD  Y    ; ACC = ACC + M[Y]
    STORE Z   ; M[Z] = ACC
    HALT
  </code></pre>

  <p><em>Tip:</em> On a real instruction set you’ll have addressing modes (immediate, direct, indirect, register),
  and system calls or traps for privileged actions (I/O, process control).</p>
</section>

## Hypervisors

🧩 Type 0 — Hardware or Firmware Hypervisor

The lowest-level form of virtualization.
Implemented in hardware (firmware layer) — below the OS.
Manages OS instances directly, sometimes before any OS boots.
Found in mainframes and enterprise servers.

Examples:

IBM PR/SM (Processor Resource/System Manager)
HP Integrity VM
Oracle LDOMs (Logical Domains)

✅ Pros:

Highest stability and performance (runs at firmware level)
Very secure and isolated
Used in mission-critical systems

❌ Cons:

Not flexible — specific to hardware vendor
Hard to modify or extend

⚙️ Type 1 — Bare-Metal Hypervisor

Runs directly on the physical hardware.
Provides virtual machines that each run a guest operating system.
No host OS between hypervisor and hardware.

Examples:

VMware ESXi
Microsoft Hyper-V (Server version)
Xen / XCP-ng
KVM (Kernel-based Virtual Machine)
Proxmox VE

✅ Pros:
High performance (no host OS overhead)
Strong isolation and security
Reliable for servers and cloud environments

❌ Cons:
Requires dedicated hardware
More complex to manage and install

⚙️ Type 2 — Hosted Hypervisor

Runs on top of a host operating system.
The hypervisor behaves like an application inside the host OS.
Ideal for development, testing, and desktop virtualization.

Examples:

VMware Workstation / Player
Oracle VirtualBox
Parallels Desktop (macOS)
QEMU
✅ Pros:
Easy to install and use
Great for personal computers and labs
Uses host OS drivers for hardware compatibility
❌ Cons:
Lower performance (extra layer of host OS)
Weaker security and stability
Host OS failure affects all VMs

### Hypervisor Comparison Table

| **Type**               | **Description**                                                               | **Examples**                           | **Advantages**                                                            | **Disadvantages**                                                    |
| ---------------------- | ----------------------------------------------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Type 0**             | Hardware/Firmware hypervisor, runs below the OS.                              | IBM PR/SM, Oracle LDOMs                | High stability, performance, and security.                                | Vendor-specific, limited flexibility.                                |
| **Type 1**             | Bare-metal hypervisor, runs directly on hardware.                             | VMware ESXi, Microsoft Hyper-V, Xen    | High performance, strong isolation, reliable for servers and cloud.       | Requires dedicated hardware, complex to manage.                      |
| **Type 2**             | Hosted hypervisor, runs on top of a host OS.                                  | VMware Workstation, VirtualBox, QEMU   | Easy to install, great for development and testing, uses host OS drivers. | Lower performance, weaker security, host OS failure affects all VMs. |
| **Paravirtualization** | Modified guest OS to improve performance by removing privileged instructions. | Xen (paravirtualized mode)             | Better performance than full virtualization in certain setups.            | Requires guest OS modification, not true virtualization.             |
| **Exokernel**          | Allocates resources directly to user-level VMs without emulation.             | Research projects, experimental setups | Low overhead, efficient resource allocation.                              | Limited adoption, requires specialized design.                       |
| **Type 1.5**           | Hybrid hypervisor, combines Type 1 and Type 2 features.                       | KVM, Proxmox VE                        | Flexibility of Type 2 with performance of Type 1.                         | May not achieve the same performance as pure Type 1 hypervisors.     |

💡 Quick Facts

🟡 Hypervisors enable virtualization — multiple OSes on one physical system.
🟡 Provide resource isolation, so one VM can’t crash another.
🟡 Common in cloud computing (AWS, Azure, Google Cloud).
🟡 Support live migration — moving a running VM between servers without downtime.
🟡 Virtualization underlies container technologies (like Docker),
though containers are lighter and share the same OS kernel.

**Key Takeaways:**

- Type 0 and Type 1 hypervisors are ideal for enterprise and production environments.
- Type 2 hypervisors are better suited for personal use, development, and testing.
- Paravirtualization and exokernels are niche solutions for specific performance or research needs.
- Type 1.5 hypervisors offer a balance between flexibility and performance.

## Processor Architecture

1️⃣ What is Processor Architecture?

Processor architecture (or CPU architecture) is the design and organization of the central processing unit — how it executes instructions, accesses memory, and interacts with I/O.

It determines:

Instruction set (what instructions the CPU can execute)
Number and types of registers
Memory addressing modes
Control logic and pipelines
Interaction with caches, main memory, and peripherals
In OS terms, it affects how processes run, how memory is accessed, and how fast system calls execute.

2️⃣ Main Components of a Processor

| Component                       | Role                                                                           |
| ------------------------------- | ------------------------------------------------------------------------------ |
| **ALU (Arithmetic Logic Unit)** | Performs arithmetic and logic operations (add, subtract, AND, OR, comparisons) |
| **Registers**                   | Very fast storage inside CPU for immediate data and instructions               |
| **Control Unit (CU)**           | Interprets instructions and directs ALU, memory, and I/O                       |
| **Cache**                       | Small, fast memory to reduce access time to main memory                        |
| **Buses**                       | Paths for data, addresses, and control signals to memory and peripherals       |

3️⃣ Processor Models / Architectures
3.1 Von Neumann Architecture

Single memory for instructions and data
CPU fetches instructions and data from the same bus → can cause Von Neumann bottleneck
Simple, flexible, most general-purpose CPUs historically follow this model
OS implication: sequential instruction execution, caching helps reduce memory contention

3.2 Harvard Architecture

Separate memories for instructions and data
CPU can fetch instructions and data simultaneously → faster execution
Often used in embedded systems, DSPs, and microcontrollers
OS implication: memory management differs; less shared memory contention

3.3 RISC (Reduced Instruction Set Computing)

Small, simple set of instructions
Load/Store architecture: only load/store instructions access memory; arithmetic uses registers
Easier pipelining → faster execution per instruction
OS implication: simpler scheduling, predictable memory access, easier to implement virtual memory efficiently
3.4 CISC (Complex Instruction Set Computing)

Large set of instructions, some complex and multi-step
Instructions may directly access memory
Pros: smaller program size

Cons: slower per instruction, more complex control logic
OS implication: context switching can be slightly more complex; caches need to handle variable-length instructions

4️⃣ CPU Interaction with OS

Processes: CPU executes process instructions in sequence; OS schedules which process runs
Memory: CPU registers and caches interact with RAM; virtual memory managed by OS
I/O: CPU communicates with devices via memory-mapped I/O or device drivers
Interrupts & System Calls: CPU switches between user mode and kernel mode when processes request OS services

5️⃣ Special CPU Features in Modern OS Context

| Feature                     | Purpose in OS                                              |
| --------------------------- | ---------------------------------------------------------- |
| **Multiple cores**          | True parallel execution of processes/threads               |
| **Pipelining**              | Overlap instruction stages to speed up execution           |
| **Superscalar**             | Execute multiple instructions per clock cycle              |
| **Hardware virtualization** | Enables hypervisors / virtual machines                     |
| **Privilege levels**        | Kernel vs. user mode, critical for protection and security |

## kernels

1️⃣ What is a Kernel?

The kernel is the core part of an operating system. It runs in privileged (kernel) mode, controlling hardware and resources.

Main responsibilities of the kernel:
Process management: create, schedule, and terminate processes; manage CPU time.
Memory management: allocate memory, handle virtual memory, and manage address spaces.
Device management: communicate with hardware via device drivers.
File system management: organize files, directories, and access permissions.
System calls interface: provide a controlled way for applications to request OS services.
Security & protection: enforce user privileges and prevent unauthorized access.

2️⃣ Types of Kernels
2.1 Monolithic Kernel

Definition:
The kernel is a single large program that runs entirely in kernel mode. All core OS services are part of the same binary.

Features:
All system services (file system, device drivers, networking, etc.) are inside the kernel.
High efficiency because functions can call each other directly.
Crashes in any part can crash the whole OS.

Pros:
Fast system calls (no inter-process communication overhead).
Simple conceptually — everything is in one place.
Good for performance-critical systems.

Cons:
Hard to maintain or extend.
Poor isolation — bugs in one module can crash the entire system.
Adding new device drivers requires recompiling the whole kernel.

Examples: Linux (traditional), early UNIX, MS-DOS (simpler OS).

2.2 Microkernel

Definition:
The kernel is minimal, handling only the most essential functions: CPU scheduling, memory management, and IPC (inter-process communication). Other services run as user-space servers.

Features:
Device drivers, file systems, network protocols run outside the kernel.
Communication with servers is via message passing.
Kernel is smaller and more modular.

Pros:
More robust and reliable: crashes in user-space servers don’t crash the kernel.
Easier to extend or update services without touching the kernel.
Better security — fewer components running in privileged mode.

Cons:
More overhead for system calls (due to message passing).
Performance can be slower than monolithic kernels if not optimized.

Examples: MINIX, QNX, Mach (basis of macOS XNU kernel), L4 family.

2.3 Hybrid Kernel

Definition:
A compromise between monolithic and microkernel. Core services run in kernel space, but some services (like drivers or file systems) can run in user space or isolated modules.

Features:
Attempts to combine performance of monolithic kernels with modularity of microkernels.
Often uses loadable kernel modules (Linux modules or Windows DLLs).

Pros:
Can extend kernel without rebooting (loadable modules).
Better isolation than purely monolithic kernel.
Performance usually better than microkernels.

Cons:
Still more complex than pure microkernel.
Not as modular or secure as a microkernel.

Examples: Windows NT, macOS XNU, modern Linux with kernel modules.

2.4 Exokernel

Definition:
An experimental minimal kernel that only allocates hardware resources and enforces protection. The OS services (file systems, network stack) run entirely in user space.

Features:
Provides resource protection without abstracting hardware too much.
Each application can implement its own OS abstractions if desired.

Pros:
Minimal overhead, very flexible.
Applications can optimize for their own needs.

Cons:
Very complex for application developers.
Rarely used in mainstream OS.

Examples: MIT Exokernel, Nemesis OS.

3️⃣ Comparison Table

| Feature                  | Monolithic            | Microkernel        | Hybrid                | Exokernel                |
| ------------------------ | --------------------- | ------------------ | --------------------- | ------------------------ |
| Kernel size              | Large                 | Minimal            | Medium                | Minimal                  |
| Services in kernel space | All                   | Only essential     | Core + some           | Only resource management |
| Performance              | High                  | Lower (due to IPC) | Medium-High           | High (minimal overhead)  |
| Reliability              | Low                   | High               | Medium-High           | Medium                   |
| Modularity               | Low                   | High               | Medium                | Very High                |
| Examples                 | Linux (classic), UNIX | MINIX, QNX         | Windows NT, macOS XNU | MIT Exokernel            |

**Key Takeaways:**

Monolithic kernels → all-in-one, fast, less secure.
Microkernels → minimal, modular, secure, slower.
Hybrid kernels → compromise: extendable, reasonably fast, common in modern OS.
Exokernels → extremely minimal, flexible, research-oriented.

## Memory Management

🧠 What Is Memory Management?

Memory management is the process by which an operating system (OS) controls and coordinates computer memory, assigning portions called memory blocks to various running programs (processes) to optimize performance.

The OS ensures:

Each process has enough memory to execute safely.
Processes do not interfere with each other’s memory space.
Memory is used efficiently (no big wasted chunks).
Data is moved between RAM and disk (when physical memory is limited).

⚙️ Core Responsibilities of Memory Management

Tracking memory usage
OS keeps records of which parts of memory are in use, and by which processes.

Allocation and deallocation
When a process starts, the OS allocates memory; when it ends, the OS reclaims it.

Protection and isolation
Each process has its own address space, preventing one process from reading or writing another’s memory.

Virtual memory management
Enables programs larger than physical RAM to run, by using part of the disk as memory (swap space).

Sharing and communication
Sometimes, processes need to share memory for efficiency — the OS allows controlled sharing.

🧩 Types of Memory in a Process

Each process has its own memory address space, usually divided into regions:
| Region | Purpose |
| --------------- | ----------------------------------------------------------------------------- |
| **Text (code)** | The program’s executable instructions. |
| **Data** | Global and static variables. |
| **Heap** | Dynamically allocated memory (e.g., from `malloc()` or `new`). Grows upward. |
| **Stack** | Stores local variables, return addresses, and function calls. Grows downward. |

```bash
+------------------+  <-- High Address
|     Stack        |
| (local vars)     |
+------------------+
|     Heap         |
| (dynamic memory) |
+------------------+
| Initialized Data |
| Uninitialized Data|
+------------------+
| Program Code     |
+------------------+  <-- Low Address
```

📦 Memory Management Techniques
1️⃣ Single Contiguous Allocation

Old/simple systems: only one program in memory at a time.
No protection needed.
Used in early computers.

2️⃣ Partitioned Allocation

Memory divided into fixed or variable partitions.
Each process fits into one partition.
Problem: fragmentation (unused memory holes).

3️⃣ Paging

Physical memory divided into frames (fixed-size chunks).
Logical memory divided into pages.
OS maintains a page table mapping virtual pages → physical frames.

Advantages:
Eliminates external fragmentation.
Allows non-contiguous memory allocation.

Disadvantage:
Slightly slower due to address translation overhead.

4️⃣ Segmentation
Memory divided based on logical segments like code, stack, heap, etc.
Each segment has a variable length.

Advantage: Logical view (easier protection).
Disadvantage: External fragmentation can occur.

5️⃣ Virtual Memory
The illusion of a large, continuous memory even if physical RAM is limited.
Achieved using disk space (swap file / paging file).

How it works:
Parts of a program not currently used are stored on disk.
When needed, OS swaps them into RAM (and possibly moves other parts out).

Benefits:
Run programs larger than physical RAM.
Multitasking more efficient.

Downside:
Slower, since disk access is much slower than RAM.

🧱 Memory Protection
The OS must prevent processes from accessing memory that isn’t theirs.

Mechanisms include:
Base and limit registers → define valid address range.
Page tables → restrict memory access per process.
Privilege levels → kernel vs user mode.
If a process accesses illegal memory → segmentation fault / access violation occurs.

🔁 Swapping
When physical memory is full:
OS can swap out inactive processes (move them to disk).
Swap in when needed again.
This allows multitasking but introduces context-switching and disk latency.

🧩 Shared Memory
Sometimes two or more processes need to share data efficiently.
OS can map a shared region into both processes’ address spaces.
Used for interprocess communication (IPC) — much faster than message passing.

## Processes

🧩 1. What is a Process?

A process is a program in execution — an active entity with its own:
Code (text)
Data (variables)
Stack (function calls)
Registers (CPU state)
Program Counter (next instruction)

The OS manages multiple processes, keeping their info in a Process Control Block (PCB) — storing ID, state, CPU registers, memory info, etc.

⚙️ 2. Process States

A process moves through several states:

```bash
| State               | Meaning                  |
| ------------------- | ------------------------ |
| **New**             | Being created            |
| **Ready**           | Waiting for CPU          |
| **Running**         | Currently executing      |
| **Waiting/Blocked** | Waiting for I/O or event |
| **Terminated**      | Finished execution       |
```

The OS’s scheduler decides which ready process gets CPU next.

🕒 3. CPU Scheduling Overview

The scheduler selects which process runs next when:

CPU becomes idle, a running process finishes or blocks, or a higher-priority process arrives (in preemptive systems).

Types of scheduling:

| Type               | Description                                                           |
| ------------------ | --------------------------------------------------------------------- |
| **Preemptive**     | CPU can be taken away from a process (e.g., Round Robin, SRTF).       |
| **Non-preemptive** | Process keeps CPU until it voluntarily releases it (e.g., FCFS, SJF). |

⚡ 4. Key Scheduling Algorithms
(1) FCFS — First Come, First Served

Non-preemptive.
Processes run in order of arrival.

How to calculate:
Sort by arrival time.

Calculate completion time sequentially.
WT = TAT − BT.
TAT = CT − AT.

✅ Simple but can cause convoy effect (long jobs delay short ones).

(2) SJF — Shortest Job First
Selects the process with the shortest burst time next.

Non-preemptive.
Pros: Minimal average waiting time.
Cons: Requires knowing burst time in advance.

(3) SRTF — Shortest Remaining Time First
Preemptive version of SJF.
If a new process arrives with a shorter remaining time → preempts current one.
Used when: Processes arrive at different times.

(4) RR — Round Robin
Each process gets a fixed time quantum (q).
After q expires, process goes to the end of the ready queue if not done.
Preemptive and fair — used in time-sharing systems.

✅ Formula trick: Shorter quantum → more responsive, more overhead.

(5) Priority Scheduling
CPU assigned to process with highest priority (lowest number often = highest).
Can be preemptive or non-preemptive.
SJF is a special case of this (priority = burst time).
Problem: Starvation → fixed by aging (gradually increasing waiting process priority).

(6) Multilevel Queue Scheduling
Ready queue divided into multiple queues (e.g., system, interactive, batch).
Each has its own scheduling policy.
Processes permanently belong to one queue.

(7) Multilevel Feedback Queue
Processes can move between queues (e.g., from high-priority short jobs to lower priority if they use too much CPU).
Used in real OSes for adaptive scheduling.

📊 5. Quick Formula Cheat Sheet

| Term                      | Formula                               |
| ------------------------- | ------------------------------------- |
| **Turnaround Time (TAT)** | CT − AT                               |
| **Waiting Time (WT)**     | TAT − BT                              |
| **Response Time (RT)**    | First CPU start time − AT             |
| **Throughput**            | # of processes completed / total time |
| **CPU Utilization**       | (Busy time / Total time) × 100%       |

🚀 6. How to Solve Scheduling Problems (Step-by-step)

List all processes (Arrival, Burst, Priority).
Sort by arrival time (for preemptive: track at each time).
Use Gantt chart — draw timeline showing which process runs when.
Note completion time (CT) for each process.
Compute TAT, WT, and average WT/TAT.

🧠 7. Example Quick Practice (RR)

| Process | Arrival | Burst |
| ------- | ------- | ----- |
| P1      | 0       | 5     |
| P2      | 1       | 7     |
| P3      | 3       | 4     |

Quantum = 2
👉 Follow queue in 2-unit chunks.
👉 Rotate ready processes as they arrive.
👉 Continue until all finish.

Resulting order: P1 → P2 → P3 → P1 → P2 → P3 → P2
Compute CT, WT, TAT accordingly.

💡 8. Key Takeaways

SJF/SRTF → minimal waiting time but needs prediction.
RR → fairness, ideal for time-sharing.
FCFS → simple, poor for mixed job sizes.
Priority → flexible but may cause starvation.
Preemptive scheduling → improves responsiveness.

🧩 CPU Scheduling Cheat Table

| **Algorithm**                            | **Preemptive?** | **Best Used For**                                               | **Advantages**                  | **Disadvantages / When Not to Use**                       | **Example Use Case**                                |
| ---------------------------------------- | --------------- | --------------------------------------------------------------- | ------------------------------- | --------------------------------------------------------- | --------------------------------------------------- |
| **FCFS (First Come, First Served)**      | ❌ No           | Batch systems, simple queues                                    | Very easy to implement          | Long jobs block short ones (**convoy effect**)            | Printing queue, simple servers                      |
| **SJF (Shortest Job First)**             | ❌ No           | Predictable CPU burst workloads                                 | Lowest average waiting time     | Needs prior knowledge of burst time; unfair to long jobs  | Batch systems with known job lengths                |
| **SRTF (Shortest Remaining Time First)** | ✅ Yes          | Mixed short/long jobs arriving at different times               | Minimizes average waiting time  | High overhead; starvation for long jobs                   | Real-time systems needing responsiveness            |
| **Priority Scheduling**                  | ✅ or ❌        | Systems with critical tasks                                     | Allows prioritization           | Starvation of low-priority jobs (fixed by **aging**)      | Real-time OS, print queues                          |
| **Round Robin (RR)**                     | ✅ Yes          | Time-sharing systems                                            | Fair, responsive to all users   | High overhead if quantum is too small; poor for long jobs | General-purpose OS (Windows, Linux user scheduling) |
| **Multilevel Queue**                     | ✅ Yes          | Systems with distinct process types (e.g., system vs user jobs) | Organized, simple               | No movement between queues; rigid                         | Desktop OS combining interactive & batch            |
| **Multilevel Feedback Queue (MLFQ)**     | ✅ Yes          | Adaptive systems, mixed workloads                               | Very flexible, fair, responsive | Complex to tune; hard to predict behavior                 | Windows, Linux, macOS kernels                       |
| **Lottery Scheduling**                   | ✅ Yes          | Experimental or research OS                                     | Randomized fairness             | Unpredictable results; not deterministic                  | Simulations, testing environments                   |

⚙️ Key Concepts You Must Remember

| Concept                   | Explanation                              |
| ------------------------- | ---------------------------------------- |
| **Arrival Time (AT)**     | When a process enters the ready queue    |
| **Burst Time (BT)**       | Total CPU time process needs             |
| **Completion Time (CT)**  | Time when process finishes execution     |
| **Turnaround Time (TAT)** | CT − AT                                  |
| **Waiting Time (WT)**     | TAT − BT                                 |
| **Response Time (RT)**    | Time from arrival to first CPU execution |
| **Throughput**            | # of processes completed / total time    |
| **CPU Utilization**       | % of time CPU is busy                    |

🧠 How to Choose Algorithm

| **Keyword in question**                          | **Likely algorithm**          |
| ------------------------------------------------ | ----------------------------- |
| “Interactive system,” “time-sharing,” “fairness” | **Round Robin**               |
| “Shortest job,” “minimize waiting time”          | **SJF / SRTF**                |
| “Priorities,” “critical tasks”                   | **Priority Scheduling**       |
| “Adaptive,” “mix of processes”                   | **MLFQ**                      |
| “Simple,” “batch jobs”                           | **FCFS**                      |
| “Processes can move between queues”              | **Multilevel Feedback Queue** |

🧮 Formula Summary (always recall)

```bash
Turnaround Time (TAT) = Completion Time - Arrival Time
Waiting Time (WT) = Turnaround Time - Burst Time
Response Time (RT) = First CPU start - Arrival Time
```

🧩 Worked examples (Gantt charts + calculations)

Given processes
| Process | Arrival (ms) | Burst (ms) |
| ------- | ------------ | ---------- |
| P0 | 0 | 9 |
| P1 | 1 | 4 |
| P2 | 2 | 9 |

We’ll compute Completion Time (CT), Turnaround Time (TAT = CT − AT), Waiting Time (WT = TAT − BT) and the average waiting time for each scheduling policy.

1. FCFS (First Come, First Served)
   Rule: Non-preemptive, run in arrival order.
   Order: P0 → P1 → P2
   Gantt chart (time ranges):

```bash
P0: 0 — 9
P1: 9 — 13
P2: 13 — 22
```

Completion times:
CT(P0) = 9
CT(P1) = 13
CT(P2) = 22

Turnaround times (TAT = CT − AT):
TAT(P0) = 9 − 0 = 9
TAT(P1) = 13 − 1 = 12
TAT(P2) = 22 − 2 = 20

Waiting times (WT = TAT − BT):
WT(P0) = 9 − 9 = 0
WT(P1) = 12 − 4 = 8
WT(P2) = 20 − 9 = 11
Average waiting time = (0 + 8 + 11) / 3 = 19/3 = 6.333… ms

2. RR with quantum = 2 (Round Robin, q = 2)

Rule: Preemptive; each ready process gets up to 2 ms, then goes to the back of the ready queue if not finished. New arrivals are appended as they occur.

Simulate step-by-step and keep ready queue order in mind.
Timeline (quantum slices):

```bash
t=0–2   : P0 (rem 9→7)
t=2–4   : P1 (rem 4→2)
t=4–6   : P0 (rem 7→5)
t=6–8   : P2 (rem 9→7)
t=8–10  : P1 (rem 2→0)  --> P1 completes at t=10
t=10–12 : P0 (rem 5→3)
t=12–14 : P2 (rem 7→5)
t=14–16 : P0 (rem 3→1)
t=16–18 : P2 (rem 5→3)
t=18–19 : P0 (rem 1→0)  --> P0 completes at t=19
t=19–21 : P2 (rem 3→1)
t=21–22 : P2 (rem 1→0)  --> P2 completes at t=22
```

Completion times:
CT(P1) = 10
CT(P0) = 19
CT(P2) = 22

Turnaround (CT − AT):
TAT(P0) = 19 − 0 = 19
TAT(P1) = 10 − 1 = 9
TAT(P2) = 22 − 2 = 20

Waiting times (TAT − BT):
WT(P0) = 19 − 9 = 10
WT(P1) = 9 − 4 = 5
WT(P2) = 20 − 9 = 11

Average waiting time = (10 + 5 + 11) / 3 = 26/3 = 8.666… ms

3. SRTF (Shortest Remaining Time First) — preemptive SJF

Rule: Always run the ready process with the smallest remaining CPU time; preempt when a newly arrived process has smaller remaining time.

Simulate:
t=0–1: P0 runs (rem 9→8)
t=1: P1 arrives (burst 4) — P1 has remaining 4 < P0's 8 → preempt P0
t=1–5: P1 runs to completion (4 ms) → CT(P1) = 5
t=5: ready: P0 (rem 8) and P2 (arrived at t=2, rem 9). Shortest is P0.
t=5–13: P0 runs remaining 8 → CT(P0) = 13
t=13–22: P2 runs remaining 9 → CT(P2) = 22

Completion times:
CT(P1) = 5
CT(P0) = 13
CT(P2) = 22

Turnaround (CT − AT):
TAT(P0) = 13 − 0 = 13
TAT(P1) = 5 − 1 = 4
TAT(P2) = 22 − 2 = 20

Waiting times (TAT − BT):
WT(P0) = 13 − 9 = 4
WT(P1) = 4 − 4 = 0
WT(P2) = 20 − 9 = 11

Average waiting time = (4 + 0 + 11) / 3 = 15/3 = 5 ms

```bash
| Algorithm |     Avg Waiting Time |
| --------- | -------------------: |
| FCFS      |            6.333… ms |
| RR (q=2)  |            8.666… ms |
| SRTF      | **5 ms** (best here) |
```

Observations:

SRTF minimized average waiting time (as expected for SJF family).
RR increased average waiting time here because the quantum caused many context switches and interruptions for the long P0 and P2. RR improves responsiveness but can increase average wait for longer jobs, depending on arrival mix and quantum.
FCFS is simple but suffers from the convoy effect (long P0 delays others that arrive later).
How to apply these quickly in exam problems (cheat tips)

FCFS: sort by arrival, run sequentially — easy CT accumulation.
SJF (non-preemptive): when CPU free, pick shortest burst among ready; no preemption.

SRTF (preemptive): at each arrival or completion, compare remaining times and possibly preempt. Useful trick: track remaining times and only re-evaluate at arrival/completion instants.

RR (quantum q): simulate in q-sized slices; maintain a FIFO ready queue; append new arrivals when they arrive (if at same instant quantum ends, make a consistent rule — arrivals at t are enqueued before choosing next).

Compute times: build Gantt chart, note CT for each process, then TAT = CT − AT, WT = TAT − BT.

Heuristics: shortest jobs tend to finish earlier under SJF/SRTF; RR favors fairness and responsiveness (short quantum ≈ more fair but more overhead).

## Concurrency, Parallelism, Threads & Interrupts

🧠 1. Concurrency

Meaning:
Multiple tasks making progress during the same time period.

Key idea: Tasks overlap in time — even if only one runs at a time (on a single CPU).

The OS switches between tasks so fast (via context switching) that it appears they run together.
Common in multitasking systems — e.g., typing in one window while downloading in another.

Example:
On a single-core CPU, when the OS rapidly switches between processes P1 and P2 — both seem to run “concurrently”.

Goal: Maximize CPU utilization and responsiveness.

⚙️ 2. Parallelism

Meaning:
Multiple tasks executing literally at the same time.
Requires multiple CPU cores or processors.
True simultaneous execution (not just switching).
Often used for computation-heavy or real-time systems.

Example:
On a quad-core CPU:
Core 1 runs P1,
Core 2 runs P2,
Core 3 runs P3,
Core 4 runs P4 — all in parallel.

Goal: Improve speed and throughput.

🔍 Concurrency vs Parallelism
| Concept | Execution | Requires Multiple Cores? | Example |
| --------------- | ------------------------------------- | ------------------------ | --------------------------------------- |
| **Concurrency** | Tasks **appear** to run at once | ❌ No | One core switches between tasks |
| **Parallelism** | Tasks **actually** run simultaneously | ✅ Yes | Multiple cores executing tasks together |

➡️ You can have concurrency without parallelism (on one CPU).
➡️ All parallel systems are concurrent, but not all concurrent systems are parallel.

🧵 3. Threads

Meaning:
A lightweight execution unit within a process.
Each process can contain one or more threads, sharing the same memory and resources (code, data, open files).
Each thread has its own stack, program counter, and registers.
Threads run concurrently (or in parallel on multi-core CPUs).

Example:
A web browser:
One thread for user interface,
One for network download,
One for rendering pages,
One for running JavaScript.

Advantages:
Faster context switching (compared to processes).
Easier inter-thread communication (shared memory).
More responsive applications.

Disadvantages:
Shared memory → risk of data corruption → need synchronization (mutex, semaphores, etc.).

Types:
User threads: Managed by user-level libraries.
Kernel threads: Managed by the operating system.

Multithreading models:
Many-to-One,
One-to-One,
Many-to-Many.

⚡ 4. Interrupts

Meaning:
A signal to the CPU indicating an event that needs immediate attention.
Interrupts pause the current process so the OS can handle an event.
After handling, the CPU resumes where it left off.

Types of Interrupts:

Type Trigger Example

| Type                   | Trigger                   | Example                           |
| ---------------------- | ------------------------- | --------------------------------- |
| **Hardware interrupt** | From external devices     | Keyboard press, disk I/O complete |
| **Software interrupt** | From software/system call | Trap instruction, divide by zero  |
| **Timer interrupt**    | From system clock         | Used for preemptive multitasking  |

Steps in interrupt handling:
CPU saves the current state (program counter, registers).
Jumps to the interrupt service routine (ISR).
Executes ISR to handle the event.
Restores state and resumes the interrupted task.

Importance in OS:
Enables asynchronous events (I/O completion, user input).
Used for preemptive scheduling — CPU timer interrupt forces context switch.

🧩 Summary:

| Concept         | Description                                  | Key Feature           | Example                            |
| --------------- | -------------------------------------------- | --------------------- | ---------------------------------- |
| **Concurrency** | Multiple tasks _making progress_ together    | Task switching        | Web browser handling multiple tabs |
| **Parallelism** | Tasks _running simultaneously_               | Multi-core execution  | Video rendering on 8 cores         |
| **Threads**     | Lightweight execution units inside a process | Share memory          | Word processor: typing + autosave  |
| **Interrupts**  | Signals that pause CPU to handle events      | Asynchronous handling | Keyboard press, I/O completion     |

## File systems & partitioning

💾 1. What Is a File System?

A file system (FS) is the method an Operating System uses to:
Store,
Organize,
Retrieve,

And manage data on storage devices (like HDDs, SSDs, USB drives, etc.).
Without a file system, your data would just be a raw block of bytes — no folders, no filenames, no structure.

🗂️ What a File System Does

File organization — groups data into files (documents, programs, media, etc.).
Directory management — organizes files into folders (directories) for hierarchy.

Metadata storage — keeps info like:
File name,
Size,
Ownership,
Permissions,
Modification time.

Space allocation — decides where each file’s data is placed on disk blocks.
Access control — enforces file permissions and user access rules.
I/O operations — provides system calls like <code>open()</code>, <code>read()</code>, <code>write()</code>, <code>close()</code>.

⚙️ Common File Systems

| OS                             | Common File Systems          | Notes                                             |
| ------------------------------ | ---------------------------- | ------------------------------------------------- |
| **Windows**                    | FAT32, NTFS, exFAT           | NTFS supports permissions, encryption, journaling |
| **Linux / UNIX**               | ext2, ext3, ext4, XFS, Btrfs | ext4 is most common on Linux systems              |
| **macOS**                      | HFS+, APFS                   | APFS optimized for SSDs and encryption            |
| **Cross-platform / Removable** | FAT32, exFAT                 | Works on many OSes, used in USB drives            |

🧱 2. What Is a Partition?

A partition is a logical division of a physical disk.
Think of it as splitting a hard drive into independent “sections,” each of which can have its own file system.

Example:

```bash
Physical Disk (500 GB)
 ├── Partition 1 (C:) → Windows NTFS
 ├── Partition 2 (D:) → Data (NTFS)
 └── Partition 3 (E:) → Linux ext4
```

Each partition behaves like a separate disk to the operating system.

🧩 Why Use Partitions?

Multi-boot systems: Install multiple OSes (Windows + Linux).
Data separation: Keep OS files and user data separate.
Backup & recovery: Reinstall OS without deleting data.
Security: Isolate sensitive data on a separate partition.
Performance: Some file systems are better for specific workloads.

🧭 Partition Table Types

| Type                           | Used by             | Notes                                             |
| ------------------------------ | ------------------- | ------------------------------------------------- |
| **MBR (Master Boot Record)**   | Older BIOS systems  | Supports up to 4 primary partitions, disks ≤ 2 TB |
| **GPT (GUID Partition Table)** | Modern UEFI systems | Supports 128+ partitions, disks > 2 TB            |

📁 3. Relationship Between Partitions and File Systems

Each partition must be formatted with a file system before it can store files.

Example:

```bash
SSD (512 GB)
 ├── Partition 1 → 100 GB → NTFS (Windows)
 ├── Partition 2 → 100 GB → ext4 (Linux)
 └── Partition 3 → 312 GB → exFAT (Shared data)
```

The OS can mount each partition into its directory tree.

🔗 Mounting (especially in UNIX/Linux)

“Mounting” means attaching a file system to a directory.

Example:
Before mounting: /mnt/data is empty.
After mounting: /mnt/data shows files from another partition or disk.
You can mount USB drives, CD-ROMs, or network shares this way.

🧠 4. File System Structure (Internal Overview)

Most file systems have 4 key parts:

| Component       | Purpose                                                               |
| --------------- | --------------------------------------------------------------------- |
| **Boot block**  | Contains startup info (used for booting OS).                          |
| **Superblock**  | Holds metadata — file system size, type, free blocks, etc.            |
| **Inode table** | Stores file attributes (owner, permissions, pointers to data blocks). |
| **Data blocks** | Contain actual file contents.                                         |

🧾 Example (UNIX-style File System)

```bash
/ (root)
 ├── /bin     → Essential commands
 ├── /home    → User files
 ├── /etc     → System config
 ├── /var     → Logs, caches
 └── /dev     → Device files
```

Each directory is just a special file listing other files.

⚖️ 5. Pros and Cons

| Concept                                    | Advantages                                                        | Disadvantages                                   |
| ------------------------------------------ | ----------------------------------------------------------------- | ----------------------------------------------- |
| **Multiple Partitions**                    | Easier backup, better organization, can dual-boot                 | Limited flexibility (space fixed per partition) |
| **Modern File Systems (e.g., NTFS, ext4)** | Support permissions, journaling (protects data), large file sizes | More complex management                         |
| **Simple File Systems (e.g., FAT32)**      | Simple, portable, compatible with many OSes                       | Lacks security & journaling                     |

🔐 6. File Permissions & Security (Quick Recap)

Each file has access rights (Read, Write, Execute).

In UNIX:

rwxr-x--x → Owner: read/write/execute; Group: read/execute; Others: execute only.
Managed by file system metadata.

🧭 In Short
| Term | Meaning |
| --------------- | -------------------------------------------------------- |
| **Partition** | Logical division of a physical disk. |
| **File system** | Data structure and rules for managing files. |
| **Formatting** | Prepares a partition with a specific file system. |
| **Mounting** | Attaching a file system to the OS’s directory tree. |
| **Metadata** | Information about files (size, permissions, timestamps). |
