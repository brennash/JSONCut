# JSONCut
A version of the Linux cut command for multi-part JSON files.<br>
Last updated 11th November 2015.

## Description
This package is an implementation in Python of the JSON cut command, 
with a few special tweaks. JSON is specifically designed so as not to have 
a particular ordering of key value pairs. However, for most applications the
output of many lines of JSON tends to retain some ordering in what keys/values 
come in what order. 

This application offers to print out the values of a specified key, or it's
typical index, in a text file containing multiple similar JSON records. So, 
in the case of something like

```json
{"keyname1":"value1","keyname2":123}
{"keyname1":"value2","keyname2":124}
```
Executing the script on field 1 would output

```
./jc -f1 myjsonfile.json
value1
value2
```

And executing the script on the keyname2 key would result in 

```
./jc -k'keyname2' myjsonfile.json
123
1234
```

It's not ideal, it's a bit buggy but it's very handy doing a cut-style 
command directly on JSON. 

## Parameters
-l,--list   Lists all the common keys for each JSON object in the file
-u,--unique Lists all the keys only found on one line, and the line number/character position
-k,--keys   Prints out the values for specified keys, on each line they're found.
-f,--fields Prints out the values associated with an index, i.e., a particular key in order.
