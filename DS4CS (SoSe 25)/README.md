# Jupyter Hub
- Hosted on BigDaMa-4 server: http://130.149.21.99/
- Registration:
    - Students are registered by the admins
        - Create user by adding a username through admin panel in Jupyter Hub
        - Username is assigned as a substring before `@` of the students email, e.g., `name@campus.tu-berlin.de` -> `name` will be a username
        - Users could be created in bulk by providing newline-separated list of usernames
    - Password is set by students themselves after the first sign-in
    - Only admins can reset the students' passwords if necessary by deleting the user and re-creating one with the same username
- Upload datasets into a shared folder on the Hub: `/srv/data/ds4cs/sose25/datasets/`
    - This allows to avoid creating a copy of the dataset across all users
- Dependencies are specified at: `/srv/scratch/requirements.txt`
    - Install by running: `sudo -E pip install -r /srv/scratch/requirements.txt`
    - Visible to all users but read-only for non-admins
    - All users share the same conda environment, so it is sufficient to install the dependencies by admins only to disseminate them across users

# Grading
- Proposed implementation: https://otter-grader.readthedocs.io/en/latest/index.html
- `./hws/demo` directory has a demo of the homework
- Reproduce as:
    - `cd` into the root of DS4CS
    - Create `venv`, activate and run `pip install -r requirements.txt`
    - run `otter assign hws/demo/demo_master.ipynb hws/demo/dist`
- Routine explanation:
    - `demo_master.ipynb` has an annotated master file of the homework
    - `dist` is an output directory ("distribution" alias):
        - `dist/autograder` has a notebook and .zip file for grading of automatically graded questions
        - `dist/student` has a notebook which should be delivered to students
- Currently implemented only for automatically graded questions (with `assert` based tests)