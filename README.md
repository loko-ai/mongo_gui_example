<html><p><a href="https://loko-ai.com/" target="_blank" rel="noopener"> <img style="vertical-align: middle;" src="https://user-images.githubusercontent.com/30443495/196493267-c328669c-10af-4670-bbfa-e3029e7fb874.png" width="8%" align="left" /> </a></p>
<h1>Mongo GUI</h1><br></html>

**Mongo GUI** example shows how to integrate your extensions with side containers and relative GUIs (e.g. <a href="https://hub.docker.com/_/mongo">mongo</a> and <a href="https://hub.docker.com/r/ugleiton/mongo-gui">mongo-gui</a>).

From the **Projects**'s tab, click on **Import from git** and copy and paste the URL of the current page 
(i.e. https://github.com/loko-ai/mongo_gui_example):
<p align="center"><img src="https://user-images.githubusercontent.com/30443495/229048981-e03d7b6f-6ef4-4064-8c0e-75052497744a.png" width="60%" /></p>

Once the project is downloaded, click and open it.  In order to start the project remember to press the **play** button on the right of the project's name.
<p align="center"><img src="https://user-images.githubusercontent.com/30443495/229157740-30adb35e-b372-4ba6-be63-c5a75a7b1530.png" width="80%" /></p>

You can click on **mongo gui** to open the GUI.

<p align="center"><img src="https://user-images.githubusercontent.com/30443495/229158332-2e21f448-ff63-42dc-8074-37b34effde9a.png" width="80%" /></p>

Let's now see how to custom the extension (See more here <a href="https://github.com/loko-ai/loko/wiki/Custom-extensions">Custom extensions</a>). 

Click right on the project's name on *Open in editor* (configure your editor using the Loko's settings first):
<p align="center"><img src="https://user-images.githubusercontent.com/30443495/229159066-637ea788-6efe-42ba-9426-0c18a7f1e1c2.png" width="80%" /></p>

Otherwise, you can open your project directly on the Loko's directory (i.e. `~/loko/projects/mongo_gui_example`).

### Config

Now we have to configure the needed side containers in `mongo_gui_example/config.json`: 

```
{
  "side_containers": {
    "mongo": {
      "image": "mongo",
      "ports": {
        "27017": null
      }
    },
    "mongo_gui": {
      "image": "ugleiton/mongo-gui",
      "ports": {
        "4321": null
      },
      "environment": {
        "MONGO_URL": "mongodb://mongo_gui_example_mongo:27017"
      },
      "expose": [
        4321
      ],
      "gui": {
        "name": "mongo gui",
        "path": "/",
        "gw": false
      }
    }
  }
}
```

Here we set the mongo-gui as the extension's GUI and name it **mongo gui**.


When you **stop** your project and click again on the **play** button, Loko starts the needed containers, and you're ready to use 
your extension. 
