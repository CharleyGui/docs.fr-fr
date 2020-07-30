---
title: Portée des espaces de noms par défaut en C#
description: Découvrez comment interroger les espaces de noms XML par défaut en LINQ to XML en C#. Utilisez une variable XNamespace et le nom local pour donner un nom qualifié à la requête.
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 912e47099f89daa9b80ac58b422d39d598509ac9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302397"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="606d9-104">Portée des espaces de noms par défaut en C\#</span><span class="sxs-lookup"><span data-stu-id="606d9-104">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="606d9-105">Les espaces de noms tels que représentés dans l'arborescence XML par défaut ne sont pas dans la portée pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="606d9-105">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="606d9-106">Si vous avez du code XML qui est dans un espace de noms par défaut, vous devez déclarer une variable <xref:System.Xml.Linq.XNamespace> et la combiner avec le nom local afin de créer un nom complet utilisable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="606d9-106">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="606d9-107">L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="606d9-107">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="606d9-108">Le premier ensemble d'exemples de cette rubrique illustre le chargement de code XML dans un espace de noms par défaut, mais son interrogation est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="606d9-108">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="606d9-109">Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="606d9-109">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="606d9-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="606d9-110">Example</span></span>  
 <span data-ttu-id="606d9-111">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="606d9-111">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="606d9-112">Code</span><span class="sxs-lookup"><span data-stu-id="606d9-112">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="606d9-113">Commentaires</span><span class="sxs-lookup"><span data-stu-id="606d9-113">Comments</span></span>  
 <span data-ttu-id="606d9-114">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="606d9-114">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="606d9-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="606d9-115">Example</span></span>  
 <span data-ttu-id="606d9-116">Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.</span><span class="sxs-lookup"><span data-stu-id="606d9-116">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="606d9-117">Par rapport à l'exemple de code incorrect illustré ci-dessus, l'approche appropriée, lors de l'utilisation du langage C#, consiste à déclarer et à initialiser un objet <xref:System.Xml.Linq.XNamespace> et à l'utiliser lors de la spécification d'objets <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="606d9-117">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="606d9-118">Dans ce cas, l'argument de la méthode <xref:System.Xml.Linq.XContainer.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="606d9-118">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="606d9-119">Code</span><span class="sxs-lookup"><span data-stu-id="606d9-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="606d9-120">Commentaires</span><span class="sxs-lookup"><span data-stu-id="606d9-120">Comments</span></span>  
 <span data-ttu-id="606d9-121">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="606d9-121">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="606d9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="606d9-122">See also</span></span>

- [<span data-ttu-id="606d9-123">Vue d’ensemble des espaces de noms (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="606d9-123">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
