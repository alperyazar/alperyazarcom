:orphan:

.. _page_projects_aPCmeter:

aPCmeter
========

This project is just for fun. It is used to monitor CPU and RAM usage of a computer via vintage looking illuminated gauges. aPCmeter uses Arduino Nano v3 as controller. It is completely an open source project and you can build your aPCmeter easily. All building steps and internals of Arduino software are explained in detail. 

Here is the aPCmeter in a nusthell:

.. figure:: /images/projects/apcmeter/BoardFinalTest.gif
   :alt: aPCmeter in a nutshell
   :align: center

   aPCmeter in a nutshell

.. list-table:: Links

   * - **This Page (Permalink)**
     - http://www.alperyazar.com/r/aPCmeter
   * - **Files (GitHub)**
     - http://www.alperyazar.com/r/aPCmeterGIT
   * - **Known Issues**
     - http://www.alperyazar.com/r/aPCmeterISSUES
   * - **Hackaday.io**
     - http://www.alperyazar.com/r/aPCmeterSKULL
   * - **Gallery**
     - http://www.alperyazar.com/r/aPCmeterGALLERY

Features
--------

Here is the summary of features in "catalog" style:

.. figure:: /images/projects/apcmeter/features_full.png
   :alt: Summary of Features of aPCmeter
   :align: center
   :width: 100 %

   Summary of Features of aPCmeter. Click on the image for larger size


What is aPCmeter?
-----------------

Actually there is nothing more to say about the project. You saw the pictures and features. It is a project just for fun. **aPCmeter** can be considered as **a PCmeter** or **alper's PCmeter** or **analog PCmeter**.

aPCmeter provides a COM port based communication interface to PC. It possible to adjust gauge positions and brightness of LEDs over this interface. aPCmeter can't detect CPU and RAM usage of computer itself. A proper computer software should drive aPCmeter hardware (LEDs and gauges). aPCmeter works like a *slave* device.

Initially I saw Analog PC Stats Meter project on the web (http://www.lungstruck.com/projects/pc-meter/) then I decided to build my own based on this idea.

.. note::
    aPCmeter project consists of only hardware components + Arduino software. No computer software is given with this project (unlike Analog PC Stats Meter project). On the other hand, a computer software **must** run to get CPU and RAM utilization information from operating system and send it to the aPCmeter. I will publish that software under different project name. You can consider aPCmeter as missing. But you can write your simple PC software because communication protocol of aPCmeter is described in detail. I will update this section after publishing the computer software (I hope that I will remember to update).

Do It Yourself (DIY)
--------------------

.. figure:: https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png
   :alt: CC BY-NC-SA 4.0
   :align: center

.. warning::

    AS IS, ABSOLUTELY NO WARRANTY. TAKE YOUR OWN RISK

If you build your own aPCmeter just download files from Github (link is given at the top) and follow the steps given in **HowToBuild** folder. I prepared very detailed document. If you have any problem, you can contact me always.

Similar Projects
----------------

I have found these projects on the web:

 * http://www.lungstruck.com/projects/pc-meter/
 * https://hackaday.io/project/10629-usb-analog-panel-meters-w-arduino
 * http://www.uchobby.com/index.php/2008/02/12/arduino-analog-gauge/
 * https://www.youtube.com/watch?v=zbE6zpmrZYw

Related Blog Posts
------------------

* :ref:`page_blog_20160202_apcmeter`
* :ref:`page_blog_20161018_apcmeter`

Updated: -

Created: March 26, 2016
