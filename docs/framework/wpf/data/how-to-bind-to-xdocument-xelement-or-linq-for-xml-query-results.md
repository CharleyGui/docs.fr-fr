---
title: 'Comment : effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920121"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Comment : effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML

Cet exemple montre comment lier des données XML à un <xref:System.Windows.Controls.ItemsControl> à l’aide de <xref:System.Xml.Linq.XDocument>.

## <a name="example"></a>Exemple

Le code XAML suivant définit une <xref:System.Windows.Controls.ItemsControl> et comprend un modèle de données pour les données de type `Planet` dans l’espace de noms XML `http://planetsNS`. Un type de données XML qui occupe un espace de noms doit inclure l’espace de noms entre accolades, et s’il s’affiche là où une extension de balisage XAML pourrait apparaître, il doit précéder l’espace de noms avec une séquence d’échappement d’accolades. Ce code crée une liaison avec les propriétés dynamiques qui correspondent aux méthodes <xref:System.Xml.Linq.XContainer.Element%2A> et <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement>. Les propriétés dynamiques permettent à XAML de se lier aux propriétés dynamiques qui partagent les noms des méthodes. Pour plus d’informations, consultez [LINQ to XML des propriétés dynamiques](linq-to-xml-dynamic-properties.md). Notez comment la déclaration d’espace de noms par défaut pour XML ne s’applique pas aux noms d’attribut.

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

Le code C# suivant appelle<xref:System.Xml.Linq.XDocument.Load%2A>et définit le contexte de données du panneau d’empilement sur tous les sous-éléments de l’élément nommé`SolarSystemPlanets`dans l’espace de noms XML`http://planetsNS`.

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

Les données XML peuvent être stockées sous forme de ressource XAML à l’aide de <xref:System.Windows.Data.ObjectDataProvider>. Pour obtenir un exemple complet, consultez [code source L2DBForm. Xaml](l2dbform-xaml-source-code.md). L’exemple suivant montre comment le code peut définir le contexte de données sur une ressource d’objet.

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

Les propriétés dynamiques qui sont mappées à <xref:System.Xml.Linq.XContainer.Element%2A> et <xref:System.Xml.Linq.XElement.Attribute%2A> offrent une certaine flexibilité dans XAML. Votre code peut également être lié aux résultats d’une requête LINQ to XML. Cet exemple se lie aux résultats de la requête triés par une valeur d’élément.

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des sources de liaison](binding-sources-overview.md)
- [Vue d’ensemble de la liaison de données WPF avec LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Exemple de liaison de données WPF à l’aide de LINQ to XML](linq-to-xml-data-binding-sample.md)
- [Propriétés dynamiques LINQ to XML](linq-to-xml-dynamic-properties.md)
