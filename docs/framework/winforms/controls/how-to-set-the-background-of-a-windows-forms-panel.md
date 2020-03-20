---
title: définir l’arrière-plan d’un panneau
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182108"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="7604c-102">Comment : définir l'arrière-plan d'un panneau Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7604c-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="7604c-103">Un contrôle <xref:System.Windows.Forms.Panel> windows Forms peut afficher à la fois une couleur de fond et une image de fond.</span><span class="sxs-lookup"><span data-stu-id="7604c-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="7604c-104">La <xref:System.Windows.Forms.Control.BackColor%2A> propriété définit la couleur de fond pour les commandes contenues, telles que les étiquettes et les boutons radio.</span><span class="sxs-lookup"><span data-stu-id="7604c-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="7604c-105">Si <xref:System.Windows.Forms.Control.BackgroundImage%2A> la propriété n’est pas définie, la <xref:System.Windows.Forms.Control.BackColor%2A> sélection remplira l’ensemble du panneau.</span><span class="sxs-lookup"><span data-stu-id="7604c-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="7604c-106">Si <xref:System.Windows.Forms.Control.BackgroundImage%2A> la propriété est définie, l’image s’affiche derrière les commandes contenues.</span><span class="sxs-lookup"><span data-stu-id="7604c-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="7604c-107">Définir l’arrière-plan de façon programmatique</span><span class="sxs-lookup"><span data-stu-id="7604c-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="7604c-108">Définissez la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du panneau <xref:System.Drawing.Color?displayProperty=nameWithType>à une valeur de type .</span><span class="sxs-lookup"><span data-stu-id="7604c-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="7604c-109">Définissez la <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriété du <xref:System.Drawing.Image.FromFile%2A> panneau <xref:System.Drawing.Image?displayProperty=nameWithType> en utilisant la méthode de la classe.</span><span class="sxs-lookup"><span data-stu-id="7604c-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
    ```vb  
    ' You should replace the bolded image
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7604c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7604c-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="7604c-111">Panel, contrôle</span><span class="sxs-lookup"><span data-stu-id="7604c-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="7604c-112">Vue d’ensemble du contrôle Panel</span><span class="sxs-lookup"><span data-stu-id="7604c-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
