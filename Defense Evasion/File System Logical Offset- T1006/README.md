# File System Logical Offsets- T1006

## Technique Description
Windows allows programs to have direct access to logical volumes. Programs with direct access may read and write files directly from the drive by analyzing file system data structures. This bypasses techniques Windows file access controls as well as file system monitoring tools. 
To demonstrate this technique we are going to use Powersploit’s Invoke-ninjacopy command. 
## Assumption
NinjaCopy should be able to copy files that are specified. 
#Execution

#Detection
