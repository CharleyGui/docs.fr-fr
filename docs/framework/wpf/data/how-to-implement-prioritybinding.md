---
title: 'Comment : implémenter PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459781"
---
# <a name="how-to-implement-prioritybinding"></a>Comment : implémenter PriorityBinding
<xref:System.Windows.Data.PriorityBinding> dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionne en spécifiant une liste de liaisons. La liste des liaisons est classée de la priorité la plus élevée à la priorité la plus basse. Si la liaison de priorité la plus élevée retourne une valeur correctement lorsqu’elle est traitée, il n’est jamais nécessaire de traiter les autres liaisons de la liste. Cela peut être le cas où la liaison de priorité la plus élevée prend beaucoup de temps pour être évaluée, la priorité la plus élevée qui retourne une valeur avec succès sera utilisée jusqu’à ce qu’une liaison d’une priorité plus élevée retourne une valeur avec succès.  
  
## <a name="example"></a>Exemple  
 Pour illustrer le fonctionnement de <xref:System.Windows.Data.PriorityBinding>, l’objet `AsyncDataSource` a été créé avec les trois propriétés suivantes : `FastDP`, `SlowerDP`et `SlowestDP`.  
  
 L’accesseur Get de `FastDP` retourne la valeur du membre de données `_fastDP`.  
  
 L’accesseur Get de `SlowerDP` attend pendant 3 secondes avant de retourner la valeur du membre de données `_slowerDP`.  
  
 L’accesseur Get de `SlowestDP` attend 5 secondes avant de retourner la valeur du membre de données `_slowestDP`.  
  
> [!NOTE]
> L’exemple est uniquement fourni à des fins de démonstration. Les instructions .NET recommandent de définir des propriétés dont l’ordre est plus lent qu’un jeu de champs. Pour plus d’informations, consultez [choix entre les propriétés et les méthodes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 La propriété <xref:System.Windows.Controls.TextBlock.Text%2A> se lie aux `AsyncDS` ci-dessus à l’aide de <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Lorsque le moteur de liaison traite les objets <xref:System.Windows.Data.Binding>, il commence par le premier <xref:System.Windows.Data.Binding>, qui est lié à la propriété `SlowestDP`. Lorsque cette <xref:System.Windows.Data.Binding> est traitée, elle ne retourne pas de valeur avec succès, car elle est en veille pendant 5 secondes, de sorte que l’élément <xref:System.Windows.Data.Binding> suivant est traité. La <xref:System.Windows.Data.Binding> suivante ne retourne pas de valeur avec succès, car elle est en veille pendant 3 secondes. Le moteur de liaison se déplace ensuite sur l’élément de <xref:System.Windows.Data.Binding> suivant, qui est lié à la propriété `FastDP`. Cette <xref:System.Windows.Data.Binding> retourne la valeur « Fast Value ». La <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « Fast Value ».  
  
 Au bout de 3 secondes, la propriété `SlowerDP` retourne la valeur « plus lente ». Le <xref:System.Windows.Controls.TextBlock> affiche ensuite la valeur « valeur plus lente ».  
  
 Une fois 5 secondes écoulées, la propriété `SlowestDP` retourne la valeur « la valeur la plus lente ». Cette liaison a la priorité la plus élevée, car elle est listée en premier. Le <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « valeur la plus lente ».  
  
 Consultez <xref:System.Windows.Data.PriorityBinding> pour plus d’informations sur ce qui est considéré comme une valeur de retour réussie d’une liaison.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
