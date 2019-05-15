---
title: 'Procédure : définir le renderer ToolStrip pour une application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: c9250b723e68ac97d1486a896392bf64c66cdfbc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591596"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a><span data-ttu-id="20206-102">Procédure : définir le renderer ToolStrip pour une application</span><span class="sxs-lookup"><span data-stu-id="20206-102">How to: Set the ToolStrip Renderer for an Application</span></span>
<span data-ttu-id="20206-103">Vous pouvez personnaliser l'apparence de vos contrôles <xref:System.Windows.Forms.ToolStrip> individuellement ou pour tous les contrôles <xref:System.Windows.Forms.ToolStrip> de votre application.</span><span class="sxs-lookup"><span data-stu-id="20206-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> controls individually or for all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20206-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="20206-104">Example</span></span>  
 <span data-ttu-id="20206-105">L'exemple de code suivant montre comment appliquer de manière sélective un convertisseur personnalisé à un contrôle <xref:System.Windows.Forms.ToolStrip> et à un contrôle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="20206-105">The following code example demonstrates how to selectively apply a custom renderer to a <xref:System.Windows.Forms.ToolStrip> control and a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="20206-106">Pour utiliser cet exemple de code, compilez et exécutez l'application, puis sélectionnez la portée du rendu personnalisé à partir du contrôle <xref:System.Windows.Forms.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="20206-106">To use this code example, compile and run the application, and then select the scope of the custom rending from the <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="20206-107">Cliquez sur **Appliquer** pour définir le convertisseur.</span><span class="sxs-lookup"><span data-stu-id="20206-107">Click **Apply** to set the renderer.</span></span>  
  
 <span data-ttu-id="20206-108">Pour afficher le rendu d’élément de menu personnalisé, sélectionnez le <xref:System.Windows.Forms.MenuStrip> option à partir de la <xref:System.Windows.Forms.ComboBox> contrôler, cliquez sur **appliquer**, puis ouvrez le **fichier** élément de menu.</span><span class="sxs-lookup"><span data-stu-id="20206-108">To see custom menu item rendering, select the <xref:System.Windows.Forms.MenuStrip> option from the <xref:System.Windows.Forms.ComboBox> control, click **Apply**, and then open the **File** menu item.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 <span data-ttu-id="20206-109">Définissez la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> pour appliquer un convertisseur personnalisé à tous les contrôles <xref:System.Windows.Forms.ToolStrip> de votre application.</span><span class="sxs-lookup"><span data-stu-id="20206-109">Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
 <span data-ttu-id="20206-110">Définissez la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> pour appliquer un convertisseur personnalisé à un contrôle <xref:System.Windows.Forms.ToolStrip> spécifique.</span><span class="sxs-lookup"><span data-stu-id="20206-110">Set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to an individual <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20206-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="20206-111">Compiling the Code</span></span>  
 <span data-ttu-id="20206-112">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="20206-112">This example requires:</span></span>  
  
- <span data-ttu-id="20206-113">des références aux assemblys System.Design, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="20206-113">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20206-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20206-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [<span data-ttu-id="20206-115">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="20206-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
