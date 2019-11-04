---
title: "Comment : fournir une bitmap pour un contrôle en vue de l'afficher dans la boîte à outils"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 61f60aaeab904dff80408a1dc46c2882fb5e22b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458311"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="7bcb6-102">Comment : fournir une bitmap pour un contrôle en vue de l'afficher dans la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="7bcb6-102">How to: Provide a Toolbox Bitmap for a Control</span></span>

<span data-ttu-id="7bcb6-103">Si vous souhaitez qu’une icône spéciale pour votre contrôle apparaisse dans la **boîte à outils** de Visual Studio, vous pouvez spécifier une image particulière à l’aide de l' <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-103">If you want to have a special icon for your control appear in the **Toolbox** of Visual Studio, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="7bcb6-104">Cette classe est un *attribut*, c’est-à-dire un type spécial de classe que vous pouvez joindre à d’autres classes.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="7bcb6-105">Pour plus d’informations sur les attributs, consultez [vue d’ensemble des attributs (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) pour les C#Visual Basic ou les [attributsC#()](../../../csharp/programming-guide/concepts/attributes/index.md) pour.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>

<span data-ttu-id="7bcb6-106">À l’aide de l' <xref:System.Drawing.ToolboxBitmapAttribute>, vous pouvez spécifier une chaîne qui indique le chemin d’accès et le nom de fichier pour une image bitmap de 16 par 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="7bcb6-107">Cette image bitmap apparaît alors en regard de votre contrôle lorsqu’elle est ajoutée à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="7bcb6-108">Vous pouvez également spécifier un <xref:System.Type>, auquel cas l’image bitmap associée à ce type est chargée.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="7bcb6-109">Si vous spécifiez à la fois un <xref:System.Type> et une chaîne, le contrôle recherche une ressource d’image portant le nom spécifié par le paramètre de chaîne dans l’assembly contenant le type spécifié par le paramètre <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="7bcb6-110">Pour spécifier une image de bitmap dans la boîte à outils concernant votre contrôle</span><span class="sxs-lookup"><span data-stu-id="7bcb6-110">To specify a Toolbox bitmap for your control</span></span>

1. <span data-ttu-id="7bcb6-111">Ajoutez le <xref:System.Drawing.ToolboxBitmapAttribute> à la déclaration de classe de votre contrôle avant le mot clé `Class` pour Visual Basic, et au-dessus de C#la déclaration de classe pour Visual.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>

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

2. <span data-ttu-id="7bcb6-112">Regénérez le projet.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-112">Rebuild the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7bcb6-113">L’image bitmap n’apparaît pas dans la boîte à outils pour les composants et les contrôles générés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="7bcb6-114">Pour afficher l’image bitmap, rechargez le contrôle par le biais de la boîte de dialogue **Choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="7bcb6-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="7bcb6-115">Pour plus d’informations, consultez [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="7bcb6-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7bcb6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bcb6-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="7bcb6-117">Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="7bcb6-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="7bcb6-118">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="7bcb6-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="7bcb6-119">Vue d’ensemble des attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bcb6-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="7bcb6-120">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="7bcb6-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
