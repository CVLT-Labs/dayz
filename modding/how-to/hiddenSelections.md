## Understanding and Implementing Hidden Selections in DayZ Modding

**Overview**  
Hidden selections are a powerful tool in DayZ modding, enabling you to use a single model while applying multiple texture variations. This approach not only optimizes resource use but also adds versatility to your designs.

This guide provides clear, step-by-step instructions for defining hidden selections in your model and configuring the necessary `model.cfg` settings to ensure textures are applied successfully. Follow these steps to enhance your modding workflow and achieve the desired visual results.

This guide also assumes you have some basic prior knowledge of how to setup your DayZ mod structure. For more information on this, reference the [Modding Basics](https://community.bistudio.com/wiki/DayZ:Modding_Basics) section of Bohemia's documentation.

---

1. Import or open the model you'd like to define a hidden selection for in DayZ Tools > ObjectBuilder

![StepOne](https://i.imgur.com/kXc304M.png)
In the example screenshot above, we'll be using a very simple model for a bag of chips.

---

2. With your mesh selected in ObjectBuilder, **Right Click** in the Named Selection Panel and select **New**  


> **Note:** *You don't have to select the entire mesh if you only want to retexture part of it, just repeat step 2 for each part you want to apply a different texture to and give it a unique name. (ex: shoe, laces, sole, etc.)*  

![StepTwo](https://i.imgur.com/5uqhmwJ.png)
I'll be using the name "``camo``" which is commonly used in the DayZ Modding community for hiddenSelections in this example.

---

3. Now that we've named the part of the model we'd like to apply a custom texture to, save the file *(File > Save As)* as something identifiable, in my example I'll use ``rabblMods_SnackBag.p3d``.

![StepThree](https://i.imgur.com/q677WWK.png)
---

4. Navigate to the directory where you saved the .p3d file in step 3, and create a new file called ``model.cfg``.
> **Note:** *I recommend using an IDE (Integrated Development Environment) such as VSCode or Notepad++*


![StepFour](https://i.imgur.com/ir21nVP.png)
---

5. Copy/paste the snippet from the code block below inside the new file, and be sure to change the class to the exact name of your model.
> **Important:** *You **must** name the class identically to the name of the p3d you saved in step 3, otherwise it simply won't work.*  


```
class CfgModels {
    class Default {
        sections[] = {};
        sectionsInherit="";
        skeletonName = "";
    };

    class rabblMods_SnackBag : Default {       
        sections[] = {"camo"};
    };
};

class CfgSkeletons
{
};
```

---

6. Open your config.cpp in the base of your mod project structure and add the the lines below to your object class definition.

```
hiddenSelections[] = {"camo"};
hiddenSelectionsTextures[] = {"path\to\your\custom\texture\here.paa"};
```

![StepSix](https://i.imgur.com/a8wOeIN.png)
The screenshot example above is a snippet from my config.cpp definitions showing the relevant lines implemented.

---

7. Save your config.cpp, package your mod and enjoy your assigned hidden selections!
![StepSeven](https://i.imgur.com/KllW7OX.png)
