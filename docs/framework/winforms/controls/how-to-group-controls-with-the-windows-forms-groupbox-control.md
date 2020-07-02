---
title: Contrôles de groupe avec contrôle GroupBox
description: Apprenez à regrouper les contrôles avec le contrôle GroupBox Windows Forms pour pouvoir créer un regroupement visuel d’éléments associés.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618062"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="96f40-103">Comment : regrouper des contrôles au moyen du contrôle GroupBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96f40-103">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="96f40-104"><xref:System.Windows.Forms.GroupBox>Les contrôles Windows Forms sont utilisés pour regrouper d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="96f40-104">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="96f40-105">Il existe trois raisons pour regrouper des contrôles :</span><span class="sxs-lookup"><span data-stu-id="96f40-105">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="96f40-106">Pour créer un regroupement visuel d’éléments de formulaire associés pour une interface utilisateur claire.</span><span class="sxs-lookup"><span data-stu-id="96f40-106">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="96f40-107">Pour créer un regroupement par programmation (des cases d’option, par exemple).</span><span class="sxs-lookup"><span data-stu-id="96f40-107">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="96f40-108">Pour déplacer les contrôles en tant qu’unité au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="96f40-108">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="96f40-109">Pour créer un groupe de contrôles</span><span class="sxs-lookup"><span data-stu-id="96f40-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="96f40-110">Dessinez un <xref:System.Windows.Forms.GroupBox> contrôle sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="96f40-110">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="96f40-111">Ajoutez d’autres contrôles à la zone de groupe, en dessinant chacun à l’intérieur de la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="96f40-111">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="96f40-112">Si vous avez des contrôles existants que vous souhaitez encadrer dans une zone de groupe, vous pouvez sélectionner tous les contrôles, les couper dans le presse-papiers, sélectionner le <xref:System.Windows.Forms.GroupBox> contrôle, puis les coller dans la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="96f40-112">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="96f40-113">Vous pouvez également les faire glisser dans la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="96f40-113">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="96f40-114">Affectez <xref:System.Windows.Forms.GroupBox.Text%2A> à la propriété de la zone de groupe une légende appropriée.</span><span class="sxs-lookup"><span data-stu-id="96f40-114">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f40-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96f40-115">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="96f40-116">GroupBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="96f40-116">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
