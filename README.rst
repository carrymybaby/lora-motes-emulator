LoRa Motes Emulator
===================

This is a useful tool to test LoRa server.

To emulate end devices (a.k.a. Motes in |LoRaWAN(TM)| protocol)

*Support* |LoRaWAN(TM)| *1.0.2 protocol*

**Using Gateways from** |Semtech(TM)|

.. |LoRaWAN(TM)| unicode:: LoRaWAN U+2122
.. |Semtech(TM)| unicode:: Semtech U+2122


System Requirements
======================

- Ubuntu
- Python(3.6, mandatory)

Installtion
===================

- Use ``pip`` to install ``pipenv``::

  (sudo) pip3 install pipenv

- Clone this repo into a directory::

    git clone https://github.com/houluy/lora-motes-emulator.git

- Use ``pipenv`` to create a virtual Python environment and install all the dependencies::

    pipenv --python 3 install
  
Here, if there is not Python 3.6 in your system, a warning will occur, and no package will be installed. It is perfect to install Python 3.6 from `source <https://www.python.org/downloads/release/python-362/>`_. Otherwise, remove the ``Pipfile.lock`` and redo the above command.

- Run the emulator to see the help::

    pipenv run python main.py -h

  or by::

    pipenv shell
    python main.py -h

Tutorial
===================

- Copy a local config file and device info file from the template, then modify the src and dest address.
- Modify device infomation in ``device.json`` you just copied.
- Install the environment, and start the virtual shell ``pipenv shell``.
- Currently, four kinds of message is supported: pull data, join confirmed data up (with or without FOpts) and MAC Commands in FRMPayload field:

::  

    python main.py pull
    python main.py join
    python main.py app -m (your uplink message, will be encoded by UTF-8) -f (your MACCommand in FOpts field)
    python main.py mac -c (your MAC Command in FRMPayload field)

If this is your first-time running, run ``pull`` and ``join`` in the very begining to register the port of gateway and join the device. The device info will be saved automatically in ``models/device.pkl`` using ``pickle``, and loaded next time.

Here is the example:

::  

    python main.py app -m helloworld -f 0302
    python main.py mac -c 0302

Contribution
===================
This repo is hosted on https://github.com/houluy/lora-motes-emulator and under MIT license, any contribution or suggestion is welcome. Just open an issue or send a pull request.
