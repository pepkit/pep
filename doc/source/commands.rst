
Commands
******************************

Looper does several things.

- ``looper run``:  Runs pipelines for each sample, for each pipeline. This will use your ``compute`` settings to build and submit scripts to your specified compute environment, or run them sequentially on your local computer.

- ``looper destroy``: Deletes all output results for this project.

- ``looper summarize``: Summarize your project results. This command parses all key-value results reported in the each sample `stats.tsv` and collates them into a large summary matrix, which it saves in the project output directory. This creates such a matrix for each pipeline type run on the project, and a combined master summary table.

- ``looper check``: Checks the run progress of the current project. This will display a summary of job status; which pipelines are currently running on which samples, which have completed, which have failed, etc.

- ``looper monitor``: (in progress)