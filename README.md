# Xamarin.Tip - Load Images on Xamarin.Forms Shared Project

#### [Problem]: Xamarin.Forms iOS images not showing
I have a Xamarin.Forms shared project. On Android all images work fine. I wanted to add them to my iOS project, but they don't show. I've added them to Assets.xcassets:

```
{
  "filename": "logo_launcher.png",
  "scale": "1x",
  "idiom": "universal"
}
```

And I use the following XAML:

```
<Image Source="logo_launcher.png" x:Name="logo" />
```

I've added all images except for the vector ones. I'm testing it on a iPhone 8 - 11.4 simulator.

Although it is deprecated, I tried to add the images to the "Resource" folder. But I couldn't even select the .png files. So that didn't work either.

I'm lost at what to do. Is there some option I need to enable, or something to include in the XAML to make it work?

**Asked by TruffelNL**

#### Solution

1. Main.xaml
```
        <Image x:Name="iconBrain">
            <Image.Source>
                <OnPlatform x:TypeArguments="ImageSource">
                    <OnPlatform.iOS><FileImageSource File="IconBrain"/></OnPlatform.iOS>
                    <OnPlatform.Android><FileImageSource File="ic_brain"/></OnPlatform.Android>
                </OnPlatform>
            </Image.Source>
        </Image>
```

2. Android: Add the images on the respective Drawable folders under Resourses directory.
3. iOS: Create a new Image Set under Assets.xcassets and add the Images.


[//]: #
   [Problem]: <https://stackoverflow.com/q/52301067/10341660>
