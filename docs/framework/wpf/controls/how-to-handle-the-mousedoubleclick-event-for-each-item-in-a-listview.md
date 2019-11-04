---
title: "Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460230"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView
Pour gérer un événement pour un élément dans un <xref:System.Windows.Controls.ListView>, vous devez ajouter un gestionnaire d’événements à chaque <xref:System.Windows.Controls.ListViewItem>. Lorsqu’un <xref:System.Windows.Controls.ListView> est lié à une source de données, vous ne créez pas explicitement de <xref:System.Windows.Controls.ListViewItem>, mais vous pouvez gérer l’événement pour chaque élément en ajoutant un <xref:System.Windows.EventSetter> à un style de <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un <xref:System.Windows.Controls.ListView> lié aux données et crée un <xref:System.Windows.Style> pour ajouter un gestionnaire d’événements à chaque <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 L’exemple suivant gère l’événement <xref:System.Windows.Controls.Control.MouseDoubleClick>.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Bien qu’il soit plus courant de lier un <xref:System.Windows.Controls.ListView> à une source de données, vous pouvez utiliser un style pour ajouter un gestionnaire d’événements à chaque <xref:System.Windows.Controls.ListViewItem> dans un <xref:System.Windows.Controls.ListView> non lié aux données, que vous ayez explicitement ou non créé un <xref:System.Windows.Controls.ListViewItem>.  Pour plus d’informations sur les contrôles <xref:System.Windows.Controls.ListViewItem> créés explicitement et implicitement, consultez <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlElement>
- [Vue d’ensemble de la liaison de données](../data/data-binding-overview.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Vue d’ensemble de ListView](listview-overview.md)
