:orphan:

.. _page_projects_isoUSBRS422:

isoUSBRS422
===========

.. note::
    isoUSBRS422v1 is on **EEVblog Mailbag** and **Dangerous Prototypes**. See `On The Web`_ section at the bottom for details. 

.. figure:: /images/projects/isousbrs422/isousbrs422_cs_coated_v1_150_150.jpg
   :align: center

isoUSBRS422 is an open source isolated USB↔RS-422/RS-485 converter board. This page is dedicated to give some information about the project and the board itself. Also necessary production steps for makers are given. This page is for version 1 (v1) board. 

.. list-table:: Links

   * - **This Page (Permalink)**
     - http://www.alperyazar.com/r/isoUSBRS422v1
   * - **Files (GitHub)**
     - http://www.alperyazar.com/r/isoUSBRS422GITv1
   * - **Known Issues**
     - http://www.alperyazar.com/r/isoUSBRS422ISSUESv1
   * - **Up-to-date BOM (with price)**
     - http://www.alperyazar.com/r/isoUSBRS422BOMv1
   * - **Hackaday.io**
     - http://www.alperyazar.com/r/isoUSBRS422SKULLv1
   * - **Gallery**
     - http://www.alperyazar.com/r/isoUSBRS422GALLERYv1
   * - **Video Tutorials**
     - http://www.alperyazar.com/r/isoUSBRS422VIDEOTUTv1

Features
--------

Here is the summary of features in "catalog" style:

.. figure:: /images/projects/isousbrs422/features_full.png
   :alt: Summary of Features of isoUSBRS422
   :align: center
   :width: 100 %

   Summary of Features of isoUSBRS422. Click on the image for larger size

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/jb3v3Kmv85k" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

* **Isolated** 5000 Vrms (IC specification, not tested by me)
* **4 different modes** RS-422, RS-485 4-wire, RS-485 2-wire, RS-485 2-wire w/echo suppression
* **5 cm x 5 cm, 2-layers PCB**
* **4 x 2.7 mm diameter mounting holes** Electrically floating
* **Baud Rate: 300 bps - 3 Mbps**
  Baud Rate = 3000000 / (n + x)
  where 'n' can be any integer between 2 and 16,384 and 'x' can be a sub-integer of the value 0, 0.125, 0.25, 0.375, 0.5, 0.625, 0.75, or 0.875. When n = 1, x = 0, i.e. baud rate divisors with values between 1 and 2 are not possible.
* **Powered from USB port** No external power supply is required. 5V from USB port is sufficient to operate the device.
* **USB overcurrent protection** Yes, by a polyfuse
* **RS-422/RS-485 line protection** Yes, it should meet IEC 61000-4-2, 61000-4-4 and IEC 61000-4-5 (IC specification, not tested by me)
* **Supported OS: Windows, Linux, MacOSX**
* **Various termination options** Different termination topologies can be selected by changing some passives on the component side using solder and iron! (Sorry, no dip switches)
* **Screw terminals for RS-422/RS-485 side**
* **LED indicators: Power, Transmit, Receive**

What is isoUSBRS422?
--------------------

As I said, basically it is an USB ↔ RS-422/RS-485 converter board. It can be used to communicate devices with RS-422/RS-485 interface by using a USB port of PC. Also, ground of USB port is isolated from ground of RS-422/RS-485 channel. It may help you to prevent `ground loops <https://en.wikipedia.org/wiki/Ground_loop_%28electricity%29>`__ in large systems. If you are not sure whether you need isolation or not, probably you do not need it. See `Galvanic isolation <https://en.wikipedia.org/wiki/Galvanic_isolation>`__ for further explanation. I will explain technical details later.

isoUSBRs422 is my first open source hardware and also KiCad experience. I did some boards for my daily job  previously, but I never published them in public domain. So, I decided to do "something" to gain experience about open source publishing and low cost PCB production. Here there are some photos:

.. figure:: /images/projects/isousbrs422/gallery/1.jpg
   :align: center

.. figure:: /images/projects/isousbrs422/gallery/2.jpg
   :align: center

.. figure:: /images/projects/isousbrs422/gallery/3.jpg
   :align: center

.. figure:: /images/projects/isousbrs422/gallery/4.jpg
   :align: center

.. figure:: /images/projects/isousbrs422/gallery/5.jpg
   :align: center

Why?
----

**Why did I design an isolated USB ↔ RS-422/RS-485 converter board?**

As I explained previously, I wanted to design and publish "something". I use USB ↔ RS-422 converter devices for my daily job heavily. I checked PCB manufacturers and decided to try Dirtypcbs. Dimension limit for the cheapest option is 5 cm x 5 cm and I decided to stick to this limit. I thought that I can design an isolated USB <-> RS-422 converter board within in this size limit and use it for my daily job. So I did it.

**Why did I chose the name isoUSBRS422? Does this board support RS-485 in addition to RS-422, right?**

Yes, it supports both protocols. My initial goal was designing an isolated USB ↔ RS-422 converter board. Because I use RS-422 mainly not RS-485. However after design I noticed that it can also be used as an RS-485 converter. Also a name like *isoUSBRS422-485* is quite long for a board name.

**Why did I use KiCad?**

