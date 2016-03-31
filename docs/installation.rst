============
Installation
============

Install the package with pip::

    $ pip install read-the-docs-template


this is a test:


ESP8266 BASIC Language Reference
BASE COMMANDS (Basic Core)
IF .. THEN:
LET:
Logic Operators:
Math Operators:
GOTO:
GOSUB AND RETURN:
FOR ... NEXT loops:
BRANCH LABELS:
PRINT:
SERIALPRINT:
SERIALPRINTLN:
BAUDRATE:
INPUT:
SERIALFLUSH:
SERIALTIMEOUT:
LOAD:
Timers And Interrupts
TIMER:
SLEEP:
REBOOT:
INTERRUPT:
FILE I/O
READ:
WRITE:
HARDWARE INTERFACE COMMANDS
PO:
PI:
PWO:
PWI:
SERVO:
AI:
LASTSTAT:
TEMP:
delay:
OLED & LCD DISPLAY COMMANDS
OLEDPRINT:
OLEDCLS:
OLEDSEND:
LCDPRINT:
LCDCLS:
LCDBL:
LCDSEND:
FUNCTIONS (NEOPIXEL WS2812)
NEO():
NEOCLS():
neostripcolor():
WEB INTERFACE COMMANDS
CLS:
WPRINT:
WPRINT with htmlvar() function:
IMAGE:
JAVASCRIPT:
CSS:
BUTTON:
IMAGEBUTTON:
TEXTBOX:
PASSWORDBOX:
SLIDER:
DROPDOWN:
LISTBOX:
ONLOAD:
WAIT:
HTMLID():
WEB MSG HANDLER COMMANDS
MSGBRANCH:
MSGGET:
MSGRETURN:
SMTP EMAIL COMMANDS
SETUPEMAIL:
EMAIL:
GRAPHICS COMMANDS
GRAPHICS
GCLS:
LINE:
CIRCLE:
ELLIPSE:
RECT:
Color pallet
WIFI COMMANDS
CONNECT:
AP:
WIFIOFF:
WIFI.SCAN():
WIFI.SSID():
WIFI.RSSI():
FUNCTIONS (THINGSPEAK API)
SENDTS:
READTS:
FUNCTIONS String
len():
instr():
mid():
left():
right():
replace():
chr():
asc():
upper():
lower():
id():
json():
FUNCTIONS (Numeric)
sqr():
sin():
cos():
tan():
log():
rnd():
millis():
int():
oct():
hex():
ramfree():
flashfree():
FUNCTIONS (Time&Date)
time():
timesetup():
FUNCTIONS (Web Related)
wget():
ip():
FUNCTIONS I2C
i2c functions:
i2c.begin():
i2c.write():
i2c.end():
i2c.requestfrom():
i2c.available():
i2c.read():
BASE COMMANDS (Basic Core)

IF .. THEN:

The if then command will compare 2 values or variables.
To check if strings are equal to each other use ‘==’, for numbers use ‘=’.
if {var or value} {=, ==,>,<,<>,>=,<=}, {var or value} then {statement to be executed if true} {else} {Statement if false}
LET:

Let will perform math or string operations on a set of values or variables and place the result in to a variable.
To ad strings together you must use the ‘&’ symbol instead of the ‘+’
Can also be used to evaluate logic operations like in the if then statement. If the result is true it will return a 1 otherwise a 0
let {Result var} = {value or var} {operator *,/,+,-,^,&} {value or var}
let {Result var} = {value or var} {=, ==,>,<,<>,<=,>=} {value or var}
Can also be used with out the let statement
bla = 5 + 5

Logic Operators:

Math Operators:

=  Equal for numbers
==  Equal for strings
> More than
< less than
<> Not Equal
>= more than or equal
<= less than or equal
+ Add (Numbers Only)
- Subtract
* Multiply
/ Divide
^ To the power of
& Add (Text)

GOTO:

Will jump to the branch label of your choice
goto {label}
GOSUB AND RETURN:

Will jump to the branch label of your choice and allow you to return to the location you call the gosub from and continue executing code after the return command is executed. The gosub command has a stack of 255 return points so it is possible to gosub from inside a gosub.
gosub {label}
return
FOR ... NEXT loops:

A for ... next loop will loop x number of times.
For x = 1 to 5;
Print x;
Next x
BRANCH LABELS:

