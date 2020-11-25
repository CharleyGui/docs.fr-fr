---
title: Navigation entre espaces de noms XPath
ms.date: 03/30/2017
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: d5350f0c8f73c5efb0f7d9e4c492a841b4978c36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720891"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="4f207-102">Navigation entre espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="4f207-102">XPath Namespace Navigation</span></span>

<span data-ttu-id="4f207-103">Pour utiliser les requêtes XPath avec des documents XML, vous devez adresser correctement les espaces de noms XML et les éléments contenus dans ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="4f207-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="4f207-104">Les espaces de noms empêchent toute ambiguïté pouvant survenir lorsque des noms sont utilisés dans plusieurs contextes ; par exemple, le nom `ID` peut faire référence à plusieurs identificateurs associés à différents éléments d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="4f207-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="4f207-105">La syntaxe des espaces de noms spécifie des URI, des noms et des préfixes qui distinguent les éléments d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="4f207-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="4f207-106">L'exemple fourni dans cette rubrique illustre l'utilisation des préfixes pour la navigation dans un document XML avec <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4f207-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="4f207-107">Pour plus d’informations sur les espaces de noms et la syntaxe, consultez [fichiers XML : présentation des espaces de noms XML](/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="4f207-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="4f207-108">Déclarations d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="4f207-108">Namespace Declarations</span></span>  

 <span data-ttu-id="4f207-109">Les déclarations d'espaces de noms permettent de distinguer et d'adresser les éléments d'un document XML lors de l'utilisation d'une instance de <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="4f207-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="4f207-110">Les préfixes d'espaces de noms fournissent une syntaxe courte pour l'adressage des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="4f207-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="4f207-111">Les préfixes sont définis par la forme : `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` Dans cette syntaxe, le préfixe « `e` » est une abréviation de l'URI formel de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4f207-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="4f207-112">Vous pouvez identifier l'élément `Body` en tant que membre de l'espace de noms `Envelope` à l'aide de la syntaxe suivante : `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="4f207-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="4f207-113">Le document XML suivant sera référencé en tant que `response.xml` dans l'exemple de navigation de la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4f207-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="4f207-114">Navigation par préfixe d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="4f207-114">Navigation by Namespace Prefix</span></span>  

 <span data-ttu-id="4f207-115">Le code fourni dans cette section utilise les objets <xref:System.Xml.XPath.XPathNavigator> et <xref:System.Xml.XmlNamespaceManager> pour sélectionner l'élément `Search` à partir du document XML dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="4f207-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="4f207-116">La requête `xpath` inclut des préfixes d’espaces de noms dans chaque élément du chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="4f207-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="4f207-117">La spécification de l'identité précise des espaces de noms qui contiennent chaque élément permet d'assurer une navigation correcte jusqu'à l'élément `Search` par la méthode <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f207-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="4f207-118">La précision des espaces de noms et des noms qualifiés complets va au-delà du caractère pratique.</span><span class="sxs-lookup"><span data-stu-id="4f207-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="4f207-119">En prenant la définition de document et le code des exemples précédents, vous constaterez qu'une navigation sans noms d'éléments qualifiés complets lève des exceptions.</span><span class="sxs-lookup"><span data-stu-id="4f207-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="4f207-120">Par exemple, la définition d'élément `<Search xmlns="http://schemas.microsoft.com/v1/Search">` et la requête de chaîne `xpath = "/s:Envelope/s:Body/Search";` sans préfixe d'espace de noms pour l'élément `Search` retournent `null` à la place de l'élément `Search`.</span><span class="sxs-lookup"><span data-stu-id="4f207-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f207-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f207-121">See also</span></span>

- [<span data-ttu-id="4f207-122">Accès à des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4f207-122">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="4f207-123">Sélection, évaluation et mise en correspondance de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="4f207-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
