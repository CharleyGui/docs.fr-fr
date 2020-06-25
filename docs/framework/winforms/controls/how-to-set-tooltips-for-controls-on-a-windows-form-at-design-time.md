---
title: "Comment : définir des info-bulles pour les contrôles d'un Windows Form au moment du design"
description: Découvrez comment définir des info-bulles pour les contrôles par programmation ou dans le Concepteur Windows Forms dans Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325974"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="7d1ea-103">Comment : définir des info-bulles pour les contrôles d’un Windows Form au moment du design</span><span class="sxs-lookup"><span data-stu-id="7d1ea-103">How to: Set ToolTips for controls on a Windows Form at design time</span></span>

<span data-ttu-id="7d1ea-104">Vous pouvez définir une <xref:System.Windows.Forms.ToolTip> chaîne dans le code ou dans le Concepteur Windows Forms dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-104">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="7d1ea-105">Pour plus d’informations sur le <xref:System.Windows.Forms.ToolTip> composant, consultez [vue d’ensemble du composant ToolTip](tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7d1ea-105">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md).</span></span>

## <a name="set-a-tooltip-programmatically"></a><span data-ttu-id="7d1ea-106">Définir une info-bulle par programmation</span><span class="sxs-lookup"><span data-stu-id="7d1ea-106">Set a ToolTip programmatically</span></span>

1. <span data-ttu-id="7d1ea-107">Ajoutez le contrôle qui affichera l’info-bulle.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-107">Add the control that will display the ToolTip.</span></span>

2. <span data-ttu-id="7d1ea-108">Utilisez la <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> méthode du <xref:System.Windows.Forms.ToolTip> composant.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-108">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a><span data-ttu-id="7d1ea-109">Définir une info-bulle dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="7d1ea-109">Set a ToolTip in the designer</span></span>

1. <span data-ttu-id="7d1ea-110">Dans Visual Studio, ajoutez un <xref:System.Windows.Forms.ToolTip> composant au formulaire.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-110">In Visual Studio, add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>

2. <span data-ttu-id="7d1ea-111">Sélectionnez le contrôle qui affichera l’info-bulle ou ajoutez-le au formulaire.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-111">Select the control that will display the ToolTip, or add it to the form.</span></span>

3. <span data-ttu-id="7d1ea-112">Dans la fenêtre **Propriétés** , affectez à l' **info-bulle de** la valeur ToolTip1 une chaîne de texte appropriée.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-112">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>

### <a name="to-remove-a-tooltip-programmatically"></a><span data-ttu-id="7d1ea-113">Pour supprimer une info-bulle par programmation</span><span class="sxs-lookup"><span data-stu-id="7d1ea-113">To remove a ToolTip programmatically</span></span>

1. <span data-ttu-id="7d1ea-114">Utilisez la <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> méthode du <xref:System.Windows.Forms.ToolTip> composant.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-114">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a><span data-ttu-id="7d1ea-115">Supprimer une info-bulle dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="7d1ea-115">Remove a ToolTip in the designer</span></span>

1. <span data-ttu-id="7d1ea-116">Dans Visual Studio, sélectionnez le contrôle qui affiche l’info-bulle.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-116">In Visual Studio, select the control that is displaying the ToolTip.</span></span>

2. <span data-ttu-id="7d1ea-117">Dans la fenêtre **Propriétés** , supprimez le texte de l' **info-bulle sur ToolTip1**.</span><span class="sxs-lookup"><span data-stu-id="7d1ea-117">In the **Properties** window, delete the text in the **ToolTip on ToolTip1**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d1ea-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d1ea-118">See also</span></span>

- [<span data-ttu-id="7d1ea-119">Vue d'ensemble du composant ToolTip</span><span class="sxs-lookup"><span data-stu-id="7d1ea-119">ToolTip Component Overview</span></span>](tooltip-component-overview-windows-forms.md)
- [<span data-ttu-id="7d1ea-120">Comment : modifier la durée avant affichage du composant ToolTip Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d1ea-120">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [<span data-ttu-id="7d1ea-121">ToolTip, composant</span><span class="sxs-lookup"><span data-stu-id="7d1ea-121">ToolTip Component</span></span>](tooltip-component-windows-forms.md)
