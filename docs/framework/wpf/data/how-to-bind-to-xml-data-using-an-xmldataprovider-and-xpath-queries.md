---
title: 'Procédure : Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: dc4fb2d5f0c48c077d2ff7ca5e5269ce5cba71e5
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400488"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Procédure : Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath
Cet exemple montre comment effectuer une liaison [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] à des données <xref:System.Windows.Data.XmlDataProvider>à l’aide d’un.  
  
 Avec un <xref:System.Windows.Data.XmlDataProvider>, les données sous-jacentes accessibles via la liaison de données dans votre application peuvent correspondre à n' [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] importe quelle arborescence de nœuds. En d’autres termes, <xref:System.Windows.Data.XmlDataProvider> un offre un moyen pratique d’utiliser n’importe [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] quelle arborescence de nœuds comme source de liaison.  
  
## <a name="example"></a>Exemples  
 Dans l’exemple suivant, les données sont incorporées directement en [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] tant qu' *îlot* de <xref:System.Windows.FrameworkElement.Resources%2A> données dans la section. Un îlot de données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] doit être encapsulé dans des balises `<x:XData>` et toujours avoir un nœud racine unique (*Inventory* dans cet exemple).  
  
> [!NOTE]
>  Le nœud racine des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] est un attribut **xmlns** qui définit l’espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] sur une chaîne vide. Il s’agit d’une condition requise pour appliquer des requêtes XPath à un îlot de données inline dans la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Dans ce cas Inline, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], et par conséquent l’îlot de données, hérite de l’espace de <xref:System.Windows> noms. Pour cette raison, vous devez définir l’espace de noms comme vide pour empêcher les requêtes XPath d’être <xref:System.Windows> qualifiées par l’espace de noms, ce qui entraînerait une inversion des requêtes.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Comme indiqué dans cet exemple, pour créer la même déclaration de liaison dans la syntaxe d’attribut, vous devez échapper les caractères spéciaux correctement. Pour plus d’informations, consultez [Entités de caractères XML et XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Le <xref:System.Windows.Controls.ListBox> affiche les éléments suivants lorsque cet exemple est exécuté. Il s’agit de tous les objets *Title*s de tous les éléments sous *Books* ayant une valeur *Stock* de *« out »* ou une valeur *Number* de 3 ou supérieure ou égale à 8. Notez qu’aucun élément *CD* n’est retourné, <xref:System.Windows.Data.XmlDataProvider.XPath%2A> car la valeur définie <xref:System.Windows.Data.XmlDataProvider> sur le indique que seuls les éléments *books* doivent être exposés (en définissant essentiellement un filtre).  
  
 ![Capture d’écran de l’exemple XPath montrant le titre de quatre livres.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 Dans cet exemple, les titres des livres s’affichent <xref:System.Windows.Data.Binding.XPath%2A> car le <xref:System.Windows.Controls.TextBlock> de la liaison <xref:System.Windows.DataTemplate> dans la est défini sur «*title*». Si vous souhaitez afficher la valeur d’un attribut, telle que le numéro *ISBN*, vous devez définir cette <xref:System.Windows.Data.Binding.XPath%2A> valeur sur «`@ISBN`».  
  
 Les propriétés **XPath** dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont gérées par la méthode XmlNode.SelectNodes. Vous pouvez modifier les requêtes **XPath** pour obtenir des résultats différents. Voici quelques exemples pour la <xref:System.Windows.Data.Binding.XPath%2A> requête sur la limite <xref:System.Windows.Controls.ListBox> de l’exemple précédent:  
  
- `XPath="Book[1]"` retourne le premier élément d’ouvrage (« XML in Action »). Notez que les index **XPath** sont basés sur 1, et non sur 0.  
  
- `XPath="Book[@*]"` retourne tous les éléments d’ouvrage avec des attributs.  
  
- `XPath="Book[last()-1]"` retourne l’avant dernier élément d’ouvrage (« Introducing Microsoft .NET »).  
  
- `XPath="*[position()>3]"` retournera tous les éléments d’ouvrage, à l’exception des 3 premiers.  
  
 Lorsque vous exécutez une requête **XPath** , elle retourne un <xref:System.Xml.XmlNode> ou une liste de XMLNodes. <xref:System.Xml.XmlNode>est un objet Common Language Runtime (CLR), ce qui signifie que vous pouvez <xref:System.Windows.Data.Binding.Path%2A> utiliser la propriété pour établir une liaison avec les propriétés de Common Language Runtime (CLR). Regardez de nouveau l’exemple précédent. Si le reste de l’exemple reste le même et que vous remplacez <xref:System.Windows.Controls.TextBlock> la liaison par ce qui suit, vous verrez les noms du XMLNodes retourné dans <xref:System.Windows.Controls.ListBox>le. Dans ce cas, le nom de tous les nœuds retournés est « *Book* ».  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Dans certaines applications, l’incorporation du [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] comme îlot de données dans la source de la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peut être gênante, car le contenu exact des données doit être connu au moment de la compilation. Par conséquent, l’obtention de données à partir d’un fichier [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] externe est également prise en charge, comme dans l’exemple suivant :  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Si les [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données résident dans un fichier distant [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] , vous devez définir l’accès aux données en affectant un approprié [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] à l' <xref:System.Windows.Data.XmlDataProvider.Source%2A> attribut comme suit:  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.ObjectDataProvider>
- [Effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Utiliser le modèle maître/détail avec des données XML hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Vue d'ensemble des sources de liaison](binding-sources-overview.md)
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
