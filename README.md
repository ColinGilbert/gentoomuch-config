This is the configuration file structure for Gentoomuch.
========================================================

Here is the basic structure:

- ``env`` is for the environment in which gentoomuch operates. You might need to change the data in some files in there prior to first running:
    - ``arch`` is for your host's architecture. Acceptable values are: ``amd64``, ``arm64``.
    - ``uid`` is the uid of the user under which you are running Gentoomuch.
    - ``gid`` is the gid of that same user.
    - ``jobs`` is for the number of simultaneous compile jobs.
- ``cpu.defines`` is where you define the flags for the CPU that you'd otherwise set in /etc/portage/make.conf
- ``kernel.configs`` is where your kernel configurations get stored. These are automatically created by the Gentoomuch tool itself.
- ``package.sets`` is where you'll add custom package sets.
- ``portage.locals`` for defining your custom portage directories.
- ``portage.global`` is where the global base state for portage exists. The tool will ingest it along with your own definitions in ``portage.locals``
- ``user.patches`` is where your patches get stored. These are automatically created by the Gentoomuch tool itself.
- ``user.removes`` is where you write down the files you want to remove after your stage4 is built.
- ``user.scripts`` is where you write down scripts that get executed after your stage4 is built.
- ``stage3.defines`` is where you create folders with files defining the building blocks from which your stage3 gets assembled:
    - ``cpu`` in which you plug in the name of the cpu configuration you've defined in ``cpu.defines``.
    - ``packages`` in which you write down the package sets you've defined in ``package.sets``. It'll also work with individual packages.
    - ``portage.local`` in which you plug in the local portage directory you've defined in ``portage.locals``.
- ``stage4.defines`` is where you define the stage4 environments that get built by the pipeline:
    - ``kconf`` is for your kernel configuration.
    - ``profile`` is for a profile you've bootstrapped.
    - ``stage3`` is for the stage3 you've defined in ``stage3.defines``.
    - ``scripts`` is the name(s) of the script(s) that get run after building a stage4. Optional.
    - ``removes`` is the name(s) of the set(s) of files you've marked for removal in ``user.removes``. Optional.
