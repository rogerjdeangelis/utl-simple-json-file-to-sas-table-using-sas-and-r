# utl-simple-json-file-to-sas-table-using-sas-and-r
Simple json file to sas table using sas and r
    Simple json file to sas table using sas and r                                                                      
                                                                                                                       
    Much of the R code is to input and output from SAS                                                                 
                                                                                                                       
    github                                                                                                             
    http://tinyurl.com/y2fd46zn                                                                                        
    https://github.com/rogerjdeangelis/utl-simple-json-file-to-sas-table-using-sas-and-r                               
                                                                                                                       
    SAS Forum                                                                                                          
    http://tinyurl.com/y48rw334                                                                                        
    https://communities.sas.com/t5/SAS-Programming/Parse-JSON-Iin-SAS-dynamically-using-keynodes-and-values/m-p/548498 
                                                                                                                       
    github (other json repos)                                                                                          
    http://tinyurl.com/yyntqsw6                                                                                        
    https://github.com/rogerjdeangelis?utf8=%E2%9C%93&tab=repositories&q=in%3Aname+json&type=&language=                
                                                                                                                       
    *_                   _                                                                                             
    (_)_ __  _ __  _   _| |_                                                                                           
    | | '_ \| '_ \| | | | __|                                                                                          
    | | | | | |_) | |_| | |_                                                                                           
    |_|_| |_| .__/ \__,_|\__|                                                                                          
            |_|                                                                                                        
    ;                                                                                                                  
                                                                                                                       
    * create json file;                                                                                                
                                                                                                                       
    filename ft15f001 "d:/json/easy.json";                                                                             
    parmcards4;                                                                                                        
    {"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}                                               
    ;;;;                                                                                                               
    run;quit;                                                                                                          
                                                                                                                       
                                                                                                                       
    d:/json/easy.json                                                                                                  
    {"name":"John","surname":"Doe","age":45,"skills":["SQL","C#","MVC"]}                                               
                                                                                                                       
    *                                                                                                                  
     _ __  _ __ ___   ___ ___  ___ ___                                                                                 
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                
    | .__/|_|  \___/ \___\___||___/___/                                                                                
    |_|                                                                                                                
    ;                                                                                                                  
                                                                                                                       
    %utl_submit_r64('                                                                                                  
       library(rio);                                                                                                   
       library(SASxport);                                                                                              
       library(data.table);                                                                                            
       want<-as.data.table(as.list(import("d:/json/easy.json"))[1:3]);                                                 
       write.xport(want,file="d:/xpt/want.xpt");                                                                       
     ');                                                                                                               
                                                                                                                       
                                                                                                                       
    libname xpt xport "d:/xpt/want.xpt";                                                                               
    data want;                                                                                                         
      set xpt.want;                                                                                                    
    run;quit;                                                                                                          
    libname xpt clear;                                                                                                 
                                                                                                                       
    *            _               _                                                                                     
      ___  _   _| |_ _ __  _   _| |_                                                                                   
     / _ \| | | | __| '_ \| | | | __|                                                                                  
    | (_) | |_| | |_| |_) | |_| | |_                                                                                   
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                  
                    |_|                                                                                                
    ;                                                                                                                  
                                                                                                                       
    Up to 40 obs from WANT total obs=1                                                                                 
                                                                                                                       
    Obs    NAME    SURNAME    AGE                                                                                      
                                                                                                                       
     1     John      Doe       45                                                                                      
                                                                                                                       
                                                                                                                       
                                                                                                                       
