ROS Installation
================


These instructions are for Ubuntu 18.04 LTS and ROS Melodic, which are officially available `here. <http://wiki.ros.org/melodic/Installation/Ubuntu>`_ 

Installing ROS
---------------

Setting up sources.list
^^^^^^^^^^^^^^^^^^^^^^^

Setup your computer to accept software from packages.ros.org:

.. code-block:: bash

    $ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

Set up your keys:
^^^^^^^^^^^^^^^^^
.. code-block:: bash

    $ sudo apt install curl # if you haven't already installed curl
    $ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -


Installing ROS Melodic
^^^^^^^^^^^^^^^^^^^^^^
Make sure your Ubuntu package index is up-to-date: 


.. code-block:: bash

    $ sudo apt update

Install ROS Melodic:

.. code-block:: bash

    $ sudo apt install ros-melodic-desktop-full

Environment setup 
^^^^^^^^^^^^^^^^^

It's convenient if the ROS environment variables are automatically added to your bash session every time a new shell is launched:   

.. code-block:: bash

    $ echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
    $ source ~/.bashrc

Dependencies for building packages
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Run the following to install the rosinstall tool and other dependencies for building ROS packages, which are convenient to have.

.. code-block:: bash 

    $ sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

Initialize your rosdep:

.. code-block:: bash 

    $ sudo rosdep init
    $ rosdep update

Test your installation
^^^^^^^^^^^^^^^^^^^^^^
Run the following to check if your packages are installed properly:

.. code-block:: bash 

    $ roscore

If you get something like the following as your terminal output you are good to go!

.. code-block:: bash 

    ... logging to /home/john/.ros/log/70b2d514-eff1-11ec-af72-701ce7f4339b/roslaunch-john-Inspiron-13-7378-22339.log
    Checking log directory for disk usage. This may take a while.
    Press Ctrl-C to interrupt
    Done checking log file disk usage. Usage is <1GB.

    started roslaunch server http://localhost:41967/
    ros_comm version 1.14.13


    SUMMARY
    ========

    PARAMETERS
    * /rosdistro: melodic
    * /rosversion: 1.14.13

    NODES

    auto-starting new master
    process[master]: started with pid [22359]
    ROS_MASTER_URI=http://localhost:11311/

    setting /run_id to 70b2d514-eff1-11ec-af72-701ce7f4339b
    process[rosout-1]: started with pid [22370]
    started core service [/rosout]

Press ``Ctrl+C`` to terminate the process (``roscore``).



Installing ``catkin_tools``
---------------------------
These instructions are for installing ``catkin_tools``, which are officially available `here  <https://catkin-tools.readthedocs.io/en/latest/installing.html>`_ 

Installing with apt-get
^^^^^^^^^^^^^^^^^^^^^^^

Firstly, ensure that your ROS repositories contain the required ``.deb`` for ``catkin_tools``:

.. code-block:: bash

    $ sudo sh \
        -c 'echo "deb http://packages.ros.org/ros/ubuntu `lsb_release -sc` main" \
            > /etc/apt/sources.list.d/ros-latest.list'
    $ wget http://packages.ros.org/ros.key -O - | sudo apt-key add -

Once you have added that repository, run these commands to install ``catkin_tools``:

.. code-block:: bash

    $ sudo apt-get update
    $ sudo apt-get install python3-catkin-tools

Testing your installation
^^^^^^^^^^^^^^^^^^^^^^^^^

Create a catkin workspace by creating a folder ``catkin_ws`` and within it, create a folder named ``src``. To do this, run:

.. code-block:: bash

    $ mkdir -p catkin_ws/src
    $ cd catkin_ws

Run ```catkin_make``` inside your ``catkin_ws`` folder:

.. code-block:: bash

    $ catkin_make

If you get something like the following as your terminal output you are good to go!

.. code-block:: bash

    Base path: /home/john/Desktop/catkin_ws
    Source space: /home/john/Desktop/catkin_ws/src
    Build space: /home/john/Desktop/catkin_ws/build
    Devel space: /home/john/Desktop/catkin_ws/devel
    Install space: /home/john/Desktop/catkin_ws/install
    Creating symlink "/home/john/Desktop/catkin_ws/src/CMakeLists.txt" pointing to "/opt/ros/melodic/share/catkin/cmake/toplevel.cmake"
    ####
    #### Running command: "cmake /home/john/Desktop/catkin_ws/src -DCATKIN_DEVEL_PREFIX=/home/john/Desktop/catkin_ws/devel -DCMAKE_INSTALL_PREFIX=/home/john/Desktop/catkin_ws/install -G Unix Makefiles" in "/home/john/Desktop/catkin_ws/build"
    ####
    -- The C compiler identification is GNU 7.5.0
    -- The CXX compiler identification is GNU 7.5.0
    -- Check for working C compiler: /usr/bin/cc
    -- Check for working C compiler: /usr/bin/cc -- works
    -- Detecting C compiler ABI info
    -- Detecting C compiler ABI info - done
    -- Detecting C compile features
    -- Detecting C compile features - done
    -- Check for working CXX compiler: /usr/bin/c++
    -- Check for working CXX compiler: /usr/bin/c++ -- works
    -- Detecting CXX compiler ABI info
    -- Detecting CXX compiler ABI info - done
    -- Detecting CXX compile features
    -- Detecting CXX compile features - done
    -- Using CATKIN_DEVEL_PREFIX: /home/john/Desktop/catkin_ws/devel
    -- Using CMAKE_PREFIX_PATH: /opt/ros/melodic
    -- This workspace overlays: /opt/ros/melodic
    -- Found PythonInterp: /usr/bin/python2 (found suitable version "2.7.17", minimum required is "2") 
    -- Using PYTHON_EXECUTABLE: /usr/bin/python2
    -- Using Debian Python package layout
    -- Using empy: /usr/bin/empy
    -- Using CATKIN_ENABLE_TESTING: ON
    -- Call enable_testing()
    -- Using CATKIN_TEST_RESULTS_DIR: /home/john/Desktop/catkin_ws/build/test_results
    -- Found gtest sources under '/usr/src/googletest': gtests will be built
    -- Found gmock sources under '/usr/src/googletest': gmock will be built
    -- Found PythonInterp: /usr/bin/python2 (found version "2.7.17") 
    -- Looking for pthread.h
    -- Looking for pthread.h - found
    -- Looking for pthread_create
    -- Looking for pthread_create - not found
    -- Looking for pthread_create in pthreads
    -- Looking for pthread_create in pthreads - not found
    -- Looking for pthread_create in pthread
    -- Looking for pthread_create in pthread - found
    -- Found Threads: TRUE  
    -- Using Python nosetests: /usr/bin/nosetests-2.7
    -- catkin 0.7.29
    -- BUILD_SHARED_LIBS is on
    -- BUILD_SHARED_LIBS is on
    -- Configuring done
    -- Generating done
    -- Build files have been written to: /home/john/Desktop/catkin_ws/build
    ####
    #### Running command: "make -j4 -l4" in "/home/john/Desktop/catkin_ws/build"
    ####

FAQs
----
