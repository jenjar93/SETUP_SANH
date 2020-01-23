#---------------Scripts to set up a NEMO configuration-----------


The folder contains the directories: 

- EXTRA_TOOLS: contains necessary files to set up NEMO and XIOS, and files to set up the RUN_DIRECTORY

- INPUTS: contains the directories for the 2017 input data, including:  
	    - ICS: contains initial conditions for 2017 (Copernicus) 
            - OBC: contains ocean boundary conditions for 2017 (Copernicus) 
            - FORCING: contains the surface forcing data for 2017 (ERA5)
            - TIDES: tidal boundary conditions (FES2014)

- DOMAIN: contains a smaller subsection of the SANH model domain, which covers the eastern side of India and the western Bay of Bengal at a 1/12th degree resolution

- SCRIPTS: contains the shell scripts...
           - main_setup.sh       > runs the subsequent scripts in the necessary order
           - load_modules.sh     > loads the necessary modules (!! These will need to be changed for your machine !!!) 
           - make_path.sh        > configures the paths (!! change paths as necessary !!) 
           - make_directories.sh > makes the directory SANH_SMALL and all subdirectories
           - make_xios.sh        > downloads and compiles XIOS
           - make_nemo.sh        > downloads and compiles NEMO
           - setup_run.sh        > copies necessary files from EXTRA_TOOLS into the RUN_DIRECTORY experiment folder (EXP_01) 



Once the above scripts have run, the directory SANH_SMALL will have been created, which contains the RUN_DIRECTORY. This is the directory from which to run NEMO.

Nagivate to the directory SANH_SMALL/RUN_DIRECTORY/EXP_01. The file namelist_cfg has already been configured for 2017 and should (hopefully) run with no problems! The namelist_cfg file contains all the model tuning and the location directories for the INPUT files. This, as well as the file_def_nemo.xml file (which sets the output variables) are the ones that you will most likely change in future.   

To run NEMO, modify the run_script.pbs (standard queue up to 24hr) and run_script_short.pbs (short queue ~20 min) scripts for your own computer cluster as the current run scripts have been configured to work with ARCHER and will not work on your machine. Then submit the run scripts to the queue! On ARCHER, a year takes approximately 2~3 hours to run.   


