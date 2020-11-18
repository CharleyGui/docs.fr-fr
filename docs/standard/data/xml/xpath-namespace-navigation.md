---
title: Navigation entre espaces de noms XPath
ms.date: 03/30/2017
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: 4d2ef71a41d19fd5bb573afab66dc8a15e19c393
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831206"
---
# <a name="xpath-namespace-navigation"></a>Navigation entre espaces de noms XPath
Pour utiliser les requêtes XPath avec des documents XML, vous devez adresser correctement les espaces de noms XML et les éléments contenus dans ces espaces de noms. Les espaces de noms empêchent toute ambiguïté pouvant survenir lorsque des noms sont utilisés dans plusieurs contextes ; par exemple, le nom `ID` peut faire référence à plusieurs identificateurs associés à différents éléments d'un document XML. La syntaxe des espaces de noms spécifie des URI, des noms et des préfixes qui distinguent les éléments d'un document XML.  
  
 L'exemple fourni dans cette rubrique illustre l'utilisation des préfixes pour la navigation dans un document XML avec <xref:System.Xml.XPath.XPathNavigator>. Pour plus d’informations sur les espaces de noms et la syntaxe, consultez [fichiers XML : présentation des espaces de noms XML](/previous-versions/dotnet/articles/bb986013(v=msdn.10)).  
  
## <a name="namespace-declarations"></a>Déclarations d'espace de noms  
 Les déclarations d'espaces de noms permettent de distinguer et d'adresser les éléments d'un document XML lors de l'utilisation d'une instance de <xref:System.Xml.XPath.XPathNavigator>. Les préfixes d'espaces de noms fournissent une syntaxe courte pour l'adressage des espaces de noms.  
  
 Les préfixes sont définis par la forme : `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` Dans cette syntaxe, le préfixe « `e` » est une abréviation de l'URI formel de l'espace de noms. Vous pouvez identifier l'élément `Body` en tant que membre de l'espace de noms `Envelope` à l'aide de la syntaxe suivante : `e:Body`.  
  
 Le document XML suivant sera référencé en tant que `response.xml` dans l'exemple de navigation de la section suivante.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a>Navigation par préfixe d'espace de noms  
 Le code fourni dans cette section utilise les objets <xref:System.Xml.XPath.XPathNavigator> et <xref:System.Xml.XmlNamespaceManager> pour sélectionner l'élément `Search` à partir du document XML dans la section précédente. La requête `xpath` inclut des préfixes d’espaces de noms dans chaque élément du chemin d’accès. La spécification de l'identité précise des espaces de noms qui contiennent chaque élément permet d'assurer une navigation correcte jusqu'à l'élément `Search` par la méthode <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>.  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 La précision des espaces de noms et des noms qualifiés complets va au-delà du caractère pratique. En prenant la définition de document et le code des exemples précédents, vous constaterez qu'une navigation sans noms d'éléments qualifiés complets lève des exceptions. Par exemple, la définition d'élément `<Search xmlns="http://schemas.microsoft.com/v1/Search">` et la requête de chaîne `xpath = "/s:Envelope/s:Body/Search";` sans préfixe d'espace de noms pour l'élément `Search` retournent `null` à la place de l'élément `Search`.  
  
## <a name="see-also"></a>Voir aussi

- [Accès à des données XML à l’aide de XPathNavigator](accessing-xml-data-using-xpathnavigator.md)
- [Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
