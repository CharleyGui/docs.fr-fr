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
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Comment : positionner les éléments enfants d'une grille
Cet exemple montre comment utiliser les méthodes d’obtenir et de définir qui sont définies sur <xref:System.Windows.Controls.Grid> la position des éléments de l’enfant.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant définit <xref:System.Windows.Controls.Grid> un`grid1`élément parent ( ) qui a trois colonnes et trois rangées. Un <xref:System.Windows.Shapes.Rectangle> élément`rect1`enfant ( ) <xref:System.Windows.Controls.Grid> est ajouté à la position de colonne zéro, position de ligne zéro. <xref:System.Windows.Controls.Button>éléments représentent des méthodes qui <xref:System.Windows.Shapes.Rectangle> peuvent être <xref:System.Windows.Controls.Grid>appelées à repositionner l’élément dans le . Lorsqu’un utilisateur clique sur un bouton, la méthode connexe est activée.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 L’exemple de code-derrière suivant gère <xref:System.Windows.Controls.Primitives.ButtonBase.Click> les méthodes que les événements de bouton soulèvent. L’exemple écrit ces <xref:System.Windows.Controls.TextBlock> appels de méthode aux éléments qui emploient des méthodes connexes obtenir pour produire les nouvelles valeurs de propriété comme des chaînes.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Voici le résultat final!

 ![une capture d’écran représente une interface utilisateur WPF avec deux colonnes, le côté droit a une grille 3 x 3 et la gauche a des boutons pour déplacer un rectangle coloré entre les colonnes et les rangées de la grille](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Grid>
- [Vue d’ensemble de Panel](panels-overview.md)
