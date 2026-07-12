Task Overview
-------------
This task involved cleaning a Python/ML Git repository that was missing a .gitignore file. Several generated and local files had already been committed to Git. The objective was to create a proper .gitignore, stop tracking unnecessary artifacts, and commit the cleanup while keeping the project source files under version control.

Ignored Artifacts
-----------------
- __pycache__/
- *.pyc
- venv/
- .ipynb_checkpoints/
- *.pkl
- .env

Challenges and Fixes
--------------------

1. .gitignore did not exist
Issue:
The repository had no .gitignore file, allowing generated files to be committed.

Solution:
Created a .gitignore containing the required Python and machine learning ignore rules.

2. Files were already tracked
Issue:
Adding files to .gitignore did not remove them from Git because they were already being tracked.

Solution:
Used git rm --cached to remove them from Git's index while keeping them on the local machine.

3. .gitignore was untracked
Issue:
After creating .gitignore, Git showed it as an untracked file.

Solution:
Added it using:
git add .gitignore

4. Final cleanup
Solution:
Committed all changes with:
git commit -m "Add .gitignore and stop tracking generated artifacts"

Verification
------------
- git status returned: Working tree clean.
- git ls-files confirmed that only the required project files remained tracked.
- Source files under src/fraud_detection/, README.md, and requirements.txt were preserved.

Outcome
-------
Successfully cleaned the repository by:
- Creating a proper .gitignore.
- Removing unnecessary Python/ML artifacts from Git tracking.
- Preserving all required source files.
- Committing the cleanup successfully.
""")

outfile="/mnt/data/Task4_Git_Repository_Cleanup_Notes.txt"
pypandoc.convert_text(text,"plain",format="md",outputfile=outfile,extra_args=["--standalone"])
print(outfile)
