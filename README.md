# Procak_Szymon_RoutePloy.Py
Simple Drone Guidance System
A simple drone guidance system given by a coding scheme. The instructions for the assignment was to create a simple drone guidance system following specific instructions.
The program must run in Python3 without error.
The size of the grid to display is 12 x 12
The following route instruction files are provided: (these are provided in docx, you will need to convert these to txt files (using the Save As option in Word, and save as Plain Text (*.txt) )
Route001.txt, Route002.txt and Route003.txt
The format of the route instructions file is as follows:
Item 1: X-Coordinate of start of route
Item 2: Y-Coordinate of start of route
Item 3 onwards: N, S, E, or W
The program must output the completed route plot grid and the route coordinates, or the reason why the grid cannot be plotted (i.e., “Error: The route is outside of the grid”).
The route instruction files must be stored in the same path (as a .txt file not docx) as the program code and when the file is loaded, do not include the path (i.e. “open(‘Route001.txt’, …)”).
Refer to the Route Plot Guidance Notes for more details and example of the type of output format that is expected for the grid layout and coordinates.

Within the actual, code file various comments have been added by myself as there have been erros occuring due to the program not being able to read the route instruction
file that has been given.

Namely, the following syntax error:
coords = read_route_file(filename)
x, y = map(int, lines[0].split())
ValueError: not enough values to unpack (expected 2, got 1)


The erorr was raised because the map function is expecting two values to unpack but is getting only one. To rectify the issue, I have since modified the code 
and added some error handling with the following:

def_read_route_file(filename):
    with open(filename, 'r') as f:
    lines = f.readlines()
if len(lines) < 2:
print (f"Error: Invalid format in {filename}. File must have at least 2 lines")
return []

try:
   x, y = map(int, lines[0].split())
   directions = lines[1].strip()
except ValueError:
print(f"Error: Invalid format in {filename}. First line must contain two intergers separated by a space")
return []
