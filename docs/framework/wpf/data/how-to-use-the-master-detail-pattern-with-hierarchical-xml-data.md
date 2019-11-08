---
title: 'Comment : utiliser le modèle maître/détail avec des données XML hiérarchiques'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733411"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>Comment : utiliser le modèle maître/détail avec des données XML hiérarchiques
Cet exemple montre comment implémenter le scénario maître/détail avec des données XML.  
  
## <a name="example"></a>Exemple  
 Cet exemple est la version de données XML de l’exemple décrit dans [utiliser le modèle maître/détail avec des données hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dans cet exemple, les données proviennent du fichier `League.xml`. Notez comment le troisième contrôle <xref:System.Windows.Controls.ListBox> suit les modifications apportées à la sélection dans la deuxième <xref:System.Windows.Controls.ListBox> en effectuant une liaison à sa propriété <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>.  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.HierarchicalDataTemplate>
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
