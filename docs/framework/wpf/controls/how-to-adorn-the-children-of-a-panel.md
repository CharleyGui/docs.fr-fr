---
title: 'Procédure : Orner les enfants d’un panneau'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 739ccaa0273e66c4650c35217a1156d64336dbbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923527"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="a79fa-102">Procédure : Orner les enfants d’un panneau</span><span class="sxs-lookup"><span data-stu-id="a79fa-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="a79fa-103">Cet exemple montre comment lier par programmation un ornement aux enfants d’un spécifié <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="a79fa-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a79fa-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a79fa-104">Example</span></span>  
 <span data-ttu-id="a79fa-105">Pour lier un ornement aux enfants d’un <xref:System.Windows.Controls.Panel>, procédez comme suit:</span><span class="sxs-lookup"><span data-stu-id="a79fa-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="a79fa-106">Déclarez un <xref:System.Windows.Documents.AdornerLayer> nouvel objet et appelez `static` la <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> méthode pour rechercher une couche d’ornement pour l’élément dont les enfants doivent être ornés.</span><span class="sxs-lookup"><span data-stu-id="a79fa-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="a79fa-107">Énumérez les enfants de l’élément parent et appelez la <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier un ornement à chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="a79fa-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="a79fa-108">L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) aux enfants d’un <xref:System.Windows.Controls.StackPanel> *myStackPanel*nommé.</span><span class="sxs-lookup"><span data-stu-id="a79fa-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
> <span data-ttu-id="a79fa-109">L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="a79fa-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79fa-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a79fa-110">See also</span></span>

- [<span data-ttu-id="a79fa-111">Vue d’ensemble des ornements</span><span class="sxs-lookup"><span data-stu-id="a79fa-111">Adorners Overview</span></span>](adorners-overview.md)
