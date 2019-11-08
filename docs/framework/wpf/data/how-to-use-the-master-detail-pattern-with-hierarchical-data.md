---
title: 'Comment : utiliser le modèle maître/détail avec des données hiérarchiques'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e4183ddc3868a1568662853b46e05348df129092
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733485"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>Comment : utiliser le modèle maître/détail avec des données hiérarchiques
Cet exemple montre comment implémenter le scénario maître/détail.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, `LeagueList` est une collection de `Leagues`. Chaque `League` a un `Name` et une collection d' `Divisions`, et chaque `Division` a un nom et une collection d' `Teams`. Chaque `Team` a un nom d’équipe.  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 Voici une capture d’écran de l’exemple. Le `Divisions` <xref:System.Windows.Controls.ListBox> effectue automatiquement le suivi des sélections dans le <xref:System.Windows.Controls.ListBox> de `Leagues` et affiche les données correspondantes. Le `Teams` <xref:System.Windows.Controls.ListBox> effectue le suivi des sélections dans les deux autres contrôles <xref:System.Windows.Controls.ListBox>.  
  
 ![Capture d’écran montrant un&#45;exemple de scénario maître détaillé.](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 Les deux points à noter dans cet exemple sont les suivants :  
  
1. Les trois contrôles <xref:System.Windows.Controls.ListBox> sont liés à la même source. Vous définissez la propriété <xref:System.Windows.Data.Binding.Path%2A> de la liaison pour spécifier le niveau de données que vous souhaitez que le <xref:System.Windows.Controls.ListBox> affiche.  
  
2. Vous devez définir la propriété <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> sur `true` sur les contrôles <xref:System.Windows.Controls.ListBox> dont vous effectuez le suivi. La définition de cette propriété permet de s’assurer que l’élément sélectionné est toujours défini en tant que <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Sinon, si le <xref:System.Windows.Controls.ListBox> obtient des données à partir d’un <xref:System.Windows.Data.CollectionViewSource>, il synchronise automatiquement la sélection et la devise.  
  
 La technique est légèrement différente quand vous utilisez des données XML. Pour obtenir un exemple, consultez [utiliser le modèle maître/détail avec des données XML hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.HierarchicalDataTemplate>
- [Effectuer une liaison à une collection et afficher des informations basées sur la sélection](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des modèles de données](data-templating-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
