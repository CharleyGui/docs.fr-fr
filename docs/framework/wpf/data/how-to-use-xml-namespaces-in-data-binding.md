---
title: 'Comment : utiliser des espaces de noms XML dans la liaison de données'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 47ce0d951df39c7b60aa2a543baf845f5471de6c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460304"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Comment : utiliser des espaces de noms XML dans la liaison de données
## <a name="example"></a>Exemple
 Cet exemple montre comment gérer les espaces de noms spécifiés dans votre source de liaison [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].

 Si vos données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] contiennent la définition d’espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] suivante :

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Vous pouvez utiliser l’élément <xref:System.Windows.Data.XmlNamespaceMapping> pour mapper l’espace de noms à un <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, comme dans l’exemple suivant. Vous pouvez ensuite utiliser la <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pour faire référence à l’espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. L' <xref:System.Windows.Controls.ListBox> dans cet exemple affiche le *titre* et le *DC : date* de chaque *élément*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Notez que le <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> que vous spécifiez ne doit pas nécessairement correspondre à celui utilisé dans la source de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ; Si le préfixe change dans le [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] source, votre mappage fonctionne toujours.

 Dans cet exemple, les données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] proviennent d’un service Web, mais l’élément <xref:System.Windows.Data.XmlNamespaceMapping> fonctionne également avec des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ou [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] incorporées dans un fichier incorporé.

## <a name="see-also"></a>Voir aussi

- [Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
