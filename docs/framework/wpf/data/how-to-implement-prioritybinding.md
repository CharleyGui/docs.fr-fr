---
title: 'Procédure : Implémenter PriorityBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: ad19db9d686469e3ade1ff188553fceb8d525674
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937442"
---
# <a name="how-to-implement-prioritybinding"></a>Procédure : Implémenter PriorityBinding
<xref:System.Windows.Data.PriorityBinding>dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionne en spécifiant une liste de liaisons. La liste des liaisons est classée de la priorité la plus élevée à la priorité la plus basse. Si la liaison de priorité la plus élevée retourne une valeur correctement lorsqu’elle est traitée, il n’est jamais nécessaire de traiter les autres liaisons de la liste. Cela peut être le cas où la liaison de priorité la plus élevée prend beaucoup de temps pour être évaluée, la priorité la plus élevée qui retourne une valeur avec succès sera utilisée jusqu’à ce qu’une liaison d’une priorité plus élevée retourne une valeur avec succès.  
  
## <a name="example"></a>Exemples  
 Pour illustrer <xref:System.Windows.Data.PriorityBinding> le fonctionnement de `AsyncDataSource` , l’objet a été créé avec les trois propriétés `FastDP`suivantes `SlowerDP`:, `SlowestDP`et.  
  
 L’accesseur get `FastDP` de retourne la valeur `_fastDP` du membre de données.  
  
 L’accesseur get `SlowerDP` de attend pendant 3 secondes avant de retourner la valeur `_slowerDP` du membre de données.  
  
 L’accesseur get `SlowestDP` de attend cinq secondes avant de retourner la valeur `_slowestDP` du membre de données.  
  
> [!NOTE]
> L’exemple est uniquement fourni à des fins de démonstration. Les [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] instructions recommandent de définir des propriétés dont l’ordre de grandeur est plus lent qu’un jeu de champs. Pour plus d’informations, consultez [choix entre les propriétés et les méthodes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 La <xref:System.Windows.Controls.TextBlock.Text%2A> propriété est liée à la classe `AsyncDS` ci <xref:System.Windows.Data.PriorityBinding>-dessus à l’aide de:  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Lorsque le moteur de liaison traite <xref:System.Windows.Data.Binding> les objets, il commence par le <xref:System.Windows.Data.Binding>premier, qui est lié à `SlowestDP` la propriété. Lorsque cette <xref:System.Windows.Data.Binding> opération est traitée, elle ne retourne pas de valeur avec succès, car elle est en veille pendant 5 secondes <xref:System.Windows.Data.Binding> , de sorte que l’élément suivant est traité. Le suivant <xref:System.Windows.Data.Binding> ne retourne pas de valeur avec succès, car il est en veille pendant 3 secondes. Le moteur de liaison se déplace ensuite sur <xref:System.Windows.Data.Binding> l’élément suivant, qui est lié `FastDP` à la propriété. La valeur «Fast Value» est retournée.<xref:System.Windows.Data.Binding> Le <xref:System.Windows.Controls.TextBlock> affiche désormais la valeur «Fast Value».  
  
 Au bout de 3 secondes, la `SlowerDP` propriété retourne la valeur «valeur plus lente». Le <xref:System.Windows.Controls.TextBlock> affiche ensuite la valeur «valeur plus lente».  
  
 Après 5 secondes, la `SlowestDP` propriété retourne la valeur «la valeur la plus lente». Cette liaison a la priorité la plus élevée, car elle est listée en premier. Le <xref:System.Windows.Controls.TextBlock> affiche désormais la valeur «valeur la plus lente».  
  
 Pour <xref:System.Windows.Data.PriorityBinding> plus d’informations sur ce qui est considéré comme une valeur de retour réussie d’une liaison, consultez.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
