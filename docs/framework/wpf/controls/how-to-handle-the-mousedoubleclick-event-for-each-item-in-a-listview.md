---
title: "Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646112"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Comment : gérer l'événement MouseDoubleClick pour chaque élément d'un ListView
Pour gérer un événement pour <xref:System.Windows.Controls.ListView>un élément dans un , <xref:System.Windows.Controls.ListViewItem>vous devez ajouter un gestionnaire d’événement à chaque . Lorsque <xref:System.Windows.Controls.ListView> l’a est lié à une source <xref:System.Windows.Controls.ListViewItem>de données, vous ne créez pas <xref:System.Windows.EventSetter> explicitement un , <xref:System.Windows.Controls.ListViewItem>mais vous pouvez gérer l’événement pour chaque élément en ajoutant un style d’un .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée <xref:System.Windows.Controls.ListView> une limite <xref:System.Windows.Style> de données et <xref:System.Windows.Controls.ListViewItem>crée un pour ajouter un gestionnaire d’événements à chacun .  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 L’exemple suivant <xref:System.Windows.Controls.Control.MouseDoubleClick> traite de l’événement.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Bien qu’il soit <xref:System.Windows.Controls.ListView> plus courant de lier une source de données <xref:System.Windows.Controls.ListViewItem> à une source de <xref:System.Windows.Controls.ListView> données, vous pouvez <xref:System.Windows.Controls.ListViewItem>utiliser un style pour ajouter un gestionnaire d’événements à chacun dans un non-data-lié indépendamment du fait que vous créez explicitement un .  Pour plus d’informations sur <xref:System.Windows.Controls.ListViewItem> les <xref:System.Windows.Controls.ItemsControl>contrôles explicitement et implicitement créés, voir .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlElement>
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Lier aux données XML à l’aide d’un XMLDataProvider et XPath Requêtes](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Vue d’ensemble de ListView](listview-overview.md)
