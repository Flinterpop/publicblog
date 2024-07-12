## Embarcadero Drawing images

### What is the relation between Canvas and Bitmap?

My example:

```
int m = StrToInt(TNumBox->Text);
    int n = StrToInt(TNumBox2->Text);
    TBitmap *bmp1=new TBitmap();
    //bmp1->LoadFromFile("tiles\\1\\0\\0.png");
    bmp1->LoadFromFile("tiles\\7\\35\\44.png");
​
    TImage1->Bitmap->Canvas->BeginScene();
    TImage1->Bitmap->Canvas->DrawBitmap( bmp1, TRect(0,0,256,256), TRect(n,n,m+n,m+n), 1.0, false );
​
    DrawX(TImage1->Bitmap->Canvas,n,n);
    TImage1->Bitmap->Canvas->EndScene();
    bmp1->Free();
```

Function Explanation

```
bmp->Canvas->DrawBitmap( bmp2, // this is source bitmap
   TRect(0,0,100,100), // source rectangular area on source bitmap
   TRect(0,0,100,100), // destination rectangular area on destbmp
   1.0, // opacity, it is successfully do  transparent copying  on to image 
   false // if it is true it uses highspeed interpolation, lower quality
   );
​
```



Basically, the `Canvas` is backed by a `Bitmap`, so when you draw anything using the canvas, the canvas will draw into the `Bitmap` it was created with.

`Canvas` is the place or medium where performs/executes the operation of **drawing**, and `Bitmap` is responsible for storing the pixel of the picture you draw.

Bitmap are close to OS, it is an array of data describing pixels. Canvas is close to what human can see in life like a painting canvas where you can draw a circle or a point, but it doesn't save how this circle pixels will represent in memory (that does bitmap). So, Canvas goes along with Bitmap.

#### Official: [https://learncplusplus.org/learn-about-bitmap-operations-in-c-builder-firemonkey/](https://learncplusplus.org/learn-about-bitmap-operations-in-c-builder-firemonkey/)

Bitmap is a standard for reading and writing pixels of images of applications on all platforms (Windows, MacOS, iOS, Android, Linux, …). A Bitmap includes bitmap information and full uncompressed image in pixels. Each pixel of this uncompressed image consists 4 color members called ARGB (Alpha Red Green Blue) and it can be set or shown as 0xAABBCCDD in hexadecimal format.

A TBitmap is a powerful graphic object used to create, manipulate and store images in memory and stored as a BMP image file (or in compressed types like JPG, PNG,…) on a disk. At the time of this writing C++Builder does not support Android64 or macOS64. Using Bitmaps and doing drawings, effects and analyzing pixels are easy by using [C++ Builder](https://www.embarcadero.com/products/cbuilder), [Delphi](https://www.embarcadero.com/products/delphi) programming languages.  TBitmap contains an internal image of the bitmap graphic and automatically manages realization of the palette when drawn. It also has an internal [Canvas](http://docwiki.embarcadero.com/Libraries/Sydney/en/FMX.Graphics.TCanvas), that allows you to draw pixels, lines, etc. Manipulating and copying image is very easy by using TBitmap Classes. All methods, properties and events of TBitmap can be found on this [TBitmap wiki](http://docwiki.embarcadero.com/Libraries/Sydney/en/FMX.Graphics.TBitmap) and It is possible to use [multi-resolution bitmaps](http://docwiki.embarcadero.com/RADStudio/Rio/en/Using_Multi-Resolution_Bitmaps)

Bitmaps can be easily used by [TImage](http://docwiki.embarcadero.com/Libraries/Rio/en/FMX.Objects.TImage) component in [C++ Builder](https://www.embarcadero.com/products/cbuilder) which has Bitmap property and it is easy to display a graphical image or graphical image files (BMP, PNG, JPG,… ) on a control. On C++Forms, Just drag Image component from the Palette (right side ) and double click MultiRessBitmap property from the Object Inspector (left side). Click this icon to import an image.
