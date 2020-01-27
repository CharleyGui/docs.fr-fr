---
title: Regrouper des contrôles avec le contrôle Panel à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745656"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="a1a8a-102">Comment : grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="a1a8a-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="a1a8a-103">Les contrôles de <xref:System.Windows.Forms.Panel> Windows Forms sont utilisés pour regrouper d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="a1a8a-104">Il existe trois raisons pour regrouper des contrôles.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-104">There are three reasons to group controls.</span></span> <span data-ttu-id="a1a8a-105">L’un est le regroupement visuel d’éléments de formulaire associés pour une interface utilisateur claire ; un autre est le regroupement par programmation, des cases d’option, par exemple ; le dernier est de déplacer les contrôles en tant qu’unité au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>

## <a name="to-create-a-group-of-controls"></a><span data-ttu-id="a1a8a-106">Pour créer un groupe de contrôles</span><span class="sxs-lookup"><span data-stu-id="a1a8a-106">To create a group of controls</span></span>

1. <span data-ttu-id="a1a8a-107">Faites glisser un contrôle <xref:System.Windows.Forms.Panel> à partir de l’onglet **Windows Forms** de la boîte à outils vers un formulaire.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-107">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>

2. <span data-ttu-id="a1a8a-108">Ajoutez d’autres contrôles au panneau, en dessinant chacun à l’intérieur du panneau.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-108">Add other controls to the panel, drawing each inside the panel.</span></span>

     <span data-ttu-id="a1a8a-109">Si vous disposez de contrôles existants que vous souhaitez encadrer dans un panneau, vous pouvez sélectionner tous les contrôles, les couper dans le presse-papiers, sélectionner le contrôle <xref:System.Windows.Forms.Panel>, puis les coller dans le panneau.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-109">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="a1a8a-110">Vous pouvez également les faire glisser dans le panneau.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-110">You can also drag them into the panel.</span></span>

3. <span data-ttu-id="a1a8a-111">Facultatif Si vous souhaitez ajouter une bordure à un panneau, définissez sa propriété <xref:System.Windows.Forms.BorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-111">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="a1a8a-112">Trois options s’offrent à vous : <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>et <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="a1a8a-112">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1a8a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1a8a-113">See also</span></span>

- [<span data-ttu-id="a1a8a-114">Panel, contrôle</span><span class="sxs-lookup"><span data-stu-id="a1a8a-114">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="a1a8a-115">Vue d’ensemble du contrôle Panel</span><span class="sxs-lookup"><span data-stu-id="a1a8a-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="a1a8a-116">Guide pratique pour définir l'arrière-plan d'un contrôle Panel</span><span class="sxs-lookup"><span data-stu-id="a1a8a-116">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
