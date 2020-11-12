---
layout: post
title:  "LightBeam project : Introduction to Kernel Development"
author: lkaroubi
categories: [ experience ]
image: assets/images/lightbeam/affiche.jpg
published: true
---

[LightBeam](https://github.com/epitech-lyon/LightBeam) is a set of 4 kernels bootstrap on several platforms.

## Description

If you want an OSdev introduction, [here is the bible](https://wiki.osdev.org/Expanded_Main_Page).

I will not give explanation on the kernel architecture and development, the subject is too large.

As a small definition, a kernel is an interface between the human and the computer. It is the core of an Operating System and is composed principally of a bootstrap which allows the machine to boot and many components --- which work together --- to maintain the machine alive.

So, the job in the OSdev is to make a bootstrap, the components 'drivers' (memory, threads, interrupts, ...) and a scheduler. Easy isn't it ?

The OSdev is a wide and complex world with a deep beauty if you dig... long... with a diamond shovel.

### What ?

As said LightBeam is a project which contain 4 micro-kernel.


|-------------------+-----------------------+---------------------------------------|
|  Architecture     |        Machine        |   Description / Source link           |
|:------------------|:----------------------|--------------------------------------:|
|<small>aarch64[^1]</small>    |  <small>raspi3[^2]</small>  | <small>[the famous raspberry 3][1]</small>           |
|-------------------+-----------------------+---------------------------------------|
|<small>rv64[^3]</small>   |  <small>sifive</small>               | <small>[embedded machine using RISC-V ISA][2]</small>|
|-------------------+-----------------------+---------------------------------------|
|<small>x86</small>                |  <small>x86-pc</small>               | <small>[classical x86 pc bootstrap][3]</small>       |
|-------------------+-----------------------+---------------------------------------|
|<small>x86_64</small>             |  <small>x86_64-pc</small>            | <small>[classical x86_64 pc bootstrap][4]</small>    |
|-------------------+-----------------------+---------------------------------------|
{: rules="groups"}

[^1]: ARM64
[^2]: raspberry3
[^3]: risc-v 64

### How ?

The OS development require a big acquaintance obtained by reading a lot of documentation. Yes, that's not sexy so far.

The compilation is assured our servitors GCC, GAS (bad choice, a compilation with GCC only would have been better) and made with a "coherent" (actually not incredible) project architecture.

## Technical side

The following description are actually simplified --- if you want to go further visit the [repository page](https://github.com/epitech-lyon/LightBeam).

### Raspi3

The LightBeam raspi3 kernel is SMP (Symetric MultiProcessing) and in graphic mode (no text mode).

As an interface for raspberry machines, I have built a (partial) driver for the bcm2837 (scalable and usable for others bcm version.

The bcmXXXX [SoC](https://en.wikipedia.org/wiki/System_on_a_chip) are the core of the raspberryX.
On top of that for the raspi3 I juste created some functions that I needed which use this driver.

Abstract steps:
  * SMP init, cpu config, escape from the chaos
  * Interrupt handling
  * Broadcom driver
  * UART driver
  * Framebuffer driver
  * ARM timer
  * CPUS routines

The memory is unfortunately not handled here.

Sample of the raspi3 boot code. Here we are applying some configurations on all the cpu cores.

```asm
_init_cpus:
    mrs x0, midr_el1
    mrs x1, mpidr_el1
    msr vpidr_el2, x0
    msr vmpidr_el2, x1

/* Disable coprocessor traps for all Cores */
    mov x0, #0x33ff
    msr cptr_el2, x0
    msr hstr_el2, xzr
    mov x0, #3 << 20
    msr cpacr_el1, x0

/* Enable CNTP for EL1 */
    mrs x0, cnthctl_el2
    orr x0, x0, #0x3
    msr cnthctl_el2, x0
    msr cntvoff_el2, xzr
/* the for el0 (util?) */
    mrs x0, cntkctl_el1
    orr x0, x0, #0x3
    msr cntkctl_el1, x0

/*  Initialize HCR_EL2 so EL1 is 64 bits for all Cores */
    mrs x0, hcr_el2
    orr x0, x0, #(1 << 31)  /* Set el1 to 64bit */
    orr x0, x0, #(1 << 1)   /* Hardwired swio */
    msr hcr_el2, x0

/* Enable instruction cache */
    mrs x0, sctlr_el1
    orr x0, x0, #(1 << 12)
    msr sctlr_el1, x0

```

Runtime screenshot of the kernel (run with *qemu*)

![runtime](https://raw.githubusercontent.com/le0kar0ub1/LightBeam/master/doc/screenshot-raspi3.png)

Documentation: [ARM documentation](https://developer.arm.com/documentation/ddi0487/aa) and [Broadcom documentation](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2836/QA7_rev3.4.pdf).

Oh! A last personal advice, for your mental health, don't work with Broadcom. (what ? It was not in your plans ?)

### Sifive

Sifive is a litte embedded machine with a RISC-V 64 cpu architecture.

LightBeam sifive kernel is SMP.

Abstract steps:
  * SMP init, cpu config, escape from the chaos
  * Weak interrupt handling
  * UART driver
  * CPUS routines

Sample of the sifive boot code. This is a dichotomy between cpu cores. The core 0 boot others which are waiting for his signal. Then, if the core acquire that he is running, we can configure him.

```asm
 # cpu get id and dichotomy
    csrr a0, mhartid
    li a3, 0
    bgt a0, a3, coreXBoot
    j core0boot

    coreXBoot:
        # Set MSIE bit to receive IPI
        li a2, MIP_MSIP
        csrw mie, a2
        .coreXwait:
            wfi
            # Only start if MIP_MSIP is set
            csrr a2, mip
            andi a2, a2, MIP_MSIP
            beqz a2, .coreXwait

            li s1, 0x02000000 # CLINT addr
            csrr s2, mhartid
            slli s2, s2, 2
            add s2, s2, s1
            sw zero, 0(s2)
            fence
            csrw mip, 0
            li a2, 5
            bltu a0, a2, coreXtriggered
            j .coreXwait

coreXtriggered:
    # stack setup
    csrr a0, mhartid
    addi a0, a0, 1
    la a1, __STACK_SIZE
    mul a0, a0, a1
    la sp, __stackcore__
    add sp, sp, a0
    j xinit
```

Documentation: [RISC-V specification](https://riscv.org/technical/specifications/) and [Sifive specification](https://sifive.cdn.prismic.io/sifive%2Fcab05224-2df1-4af8-adee-8d9cba3378cd_tilelink-spec-1.8.0.pdf).

### x86_64-pc

Back to basics, x86 architecture.

abstract steps:
  * CPU config
  * interrupt handling
  * VGA driver (text mode)
  * Virtual memory handling

Sample of the x86_64 boot code. This is the entry point of the kernel. We are doing some sanity checks, setting up a temporary pagination (Virtual Memory) and then jump in the kernel main initialization.

```assembly
_start:
    cli
    cld
    LV2P $stack_top, %esp

    pushl %ebx # phys multiboot structure

    call sanity_multiboot
    call cpuid_detect
    call lm_ckeckup

    call setup_paging

    LV2P $gdtptr_phys, %eax
    lgdt (%eax)

    popl %ebx
    ljmp $KERNEL_CODE_SELECTOR, $(lmworld - __KERNEL_ADDR_TRNS)

    hlt

```

Documentation: [IA-32 manual](https://software.intel.com/content/www/us/en/develop/articles/intel-sdm.html).

### Improve ?

The goal was to discover several architectures, not to build a big and efficient kernel. The job was in part to create a maximum of shared code cross-architecture, unfortunately it hasn't been a success.

I lost control of my code for several reasons, the main one is that while in learning phase I have modified the structure of the project to improve the coherence.

A non-exhaustive list of improvements:
  * Best project architecture
  * Handle more platforms
  * Bigger kernel for each platforms
  * and so on...

## What's next

After a little trip in the OS development, my goal is to create a x86_64 kernel more or less (but not the most) big which goes up to TTY interface.

Here is the link of [Cosmos](https://github.com/Epitech-Lyon/Cosmos) kernel with a road map and the source code.

[1]: https://github.com/le0kar0ub1/LightBeam/tree/master/src/target/aarch64/raspi/raspi3
[2]: https://github.com/le0kar0ub1/LightBeam/tree/master/src/target/riscv/riscv64/sifive
[3]: https://github.com/le0kar0ub1/LightBeam/tree/master/src/target/x86/i386
[4]: https://github.com/le0kar0ub1/LightBeam/tree/master/src/target/x86/x86_64