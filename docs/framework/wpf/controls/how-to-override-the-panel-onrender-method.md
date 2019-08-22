---
title: 'Procédure : Substituer la méthode OnRender de Panel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666717"
---
# <a name="how-to-override-the-panel-onrender-method"></a><span data-ttu-id="177ae-102">Procédure : Substituer la méthode OnRender de Panel</span><span class="sxs-lookup"><span data-stu-id="177ae-102">How to: Override the Panel OnRender Method</span></span>
<span data-ttu-id="177ae-103">Cet exemple montre comment substituer la <xref:System.Windows.Controls.Panel.OnRender%2A> méthode de afin d’ajouter des <xref:System.Windows.Controls.Panel> effets graphiques personnalisés à un élément Layout.</span><span class="sxs-lookup"><span data-stu-id="177ae-103">This example shows how to override the <xref:System.Windows.Controls.Panel.OnRender%2A> method of <xref:System.Windows.Controls.Panel> in order to add custom graphical effects to a layout element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="177ae-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="177ae-104">Example</span></span>  
 <span data-ttu-id="177ae-105">Utilisez la <xref:System.Windows.Controls.Panel.OnRender%2A> méthode pour ajouter des effets graphiques à un élément Panel rendu.</span><span class="sxs-lookup"><span data-stu-id="177ae-105">Use the <xref:System.Windows.Controls.Panel.OnRender%2A> method in order to add graphical effects to a rendered panel element.</span></span> <span data-ttu-id="177ae-106">Par exemple, vous pouvez utiliser cette méthode pour ajouter des effets de bordure ou d’arrière-plan personnalisés.</span><span class="sxs-lookup"><span data-stu-id="177ae-106">For example, you can use this method to add custom border or background effects.</span></span> <span data-ttu-id="177ae-107">Un <xref:System.Windows.Media.DrawingContext> objet est passé comme argument, qui fournit des méthodes pour dessiner des formes, du texte, des images ou des vidéos.</span><span class="sxs-lookup"><span data-stu-id="177ae-107">A <xref:System.Windows.Media.DrawingContext> object is passed as an argument, which provides methods for drawing shapes, text, images, or videos.</span></span> <span data-ttu-id="177ae-108">Par conséquent, cette méthode est utile pour la personnalisation d’un objet Panel.</span><span class="sxs-lookup"><span data-stu-id="177ae-108">As a result, this method is useful for customization of a panel object.</span></span>  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="177ae-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="177ae-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="177ae-110">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="177ae-110">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="177ae-111">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="177ae-111">How-to Topics</span></span>](panel-how-to-topics.md)
