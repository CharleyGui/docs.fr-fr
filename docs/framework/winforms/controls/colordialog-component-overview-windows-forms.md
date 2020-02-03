---
title: Vue d'ensemble du composant ColorDialog
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736967"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="3d891-102">Vue d'ensemble du composant ColorDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3d891-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="3d891-103">Le composant Windows Forms <xref:System.Windows.Forms.ColorDialog> est une boîte de dialogue préconfigurée qui permet à l’utilisateur de sélectionner une couleur dans une palette et d’ajouter des couleurs personnalisées à cette palette.</span><span class="sxs-lookup"><span data-stu-id="3d891-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="3d891-104">Il s’agit de la même boîte de dialogue que celle que vous voyez dans d’autres applications Windows pour sélectionner des couleurs.</span><span class="sxs-lookup"><span data-stu-id="3d891-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="3d891-105">Vous pouvez l'utiliser dans votre application Windows comme alternative à la configuration de votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3d891-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="3d891-106">La couleur sélectionnée dans la boîte de dialogue est retournée dans la propriété <xref:System.Windows.Forms.ColorDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d891-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="3d891-107">Si la propriété <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> est définie sur `false`, le bouton « définir des couleurs personnalisées » est désactivé et l’utilisateur est limité aux couleurs prédéfinies dans la palette.</span><span class="sxs-lookup"><span data-stu-id="3d891-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="3d891-108">Si la propriété <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> est définie sur `true`, l’utilisateur ne peut pas sélectionner les couleurs désélectionnées.</span><span class="sxs-lookup"><span data-stu-id="3d891-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="3d891-109">Pour afficher la boîte de dialogue, vous devez appeler sa méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d891-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d891-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d891-110">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="3d891-111">ColorDialog, composant</span><span class="sxs-lookup"><span data-stu-id="3d891-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="3d891-112">Contrôles et composants de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="3d891-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="3d891-113">Guide pratique pour modifier l’apparence du composant ColorDialog Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d891-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
