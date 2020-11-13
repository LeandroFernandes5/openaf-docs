---
layout: default
title: "Beginner: Accessing object keys with spaces in OpenAF templates (Handlebars)"
parent: Guides
grand_parent: OpenAF docs
---

# Accessing object keys with spaces in OpenAF templates (Handlebars)

If you ever came across a similar JSON map to this:

````javascript
{
   "Update"      : "2019-08-24T12:34:56.789Z",
   "Stats"       : {
      "Memory stats": {
         "Free memory" : 1234,
         "Total memory": 5678
      }
   }
}
````

You know that to access JSON map keys with space in javascript you need to do something like this:

````javascript
print("Update: " + myMap.Update);
print("Free mem: " + myMap.Stats["Memory stats"]["Free memory"] + "MB");
````

To replicate in a [HandleBars](https://handlebarsjs.com) template you would write for the first line:

````html
Update: {{Update}}
````

But, how to access the keys with space in [HandleBars](https://handlebarsjs.com)?

````html
Update: {{Update}}
Free mem: {{Stats.[Memory stats].[Free memory]}}MB
````

So the final code would be, for example:

````javascript
tprint("Update: {{Update}}", myMap);
tprint("Free mem: {{Stats.[Memory stats].[Free memory]}}MB", myMap);
````