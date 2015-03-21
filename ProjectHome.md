This application aims to make it super simple to create a mobile website in nothing but python!  We do all of the hard work for you with [Jquery Mobile](http://jquerymobile.com) :)

# An example #

![http://osucabs.com/static/images/example.png](http://osucabs.com/static/images/example.png)

# Lets Get Started! #

### Check out the code ###
```
hg clone https://pymobli.googlecode.com/hg/ pymobli 
cd pymobli
```
### Get project requirements ###
```
pip install -r requirements.txt
or 
pip install web.py
or
easy_install web.py
```
Awesome, you're good to go now!

## Create a new file ##
**Note if you're impatient, just go check out example.py**

**In your favorite editor create a new file index.py with this:**

```
#!/usr/bin/env python
from pymobli import Page, Button, Title, Link, Button, ButtonGroup, Inline, List
import web
urls = (
    '/', 'index',
)
app = web.application(urls, globals())
render = web.template.render('html/')

class index:        
    def GET(self):

        page = Page("Example Page Title")

        page.header.add(Button(title="Back",href="#", icon="arrow-l", theme="e"))
        page.header.add(Title(title="Example Page"))
        page.header.add(Link(title="Yahoo",href="http://www.yahoo.com"))

        l  = List(inset="true")
        ## Link definitions
        l.add(Link("OHIO STATE","http://osu.edu"))
        l.add(Link(title="Google",href="http://www.google.com"))
        d = {"title":"My Blog", "href":"http://patrickshuff.com"}
        l.add(Link("Broken Link"))
        l.add(Link(**d))
        page.content.append(l)

        l  = List(inset="true")
        l.add(Link("OHIO STATE","http://osu.edu"))
        l.add(Link(title="Google",href="http://www.google.com"))
        d = {"title":"My Blog", "href":"http://patrickshuff.com"}
        l.add(Link("Broken Link"))
        l.add(Link(**d))
        page.content.append(l)

        page.content.append(Button("This is a button","http://jquery.com"))

        page.content.append(Button('This is an "a" themed button',"http://jquery.com", theme="a"))
        page.content.append(Button('This is a "b" themed button',"http://jquery.com", theme="b"))
        
        b = ButtonGroup()
        b.add(Button("This is a button group","http://jquery.com"))
        b.add(Button("Boom","http://boom.com"))

        page.content.append(b)

        b = ButtonGroup(style="horizontal")
        b.add(Button("Yes", theme="e"))
        b.add(Button("No"))
        b.add(Button("Maybe"))
        page.content.append(b)

        b = ButtonGroup(style="horizontal")
        b.add(Button("Up", icon="arrow-u"))
        b.add(Button("Down", icon="arrow-d"))
        b.add(Button("X", icon="delete"))
        page.content.append(b)

        return render.generic(page)

if __name__ == "__main__":
    app.run()


```
### Now run it!! ###
```
python index.py
```

Now point your browser to http://localhost:8080

**Whoa, you already created a basic page....sweet!!**