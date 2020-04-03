---
title: 'Comment : spécifier une position de menu contextuel personnalisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635749"
---
# <a name="how-to-specify-a-custom-popup-position"></a><span data-ttu-id="90cd4-102">Comment : spécifier une position de menu contextuel personnalisée</span><span class="sxs-lookup"><span data-stu-id="90cd4-102">How to: Specify a Custom Popup Position</span></span>
<span data-ttu-id="90cd4-103">Cet exemple montre comment spécifier une position personnalisée pour un <xref:System.Windows.Controls.Primitives.Popup> contrôle lorsque la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété est réglée à <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="90cd4-103">This example shows how to specify a custom position for a <xref:System.Windows.Controls.Primitives.Popup> control when the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90cd4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="90cd4-104">Example</span></span>  
 <span data-ttu-id="90cd4-105">Lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> la propriété <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>est <xref:System.Windows.Controls.Primitives.Popup> réglée à , <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> les appels d’une instance définie du délégué.</span><span class="sxs-lookup"><span data-stu-id="90cd4-105">When the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property is set to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, the <xref:System.Windows.Controls.Primitives.Popup> calls a defined instance of the <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate.</span></span> <span data-ttu-id="90cd4-106">Ce délégué retourne un ensemble de points possibles qui sont par rapport au coin supérieur <xref:System.Windows.Controls.Primitives.Popup>gauche de la zone cible et le coin supérieur gauche de la .</span><span class="sxs-lookup"><span data-stu-id="90cd4-106">This delegate returns a set of possible points that are relative to the top-left corner of the target area and the top-left corner of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span> <span data-ttu-id="90cd4-107">Le <xref:System.Windows.Controls.Primitives.Popup> placement se produit au point qui offre la meilleure visibilité.</span><span class="sxs-lookup"><span data-stu-id="90cd4-107">The <xref:System.Windows.Controls.Primitives.Popup> placement occurs at the point that provides the best visibility.</span></span>  
  
 <span data-ttu-id="90cd4-108">L’exemple suivant montre comment définir <xref:System.Windows.Controls.Primitives.Popup> la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> position <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>d’un en fixant la propriété à .</span><span class="sxs-lookup"><span data-stu-id="90cd4-108">The following example shows how to define the position of a <xref:System.Windows.Controls.Primitives.Popup> by setting the <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> property to <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.</span></span> <span data-ttu-id="90cd4-109">Il montre également comment créer <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> et attribuer un <xref:System.Windows.Controls.Primitives.Popup>délégué afin de positionner le .</span><span class="sxs-lookup"><span data-stu-id="90cd4-109">It also shows how to create and assign a <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegate in order to position the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  <span data-ttu-id="90cd4-110">Le délégué de <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> rappel renvoie deux objets.</span><span class="sxs-lookup"><span data-stu-id="90cd4-110">The callback delegate returns two <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objects.</span></span>  <span data-ttu-id="90cd4-111">Si <xref:System.Windows.Controls.Primitives.Popup> le est caché par un bord <xref:System.Windows.Controls.Primitives.Popup> d’écran à la première position, le est placé à la deuxième position.</span><span class="sxs-lookup"><span data-stu-id="90cd4-111">If the <xref:System.Windows.Controls.Primitives.Popup> is hidden by a screen edge at the first position, the <xref:System.Windows.Controls.Primitives.Popup> is placed at the second position.</span></span>  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 <span data-ttu-id="90cd4-112">Pour l’échantillon complet, voir [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span><span class="sxs-lookup"><span data-stu-id="90cd4-112">For the complete sample, see [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90cd4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90cd4-113">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Popup>
- [<span data-ttu-id="90cd4-114">Aperçu popup</span><span class="sxs-lookup"><span data-stu-id="90cd4-114">Popup overview</span></span>](popup-overview.md)
- [<span data-ttu-id="90cd4-115">Articles comment faire</span><span class="sxs-lookup"><span data-stu-id="90cd4-115">How-to articles</span></span>](popup-how-to-topics.md)
