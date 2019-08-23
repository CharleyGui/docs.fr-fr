---
title: 'Procédure : fournir une image bitmap de boîte à outils pour un contrôle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
ms.openlocfilehash: 428af7e4396fde8ac29046d73adda95dbe2182f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910473"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Procédure : fournir une image bitmap de boîte à outils pour un contrôle
Si vous souhaitez qu’une icône spéciale pour votre contrôle apparaisse dans la **boîte à outils**, vous pouvez spécifier une image particulière à <xref:System.Drawing.ToolboxBitmapAttribute>l’aide de. Cette classe est un *attribut*, c’est-à-dire un type spécial de classe que vous pouvez joindre à d’autres classes. Pour plus d’informations sur les attributs, consultez [vue d’ensemble des attributs (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) pour les C#Visual Basic ou les [attributsC#()](../../../csharp/programming-guide/concepts/attributes/index.md) pour.  
  
 À l’aide de ,vouspouvezspécifierunechaînequiindiquelechemind’accèsetlenomdefichierpouruneimagebitmapde16par16pixels.<xref:System.Drawing.ToolboxBitmapAttribute> Cette image bitmap apparaît alors en regard de votre contrôle lorsqu’elle est ajoutée à la **boîte à outils**. Vous pouvez également spécifier un <xref:System.Type>, auquel cas l’image bitmap associée à ce type est chargée. Si vous spécifiez à <xref:System.Type> la fois un et une chaîne, le contrôle recherche une ressource d’image portant le nom spécifié par le paramètre de chaîne dans l’assembly contenant <xref:System.Type> le type spécifié par le paramètre.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Pour spécifier une image de bitmap dans la boîte à outils concernant votre contrôle  
  
1. Ajoutez à la déclaration de classe de votre contrôle avant le `Class` mot clé pour Visual Basic, et au-dessus de la déclaration de classe pour Visual. C# <xref:System.Drawing.ToolboxBitmapAttribute>  
  
    ```vb  
    ' Specifies the bitmap associated with the Button type.  
    <ToolboxBitmap(GetType(Button))> Class MyControl1  
    ' Specifies a bitmap file.  
    End Class  
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _  
       Class MyControl2  
    End Class  
    ' Specifies a type that indicates the assembly to search, and the name   
    ' of an image resource to look for.  
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl  
    End Class  
    ```  
  
    ```csharp  
    // Specifies the bitmap associated with the Button type.  
    [ToolboxBitmap(typeof(Button))]  
    class MyControl1 : UserControl  
    {  
    }  
    // Specifies a bitmap file.  
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]  
    class MyControl2 : UserControl  
    {  
    }  
    // Specifies a type that indicates the assembly to search, and the name   
    // of an image resource to look for.  
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]  
    class MyControl : UserControl  
    {  
    }  
    ```  
  
2. Regénérez le projet.  
  
    > [!NOTE]
    > L’image bitmap n’apparaît pas dans la boîte à outils pour les composants et les contrôles générés automatiquement. Pour afficher l’image bitmap, rechargez le contrôle par le biais de la boîte de dialogue **Choisir des éléments de boîte à outils**. Pour plus d’informations, consultez [Procédure pas à pas : Remplissage automatique de la boîte à outils](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)avec des composants personnalisés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Développement de contrôles Windows Forms au moment du design](developing-windows-forms-controls-at-design-time.md)
- [Vue d’ensemble des attributs (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Attributs (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
