---
title: 'Procédure : récupérer un seul attribut (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 34c390fbffc1aea68a2fd8ae64b17d2637a1f4f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397854"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="bc9a5-102">Comment : récupérer un seul attribut (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc9a5-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bc9a5-103">Cette rubrique explique comment récupérer un seul attribut d'un élément, étant donné le nom de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="bc9a5-104">Ceci est utile pour écrire des expressions de requête où vous souhaitez rechercher un élément qui possède un attribut particulier.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="bc9a5-105">La méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement> retourne l'objet <xref:System.Xml.Linq.XAttribute> avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9a5-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc9a5-106">Example</span></span>  
 <span data-ttu-id="bc9a5-107">L'exemple suivant utilise la méthode <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="bc9a5-108">Cet exemple recherche tous les descendants dans l'arborescence nommés `Phone`, puis recherche l'attribut nommé `type`.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="bc9a5-109">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="bc9a5-109">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="bc9a5-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc9a5-110">Example</span></span>  
 <span data-ttu-id="bc9a5-111">Si vous souhaitez récupérer la valeur de l'attribut vous pouvez le convertir, comme vous le feriez avec des objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bc9a5-112">l’exemple ci-dessous illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="bc9a5-113">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="bc9a5-113">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="bc9a5-114">fournit des opérateurs de conversion explicites pour la classe <xref:System.Xml.Linq.XAttribute> vers `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9a5-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc9a5-115">Example</span></span>  
 <span data-ttu-id="bc9a5-116">L'exemple suivant illustre le même code pour un attribut qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bc9a5-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="bc9a5-117">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bc9a5-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="bc9a5-118">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="bc9a5-118">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc9a5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc9a5-119">See also</span></span>

- [<span data-ttu-id="bc9a5-120">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc9a5-120">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
