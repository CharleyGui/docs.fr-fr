---
title: Comment contrôler les préfixes namespace (C) (LINQ à XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141378"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="1af8d-102">Comment contrôler les préfixes namespace (C) (LINQ à XML)</span><span class="sxs-lookup"><span data-stu-id="1af8d-102">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="1af8d-103">Cette rubrique décrit comment contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="1af8d-103">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="1af8d-104">Dans de nombreux cas, il n'est pas nécessaire de contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="1af8d-104">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="1af8d-105">Cependant, certains outils de programmation XML requièrent un contrôle spécifique des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="1af8d-105">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="1af8d-106">Par exemple, vous pourriez manipuler une feuille de style XSLT ou un document XAML qui contient des expressions XPath incorporées qui font référence à des préfixes d'espaces de noms spécifiques ; dans ce cas, il est important que le document soit sérialisé avec ces préfixes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1af8d-106">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="1af8d-107">Il s'agit de la raison la plus courante de contrôle des préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="1af8d-107">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="1af8d-108">Le contrôle des préfixes d'espaces de noms peut également s'avérer nécessaire lorsque vous souhaitez que les utilisateurs modifient le document XML manuellement et que vous souhaitez créer des préfixes d'espaces de noms faciles à taper pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1af8d-108">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="1af8d-109">Par exemple, vous pourriez générer un document XSD.</span><span class="sxs-lookup"><span data-stu-id="1af8d-109">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="1af8d-110">Les conventions applicables aux schémas suggèrent que vous utilisiez `xs` ou `xsd` comme préfixe de l'espace de noms de schéma.</span><span class="sxs-lookup"><span data-stu-id="1af8d-110">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="1af8d-111">Pour contrôler les préfixes d'espaces de noms, vous devez insérer des attributs qui déclarent des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="1af8d-111">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="1af8d-112">Si vous déclarez les espaces de noms avec des préfixes spécifiques, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tentera d'honorer les préfixes d'espaces de noms lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="1af8d-112">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="1af8d-113">Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où l'espace de noms du nom de l'attribut est <xref:System.Xml.Linq.XNamespace.Xmlns%2A> et le nom de l'attribut est le préfixe d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1af8d-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="1af8d-114">La valeur de l'attribut est l'URI de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1af8d-114">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1af8d-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1af8d-115">Example</span></span>  
 <span data-ttu-id="1af8d-116">Cet exemple déclare deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="1af8d-116">This example declares two namespaces.</span></span> <span data-ttu-id="1af8d-117">Il spécifie que l’espace de noms `http://www.adventure-works.com` a le préfixe `aw` et que l’espace de noms `www.fourthcoffee.com` a le préfixe `fc`.</span><span class="sxs-lookup"><span data-stu-id="1af8d-117">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
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
  
 <span data-ttu-id="1af8d-118">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1af8d-118">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1af8d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1af8d-119">See also</span></span>

- [<span data-ttu-id="1af8d-120">Vue d’ensemble des espaces de noms (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1af8d-120">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
