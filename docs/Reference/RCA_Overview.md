# Run-Control App (RCA) Overview 

The Run-Control App (RCA) can generate and examine GenevaERS run-control files: 
- View Definition Parameters (VDP)
- Extract-Phase Logic Table (XLT)
- Reference-Phase Logic Table (JLT)

When in Generate mode (that is, when the **GENERATE_RC_FILES** parameter is set to Y), the Run-Control App reads views (and all their associated metadata) that have been defined in the GenevaERS Workbench, then converts them into files for the Performance Engine to process. The RCA contains the logic to optimize a group of views for a single pass of the source data.

The input can be from:
- Workbench XML (WBXML), as exported from the Workbench, 
- Directly from the database used by the Workbench, or 
- View Definition Parameters XML (VDPXML) (a deprecated format). 

For WBXML input, XML files are supplied in members of the PDS WBXMLI. For database (DB2 or Postgres) input, database parameters must be supplied, along with the GenevaERS environment ID and a list of either view numbers or view folder numbers. The view numbers are supplied in the file DBVIEWS, and the view folder numbers are supplied in the file DBFLDRS.

The file RUNVIEWS is used to select a subset of views. This may be useful when the input is from WBXML or VDPXML.

The output is put in files VDPNEW (input to all Performance Engine jobs), XLTNEW (input to GVBMR95E), and JLTNEW (input to GVBMR95R, if there are any lookups defined in the views).   

Whether or not the Run-Control App is in Generate mode, it can examine the VDP, XLT, and JLT and create reports, which are written to VDPRPT, XLTRPT, and JLTRPT respectively.

Any combination of the parameters **VDP_REPORT**, **XLT_REPORT**, and **JLT_REPORT** may be used to specify the reports you require.

Each report requested must have the corresponding DD statement defined for input (VDPNEW, XLTNEW, JLTNEW) and output (VDPRPT, XLTRPT, JLTRPT).

If the parameter **COMPARE** is set to **Y**, the RCA will compare and report on two sets of run-control files. In this case the corresponding DD statements for both inputs must be provided (VDPNEW, XLTNEW, JLTNEW, and VDPOLD, XLTOLD, JLTOLD).

Specify the report output format with **REPORT_FORMAT**.
