# flask-mega-tutorial-2018
https://habr.com/ru/post/346306/

1) python3 -m venv venv
2) add venv in project settings
3) pip install -r requirements.txt
4) docker pull docker.elastic.co/elasticsearch/elasticsearch:6.4.3
5) docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:6.4.3


FIXME: CLI from lesson 13 don't work!

Debug & UnitTests in PyCharm:
https://blog.miguelgrinberg.com/post/setting-up-a-flask-application-in-pycharm

**Adding a Run and Debug Configuration**

One of the first things you'll probably want to do is run your project. PyCharm works with the concept of "configurations", which are sets of parameters that define a run or debug task. To create or edit configurations you have to select Run|Edit Configurations... from the menu. If this option appears disabled, you just need to wait a little bit and let PyCharm complete its initial background parsing of the project.

To create a new configuration, click the + sign, and then select Python. For the Name field, enter a description of this configuration, such as "webapp". I like to check the Single Instance Only option, because for a web application it isn't very useful to run multiple instances.

Under Script path you need to select the flask tool, which is located in the bin directory of your virtual environment. Here you can use the little ... button to the right to browse and select this script. If you store your virtual environments outside of your project, or if you use a virtual environment wrapper such as pipenv which has its own location for virtualenvs, you will need to find out where the virtualenv is located and browse to that directory and then down into bin to find the flask command. If your virtualenv is in the same directory as your project this is much easier to do. I should note that if you are doing this on Windows, your virtualenv is not going to have a "bin" subdirectory. On Windows look for a Scripts subdirectory, and inside it look for a flask.exe file to select.

In the Parameters field you are going to enter run. This combined with the previous option configure PyCharm to run the familiar flask run command.

As I'm sure you also remember, the flask command requires a FLASK_APP environment variable to point to your Flask application. This variable needs to be defined in the Environment variables section. The value of the variable will be the same value you use when you run your application from the command line. If you are using a .flaskenv file in your project, then you are all set, the environment variable will be imported from there.

The final change you need to make is to set the Working directory to point to the top-level directory of your project instead of to the location of the flask command.

You can now close the configuration window. The dropdown on the top-right of your main PyCharm window should now be set to the configuration you just added. If you now click the green "play" button your project should start, and if instead you click the green "bug" button the project will start under the debugger. Running with the debugger is very useful, because you can set breakpoints to stop the program execution and inspect variables or run a part of your application step by step.

**Running Unit Tests**

In addition to being able to run and debug your application, it is useful to have PyCharm run your unit tests. This requires a second configuration to be added to the project. So go back to the Run|Edit Configurations... menu option, and then click the + button once again, to create a new configuration. This time select the Python tests configuration type, and then pick the test runner that you would like to use. In the video demonstration above I picked Unittests, which is the runner based on the Python's unittest package.

Set the name of the configuration to tests of something similar. In the Target field make sure Script path is selected, and then choose the directory where your tests are located by clicking on the ... button to the right. In the Pattern field, enter a file pattern that applies to all the modules that contain tests. A few common patterns are test_*.py, *_test.py or *test*.py. To complete the test configuration, set the Working directory field to the top-level directory of your project.

After you close the configurations window, the dropdown in the top right of the PyCharm window will have tests selected. You can use this dropdown to go back to the webapp configuration when you need to. With tests selected, you can click the green run button to run your unit tests. PyCharm detects you are running tests, so it uses a dedicated panel in the bottom portion of the window to show you how the tests are doing. Any tests that fail will be displayed, and if you click on each one you can see the output it produced. You can also opt to run the tests under the debugger by clicking the green bug button, and that gives you the power to set breakpoints and run a specific part of a test step by step.

PyCharm also adds a little run button on the sidebar, next to each unit test function or method, and this is extremely convenient, as it allows you to run or debug a single test just by clicking its button.
 
