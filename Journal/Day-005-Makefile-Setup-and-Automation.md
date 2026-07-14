Day 005 - Makefile Setup and Automation

Date:
14 July 2026

Task Objective:
Repair the existing Makefile so that the machine learning project automation works correctly. The Makefile should create a virtual environment, install dependencies, process data, train the model, execute tests, and provide a cleanup target.

Tasks Completed:
- Navigated to the project directory.
- Opened and reviewed the existing Makefile.
- Corrected the Makefile by defining all required targets:
  - setup
  - data
  - train
  - test
  - clean
  - all
- Declared all targets under .PHONY.
- Ensured every recipe line was indented using a TAB character.
- Configured the setup target to create the virtual environment and install project dependencies.
- Configured the data target to execute the data processing script.
- Configured the train target to execute the model training script.
- Configured the test target to run the project's pytest tests.
- Configured the clean target to remove __pycache__ directories, .pytest_cache, and all files inside the models directory.
- Configured the all target to execute setup, data, train, and test sequentially.
- Successfully executed "make all" and confirmed all tests passed.

Failures Encountered:

1. Incorrect Project Directory
Issue:
Initially attempted to enter an incorrect project directory, which resulted in:
cd: /root/code/fraud-de: No such file or directory

Cause:
The directory name was incomplete.

Resolution:
Navigated to the correct directory:
cd /root/code/fraud-detection

------------------------------------------------------------

2. Existing Makefile Did Not Meet Requirements
Issue:
The provided Makefile was incomplete and failed to satisfy the required automation workflow.

Cause:
Some required targets and project standards were missing.

Resolution:
Updated the Makefile by:
- Adding all required targets.
- Defining the correct commands for each target.
- Declaring all targets as .PHONY.
- Ensuring proper execution order using the "all" target.

------------------------------------------------------------

3. Recipe Indentation Requirement
Issue:
Makefiles require every command beneath a target to begin with a TAB character.

Cause:
Using spaces instead of a TAB causes Make to fail with a "missing separator" error.

Resolution:
Verified that every command line in the Makefile begins with an actual TAB character.

------------------------------------------------------------

4. Dependency Installation
Issue:
The setup target needed to create a Python virtual environment and install all required dependencies before executing project scripts.

Resolution:
Configured the setup target to:
- Create the mlops-venv virtual environment.
- Install all packages listed in requirements.txt.

------------------------------------------------------------

Verification:
Executed:

make all

Result:
- Virtual environment created successfully.
- Dependencies installed successfully.
- Data processing completed successfully.
- Model training completed successfully.
- Pytest executed successfully.
- All tests passed successfully.
- The Makefile met all task requirements.

Key Learning:
- Learned how Makefiles automate repetitive development tasks.
- Understood the purpose of .PHONY targets.
- Learned the importance of TAB indentation in Makefiles.
- Practiced creating reusable automation workflows for machine learning projects.
- Gained experience using make commands to simplify project setup, execution, testing, and cleanup.
