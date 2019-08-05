# HTML/CSS

Agenda:-
1. HTML -> v5
2. CSS -> v3
3. Connect HTML to Python via CGI
4. Interface -> Web -> Desktop Server (For Making it Interactive)


## HTML

* HTML is a upgraded version of MS Office but it is browsable

refresh the page after 3 seconds to the given URL; 3= no. of seconds

```
<meta http-equiv="refresh" content="3" ;url=https://www.google.com />
```
For comment in html
```
<--

-->
```
iframe tag= for inserting a page into a page, or you can put a image or a video
```
<iframe src="index.html" height="500" width="700"> 

</iframe>
```

User Input
```
<FORM>
<input type=date> </input>

<input  name="x"> # Saving a variable which is visible in URL

<input type"text" name="y" placeholder="Enter your name"> # placeholder=> inputs the text into the box

<input type="number">

<input type="radio" name="n" value="python"> python <br/>
<input type="radio" name="n" value="Go"> Go    <br/>
<input type="radio" name="n" value="Java"> Java  <br/>
# value attribute sends the value of selected button to the backend data

<input type="checkbox" name="a"> ML <br/>
<input type="checkbox" name="b"> CLOUD <br/>
<input type="checkbox" name="c"> AI <br/>
# For selecting multiple options using checkboxes

<textarea   name="s" cols="50" rows="15">
Type Here
</textarea>
# name has the variable "s" which includes the value of the box; cols and rows defines the size of box in terms of rows and columns


<input  type="submit"
>


</FORM>
```
CGI = Common Gateway Interface => Its is driver  user for integrating(communication) between backend(Python, JAVA) and Apache Server



Remove the color of the terminal output
```
unalias ls
```

Making backend:-

```/var/www/cgi-bin```

```cmd.cgi```
```
#!/usr/bin/python3

import cgi
import cgitb
# to show common error in webbrowser
cgitb.enable()

print("Content-type:text/html")
print("")

webdata=cgi.FieldStorage() # this will collect all the html code with data

# Now extracting value of x
data=webdata.getvalue('x')

# Sending output to client via web server
print(data)

```
```
chmod +x cmd.cgi
```
* **Always set selinux to disabled for CGI**

setting up the html file for CGI
```
<FORM action="/cgi-bin/cmd.cgi">

</FORM>
```
```For seeing the error```
```
tailf /var/log/httpd/error_log
```

For inserting the command of terminal in text box [insert code in same file as previous]
```
import subprocess

output=subprocess.getoutput(data)
print(output)
```

for inserting any output into a HTML tag
```
import subprocess

output=subprocess.getoutput(data)
print("<h1>")
print(output)
print("</h1>")
```

for not showing the data of variable in URL
```
<Form method="POST">

</form>
```


```pre``` tag shows the original format of command output
```
print("<pre>")
print(output)
print("</pre>")
```

For executing sudo commands with CGI:-

```cd /etc/sudoers.d/```

```vi 90-cloud-init-users```

add this command in file for making apache a sudo user
```
apache ALL=(ALL) NOPASSWD:ALL
```

For installing apache in UBUNTU
```
apt-get install apache2
```
activate CGI for UBUNTU only
```
a2enmod cgi
```