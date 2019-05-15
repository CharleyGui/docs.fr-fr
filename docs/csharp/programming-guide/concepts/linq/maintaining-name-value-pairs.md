---
title: Gestion des paires nom/valeur (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 4577ff032eaf25e519e687a0eea969bf76ca3540
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596955"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="fbfd5-102">Gestion des paires nom/valeur (C#)</span><span class="sxs-lookup"><span data-stu-id="fbfd5-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="fbfd5-103">De nombreuses applications doivent maintenir des informations qu'il est préférable de conserver sous forme de paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="fbfd5-104">Il peut s'agir d'informations de configuration ou de paramètres globaux.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fbfd5-105">contient des méthodes qui facilitent la maintenance d'un ensemble de paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-105">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="fbfd5-106">Vous pouvez conserver les informations en tant qu'attributs ou en tant qu'ensemble d'éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="fbfd5-107">L'une des différences est qu'il ne peut y avoir qu'un seul attribut avec un nom donné pour un élément.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="fbfd5-108">Cette limitation ne s'applique pas aux éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="fbfd5-109">SetAttributeValue et SetElementValue</span><span class="sxs-lookup"><span data-stu-id="fbfd5-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="fbfd5-110">Les deux méthodes qui facilitent la conservation de paires nom/valeur sont <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> et <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="fbfd5-111">Ces deux méthodes ont une sémantique similaire.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="fbfd5-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> peut ajouter, modifier ou supprimer des attributs d'un élément.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="fbfd5-113">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d'un attribut qui n'existe pas, la méthode crée un nouvel attribut et l'ajoute à l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="fbfd5-114">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d'un attribut existant et avec du contenu spécifié, le contenu de l'attribut est remplacé par le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="fbfd5-115">Si vous appelez <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> avec un nom d'un attribut existant et que vous spécifiez une valeur Null pour le contenu, l'attribut est supprimé de son parent.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="fbfd5-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> peut ajouter, modifier ou supprimer des éléments enfants d'un élément.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="fbfd5-117">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d'un élément enfant qui n'existe pas, la méthode crée un nouvel élément et l'ajoute à l'élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="fbfd5-118">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d'un élément existant et avec du contenu spécifié, le contenu de l'élément est remplacé par le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="fbfd5-119">Si vous appelez <xref:System.Xml.Linq.XElement.SetElementValue%2A> avec un nom d'un élément existant et que vous spécifiez une valeur Null pour le contenu, l'élément est supprimé de son parent.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbfd5-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbfd5-120">Example</span></span>  
 <span data-ttu-id="fbfd5-121">L'exemple suivant crée un élément sans attribut.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="fbfd5-122">Il utilise ensuite la méthode <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> pour créer et maintenir une liste de paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="fbfd5-123">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fbfd5-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="fbfd5-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbfd5-124">Example</span></span>  
 <span data-ttu-id="fbfd5-125">L'exemple suivant crée un élément sans élément enfant.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="fbfd5-126">Il utilise ensuite la méthode <xref:System.Xml.Linq.XElement.SetElementValue%2A> pour créer et maintenir une liste de paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="fbfd5-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="fbfd5-127">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="fbfd5-127">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbfd5-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbfd5-128">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="fbfd5-129">Modification d’arborescences XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fbfd5-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
