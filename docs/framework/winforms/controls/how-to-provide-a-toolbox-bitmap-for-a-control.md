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
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="b81f3-102">Procédure : fournir une image bitmap de boîte à outils pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="b81f3-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="b81f3-103">Si vous souhaitez qu’une icône spéciale pour votre contrôle apparaisse dans la **boîte à outils**, vous pouvez spécifier une image particulière à <xref:System.Drawing.ToolboxBitmapAttribute>l’aide de.</span><span class="sxs-lookup"><span data-stu-id="b81f3-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="b81f3-104">Cette classe est un *attribut*, c’est-à-dire un type spécial de classe que vous pouvez joindre à d’autres classes.</span><span class="sxs-lookup"><span data-stu-id="b81f3-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="b81f3-105">Pour plus d’informations sur les attributs, consultez [vue d’ensemble des attributs (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) pour les C#Visual Basic ou les [attributsC#()](../../../csharp/programming-guide/concepts/attributes/index.md) pour.</span><span class="sxs-lookup"><span data-stu-id="b81f3-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="b81f3-106">À l’aide de ,vouspouvezspécifierunechaînequiindiquelechemind’accèsetlenomdefichierpouruneimagebitmapde16par16pixels.<xref:System.Drawing.ToolboxBitmapAttribute></span><span class="sxs-lookup"><span data-stu-id="b81f3-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="b81f3-107">Cette image bitmap apparaît alors en regard de votre contrôle lorsqu’elle est ajoutée à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="b81f3-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="b81f3-108">Vous pouvez également spécifier un <xref:System.Type>, auquel cas l’image bitmap associée à ce type est chargée.</span><span class="sxs-lookup"><span data-stu-id="b81f3-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="b81f3-109">Si vous spécifiez à <xref:System.Type> la fois un et une chaîne, le contrôle recherche une ressource d’image portant le nom spécifié par le paramètre de chaîne dans l’assembly contenant <xref:System.Type> le type spécifié par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="b81f3-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="b81f3-110">Pour spécifier une image de bitmap dans la boîte à outils concernant votre contrôle</span><span class="sxs-lookup"><span data-stu-id="b81f3-110">To specify a Toolbox bitmap for your control</span></span>  
  
1. <span data-ttu-id="b81f3-111">Ajoutez à la déclaration de classe de votre contrôle avant le `Class` mot clé pour Visual Basic, et au-dessus de la déclaration de classe pour Visual. C# <xref:System.Drawing.ToolboxBitmapAttribute></span><span class="sxs-lookup"><span data-stu-id="b81f3-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
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
  
2. <span data-ttu-id="b81f3-112">Regénérez le projet.</span><span class="sxs-lookup"><span data-stu-id="b81f3-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b81f3-113">L’image bitmap n’apparaît pas dans la boîte à outils pour les composants et les contrôles générés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b81f3-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="b81f3-114">Pour afficher l’image bitmap, rechargez le contrôle par le biais de la boîte de dialogue **Choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="b81f3-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="b81f3-115">Pour plus d’informations, consultez [Procédure pas à pas : Remplissage automatique de la boîte à outils](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)avec des composants personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b81f3-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81f3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b81f3-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="b81f3-117">Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="b81f3-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="b81f3-118">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="b81f3-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="b81f3-119">Vue d’ensemble des attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b81f3-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="b81f3-120">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="b81f3-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
