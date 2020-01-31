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
ms.openlocfilehash: ba2619354403793aea7ca15d43649da9637079a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744741"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="08ae1-102">Comment : définir l'arrière-plan d'un panneau Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08ae1-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="08ae1-103">Un contrôle Windows Forms <xref:System.Windows.Forms.Panel> peut afficher une couleur d’arrière-plan et une image d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="08ae1-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="08ae1-104">La propriété <xref:System.Windows.Forms.Control.BackColor%2A> définit la couleur d’arrière-plan des contrôles contenus, tels que les étiquettes et les cases d’option.</span><span class="sxs-lookup"><span data-stu-id="08ae1-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="08ae1-105">Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> n’est pas définie, la sélection <xref:System.Windows.Forms.Control.BackColor%2A> remplit tout le panneau.</span><span class="sxs-lookup"><span data-stu-id="08ae1-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="08ae1-106">Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> est définie, l’image est affichée derrière les contrôles contenus.</span><span class="sxs-lookup"><span data-stu-id="08ae1-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="08ae1-107">Pour définir l’arrière-plan par programmation</span><span class="sxs-lookup"><span data-stu-id="08ae1-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="08ae1-108">Affectez à la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du panneau une valeur de type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="08ae1-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="08ae1-109">Définissez la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du panneau à l’aide de la méthode <xref:System.Drawing.Image.FromFile%2A> de la classe <xref:System.Drawing.Image?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="08ae1-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08ae1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08ae1-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="08ae1-111">Panel, contrôle</span><span class="sxs-lookup"><span data-stu-id="08ae1-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="08ae1-112">Vue d’ensemble du contrôle Panel</span><span class="sxs-lookup"><span data-stu-id="08ae1-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
