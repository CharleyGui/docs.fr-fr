---
title: Guide pratique pour définir le niveau de compression JPEG
description: Découvrez comment ajuster la qualité d’une image JPEG en modifiant son niveau de compression sur Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: 1f6a96e8a05fff40eb08da0ce318faa86a06cc3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618712"
---
# <a name="how-to-set-jpeg-compression-level"></a>Guide pratique pour définir le niveau de compression JPEG
Vous pouvez modifier les paramètres d’une image quand vous enregistrez l’image sur disque de façon à réduire la taille du fichier ou améliorer sa qualité. Vous pouvez ajuster la qualité d’une image JPEG en changeant son niveau de compression. Pour spécifier le niveau de compression lors de l’enregistrement d’une image JPEG, vous devez créer un <xref:System.Drawing.Imaging.EncoderParameters> objet et le passer à la <xref:System.Drawing.Image.Save%2A> méthode de la <xref:System.Drawing.Image> classe. Initialisez l' <xref:System.Drawing.Imaging.EncoderParameters> objet afin qu’il dispose d’un tableau qui se compose d’un <xref:System.Drawing.Imaging.EncoderParameter> . Lorsque vous créez le <xref:System.Drawing.Imaging.EncoderParameter> , spécifiez l' <xref:System.Drawing.Imaging.Encoder.Quality> encodeur et le niveau de compression souhaité.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant crée un <xref:System.Drawing.Imaging.EncoderParameter> objet et enregistre trois images JPEG. Chaque image JPEG est enregistrée avec un niveau de qualité différent, en modifiant la `long` valeur passée au <xref:System.Drawing.Imaging.EncoderParameter> constructeur. Un niveau de qualité de 0 correspond à la plus grande compression, et un niveau de qualité de 100 correspond à la compression minimale.  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- une application Windows Forms ;  
  
- <xref:System.Windows.Forms.PaintEventArgs>, Qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler> .  
  
- Un fichier image nommé `TestPhoto.jpg` et qui se trouve sur **c:\\**.  
  
## <a name="see-also"></a>Voir aussi

- [Comment : déterminer les paramètres pris en charge par un encodeur](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [Types de bitmaps](types-of-bitmaps.md)
- [Utilisation d'encodeurs et de décodeurs d'images dans GDI+ managé](using-image-encoders-and-decoders-in-managed-gdi.md)
