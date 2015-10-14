#Step 2 - Calling Peaks via MACS2
Command line documentation provided by Jonathan Reeder (Please see GENOMICS Documentation)

###Calling Peaks
1. *macs2 -t markoutputfromstep1.sam -c markcontroloutputfromstep1.sam -f SAM -g hs -n outputname -B*
    1. The -n outputname tells macs2 what you want the output files to be named. This can be whatever you want. Files will be output in whatever directory you;re in when you run this command.
    2. -B parameter tells macs to also build the .bdg files that can be used for making heatmaps or metagene profiles or viewing in IGV. If you only need to call peaks then do not use this parameter to speed up peak calling significantly.
    3. -broad parameter calls broad peaks. If you're using a [histone mark](http://www.nature.com/scitable/definition/histone-histones-57), you should add a -broad parameter at the end. Transcription factors should be used without -broad.
