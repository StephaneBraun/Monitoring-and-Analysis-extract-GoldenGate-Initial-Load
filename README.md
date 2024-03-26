# Monitoring-and-Analysis-extract-GoldenGate-Initial-Load
Tail report file for extract initial and generate statistics per table in number of rows and duration in the form of a flat file and Excel sheet


This utility allows you to display the GoldenGate 21c microservices reports in real time for the extract initial load and then from this report file to generate a flat file and an xlsx file which presents the summary of the statistics with the following information:

  - Tablename
  - Date and time of start and end of processing per table
  - Number of rows retrieved per table
  - Extract duration per table in seconds
  - Number of rows retrieved per second per table
  - % in number of rows per table compared to the total number of rows extracted
  - % of duration per table compared to total duration

This utility only works with a Linux environment (Windows not supported)

This allows to :

- present the performance of the extract,
- to make projections of the duration in the event of a table addition,
- quickly identify the largest tables and their extraction duration,
- to plan the addition of new extracts with an optimized distribution of tables to reduce execution time.


Prerequisites:

    JDK 1.8 minimum


Launching the utility:

    java -jar /app/tools/initialLoadAnalysis.jar path of report file extract name

Example :

    java -jar /app/tools/initialLoadAnalysis.jar /app/goldengate/oracle/deploy/var/lib/report EXT1



The result files will be generated in the same directory as the GoldenGate report file. We have 2 output files:

  - CSV 
  - XLSX


The utility searches for the Linux process executing the extract initial load corresponding to the name of the process passed as a parameter with a ps command.
  If the process is running, we display the report file via the equivalent of a tail -f.
  If the process is already finished or when it ends, the output files are generated.