A branch label allows you to jump from one part of the program to another. It can be a single string of characters with no spaces.
{label} (branch labels like in qbasic. No colon required)
PRINT:

Will output text or a variable to the serial interface and the browser with a new line.
print {value or var}
SERIALPRINT:

Will output text or a variable to the serial interface only. No new line or added.
serialprint {value or var}
SERIALPRINTLN:

Will output text or a variable to the serial interface only. Will terminate with a new line.
serialprintln {value or var}
BAUDRATE:

Will set the baudrate for serial communications.
baudrate {value or var}
INPUT:

Will request input via serial from the user and place it in to a variable. Variable dose not need to be declared prior to request.
input {optional string or var to display in prompt} {value or var}
SERIALFLUSH:

Will clear the serial input buffer. Discards all characters stored in the buffer.
serialflush
SERIALTIMEOUT:

Will cause the input command to return what ever is in the serial  buffer even if there is no CR LF. Specifying a value of 0 will disable the serial time out. Any non-zero value will be the number of milliseconds it will wait before timing out on an input command.
serialtimeout {value or var}
LOAD:

Will load another basic program in to memory. Useful for chaining programs together.
Will load other program in to memory and start executing it from the beginning.
All variables previously used will stay in memory and be available to the program that is loaded.
Useful for breaking a project up. ex. 
​LOAD "\myscript.bas"  or LOAD "\uploads\myscript.bas"
load {other program name}
Timers And Interrupts

TIMER:

The Timer command will allow you periodically run a branch. The branch must end with the wait command. Setting the timer to 0 will disable it.
To Set timer:
timer {string or var for wait time in milliseconds}, {branch label}
To Disable timer:
timer 0
SLEEP:

Will put device to sleep for a number of seconds. This will save power and allow for extended use on batteries.
Things to note. Sleep mode will cause a full reboot of the device. It will start the device and run the default program from the beginning. It takes 30 seconds before the device starts the default program after reboot.
GPIO16 needs to be tied to RST to wake from Sleep.
sleep {value or var in seconds}
REBOOT:

Will reboot the device upon execution.
reboot
INTERRUPT:

Will execute a specific branch when a pins status changes. The interrupt polling only occurs when the esp is waiting and useful for things like push buttons trigger events. The branch must end with the wait command.
interrupt {pin no} {branch label}
to disable an interrupt specify no branch label.
interrupt {pin no}
FILE I/O

READ:

The read command allows you to retrieve information persistently stored in the flash memory of the ESP8266 module.
read {string or var for name of data element} {Var to place contents of data element in to}
WRITE:

The write command allows you to persistently store a data element in flash memory.
write {string or var for name of data element} {Var or sting to write to data element}
HARDWARE INTERFACE COMMANDS

For i2c functions see here.
PO:

po allows you to set pin on the esp high or low
po {pin no value or var} {value or var 1/0}
alternative as function
io(po,{pin},{value})
PI:

Will place the high or low status of a pin in to the variable chose.
Useful for reading push buttons and other electronic inputs.
pi {pin no} {var to place result 1/0}
alternative as function
io(pi,{pin})
PWO:

pwo allows you to set pin on the esp for PWM output
pwo {pin no value or var} {value or var}
alternative as function
io(pwo,{pin},{value})
PWI:

Will place pwm input status of a pin in to the variable chose.
Useful for reading push buttons and other electronic inputs.
pwi {pin no} {var to place result in}
alternative as function
io(pwi,{pin})
SERVO:

Will set the angle of a servo connected to the the pin.
Angle must be between 0 and 180.
servo {pin no} {value or var 0 to 180}
alternative as function
io(servo,{pin},{value})
AI:

Analog input is only available on the pin marked "ADC" on the ESP-12.
Useful for retrieving input from photo resistors and other devices.
ai {var to place result in}
LASTSTAT:

This will return the last polled status of a pin such as an interrupt and retain the value until it has changed again in another polling event. Also it will allow you to see the last value sent to a pin for servo, pwm or po.
io(laststat,{pin no})
TEMP:

Will retrieve temperature sensor reading from certain 1 wire devices connected to pin 2. See example here
temp {Device ID} {Variable name to place data in to}
delay:

Will wait for a number of milliseconds before continuing execution.
Useful for making leds blink
delay {Var or value}
OLED & LCD DISPLAY COMMANDS

