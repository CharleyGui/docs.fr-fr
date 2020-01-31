---
title: Modifier les bordures de formulaire
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739566"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="75bfa-102">Comment : modifier les bordures des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75bfa-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="75bfa-103">Vous pouvez choisir parmi plusieurs styles de bordure quand vous déterminez l'apparence et le comportement de vos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="75bfa-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="75bfa-104">En modifiant la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A>, vous pouvez contrôler le comportement de redimensionnement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="75bfa-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="75bfa-105">De plus, la définition de <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affecte l'affichage de la barre de légende et de ses boutons.</span><span class="sxs-lookup"><span data-stu-id="75bfa-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="75bfa-106">Pour plus d'informations, consultez <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="75bfa-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="75bfa-107">Cette tâche est très bien prise en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75bfa-107">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="75bfa-108">Voir aussi [Comment : modifier les bordures d’Windows Forms à l’aide du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="75bfa-108">See also [How to: Change the Borders of Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="75bfa-109">Pour définir le style de bordure des Windows Forms par programmation</span><span class="sxs-lookup"><span data-stu-id="75bfa-109">To set the border style of Windows Forms programmatically</span></span>  
  
- <span data-ttu-id="75bfa-110">Affectez à la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A> le style souhaité.</span><span class="sxs-lookup"><span data-stu-id="75bfa-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="75bfa-111">L’exemple de code suivant définit le style de bordure des `DlgBx1` de formulaire sur <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="75bfa-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="75bfa-112">Consultez également [Comment : créer des boîtes de dialogue au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="75bfa-112">Also see [How to: Create Dialog Boxes at Design Time](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).</span></span>  
  
     <span data-ttu-id="75bfa-113">En outre, si vous avez choisi un style de bordure pour le formulaire qui fournit des boutons de **réduction** et d' **agrandissement** facultatifs, vous pouvez spécifier si vous souhaitez que l’un ou l’autre ou les deux boutons soient fonctionnels.</span><span class="sxs-lookup"><span data-stu-id="75bfa-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="75bfa-114">Ils sont utiles quand vous souhaitez contrôler étroitement l'expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="75bfa-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="75bfa-115">Les boutons **réduire** et **agrandir** sont activés par défaut et leurs fonctionnalités sont manipulées par le biais de la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="75bfa-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bfa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75bfa-116">See also</span></span>

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [<span data-ttu-id="75bfa-117">Bien démarrer avec Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75bfa-117">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
