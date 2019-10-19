# MIDAS-Analyser-code development for life time measurement of nuclei for-DE-E-Telscope, HPGE detector set up  @iThemba Lab, Cape Town
# Structure present code  follows http://lmu.web.psi.ch/docu/manuals/bulk_manuals/software/midas195/html/analyzer_struct.html
As

    The Midas Analyzer application is composed of a collection of files providing a framework in which the user can gain access to the online data during data acquisition or offline data through a replay of a stored data save-set.

    The Midas distribution contains 2 directories where predefined set of analyzer files and their corresponding working demo code are available. The internal functionality of both example is similar and differ only on the histogram tool used for the data representation. These analyzer set are specific to 2 major data analysis tools i.e: ROOT, HBOOK:
        examples/experiment: Analyzer tailored towards ROOT analysis
        examples/hbookexpt: Analyzer tailored towards HBOOK with PAW.

    The purpose of the demo analyzer is to demonstrate the analyzer structure and to provide the user a set of code "template" for further development. The demo will run online or offline following the information given further down. The analysis goal is to:
        Initialize the ODB with predefined (user specific) structure (experim.h).
        Allocate memory space for histogram definition (booking).
        Acquire data from the frontend (or data file).
        Process the incoming data bank event-by-event through user specific code (module).
        Generate computed quantitied banks (in module).
        Fill (increment) predefined histogram with data available within the user code.
        Produce a result file containing histogram results and computed data (if possible) for further replay through dedicated analysis tool (PAW, ROOT).

    The analyzer is structured with the following files:
        experim.h
            ODB experiment include file defining the ODB structure required by the analyzer.
        analyzer.c: main user core code.
            Defines the incoming bank structures
            Defines the analyzer modules
            Initialize the ODB structure requirements
            Provides Begin_of_Run and End_of_Run functions with run info logging example.
        adccalib.c, adcsum.c, scaler.c (Root example)
            Three user analysis modules to where events from the demo frontend.c sends data to.
        Makefile
            Specific makefile for building the corresponding frontend and analyzer code. The frontend code is build against the camacnul.c driver providing a simulated data stream.