For i2c functions see here.
I2C pins are 0 and 2. On NodeMCU boards they are labeled as D3 and D4.
OLEDPRINT:

Will print to the OLED display at specified position. X postion for edge of display will differ for some models.
oledprint {String or var} {x position value or var} {y position value or var}
OLEDCLS:

Will clear the screen.
oledcls
OLEDSEND:

Will send a value to the display. This is for sending native commands and requires a byte as a number. Refer to OLED display command documentation from manufactures spec.
oledsend {Value or var}
1602 LCD COMMANDS
LCDPRINT:

Will print to the OLED display at specified position. X postion for edge of display will differ for some models.
lcdprint {String or var} {x position value or var} {y position value or var}
LCDCLS:

Will clear the screen.
lcdcls
LCDBL:

Will turn the back light on or off. 1 for on, 0 for off.
lcdbl {value or var}
LCDSEND:

Will send a value to the display. This is for sending native commands and requires a byte as a number. Refer to LCD display command documentation from manufactures spec.  MODE: 0=COMMAND, 1=DATA, 2=FOUR_BITS
lcdsend {Value or var to send} {Value or Var for mode}
FUNCTIONS (NEOPIXEL WS2812)

To use NEO Pixel strips you must connect the signal to pin 15, D8 for node mcu boards.
NEO():

Will set the desired pixel led to the color specified with an RGB (Red, Green, Blue) value.
neo({LED NO},{R},{G},{B})
NEOCLS():

Will turn off all the leds on the strip.
neocls()
neostripcolor():

Will set a range of leds to the desired color.
neostripcolor({start pixel},{end pixel},{R},{G},B})
WEB INTERFACE COMMANDS

CLS:

Will clear the screen and GUI buffer
cls
WPRINT:

Will print text to the browser. Text will be sent to the browser upon the wait command. Note that there is no new line after it is printed so you must add html to create a new line or horizontal rule.
wprint {value or var}
WPRINT with htmlvar() function:

To place a dynamic variable that will update on each refresh of the page with the current contents of that variable use the htmlvar function.
Each time browser is refreshed the latest contents of the variable are place in the page.
wprint htmlvar({var name})
IMAGE:

Will insert an image in to the web page. Image file should be uploaded to device using the file manager.
image {image file name}
JAVASCRIPT:

Will allow you to include javascript files in your page. File must be uploaded to the device using the file manager.
javascript {filename}
CSS:

Will allow you to include css files in your page. File must be uploaded to the device using the file manager.
See the CSS example here.
css {filename}
BUTTON:

Functions like a goto command. Will be sent to the browser on the wait command.
Will goto the branch label when clicked in the browser
button {value or var} {Branch Label}
IMAGEBUTTON:

Functions like a goto command. Will be sent to the browser on the wait command.
Will goto the branch label when clicked in the browser. The image file must be uploaded to the device using the file manager.
imagebutton {image file name} {Branch Label}
TEXTBOX:

The text inside the text entry filed will be what ever is in the variable.
Will be displayed in the browser on the wait command
textbox {var name}
PASSWORDBOX:

The text inside the password entry filed will be what ever is in the variable.
Will be displayed in the browser on the wait command
passwordbox {var name}
SLIDER:

The slider will be created with a maximum and minimum value.
slider {Var name} {min value} {max value}
DROPDOWN:

The selected item will be placed in to the variable.
dropdown {Item list seperated by commas} {var name}
example
dropdown "One,Two,Three" bla
LISTBOX:

The selected item will be placed in to the variable.
listbox {Item list seperated by commas} {var name} {Height in items}
example
listbox "One,Two,Three" bla 5
ONLOAD:

Optional branch to be executed any time a page is loaded from the device. This code will be executed before the page is returned but after any branches for buttons. Branch must terminate with wait command.
onload {branch label}
WAIT:

Sends all the accumulated gui commands to the browser.
The browser will display once this command is run
wait
HTMLID():

The html id function will return the randomly generated id for the last gui object created. Useful for javascript interaction capabilities.
htmlid()
WEB MSG HANDLER COMMANDS

Msg handler events will only be  handed when there is a request t the url http://device ip/msg is used.
Se example /msg-url-usage.html for more information.
MSGBRANCH:

Will set the branch for handling msg input urls. This branch will exicute when the url "ESP-IP-address/msg" is accessed.
msgbranch {branch label}
MSGGET:

