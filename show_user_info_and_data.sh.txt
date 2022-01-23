#!/bin/bash                                          
                                                     
#check args                                          
if [ "$#" -ne 2 ]; then                              
    echo "No args found."                            
    exit                                             
fi                                                   
                                                     
user=$1                                              
path=$2                                              
exit_status=0                                        
                                                     
#check user                                          
if [ $user == "root" ]; then                         
    exit_status=42                                   
    echo "Finding 'root' user data is not allowed!"  
    echo "error exit code $exit_status"              
    exit                                             
fi                                                   
                                                     
cls||clear   
#find files                            
for i in $(find $2 -user $1)           
do                                     
echo "$i is found!"                    
done                                   
                                       
#file count                            
echo -n "Total: "                      
find $path -user $user | wc -l         
                                       
#pid                                   
ps -u $user -o pid,user,command                                                