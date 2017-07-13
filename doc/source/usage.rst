Usage 
******************************

Looper doesn't just run pipelines; it can also check and summarize the progress of your jobs, as well as remove all files created by them.

Each task is controlled by one of the five main commands ``run``, ``summarize``, ``destroy``, ``check``, ``clean``.

- ``looper run``:  Runs pipelines for each sample, for each pipeline. This will use your ``compute`` settings to build and submit scripts to your specified compute environment, or run them sequentially on your local computer.

- ``looper summarize``: Summarize your project results. This command parses all key-value results reported in the each sample `stats.tsv` and collates them into a large summary matrix, which it saves in the project output directory. This creates such a matrix for each pipeline type run on the project, and a combined master summary table.

- ``looper check``: Checks the run progress of the current project. This will display a summary of job status; which pipelines are currently running on which samples, which have completed, which have failed, etc.

- ``looper destroy``: Deletes all output results for this project.


Command-line usage:
******************************

Here you can see the command-line usage instructions for the main looper command and for each subcommand:


``looper --help``
----------------------------------

.. code-block:: shell

	version: 0.6.0-dev
	usage: looper [-h] [-V] {run,summarize,destroy,check,clean} ...
	
	looper - Loop through samples and submit pipelines.
	
	positional arguments:
	  {run,summarize,destroy,check,clean}
	    run                 Main Looper function: Submit jobs for samples.
	    summarize           Summarize statistics of project samples.
	    destroy             Remove all files of the project.
	    check               Checks flag status of current runs.
	    clean               Runs clean scripts to remove intermediate files of
	                        already processed jobs.
	
	optional arguments:
	  -h, --help            show this help message and exit
	  -V, --version         show program's version number and exit
	
	For subcommand-specific options, type: 'looper <subcommand> -h'
	https://github.com/epigen/looper For debug options, type: 'looper -h
	--details'

``looper run --help``
----------------------------------

.. code-block:: shell

	version: 0.6.0-dev
	usage: looper run [-h] [-t TIME_DELAY] [--ignore-flags] [--compute COMPUTE]
	                  [--env ENV] [--limit LIMIT] [--file-checks] [-d]
	                  [--sp SUBPROJECT]
	                  config_file
	
	positional arguments:
	  config_file           Project configuration file (YAML).
	
	optional arguments:
	  -h, --help            show this help message and exit
	  -t TIME_DELAY, --time-delay TIME_DELAY
	                        Time delay in seconds between job submissions.
	  --ignore-flags        Ignore run status flags? Default: False. By default,
	                        pipelines will not be submitted if a pypiper flag file
	                        exists marking the run (e.g. as 'running' or
	                        'failed'). Set this option to ignore flags and submit
	                        the runs anyway.
	  --compute COMPUTE     YAML file with looper environment compute settings.
	  --env ENV             Employ looper environment compute settings.
	  --limit LIMIT         Limit to n samples.
	  --file-checks         Perform input file checks. Default=True.
	  -d, --dry-run         Don't actually submit the project/subproject.
	  --sp SUBPROJECT       Name of subproject to use, as designated in the
	                        project's configuration file

``looper summarize --help``
----------------------------------

.. code-block:: shell

	version: 0.6.0-dev
	usage: looper summarize [-h] [--file-checks] [-d] [--sp SUBPROJECT]
	                        config_file
	
	positional arguments:
	  config_file      Project configuration file (YAML).
	
	optional arguments:
	  -h, --help       show this help message and exit
	  --file-checks    Perform input file checks. Default=True.
	  -d, --dry-run    Don't actually submit the project/subproject.
	  --sp SUBPROJECT  Name of subproject to use, as designated in the project's
	                   configuration file

``looper destroy --help``
----------------------------------

.. code-block:: shell

	version: 0.6.0-dev
	usage: looper destroy [-h] [--file-checks] [-d] [--sp SUBPROJECT] config_file
	
	positional arguments:
	  config_file      Project configuration file (YAML).
	
	optional arguments:
	  -h, --help       show this help message and exit
	  --file-checks    Perform input file checks. Default=True.
	  -d, --dry-run    Don't actually submit the project/subproject.
	  --sp SUBPROJECT  Name of subproject to use, as designated in the project's
	                   configuration file

``looper check --help``
----------------------------------

.. code-block:: shell

	version: 0.6.0-dev
	usage: looper check [-h] [--file-checks] [-d] [--sp SUBPROJECT] config_file
	
	positional arguments:
	  config_file      Project configuration file (YAML).
	
	optional arguments:
	  -h, --help       show this help message and exit
	  --file-checks    Perform input file checks. Default=True.
	  -d, --dry-run    Don't actually submit the project/subproject.
	  --sp SUBPROJECT  Name of subproject to use, as designated in the project's
	                   configuration file

``looper clean --help``
----------------------------------

.. code-block:: shell

	version: 0.6.0-dev
	usage: looper clean [-h] [--file-checks] [-d] [--sp SUBPROJECT] config_file
	
	positional arguments:
	  config_file      Project configuration file (YAML).
	
	optional arguments:
	  -h, --help       show this help message and exit
	  --file-checks    Perform input file checks. Default=True.
	  -d, --dry-run    Don't actually submit the project/subproject.
	  --sp SUBPROJECT  Name of subproject to use, as designated in the project's
	                   configuration file

``looper --help --details``
----------------------------------

.. code-block:: shell

	version: 0.6.0-dev
	usage: looper [-h] [-V] [--logfile LOGFILE] [--verbosity {0,1,2,3,4}]
	              [--logging-level LOGGING_LEVEL] [--dbg]
	              {run,summarize,destroy,check,clean} ...
	
	looper - Loop through samples and submit pipelines.
	
	positional arguments:
	  {run,summarize,destroy,check,clean}
	    run                 Main Looper function: Submit jobs for samples.
	    summarize           Summarize statistics of project samples.
	    destroy             Remove all files of the project.
	    check               Checks flag status of current runs.
	    clean               Runs clean scripts to remove intermediate files of
	                        already processed jobs.
	
	optional arguments:
	  -h, --help            show this help message and exit
	  -V, --version         show program's version number and exit
	  --logfile LOGFILE     Optional output file for looper logs (default: None)
	  --verbosity {0,1,2,3,4}
	                        Choose level of verbosity (default: None)
	  --logging-level LOGGING_LEVEL
	                        Set logging level (default: None)
	  --dbg                 Turn on debug mode (default: False)
	
	For subcommand-specific options, type: 'looper <subcommand> -h'
	https://github.com/epigen/looper
