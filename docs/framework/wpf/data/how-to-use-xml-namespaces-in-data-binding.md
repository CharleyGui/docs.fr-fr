---
title: 'Comment : utiliser des espaces de noms XML dans la liaison de données'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740572"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Comment : utiliser des espaces de noms XML dans la liaison de données
## <a name="example"></a>Exemple
 Cet exemple montre comment gérer les espaces de noms spécifiés dans votre source de liaison XML.

 Si vos données XML comportent la définition d’espace de noms XML suivante :

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Vous pouvez utiliser l’élément <xref:System.Windows.Data.XmlNamespaceMapping> pour mapper l’espace de noms à un <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, comme dans l’exemple suivant. Vous pouvez ensuite utiliser la <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pour faire référence à l’espace de noms XML. L' <xref:System.Windows.Controls.ListBox> dans cet exemple affiche le *titre* et le *DC : date* de chaque *élément*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Notez que le <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> que vous spécifiez ne doit pas nécessairement correspondre à celui utilisé dans la source XML. Si le préfixe change dans la source XML, votre mappage fonctionne toujours.

 Dans cet exemple particulier, les données XML proviennent d’un service Web, mais l’élément <xref:System.Windows.Data.XmlNamespaceMapping> fonctionne également avec des données XML ou XML inline dans un fichier incorporé.

## <a name="see-also"></a>Voir aussi

- [Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
