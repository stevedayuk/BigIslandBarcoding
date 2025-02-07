Fork from https://github.com/Redth/BigIslandBarcoding with code updated to make it run and compile following the last visual studios version and MAUI preview

Current preview : RC2

Current package : https://www.nuget.org/packages/ZXing.Net.Maui.Jgdev/ 1.0.4

Note : it seem the IOS version doesn't work (see https://github.com/julienGrd/BigIslandBarcoding/issues/1). I don't have the equipment to test the IOS version, please don't hesitate to investigate and submit a PR if you are able to correct it.

# ZXing.Net.MAUI
The successor to ZXing.Net.Mobile

![zxing net maui](https://user-images.githubusercontent.com/271950/129272315-b3f5a468-c585-49f2-bbab-68a884618b94.png)

## Barcode Scanning

```xaml
<zxing:CameraBarcodeReaderView
  x:Name="cameraBarcodeReaderView"
  BarcodesDetected="BarcodesDetected" />
```

Configure Reader options
```csharp
cameraBarcodeReaderView.Options = new BarcodeReaderOptions
{
  Formats = BarcodeFormats.OneDimensional,
  AutoRotate = true,
  Multiple = true
};
```

Toggle Torch
```csharp
cameraBarcodeReaderView.IsTorchOn = !cameraBarcodeReaderView.IsTorchOn;
```

Flip between Rear/Front cameras
```csharp
cameraBarcodeReaderView.CameraLocation
  = cameraBarcodeReaderView.CameraLocation == CameraLocation.Rear ? CameraLocation.Front : CameraLocation.Rear;
```

Handle detected barcode(s)
```csharp
protected void BarcodesDetected(object sender, BarcodeDetectionEventArgs e)
{
  foreach (var barcode in e.Results)
    Console.WriteLine($"Barcodes: {barcode.Format} -> {barcode.Value}");
}
```

## Barcode Generator View
```xaml
<zxing:BarcodeGeneratorView
  HeightRequest="100"
  WidthRequest="100"
  ForegroundColor="DarkBlue"
  Value="https://dotnet.microsoft.com"
  Format="QrCode"
  Margin="3" />
```