Will retrieve a url argument and place it in a variable.
msgget {url arg} {variable name}
Example:
Will retrieve the url argument "color" and place it in to myColorVar
Use browser to access "ESP-IP-address/msgcolor=blue"
msgget "collor" myColorVar
MSGRETURN:

Will set the text to be returned by the browser. No additional html is provide. Will over write previous return text if called more than once. Text will be returned when interpreter encounters the  wait command.
msgreturn {variable name or string for return}
SMTP EMAIL COMMANDS

You will need an SMTP server such as http://www.smtp2go.com/
SMTP Server: mail.smtp2go.com
Port: 2525
For sending sms message to phones look up your criers sms gateway.
http://martinfitzpatrick.name/list-of-email-to-sms-gateways/
SETUPEMAIL:

Will configure the email server. Requires the server, port, user name and password.
setupemail {String for server} {Value for port} {String for user name} {String for password}
EMAIL:

Will send an email using the from and to address using the subject and body.
email {String To email} {String From Email} {String Subject} {String Body}
GRAPHICS COMMANDS

Colors are optional. If no color is specified it will default to black
For examples you can look at /graphics-example.html and /graphic-clock-example.html
GRAPHICS

Adds a graphics element to the page
Each parameter can be a variable or a value.
graphics {width} {height}
GCLS:

Will clear the graphics buffer.
gcls
LINE:

Creates a line in the graphic element
Each parameter can be a variable or a value.
line {x1} {y1} {x2} {y2} {color}
CIRCLE:

Creates a circle in the graphic element
Each parameter can be a variable or a value.
circle {x1} {y1} {radius}  {color}

ELLIPSE:

Creates a ellipse in the graphic element
Each parameter can be a variable or a value.
ellipse {x1} {y1} {radiusX} {radiusY} {color}
RECT:

Creates a rectangle in the graphic element
Each parameter can be a variable or a value.
rect {x1} {y1} {radiusX} {radiusY} {color}
Color pallet

0 = Black
1 = Navy
2 = Green
3 = Teal
4 = Maroon
5 = Purple
6 = Olive
7 = Silver
8 = Gray
9 = Blue
10 = Lime
11 = Aqua
12 = Red
13 = Fuchsia
14 = Yellow
15 = White
WIFI COMMANDS

CONNECT:

Will connect you to the wifi network using the ssid and password. Optionally you may specify the ip ADDRESS, Gateway and sub net mask for a static ip.
connect {Var or String for SSID} {Var Or String for password}
Static ip:
connect {Var or String for SSID} {Var Or String for password} {ip var or sting} {gateway var or sting}  {netmask var or sting}
 
AP:

Will create an acces point with the name and password you specify.
If the password is not specified it will be an open network.
ap {Var or String for SSID} {Var Or String for password}
WIFIOFF:

Will turn of all networking for sta and ap mode. The WiFioff command can be called in order to disable all networking. The ap or connect command if run after WiFioff will activate that particular WiFi mode. You can turn them both back on at any point with each of there commands.
wifioff
WIFI.SCAN():

Will return the number of available wifi networks. See an example here.
wifi.scan()
WIFI.SSID():

Returns the network name for the selected network. See an example here.
Must run a wifi.scan() first.
wifi.ssid({Var for network number})
WIFI.RSSI():

Returns the signal strength for the selected network. See an example here.
Must run a wifi.scan() first.
wifi.rssi({Var for network number})


FUNCTIONS (THINGSPEAK API)

To get started with thing speak visit there web site at https://thingspeak.com/
You need to have an account and channel/api key all set up.
These functions will only work if the esp is connected to a network with the internet.
SENDTS:

Will post the fields contents to the thingspeak service. Must use the thingspeak key and filed number.
SENDTS({KEY},{FILED NUMBER},{FIELD CONTENTS})
READTS:

Will return the last value published for the desired field. Must use the thingspeak key, channel id and filed number.
readts({KEY},{CHANNEL ID},{FIELD NUMBER})
FUNCTIONS String

Functions can be called in place of variables and will typically return value.
Function names are not case sensitive. ie. LeN() and len() are both valid
NOTE: No spaces should be used in side a function. Only commas if there are multiple values to be parsed.
let bla = len("hello world") is ok
let ble = len(   "hello world"   ) is not ok.
String  Functions:
len():

Will return the length of the string
len({string or var name})
instr():

Will return location of a sub string within a string.
len({string or var name},{string or var name to locate})
mid():

