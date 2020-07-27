---
title: "Comment : positionner les éléments enfants d'une grille"
description: Découvrez comment utiliser les méthodes d’obtention et de définition définies sur une grille Windows Presentation Foundation pour positionner des éléments enfants.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167390"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="47ef2-103">Comment : positionner les éléments enfants d'une grille</span><span class="sxs-lookup"><span data-stu-id="47ef2-103">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="47ef2-104">Cet exemple montre comment utiliser les méthodes d’obtention et de définition définies sur <xref:System.Windows.Controls.Grid> pour positionner des éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="47ef2-104">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ef2-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="47ef2-105">Example</span></span>  
 <span data-ttu-id="47ef2-106">L’exemple suivant définit un <xref:System.Windows.Controls.Grid> élément parent ( `grid1` ) qui comporte trois colonnes et trois lignes.</span><span class="sxs-lookup"><span data-stu-id="47ef2-106">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="47ef2-107">Un <xref:System.Windows.Shapes.Rectangle> élément enfant ( `rect1` ) est ajouté à la <xref:System.Windows.Controls.Grid> position de colonne zéro, à la position de ligne zéro.</span><span class="sxs-lookup"><span data-stu-id="47ef2-107">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="47ef2-108"><xref:System.Windows.Controls.Button>les éléments représentent des méthodes qui peuvent être appelées pour repositionner l' <xref:System.Windows.Shapes.Rectangle> élément dans le <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="47ef2-108"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="47ef2-109">Quand un utilisateur clique sur un bouton, la méthode associée est activée.</span><span class="sxs-lookup"><span data-stu-id="47ef2-109">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="47ef2-110">L’exemple de code-behind suivant gère les méthodes que <xref:System.Windows.Controls.Primitives.ButtonBase.Click> déclenchent les événements de bouton.</span><span class="sxs-lookup"><span data-stu-id="47ef2-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="47ef2-111">L’exemple écrit ces appels de méthode aux <xref:System.Windows.Controls.TextBlock> éléments qui utilisent des méthodes d’extraction associées pour générer en sortie les nouvelles valeurs de propriété sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="47ef2-111">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="47ef2-112">Voici le résultat final !</span><span class="sxs-lookup"><span data-stu-id="47ef2-112">Here is the finished result!</span></span>

 ![une capture d’écran illustre une interface utilisateur WPF avec deux colonnes, la partie droite a une grille 3 x 3 et la gauche a des boutons pour déplacer un rectangle de couleur entre les colonnes et les lignes de la grille](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="47ef2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47ef2-114">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="47ef2-115">Vue d'ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="47ef2-115">Panels Overview</span></span>](panels-overview.md)
