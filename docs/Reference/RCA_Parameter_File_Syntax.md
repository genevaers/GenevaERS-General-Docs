# Run-Control App (RCA) Parameter File Syntax

put examples at bottom 

Note: each parameter must be on a separate line 

link to sample JCL 

## Format: RCAPARM file  

<pre>
     ┌─GENERATE_RC_FILES=Y─┤ generation options ├─┐        
►►───┼────────────────────────────────────────────┼─────────────────────────────► 
     └─GENERATE_RC_FILES=N────────────────────────┘       

►────┤ general options ├───────────────────────────────────────────────────────►◄ 

</pre>

### generation options:

<pre>
►────┬─INPUT_TYPE=WBXML─────────────────────────────┬───────────────────────────►  
     ├─INPUT_TYPE=VDPXML────────────────────────────┤    
     ├─INPUT_TYPE=DB2───────┤ database parameters ├─┤  
     └─INPUT_TYPE=POSTGRES──┤ database parameters ├─┘       
       
</pre>

### database parameters:

<pre>
├────DB_SERVER=<i>server</i>──────────────────────────────────────────────────────────►  

►────DB_PORT=<i>port</i>──────────────────────────────────────────────────────────────►  

►────DB_DATABASE=<i>database-name</i>─────────────────────────────────────────────────►  
    
►────DB_SCHEMA=<i>db-schema</i>───────────────────────────────────────────────────────►  
   
►────ENVIRONMENT_ID=<i>GenevaERS-environment-id</i>───────────────────────────────────┤  
</pre>

### general options:
<pre>
     ┌─VDP_REPORT=N─┐                                                     
├────┼──────────────┼───────────────────────────────────────────────────────────► 
     └─VDP_REPORT=Y─┘                                                     

     ┌─XLT_REPORT=N─┐                                                     
►────┼──────────────┼───────────────────────────────────────────────────────────► 
     └─XLT_REPORT=Y─┘                                                     

     ┌─JLT_REPORT=N─┐                                                     
►────┼──────────────┼───────────────────────────────────────────────────────────► 
     └─JLT_REPORT=Y─┘                                                     

     ┌─REPORT_FORMAT=TEXT──┐                                                     
►────┼─────────────────────┼────────────────────────────────────────────────────► 
     ├─REPORT_FORMAT=CSV───┤    
     └─REPORT_FORMAT=HTML──┘  

     ┌─COMPARE=N─┐                                                       
►────┼───────────┼──────────────────────────────────────────────────────────────► 
     └─COMPARE=Y─┘                                                       

     ┌─NUMBER_MODE=STANDARD─┐                                                     
►────┼──────────────────────┼───────────────────────────────────────────────────► 
     └─NUMBER_MODE=LARGE────┘                                                     
                                       
     ┌─LOG_LEVEL=STANDARD─┐                                                       
►────┼────────────────────┼─────────────────────────────────────────────────────┤ 
     └─LOG_LEVEL=DEBUG────┘                                                        
</pre>
  
## Format: DBFLDRS file
<pre>
<i>►►───┬───────────────┬─────────────────────────────────────────────────────────►◄</i> 
<i>     │ ┌───────────┐ │                                                        </i>
<i>     │ ▼           │ │                                                        </i>
<i>     └───folder-id─┴─┘ </i>
</pre>
  
## Format: DBVIEWS file
<pre>
<i>►►───┬─────────────┬───────────────────────────────────────────────────────────►◄</i> 
<i>     │ ┌─────────┐ │                                                        </i>
<i>     │ ▼         │ │                                                        </i>
<i>     └───view-id─┴─┘ </i>
</pre>
Note: If INPUT_TYPE=DB2, then both the DBVIEWS file and the DBFLDRS file are read. A list of view numbers to process is then derived from the union of the two files. If both files are either empty or missing, then an error is returned.    

## Format: RUNVIEWS file
<pre>
<i>►►───┬─────────────┬───────────────────────────────────────────────────────────►◄</i>
<i>     │ ┌─────────┐ │                                                        </i>
<i>     │ ▼         │ │                                                        </i>
<i>     └───view-id─┴─┘ </i>
</pre>
Note: If the RUNVIEWS file is empty, all views are selected.  

## Description

*`server`*
The IP address or domain name of the database host system.

*`port`*
The port number identifying the database.

*`database-name`*  
This is the name of the Db2 database or Postgres database where your metadata resides.  
For Postgres, this is the name set in the dbname parameter at database creation e.g. dbname=genevaers.
  
*`db-schema`*    
This is the name of the database schema where your metadata resides. (For example, GENDEV.)  
For Postgres, this is the name set in schemaV at database creation.  (For example, schemaV=gendev.)  
  
*`environment-id`*    
This is the ID of the GenevaERS environment where the GenevaERS views to be selected reside.
    

