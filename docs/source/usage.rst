Installation
============

Install Armoniax node tools from source
---------------------------------------

If you build for the first time, you should write

.. code:: shell

   git clone https://github.com/armoniax/amax.meta.chain.git

   git submodule update --init --recursive

   ./scripts/amax_build.sh

Otherwise, you can use make -j instead.

Install from docker image
-------------------------

Use the following commands to download offical docker image from docker hub.

.. code:: shell

   docker pull armoniax/amnod
