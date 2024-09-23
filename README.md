# Customizable Song Scripts (UD extension)

The song scripts in this extension to the [Unrestricted Difficulties](https://github.com/AppleHair/FNF-UnrestDiffs) framework contain special attributes which let you customize the script's default behavior without replacing it. This was used for preventing conflicts between multible mods that modify the same song script, but was later deprecated in favor of variation-specific song scripts. The attributes should be set using a module on `onCountdownStart` callback. For example, Here's a module that replaces senpai's conversation when the current variation is "b-side":

```haxe
import funkin.play.PlayState;
import funkin.modding.module.Module;

class senpaiBSideHandler extends Module {
	function new() {
		super('senpai-b-side-handler');
	}

    public override function onCountdownStart():Void {
        if (PlayState.instance.currentVariation != "b-side") {return;}

        switch (PlayState.instance.currentSong.id) {
        case "senpai":
            PlayState.instance.currentSong.scriptSet("conversationId", "senpai-B-sides");
        }
    }
}
```

To learn how to customize other song scripts, you should go look inside the scripts and see what they do and how they use each attribute. Attributes which are meant to be modified on `onCountdownStart` are using the public access modifier and are present in the highest part of the class block.

## Disclaimer

This system is deprecated in favor of a variation-specific song scripts system since UD v1.1.0. This was just a temporary solution to prevent conflicts between mods that modify the same song script and was made into an extension to allow backwards compatibility with mods that use it, and to be used as a template for new vatiation-specific song scripts. Therefore, this extension will still get updates to include all of the latest changes to all of the scripts that were originally included here.