Couple of years ago, I designed 3 different boards for my project design course in collage using DipTrace. DipTrace is great and I would continue to use it if I didn't decide to publish my project and make it open source. DipTrace has *freeware* version for non-commercial users. However, this version has limitation on number of total pins on a single PCB. I think that software used for an open source project should be free (as in beer and freedom) as much as possible. Also, I had to create some parts in library for this project. If I use DipTrace, later I may hit the pin limit for my other projects and I have to move another software. For these reasons, I eliminate Eagle. I think that, it is easier to learn and use DipTrace than Eagle.

As *free* PCB design softwares, I tried gEDA and KiCad. I encountered some stability issues in gEDA then I selected to use KiCad. This is my first KiCad and experience and now I am happy with my decision. I recommend KiCad. It has quite good documentation and there are great videos on YouTube explaining almost all aspects of the software. Also there are active helping forums on the internet.

**Why the heck did I select a USB chip from FTDI? Don't I know that they did stupid things in the past? Am I supporting them?**

Yes, I know and I am not an FTDI fanboy. For those who don't know the subject:

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/eU66as4Bbds" frameborder="0" allowfullscreen></iframe></center>

And http://hackaday.com/2014/10/22/watch-that-windows-update-ftdi-drivers-are-killing-fake-chips/

I started to desing and selected to components prior to FTDI thing. I learned the issue in the beginning of the layout. I was very excited to finish my board and decided to finish it. So, that's the story. Now, I can't proudly say that "Hey, I am using an FTDI chip on my board". I know that, many of hackers and makers encountered problems due to stupidity of this company. Since this is an open source project and aims makers especially, I am not very happy with this chip. But this is the case.

Do It Yourself (DIY)
--------------------

.. figure:: https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png
   :alt: CC BY-NC-SA 4.0
   :align: center

.. warning::
    AS IS, ABSOLUTELY NO WARRANTY. TAKE YOUR OWN RISK

Your read the features list and are fascinated about the project (LOL). You look forward to make your own isoUSBRS422 board and use it in your projects. Here is the good new: This is an open source project and you can make your own copy for non-commercial purposes!

.. note::
    This project is published under CC BY-NC-SA 4.0 license. It means that you can make your own copy for non-commercial purposes. Even, you can modify the project files, ex. PCB, if you refer to this original work properly and redistribute your version with the same license. See https://creativecommons.org/licenses/by-nc-sa/4.0/ for further details. :ref:`Contact <page_contact>` if you have any questions.

.. note::
    As I said in *Part 2 - Project Files* video (see below), I may have some extra PCBs or even components in my hand. I may able to send you if you **REALLY** want to make your own board, free of charge. Please :ref:`contact <page_contact>` if you are interested in.

Video Tutorials
^^^^^^^^^^^^^^^

I prepared 6 tutorial videos with total runtime ~1.5 hours (!) for makers. Below, videos are given in order. Also you can find a ordered playlist here: http://www.alperyazar.com/r/isoUSBRS422VIDEOTUTv1

**Part 0 - Introduction**

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/EZh2zi6m1yI" frameborder="0" allowfullscreen></iframe></center>

**Part 1 - Features**

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/jb3v3Kmv85k" frameborder="0" allowfullscreen></iframe></center>

**Part 2 - Project Files**

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/QmU2l9yxdq4" frameborder="0" allowfullscreen></iframe></center>

**Part 3 - Board Production**

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/mPhScHU1XKU" frameborder="0" allowfullscreen></iframe></center>

**Part 4 - Driver Installation, Programming, Functional Verification**

.. raw:: html

   <center><iframe width="560" height="315" src="https://www.youtube.com/embed/gxzl12bP4j4" frameborder="0" allowfullscreen></iframe></center>

**Part 5 - Operation Modes**

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/e4YLkROiQLc" frameborder="0" allowfullscreen></iframe></center>

**Part 6 - Known Issues**

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/GGQSbGbkveA" frameborder="0" allowfullscreen></iframe></center>

On The Web
----------

isoUSBRS422 project is also shown up on some websites.

Dangerous Prototypes
^^^^^^^^^^^^^^^^^^^^

`Blog post of Dangerous Prototypes about isoUSBRS422 project <http://dangerousprototypes.com/2015/12/17/isousbrs422-an-open-source-isolated-usb-rs422rs485-converter-board/>`__

EEVblog
^^^^^^^

.. raw:: html

    <center><iframe width="560" height="315" src="https://www.youtube.com/embed/dXbbJOH59oo?start=822" frameborder="0" allowfullscreen></iframe></center>

isoUSBRS422v1 board is shown up in `EEVblog #833 - Mailbag <https://www.youtube.com/watch?v=dXbbJOH59oo>`__ episode between **13:42** - **18:26**.

Related Blog Posts
------------------

* :ref:`page_blog_20141223_isousbrs422`
* :ref:`page_blog_20141224_isousbrs422`
* :ref:`page_blog_20150113_isousbrs422`
* :ref:`page_blog_20150509_isousbrs422`
* :ref:`page_blog_20151114_isousbrs422`
* :ref:`page_blog_20151226_eevblog`
* :ref:`page_blog_20151229_isousbrs422`

Updated: -

Created: December 22, 2014
