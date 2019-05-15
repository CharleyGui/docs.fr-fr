---
title: 'Procédure : créer un formulaire Windows redimensionnable pour l’entrée de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: 1b27c0e67aae1935c4216654d9f3ddf557719572
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588939"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="dfdc9-102">Procédure : créer un formulaire Windows redimensionnable pour l’entrée de données</span><span class="sxs-lookup"><span data-stu-id="dfdc9-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="dfdc9-103">Une bonne disposition répond correctement aux modifications des dimensions de son formulaire parent.</span><span class="sxs-lookup"><span data-stu-id="dfdc9-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="dfdc9-104">Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.TableLayoutPanel> pour organiser la disposition de votre formulaire afin de redimensionner et de positionner vos contrôles de façon cohérente à mesure que les dimensions du formulaire changent.</span><span class="sxs-lookup"><span data-stu-id="dfdc9-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="dfdc9-105">Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> est également utile quand des modifications du contenu de vos contrôles entraîne une modification de la disposition.</span><span class="sxs-lookup"><span data-stu-id="dfdc9-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="dfdc9-106">Vous pouvez effectuer les tâches décrites dans cette procédure dans l'environnement Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dfdc9-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="dfdc9-107">Consultez également [procédure pas à pas : Création d’un formulaire Windows redimensionnable pour l’entrée de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dfdc9-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfdc9-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="dfdc9-108">Example</span></span>  
 <span data-ttu-id="dfdc9-109">L'exemple suivant montre comment utiliser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> pour générer une disposition qui répond correctement quand l'utilisateur redimensionne le formulaire.</span><span class="sxs-lookup"><span data-stu-id="dfdc9-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="dfdc9-110">Il illustre également une disposition qui répond correctement à la localisation.</span><span class="sxs-lookup"><span data-stu-id="dfdc9-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dfdc9-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="dfdc9-111">Compiling the Code</span></span>  
 <span data-ttu-id="dfdc9-112">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="dfdc9-112">This example requires:</span></span>  
  
- <span data-ttu-id="dfdc9-113">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="dfdc9-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdc9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfdc9-114">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="dfdc9-115">Guide pratique pour Ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="dfdc9-115">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="dfdc9-116">Guide pratique pour Créer qu'un Windows Forms de disposition qui répond bien à la localisation</span><span class="sxs-lookup"><span data-stu-id="dfdc9-116">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="dfdc9-117">Expérience utilisateur Microsoft Windows, Recommandations officielles à destination des développeurs et des concepteurs d’interfaces utilisateur. Redmond, Washington : Microsoft Press, 1999. (USBN : 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="dfdc9-117">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
