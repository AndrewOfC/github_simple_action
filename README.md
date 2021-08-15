

# Contents

| Directory | Contents |
| --- | --- |
| simple_action | Simple CMake project with 1 library |
| multiple_jobs | Project comprised of multiple libraries and jobs and final linkage |

# Running 

```bash
$ cd simple_action
$ mkdir build
$ cd build
$ make -j
	⁃	$ ./demo
``` 


The heart of your CI in GitHub will be the files in <repo>/.github/workflows/<workflow>.yaml


Each workflow file will represent a task to be done.


# YAML

  [yaml](https://yaml.org/)
  

# Simple run

This is a simple [workflow file](https://github.com/AndrewOfC/github_simple_action/blob/master/.github/workflows/build.yml)

* Check out the code from the repository
* Create a build directory
* Run cmake in the build directory
* Build the project

```yaml
name: Build
on: [push]
jobs:
  BuildAndTest:
    runs-on: ubuntu-18.04
    defaults:
      run:
        shell: bash
    steps:
      - name: Check out repository
        uses: actions/checkout@v2
      - run: mkdir build
      - name: CMake
        working-directory: build
        run: cmake ..
      - name: Build
        working-directory: build
        run: make -j `nproc`
      - name: Test
        working-directory: build
        run: ./demo


```

## Breakdown

### Name

It creates a workflow named "Build".  The history of the workflow runs can be found under the ['Actions' tab](https://github.com/AndrewOfC/github_simple_action/actions) for any given GitHub project

## Job BuildAndTest

It has one job "BuildAndTest".    Multiple jobs will run in parallel on different machines.  
Jobs contain 'steps:' of a [yaml sequence](https://yaml.org/spec/1.2/spec.html#id2790320) that are executed in order.  If any fail(i.e. exiting with non-zero status), the entire job will fail and so will the workflow.

Each step is a [yaml mapping](https://yaml.org/spec/1.2/spec.html#id2790832) of the following fields:

| Field                | Value |
| ----                 | ---- |
| name: (optional)     | name of the step to be displayed in summaries|
| run:                 | command to run.  Subject to shell variable and string manipulation|
| working-directory:   | working directory to execute in|
| uses:                | A prepackaged action  |

Each step must contain either 'run' or 'uses'
