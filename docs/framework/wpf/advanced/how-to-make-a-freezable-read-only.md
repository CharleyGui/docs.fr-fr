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
# <a name="how-to-make-a-freezable-read-only"></a>Comment : mettre un Freezable en lecture seule
Cet exemple montre comment rendre un <xref:System.Windows.Freezable> en lecture seule en appelant sa méthode <xref:System.Windows.Freezable.Freeze%2A>.  
  
 Vous ne pouvez pas geler un objet <xref:System.Windows.Freezable> si l’une des conditions suivantes est `true` à propos de l’objet :  
  
- Il a des propriétés animées ou liées aux données.  
  
- Elle possède des propriétés qui sont définies par une ressource dynamique. Pour plus d’informations sur les ressources dynamiques, consultez [ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Il contient <xref:System.Windows.Freezable> sous-objets qui ne peuvent pas être figés.  
  
 Si ces conditions sont `false` pour votre objet <xref:System.Windows.Freezable> et que vous n’envisagez pas de la modifier, pensez à la figer pour obtenir des avantages en matière de performances.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant gèle un <xref:System.Windows.Media.SolidColorBrush>, qui est un type d' <xref:System.Windows.Freezable> objet.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Pour plus d’informations sur les objets <xref:System.Windows.Freezable>, consultez [vue d’ensemble des objets Freezable](freezable-objects-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [Vue d’ensemble des objets Freezable](freezable-objects-overview.md)
- [Rubriques de guide pratique](base-elements-how-to-topics.md)
