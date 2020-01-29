---
title: Contrôles de groupe avec contrôle GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: bb7476c410d2802b5d32cc9842a778f290765e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736652"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="c3fd0-102">Comment : regrouper des contrôles au moyen du contrôle GroupBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c3fd0-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="c3fd0-103">Les contrôles de <xref:System.Windows.Forms.GroupBox> Windows Forms sont utilisés pour regrouper d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="c3fd0-104">Il existe trois raisons pour regrouper des contrôles :</span><span class="sxs-lookup"><span data-stu-id="c3fd0-104">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="c3fd0-105">Pour créer un regroupement visuel d’éléments de formulaire associés pour une interface utilisateur claire.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="c3fd0-106">Pour créer un regroupement par programmation (des cases d’option, par exemple).</span><span class="sxs-lookup"><span data-stu-id="c3fd0-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="c3fd0-107">Pour déplacer les contrôles en tant qu’unité au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="c3fd0-108">Pour créer un groupe de contrôles</span><span class="sxs-lookup"><span data-stu-id="c3fd0-108">To create a group of controls</span></span>  
  
1. <span data-ttu-id="c3fd0-109">Dessinez un contrôle <xref:System.Windows.Forms.GroupBox> sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="c3fd0-110">Ajoutez d’autres contrôles à la zone de groupe, en dessinant chacun à l’intérieur de la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="c3fd0-111">Si vous avez des contrôles existants que vous souhaitez encadrer dans une zone de groupe, vous pouvez sélectionner tous les contrôles, les couper dans le presse-papiers, sélectionner le contrôle <xref:System.Windows.Forms.GroupBox>, puis les coller dans la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="c3fd0-112">Vous pouvez également les faire glisser dans la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-112">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="c3fd0-113">Affectez une légende appropriée à la propriété <xref:System.Windows.Forms.GroupBox.Text%2A> de la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="c3fd0-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fd0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3fd0-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="c3fd0-115">GroupBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="c3fd0-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
