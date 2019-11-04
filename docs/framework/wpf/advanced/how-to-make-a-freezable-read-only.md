---
title: 'Comment : mettre un Freezable en lecture seule'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460073"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="ed335-102">Comment : mettre un Freezable en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ed335-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="ed335-103">Cet exemple montre comment rendre un <xref:System.Windows.Freezable> en lecture seule en appelant sa méthode <xref:System.Windows.Freezable.Freeze%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed335-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="ed335-104">Vous ne pouvez pas geler un objet <xref:System.Windows.Freezable> si l’une des conditions suivantes est `true` à propos de l’objet :</span><span class="sxs-lookup"><span data-stu-id="ed335-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="ed335-105">Il a des propriétés animées ou liées aux données.</span><span class="sxs-lookup"><span data-stu-id="ed335-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="ed335-106">Elle possède des propriétés qui sont définies par une ressource dynamique.</span><span class="sxs-lookup"><span data-stu-id="ed335-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="ed335-107">Pour plus d’informations sur les ressources dynamiques, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="ed335-107">For more information about dynamic resources, see the [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
- <span data-ttu-id="ed335-108">Il contient <xref:System.Windows.Freezable> sous-objets qui ne peuvent pas être figés.</span><span class="sxs-lookup"><span data-stu-id="ed335-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="ed335-109">Si ces conditions sont `false` pour votre objet <xref:System.Windows.Freezable> et que vous n’envisagez pas de la modifier, pensez à la figer pour obtenir des avantages en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="ed335-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed335-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed335-110">Example</span></span>  
 <span data-ttu-id="ed335-111">L’exemple suivant gèle un <xref:System.Windows.Media.SolidColorBrush>, qui est un type d' <xref:System.Windows.Freezable> objet.</span><span class="sxs-lookup"><span data-stu-id="ed335-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="ed335-112">Pour plus d’informations sur les objets <xref:System.Windows.Freezable>, consultez [vue d’ensemble des objets Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ed335-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed335-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed335-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="ed335-114">Vue d’ensemble des objets Freezable</span><span class="sxs-lookup"><span data-stu-id="ed335-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="ed335-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="ed335-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
