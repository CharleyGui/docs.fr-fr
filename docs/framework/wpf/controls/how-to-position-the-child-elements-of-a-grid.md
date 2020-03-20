---
title: "Comment : positionner les éléments enfants d'une grille"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186718"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="44309-102">Comment : positionner les éléments enfants d'une grille</span><span class="sxs-lookup"><span data-stu-id="44309-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="44309-103">Cet exemple montre comment utiliser les méthodes d’obtenir et de définir qui sont définies sur <xref:System.Windows.Controls.Grid> la position des éléments de l’enfant.</span><span class="sxs-lookup"><span data-stu-id="44309-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44309-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="44309-104">Example</span></span>  
 <span data-ttu-id="44309-105">L’exemple suivant définit <xref:System.Windows.Controls.Grid> un`grid1`élément parent ( ) qui a trois colonnes et trois rangées.</span><span class="sxs-lookup"><span data-stu-id="44309-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="44309-106">Un <xref:System.Windows.Shapes.Rectangle> élément`rect1`enfant ( ) <xref:System.Windows.Controls.Grid> est ajouté à la position de colonne zéro, position de ligne zéro.</span><span class="sxs-lookup"><span data-stu-id="44309-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="44309-107"><xref:System.Windows.Controls.Button>éléments représentent des méthodes qui <xref:System.Windows.Shapes.Rectangle> peuvent être <xref:System.Windows.Controls.Grid>appelées à repositionner l’élément dans le .</span><span class="sxs-lookup"><span data-stu-id="44309-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="44309-108">Lorsqu’un utilisateur clique sur un bouton, la méthode connexe est activée.</span><span class="sxs-lookup"><span data-stu-id="44309-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="44309-109">L’exemple de code-derrière suivant gère <xref:System.Windows.Controls.Primitives.ButtonBase.Click> les méthodes que les événements de bouton soulèvent.</span><span class="sxs-lookup"><span data-stu-id="44309-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="44309-110">L’exemple écrit ces <xref:System.Windows.Controls.TextBlock> appels de méthode aux éléments qui emploient des méthodes connexes obtenir pour produire les nouvelles valeurs de propriété comme des chaînes.</span><span class="sxs-lookup"><span data-stu-id="44309-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="44309-111">Voici le résultat final!</span><span class="sxs-lookup"><span data-stu-id="44309-111">Here is the finished result!</span></span>

 ![une capture d’écran représente une interface utilisateur WPF avec deux colonnes, le côté droit a une grille 3 x 3 et la gauche a des boutons pour déplacer un rectangle coloré entre les colonnes et les rangées de la grille](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="44309-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44309-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="44309-114">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="44309-114">Panels Overview</span></span>](panels-overview.md)
