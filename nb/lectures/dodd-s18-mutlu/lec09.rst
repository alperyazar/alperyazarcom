.. _lec_dood_s18_lec09_page:

Lecture 09 - Von Neumann Model, ISA, LC-3 and MIPS
==================================================

.. warning ::

    Stopped at 28:10, beginning of LC-3.

Info
----

* `Video Link <https://www.youtube.com/watch?v=AAPwKjm_CpA>`__
* `Lecture Slides <https://safari.ethz.ch/digitaltechnik/spring2018/lib/exe/fetch.php?media=digitaldesign-2018-lc-3andmips-afterlecture.pdf>`__

Reading
-------

* Chapter 4, 5, Appendicies A and C (ISA and microarchitecture of LC-3) in [patt2005introduction]_
* Chapter 5, 6, Appendix B (MIPS instructions) in [harris2012digital]_
* [von1946preliminary]_

Reading Notes
^^^^^^^^^^^^^

Lecture Minutes
---------------

* **04:50** Combinational and sequential circuits are assumed to be learned. We can build
  decision elements and storage elements by using them. They are basic elements of a computer.
  Computer needs data and program which is set of instructions. :term:`instruction` is defined.
* **06:20** We need a model to build a computer. A fundamental model in 1946 was proposed by
  Jonn von Neumann. He proposed a model in [von1946preliminary]_. The model consists of 5
  parts: **Memory**, **Processing Unit**, **Input**, **Output** and **Control Unit**
* **08:00** Two architecture will be covered: **LC-3**, **MIPS**
* **08:15** The von Neumann model:

    .. figure:: images/l09-von_neumann_model.png
        :align: center

        *Taken directly from the lecture notes. © belongs to Prof. Mutlu*

* **09:00** Solid lines move data, they are data lines. Dash lines are control lines.
* **10:00** Memory stores data and programs (both). Memory contains bits. Bits are grouped
  into bytes (8 bits) and words (8, 16, 32 bits). Size of word is defined for particular
  architecture. How bits are accessed determines the **addressability**. For example
  word-addressable or byte-addressable (8-bit addressable). Total number of addresses is
  the **address space**. For example 2^16 address space requires 16-bit address.
* **12:30** In word-addressable memory, each data word has a unique address. Similarly in
  byte-addressable memory each byte has a unique address.
* **15:10** :term:`endianness` is defined.
* **16:30** Is it really important? No, it is a convention. As far as we don't exchange data
  between two system, we will be safe.
* **17:30** There are two ways of accessing memory. For reading or loading and for writing
  and storing. Two registers are defined: **MAR** (Memory Address Register) and
  **MBR** (Memory Data Register). For reading 1) load MAR with the address. 2) Memory will
  place data in MDR. For reading 1) load MAR with address and MDR with data 2) Activate
  write enable signal.
* **19:15** Processing unit has many **functional units**. Let's start with :term:`ALU`.
  Example instructions: ADD, AND, NOT, sub, mult, nor, sll, slr, slt. There are also
  **registers**. For every operation no need to access memory. A register typically holds
  one word. See :term:`register` and :term:`register set`. Each register may have specific
  usage for a processır.
* **25:10** Input and put are called peripherals like keyboard, monitor, etc.
* **25:45** Control unit is the conductor of the orchestra. Currently executed instruction
  is stored in **instruction register (IR)**. Another register is needed to keep the address
  of the next instruction execute called **program counter (PC)** or **instruction pointer (IP)**.
* **27:20** Programmer sees memory, registers (may include IR) and program counter. Values can
  be modified using instructions.

Glossary
--------

.. glossary::

    ALU

        Arithmetic and Logic Unit

    big endian

        Address of MSB (most significant byte) is smaller than
        address of LSB (least significant byte). For example
        MSB is at byte address 0, LSB is at byte address 3.
        Check :term:`little endian` and :term:`endianness`

    endianness

        Let's say that our word length is 32 bit and memory is byte addressable.
        In each word, there are 4 separately accessible byte locations. Which one
        has address 0 and which one has address 3?
        We prefer ordered sequence either 0-1-2-3 or 3-2-1-0.
        Check :term:`little endian` and :term:`big endian`.
        The term comes from Jonathan Swift's
        Gulliver's Travels book. A story about broking eggs. Here is a picture:

            .. figure:: images/l09-endianness_egg.png
                :align: center

                *Taken directly from the lecture notes. © belongs to Prof. Mutlu*

        Here is the summary:

            .. figure:: images/l09-big_little_endian.png
                :align: center

                *Taken directly from the lecture notes. © belongs to Prof. Mutlu*

    instruction

        The smallest piece of work in a computer.


    little endian

        Address of MSB (most significant byte) is greater than
        address of LSB (least significant byte). For example
        MSB is at byte address 3, LSB is at byte address 0.
        Check :term:`big endian` and :term:`endianness`

    register

        Fast and generally word sized memory in processing unit

    register set

        Also known as register set is collection of register. For example,
        LC-3 has 8 general purpose registers (GPR). MIPS has 32 registers.

    word
    
        The :term:`ALU` processes quantities that are referred as words

    word length

        Length of a :term`word`. MIPS is 32 bits for example.

.. index::
    addressability
    address space
