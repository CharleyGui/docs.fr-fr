---
title: Vue d’ensemble du contrôle Splitter
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 3d6da8daf9bb0e8df4f69554a87725a7ddb65acb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742891"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="6be5b-102">Vue d'ensemble du contrôle Splitter (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6be5b-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="6be5b-103">Bien que <xref:System.Windows.Forms.SplitContainer> remplace et ajoute des fonctionnalités au contrôle <xref:System.Windows.Forms.Splitter> des versions antérieures, <xref:System.Windows.Forms.Splitter> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="6be5b-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="6be5b-104">Les contrôles de <xref:System.Windows.Forms.Splitter> Windows Forms sont utilisés pour redimensionner les contrôles ancrés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6be5b-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="6be5b-105">Le contrôle <xref:System.Windows.Forms.Splitter> est souvent utilisé sur les formulaires avec des contrôles qui ont des longueurs différentes de données à présenter, comme l’Explorateur Windows, dont les volets de données contiennent des informations de largeurs différentes à différents moments.</span><span class="sxs-lookup"><span data-stu-id="6be5b-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="6be5b-106">Utilisation du contrôle Splitter</span><span class="sxs-lookup"><span data-stu-id="6be5b-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="6be5b-107">Quand l’utilisateur pointe le pointeur de la souris sur le bord non ancré d’un contrôle qui peut être redimensionné par un contrôle Splitter, le pointeur change d’apparence pour indiquer que le contrôle peut être redimensionné.</span><span class="sxs-lookup"><span data-stu-id="6be5b-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="6be5b-108">Avec le contrôle Splitter, l’utilisateur peut redimensionner le contrôle ancré qui le précède immédiatement.</span><span class="sxs-lookup"><span data-stu-id="6be5b-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="6be5b-109">Par conséquent, pour permettre à l’utilisateur de redimensionner un contrôle ancré au moment de l’exécution, ancrez le contrôle pour qu’il soit redimensionné sur un bord d’un conteneur, puis ancrez un contrôle Splitter au même côté de ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="6be5b-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be5b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6be5b-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="6be5b-111">Guide pratique pour fixer des contrôles sur des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6be5b-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="6be5b-112">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6be5b-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
