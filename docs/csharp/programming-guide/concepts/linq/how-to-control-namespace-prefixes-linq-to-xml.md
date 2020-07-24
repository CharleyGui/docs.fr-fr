---
title: Comment contrôler les préfixes d’espaces de noms (C#) (LINQ to XML)
description: Découvrez comment contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML dans LINQ to XML en C#. Certaines situations requièrent le contrôle des préfixes d’espaces de noms.
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: b0c5cbfa7488f3a7105595830ef6765e6bfb1f12
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105310"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="b1126-104">Comment contrôler les préfixes d’espaces de noms (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b1126-104">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="b1126-105">Cette rubrique décrit comment contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="b1126-105">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="b1126-106">Dans de nombreux cas, il n'est pas nécessaire de contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b1126-106">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="b1126-107">Cependant, certains outils de programmation XML requièrent un contrôle spécifique des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b1126-107">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="b1126-108">Par exemple, vous pourriez manipuler une feuille de style XSLT ou un document XAML qui contient des expressions XPath incorporées qui font référence à des préfixes d'espaces de noms spécifiques ; dans ce cas, il est important que le document soit sérialisé avec ces préfixes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b1126-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="b1126-109">Il s'agit de la raison la plus courante de contrôle des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b1126-109">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="b1126-110">Le contrôle des préfixes d'espaces de noms peut également s'avérer nécessaire lorsque vous souhaitez que les utilisateurs modifient le document XML manuellement et que vous souhaitez créer des préfixes d'espaces de noms faciles à taper pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b1126-110">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="b1126-111">Par exemple, vous pourriez générer un document XSD.</span><span class="sxs-lookup"><span data-stu-id="b1126-111">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="b1126-112">Les conventions applicables aux schémas suggèrent que vous utilisiez `xs` ou `xsd` comme préfixe de l'espace de noms de schéma.</span><span class="sxs-lookup"><span data-stu-id="b1126-112">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="b1126-113">Pour contrôler les préfixes d'espaces de noms, vous devez insérer des attributs qui déclarent des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b1126-113">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="b1126-114">Si vous déclarez les espaces de noms avec des préfixes spécifiques, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tentera d'honorer les préfixes d'espaces de noms lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="b1126-114">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="b1126-115">Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où l'espace de noms du nom de l'attribut est <xref:System.Xml.Linq.XNamespace.Xmlns%2A> et le nom de l'attribut est le préfixe d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b1126-115">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="b1126-116">La valeur de l'attribut est l'URI de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b1126-116">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1126-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1126-117">Example</span></span>  
 <span data-ttu-id="b1126-118">Cet exemple déclare deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b1126-118">This example declares two namespaces.</span></span> <span data-ttu-id="b1126-119">Il spécifie que l’espace de noms `http://www.adventure-works.com` a le préfixe `aw` et que l’espace de noms `www.fourthcoffee.com` a le préfixe `fc`.</span><span class="sxs-lookup"><span data-stu-id="b1126-119">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b1126-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b1126-120">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1126-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1126-121">See also</span></span>

- [<span data-ttu-id="b1126-122">Vue d’ensemble des espaces de noms (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b1126-122">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
