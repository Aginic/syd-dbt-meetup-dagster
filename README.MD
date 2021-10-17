## Repository with code examples for the Sydney dbt meetup of October 2021: Let's talk orchestration. An Intro to scheduling dbt with Dagster.

### Slides for the talk
[Slides](./Sydney+dbt+meetup+-+Benoit+Perigaud+-+dbt+and+Dagster.pdf)

### Setup a virtual environment
Create a Python virtual environment (through conda or the env module) and install all packages from the requirements.txt: `pip install -r /path/to/requirements.txt`

### Setup dbt
- Setup your `profiles.yml` file with your database credentials. The dbt project name is `jaffle_shop`.
- Try your dbt connection by opening a shell in the `jaffle_shop` folder and running `dbt debug`
- Do a `dbt seed` in the same folder to make sure that the correct rights are setup to write to the DB

### Setup dagster
- Minimal setup
    - Update the file `dbt_pipeline.py` with the correct paths for your dbt executable (you can do a `where dbt` while in the venv) and your dbt project
    - If you want to run dagster in a "persistent mode", set up the env variable DAGSTER_HOME (e.g. `export DAGSTER_HOME=~/.dagster` in bash/zsh)
    - Update the `workspace.yaml` file with the correct python path for your venv (running `where python` from your venv)
    - Run `dagit` and open the web interface
- Optional setup
    - For storing results in a Postgres DB instead of SQLite, create/modify your file `DAGSTER_HOME/dagster.yaml` following all the "xxx_storage" entries in the example `example_dagster.yaml`
    - For setting up concurrency limits, modify `DAGSTER_HOME/dagster.yaml` to add a configuration for the run_coordinator