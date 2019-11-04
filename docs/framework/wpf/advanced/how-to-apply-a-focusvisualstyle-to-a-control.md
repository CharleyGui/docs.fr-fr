---
title: 'Comment : appliquer un FocusVisualStyle à un contrôle'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459806"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="faf56-102">Comment : appliquer un FocusVisualStyle à un contrôle</span><span class="sxs-lookup"><span data-stu-id="faf56-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="faf56-103">Cet exemple montre comment créer un style de focus visuel dans les ressources et appliquer le style à un contrôle à l’aide de la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="faf56-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf56-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="faf56-104">Example</span></span>  
 <span data-ttu-id="faf56-105">L’exemple suivant définit un style qui crée une composition de contrôle supplémentaire qui s’applique uniquement lorsque le contrôle est axé sur le clavier dans le [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="faf56-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="faf56-106">Pour ce faire, vous devez définir un style avec un <xref:System.Windows.Controls.ControlTemplate>, puis référencer ce style en tant que ressource lors de la définition de la propriété <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="faf56-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="faf56-107">Un rectangle externe ressemblant à une bordure est placé en dehors de la zone rectangulaire.</span><span class="sxs-lookup"><span data-stu-id="faf56-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="faf56-108">Sauf modification contraire, le dimensionnement du style utilise le <xref:System.Windows.FrameworkElement.ActualHeight%2A> et <xref:System.Windows.FrameworkElement.ActualWidth%2A> du contrôle rectangulaire où le style de focus visuel est appliqué.</span><span class="sxs-lookup"><span data-stu-id="faf56-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="faf56-109">Cet exemple définit des valeurs négatives pour le <xref:System.Windows.FrameworkElement.Margin%2A> pour que la bordure apparaisse légèrement en dehors du contrôle ayant le focus.</span><span class="sxs-lookup"><span data-stu-id="faf56-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="faf56-110">Un <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> est additif pour tout style de modèle de contrôle qui provient d’un style explicite ou d’un style de thème. le style principal d’un contrôle peut toujours être créé à l’aide d’un <xref:System.Windows.Controls.ControlTemplate> et définir ce style sur la propriété <xref:System.Windows.FrameworkElement.Style%2A>.</span><span class="sxs-lookup"><span data-stu-id="faf56-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="faf56-111">Les styles visuels de focus doivent être utilisés de manière cohérente sur un thème ou une interface utilisateur, plutôt que d’utiliser un autre pour chaque élément pouvant être actif.</span><span class="sxs-lookup"><span data-stu-id="faf56-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="faf56-112">Pour plus d’informations, consultez la rubrique [stylisation du focus dans les contrôles et FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="faf56-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf56-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faf56-113">See also</span></span>

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [<span data-ttu-id="faf56-114">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="faf56-114">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="faf56-115">FocusVisualStyle et application d'un style au focus dans les contrôles</span><span class="sxs-lookup"><span data-stu-id="faf56-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](styling-for-focus-in-controls-and-focusvisualstyle.md)
