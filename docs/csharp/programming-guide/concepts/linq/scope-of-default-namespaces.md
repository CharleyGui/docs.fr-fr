---
title: Portée des espaces de noms par défaut en C#1
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 2eee1b0c79f585710962d8e84fe584bca6b8228b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483603"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="3c9bb-102">Portée des espaces de noms par défaut en C\#</span><span class="sxs-lookup"><span data-stu-id="3c9bb-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="3c9bb-103">Les espaces de noms tels que représentés dans l'arborescence XML par défaut ne sont pas dans la portée pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="3c9bb-104">Si vous avez du code XML qui est dans un espace de noms par défaut, vous devez déclarer une variable <xref:System.Xml.Linq.XNamespace> et la combiner avec le nom local afin de créer un nom complet utilisable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="3c9bb-105">L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="3c9bb-106">Le premier ensemble d'exemples de cette rubrique illustre le chargement de code XML dans un espace de noms par défaut, mais son interrogation est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="3c9bb-107">Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c9bb-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c9bb-108">Example</span></span>  
 <span data-ttu-id="3c9bb-109">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3c9bb-110">Code</span><span class="sxs-lookup"><span data-stu-id="3c9bb-110">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="3c9bb-111">Commentaires</span><span class="sxs-lookup"><span data-stu-id="3c9bb-111">Comments</span></span>  
 <span data-ttu-id="3c9bb-112">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="3c9bb-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="3c9bb-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c9bb-113">Example</span></span>  
 <span data-ttu-id="3c9bb-114">Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="3c9bb-115">Par rapport à l'exemple de code incorrect illustré ci-dessus, l'approche appropriée, lors de l'utilisation du langage C#, consiste à déclarer et à initialiser un objet <xref:System.Xml.Linq.XNamespace> et à l'utiliser lors de la spécification d'objets <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="3c9bb-116">Dans ce cas, l'argument de la méthode <xref:System.Xml.Linq.XContainer.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="3c9bb-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3c9bb-117">Code</span><span class="sxs-lookup"><span data-stu-id="3c9bb-117">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="3c9bb-118">Commentaires</span><span class="sxs-lookup"><span data-stu-id="3c9bb-118">Comments</span></span>  
 <span data-ttu-id="3c9bb-119">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="3c9bb-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c9bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c9bb-120">See also</span></span>

- [<span data-ttu-id="3c9bb-121">Utilisation des espaces de noms XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3c9bb-121">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)
