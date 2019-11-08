---
title: "Comment : effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath"
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: f075d646539de5d68e1c9c75d9664451125e9919
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733554"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>Comment : effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath
Cet exemple montre comment effectuer une liaison à des données XML à l’aide d’un <xref:System.Windows.Data.XmlDataProvider>.  
  
 Avec un <xref:System.Windows.Data.XmlDataProvider>, les données sous-jacentes accessibles via la liaison de données dans votre application peuvent correspondre à n’importe quelle arborescence de nœuds XML. En d’autres termes, une <xref:System.Windows.Data.XmlDataProvider> offre un moyen pratique d’utiliser n’importe quelle arborescence de nœuds XML en tant que source de liaison.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les données sont incorporées directement sous la forme d’un *îlot de données* XML dans la section <xref:System.Windows.FrameworkElement.Resources%2A>. Un îlot de données XML doit être encapsulé dans des balises `<x:XData>` et avoir toujours un seul nœud racine, qui est un *inventaire* dans cet exemple.  
  
> [!NOTE]
> Le nœud racine des données XML a un attribut **xmlns** qui définit l’espace de noms XML sur une chaîne vide. Il s’agit d’une condition requise pour appliquer des requêtes XPath à un îlot de données inline dans la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Dans ce cas Inline, l' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], et donc l’îlot de données, hérite de l’espace de noms <xref:System.Windows>. Pour cette raison, vous devez définir l’espace de noms comme vide pour empêcher les requêtes XPath d’être qualifiées par l’espace de noms <xref:System.Windows>, ce qui entraînerait une inversion des requêtes.  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Comme indiqué dans cet exemple, pour créer la même déclaration de liaison dans la syntaxe d’attribut, vous devez échapper les caractères spéciaux correctement. Pour plus d’informations, consultez [Entités de caractères XML et XAML](../../xaml-services/xml-character-entities-and-xaml.md).  
  
 Le <xref:System.Windows.Controls.ListBox> affiche les éléments suivants lorsque cet exemple est exécuté. Il s’agit de tous les objets *Title*s de tous les éléments sous *Books* ayant une valeur *Stock* de *« out »* ou une valeur *Number* de 3 ou supérieure ou égale à 8. Notez qu’aucun élément *CD* n’est retourné, car la valeur <xref:System.Windows.Data.XmlDataProvider.XPath%2A> définie sur la <xref:System.Windows.Data.XmlDataProvider> indique que seuls les éléments *books* doivent être exposés (en définissant un filtre de façon générale).  
  
 ![Capture d’écran de l’exemple XPath montrant le titre de quatre livres.](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 Dans cet exemple, les titres des livres s’affichent parce que la <xref:System.Windows.Data.Binding.XPath%2A> de la liaison <xref:System.Windows.Controls.TextBlock> dans le <xref:System.Windows.DataTemplate> est définie sur «*title*». Si vous souhaitez afficher la valeur d’un attribut, telle que le numéro *ISBN*, vous devez définir cette <xref:System.Windows.Data.Binding.XPath%2A> valeur sur «`@ISBN`».  
  
 Les propriétés **XPath** dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont gérées par la méthode XmlNode.SelectNodes. Vous pouvez modifier les requêtes **XPath** pour obtenir des résultats différents. Voici quelques exemples pour la requête <xref:System.Windows.Data.Binding.XPath%2A> sur les <xref:System.Windows.Controls.ListBox> liés de l’exemple précédent :  
  
- `XPath="Book[1]"` retourne le premier élément d’ouvrage (« XML in Action »). Notez que les index **XPath** sont basés sur 1, et non sur 0.  
  
- `XPath="Book[@*]"` retourne tous les éléments d’ouvrage avec des attributs.  
  
- `XPath="Book[last()-1]"` retourne l’avant dernier élément d’ouvrage (« Introducing Microsoft .NET »).  
  
- `XPath="*[position()>3]"` retournera tous les éléments d’ouvrage, à l’exception des 3 premiers.  
  
 Lorsque vous exécutez une requête **XPath** , elle retourne un <xref:System.Xml.XmlNode> ou une liste de XMLNodes. <xref:System.Xml.XmlNode> est un objet common language runtime (CLR), ce qui signifie que vous pouvez utiliser la propriété <xref:System.Windows.Data.Binding.Path%2A> pour établir une liaison avec les propriétés common language runtime (CLR). Regardez de nouveau l’exemple précédent. Si le reste de l’exemple reste le même et que vous modifiez la liaison de <xref:System.Windows.Controls.TextBlock> à ce qui suit, vous verrez les noms du XmlNodes retourné dans le <xref:System.Windows.Controls.ListBox>. Dans ce cas, le nom de tous les nœuds retournés est « *Book* ».  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Dans certaines applications, l’incorporation du XML en tant qu’îlot de données dans la source de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page peut être gênante, car le contenu exact des données doit être connu au moment de la compilation. Par conséquent, l’obtention des données à partir d’un fichier XML externe est également prise en charge, comme dans l’exemple suivant :  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Si les données XML résident dans un fichier XML distant, vous devez définir l’accès aux données en affectant une URL appropriée à l’attribut <xref:System.Windows.Data.XmlDataProvider.Source%2A> comme suit :  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.ObjectDataProvider>
- [Effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [Utiliser le modèle maître/détail avec des données XML hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Vue d'ensemble des sources de liaison](binding-sources-overview.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
