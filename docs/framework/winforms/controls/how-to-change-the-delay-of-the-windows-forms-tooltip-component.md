---
title: Modifier le délai du composant ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746591"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a><span data-ttu-id="43c6c-102">Comment : modifier la durée avant affichage du composant ToolTip Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43c6c-102">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>
<span data-ttu-id="43c6c-103">Il existe plusieurs valeurs de délai que vous pouvez définir pour un composant Windows Forms <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="43c6c-103">There are multiple delay values that you can set for a Windows Forms <xref:System.Windows.Forms.ToolTip> component.</span></span> <span data-ttu-id="43c6c-104">L’unité de mesure pour toutes ces propriétés est en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="43c6c-104">The unit of measure for all these properties is milliseconds.</span></span> <span data-ttu-id="43c6c-105">La propriété <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> détermine la durée pendant laquelle l’utilisateur doit pointer sur le contrôle associé pour que la chaîne d’info-bulle s’affiche.</span><span class="sxs-lookup"><span data-stu-id="43c6c-105">The <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> property determines how long the user must point at the associated control for the ToolTip string to appear.</span></span> <span data-ttu-id="43c6c-106">La propriété <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> définit le nombre de millisecondes nécessaires pour que les chaînes d’info-bulle suivantes s’affichent lorsque la souris passe d’un contrôle associé à une info-bulle à un autre.</span><span class="sxs-lookup"><span data-stu-id="43c6c-106">The <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> property sets the number of milliseconds it takes for subsequent ToolTip strings to appear as the mouse moves from one ToolTip-associated control to another.</span></span> <span data-ttu-id="43c6c-107">La propriété <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> détermine la durée d’affichage de la chaîne d’info-bulle.</span><span class="sxs-lookup"><span data-stu-id="43c6c-107">The <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> property determines the length of time the ToolTip string is shown.</span></span> <span data-ttu-id="43c6c-108">Vous pouvez définir ces valeurs individuellement ou en définissant la valeur de la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> ; les autres propriétés de délai sont définies en fonction de la valeur affectée à la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>.</span><span class="sxs-lookup"><span data-stu-id="43c6c-108">You can set these values individually, or by setting the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property; the other delay properties are set based on the value assigned to the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property.</span></span> <span data-ttu-id="43c6c-109">Par exemple, lorsque <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> a la valeur N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> a la valeur N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> est définie sur la valeur de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divisée par cinq (ou N/5) et <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> est définie sur une valeur qui est cinq fois la valeur de la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> (ou 5N).</span><span class="sxs-lookup"><span data-stu-id="43c6c-109">For example, when <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> is set to a value N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> is set to N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> is set to the value of <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divided by five (or N/5), and <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> is set to a value that is five times the value of the <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> property (or 5N).</span></span>  
  
### <a name="to-set-the-delay"></a><span data-ttu-id="43c6c-110">Pour définir le délai</span><span class="sxs-lookup"><span data-stu-id="43c6c-110">To set the delay</span></span>  
  
1. <span data-ttu-id="43c6c-111">Définissez les propriétés suivantes comme indiqué dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="43c6c-111">Set the following properties as shown in this example.</span></span>  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="43c6c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43c6c-112">See also</span></span>

- [<span data-ttu-id="43c6c-113">Vue d’ensemble du composant ToolTip</span><span class="sxs-lookup"><span data-stu-id="43c6c-113">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="43c6c-114">Guide pratique pour définir des info-bulles pour les contrôles d'un Windows Form au moment du design</span><span class="sxs-lookup"><span data-stu-id="43c6c-114">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [<span data-ttu-id="43c6c-115">ToolTip, composant</span><span class="sxs-lookup"><span data-stu-id="43c6c-115">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
