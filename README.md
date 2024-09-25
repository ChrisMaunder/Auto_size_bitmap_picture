# An auto-sizing bitmap picture control

A picture control that displays a picture according to the size of the control, and not the picture itself.




![Sample Image](https://raw.githubusercontent.com/ChrisMaunder/bitmappicture/master/docs/assets/BitmapPicture.gif)

## Introduction

The Picture control available from the dialog editor component bar is great for quickly displaying a picture in a dialog, but it only displays the picture at the original picture's size. A problem occurs if you want to display a bitmap which must be aligned with other controls (eg. a bitmap of an arrow). If you change the size of the dialog box font, then the size and position of each control will also change, but the size of the displayed bitmap will not, resulting in a mis-aligned picture. The problem also occurs if the system font size is changed (The matrox millenium drivers allow you to do this). 

To overcome this problem I wrote a `CStatic `derived class that displays a bitmap according to the size of the underlying `CStatic `window. When the font size changes, the `CStatic `window size changes, and the bitmap will be StretchBlt'd to the new size. This allows images to be displayed smaller and larger than their original size. 

The easist way to use this class is to add the `CBitmapPicture `class to your project then create a `CStatic `object to your dialog, and attach a member variable of type `CBitmapPicture `to the object. Then in your `OnInitDialog `function, call `CBitmapPicture::SetBitmap` to set the bitmap to be used. 

```cpp
BOOL SetBitmap(UINT nIDResource);           // Loads bitmap from resource ID
BOOL SetBitmap(LPCTSTR lpszResourceName);   // Loads bitmap from resource name
BOOL SetBitmap(HBITMAP hBitmap);            // Not recommended, as reloads can't                                            // be done
```
