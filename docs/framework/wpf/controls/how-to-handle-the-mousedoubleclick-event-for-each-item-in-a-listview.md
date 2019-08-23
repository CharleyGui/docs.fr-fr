---
title: 'Procédure : Gérer l’événement MouseDoubleClick pour chaque élément d’un ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962060"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Procédure : Gérer l’événement MouseDoubleClick pour chaque élément d’un ListView
Pour gérer un événement pour un élément dans un <xref:System.Windows.Controls.ListView>, vous devez ajouter un gestionnaire d’événements à chacun <xref:System.Windows.Controls.ListViewItem>. Quand un <xref:System.Windows.Controls.ListView> est lié à une source de données, vous ne créez pas <xref:System.Windows.Controls.ListViewItem>explicitement un, mais vous pouvez gérer l’événement pour chaque élément en <xref:System.Windows.EventSetter> ajoutant un à un style <xref:System.Windows.Controls.ListViewItem>de.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un lié <xref:System.Windows.Controls.ListView> aux données et crée un <xref:System.Windows.Style> pour ajouter un gestionnaire d’événements à chacun. <xref:System.Windows.Controls.ListViewItem>  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 L’exemple suivant gère l' <xref:System.Windows.Controls.Control.MouseDoubleClick> événement.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Bien qu’il soit plus courant de lier <xref:System.Windows.Controls.ListView> un à une source de données, vous pouvez utiliser un style pour ajouter un gestionnaire d' <xref:System.Windows.Controls.ListViewItem> événements à chaque dans un non lié <xref:System.Windows.Controls.ListView> aux données, que vous ayez ou <xref:System.Windows.Controls.ListViewItem>non explicitement créé un.  Pour plus d’informations sur les contrôles créés <xref:System.Windows.Controls.ListViewItem> explicitement et implicitement, consultez. <xref:System.Windows.Controls.ItemsControl>  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlElement>
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Application d’un style et création de modèles](styling-and-templating.md)
- [Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Vue d’ensemble de ListView](listview-overview.md)