Will return the string from the start position to the end position inside of the input string.
mid({string or var name},{Start position},{number of characters})
left():

Will return the string left of the start position.
left({string or var name},{Start position})
right():

Will return the string right of the start position.
right({string or var name},{Start position})
replace():

Will return a string after replacing the search text with the replacement text.
replace({string or var name},{string to search for},{replacement for string})
chr():

Will return a character for the given number.
chr({string or var name})
asc():

Will return a number for the first character in a string.
asc({string or var name})
upper():

Will return the supplied sting in UPPERCASE.
upper({string or var name})
lower():

Will return the supplied sting in lowercase.
lower({string or var name})
id():

Will return the unique id of the chip.
id()
json():

Will parse a json string for the articular named data element within it.
json({string or var name for data to be parsed},{string or var name for key name in data})
FUNCTIONS (Numeric)

 
Search
FUNCTIONS
Functions can be called in place of variables and will typically return value.
Function names are not case sensitive. ie. LeN() and len() are both valid
NOTE: No spaces should be used in side a function. Only commas if there are multiple values to be parsed.
let bla = len("hello world") is ok
let ble = len(   "hello world"   ) is not ok.
Math Functions:
sqr():

Will return the square root.
sqr({value or var name})
sin():

Will return the sign of an angle.
sin({value or var name})
cos():

Will return the cosign of an angle.
cos({value or var name})
tan():

Will return the tangent of an angle.
tan({value or var name})
log():

Will return the log of the provided value.
log({value or var name})
rnd():

Will return a random number up to the value set.
rnd({value or var name})
millis():

Will return number of milliseconds since boot time.
millis()
int():

Will return an integer value.  
int({string or var name})
oct():

Will return the oct value of an integer.  
oct({string or var name})
hex():

Will return the hex value of an integer.  
hex({string or var name})
ramfree():

Will return the amount of ram free in bytes.  
ramfree()
flashfree():

Will return the amount of flash free in bytes. This is only applicable to flash designated for the file system.
flashfree()
FUNCTIONS (Time&Date)

 
FUNCTIONS
Functions can be called in place of variables and will typically return value.
Function names are not case sensitive. ie. LeN() and len() are both valid
NOTE: No spaces should be used in side a function. Only commas if there are multiple values to be parsed.
let bla = len("hello world") is ok
let ble = len(   "hello world"   ) is not ok.
Time and date functions:
time():

Will return the date and time as a string.  You can optionally specify the format you want it back in.
Options: month, date, hour, min, sec, year, dow (Day of the week, ex. fri)
time({Optional specification of format})
with an option.
time("year")
timesetup():

Will set up the time time zone and daylight savings attribute.
timesetup({number or var for time zone},{number or var for dst})
FUNCTIONS (Web Related)

 
Search
FUNCTIONS
Functions can be called in place of variables and will typically return value.
Function names are not case sensitive. ie. LeN() and len() are both valid
NOTE: No spaces should be used in side a function. Only commas if there are multiple values to be parsed.
let bla = len("hello world") is ok
let ble = len(   "hello world"   ) is not ok.
Internet functions:
wget():

Will fetch the html contents of a web page and return it as a string.
Do not put "http://" in front of the url. Defaults to port 80 if none is specified. 
wget({String or var name for url},{Optional port number})
ip():

Will return the units ip address as a string.
ip()
FUNCTIONS I2C

Functions can be called in place of variables and will typically return value.
Function names are not case sensitive. ie. LeN() and len() are both valid
NOTE: No spaces should be used in side a function. Only commas if there are multiple values to be parsed.
let bla = len("hello world") is ok
let ble = len(   "hello world"   ) is not ok.
i2c functions:

For more information on usage look at this example.
i2c.begin():

Will begin transmission to the I2C device with desired address.
i2c.begin({value or var for device address})
i2c.write():

Will write a single value (1 character) to the i2c device.
i2c.write({value or var for data})
i2c.end():

Will terminate the i2c contamination with a particular device.
i2c.end()
i2c.requestfrom():

Will request a quantity of bytes from  device.
i2c.requestfrom({value or var for device id},{value or var for number of bytes to request})
i2c.available():

Returns the number of bytes available for retrieval with i2c.read().
i2c.available()
i2c.read():

Will return a single character as an integer. Character returned will be next out of buffer.
i2c.read()