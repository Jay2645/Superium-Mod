This project is intended to demonstrate making mods for Superium.

Bad news: It requires you to at least know the basics of the Unreal Engine 4 editor. You don't need to dive into code or anything (unless you want to!), but the problem with Unreal Engine 4 is that there's no "simple" way to add mods.

## How it works

So, here's how the game is laid out:

```
GAME FOLDER
-- Engine
---- Stuff we don't care about
-- Superium
---- Content
------ Paks
-------- A bunch of .pak files
-------- A couple <FILENAME>-AssetRegistry.bin files
-- Superium.exe
```

Inside that `Paks` folder are a few .pak files. Each one of these represents a bunch of "cooked" content. These are models, blueprints, code, etc. that are included inside the game. Any DLC is also another .pak file, and any mods are more .pak files! To make a mod, all you have to do is create one of these .pak files, add it to this folder, and the game will automatically find it during startup.

This project contains a couple "example" mods, so you can get a feel for how things work.

## Making a mod

1. Clone this repository. It's already set up for your mod, including links to the Superpower code in the Plugins folder. If you want to make a project from scratch, ensure that you call your project "Superium" -- using *any* other name will cause the game to not "know" about your mod! If making a project from scratch, also ensure that your .uproject name is `superium.uproject`.

2. Create a new Unreal Engine 4 plugin using Edit -> Plugins. This will contain *everything* inside your mod. If you don't want to add any C++ code, just create a "Content Only" plugin. If you need code, then use a Blank Plugin or whatever you want to do. Name the plugin whatever you want your mod to be called.

3. Place everything you need inside the `Content` folder in your plugin.

4. [Follow the instructions here](https://wiki.unrealengine.com/Modding:_Adding_mod-support_to_your_Unreal_Engine_4_project#MyFirstMod_Profile), under "MyFirstMod Profile." Feel free to skim the rest if you're confused as to what's going on, but all you need to do is to follow the directions under "MyFirstMod Profile." **NOTE:** There's a mistake in the tutorial! Make sure `Include Engine Content` is **CHECKED** when making your profile! Otherwise it'll fail.

5. Once your mod is ready, use the Project Launcher to launch the profile you created for your mod. It'll create a .pak file for you (check the log it outputs to see where -- usually it's under `Plugins/<MOD NAME>/Saved/StagedBuilds/WindowsNoEditor/Superium/Plugins/<MOD NAME>/Content/Paks/WindowsNoEditor/<MOD NAME>Superium-WindowsNoEditor.pak`.

6. Copy that .pak file into the game's `Superium/Content/Paks` folder.

7. Rename the .pak file to `<MOD NAME>.pak`. For example, a mod named ExampleMod would be called `ExampleMod.pak`.

8. Almost there! Now we need to grab the AssetRegistry for your mod, located in `Plugins/<MOD NAME>/Saved/Cooked/WindowsNoEditor/Superium/Plugins/<MOD NAME>/AssetRegistry.bin`.

9. Copy `AssetRegistry.bin` into that same `Superium/Content/Paks` folder.

10. Rename the `AssetRegistry.bin` file you just copied to `<MOD NAME>-AssetRegistry.bin`. Using the ExampleMod name above would create `ExampleMod-AssetRegistry.bin`.

11. All done! Boot up the game and see if your mod works!