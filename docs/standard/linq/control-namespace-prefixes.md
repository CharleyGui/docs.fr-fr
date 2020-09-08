---
title: Comment contrôler les préfixes d’espaces de noms-LINQ to XML
description: Vous pouvez contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML en C# et Visual Basic. Pour ce faire, insérez des attributs qui déclarent des espaces de noms.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552452"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a><span data-ttu-id="dcf63-104">Guide pratique pour contrôler les préfixes d’espace de noms (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="dcf63-104">How to control namespace prefixes (LINQ to XML)</span></span>

<span data-ttu-id="dcf63-105">Cet article explique comment contrôler les préfixes d’espaces de noms lors de la sérialisation d’une arborescence XML en C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dcf63-105">This article describes how to control namespace prefixes when serializing an XML tree in C# and Visual Basic.</span></span>

<span data-ttu-id="dcf63-106">Dans de nombreux cas, il n’est pas nécessaire de contrôler les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="dcf63-106">In many situations, it's not necessary to control namespace prefixes.</span></span> <span data-ttu-id="dcf63-107">Toutefois, certains outils de programmation XML en ont besoin.</span><span class="sxs-lookup"><span data-stu-id="dcf63-107">However, certain XML programming tools require it.</span></span> <span data-ttu-id="dcf63-108">Par exemple, vous pouvez manipuler une feuille de style XSLT ou un document XAML qui contient des expressions XPath incorporées qui font référence à des préfixes d’espaces de noms spécifiques.</span><span class="sxs-lookup"><span data-stu-id="dcf63-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes.</span></span> <span data-ttu-id="dcf63-109">Dans ce cas, il est important que le document soit sérialisé avec ces préfixes.</span><span class="sxs-lookup"><span data-stu-id="dcf63-109">In such a case, it's important that the document be serialized with those prefixes.</span></span> <span data-ttu-id="dcf63-110">Il s’agit d’une raison courante de contrôler les préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="dcf63-110">This is a common reason for controlling namespace prefixes.</span></span>

<span data-ttu-id="dcf63-111">Une autre raison est que vous souhaitez que les utilisateurs modifient le document XML manuellement et que vous souhaitiez créer des préfixes d’espaces de noms qui sont pratiques pour l’utilisateur à taper.</span><span class="sxs-lookup"><span data-stu-id="dcf63-111">Another reason is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="dcf63-112">Par exemple, vous pourriez générer un document XSD.</span><span class="sxs-lookup"><span data-stu-id="dcf63-112">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="dcf63-113">Les conventions applicables aux schémas suggèrent que vous utilisiez `xs` ou `xsd` comme préfixe de l'espace de noms de schéma.</span><span class="sxs-lookup"><span data-stu-id="dcf63-113">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>

<span data-ttu-id="dcf63-114">Pour contrôler les préfixes d'espaces de noms, vous devez insérer des attributs qui déclarent des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="dcf63-114">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="dcf63-115">Si vous déclarez les espaces de noms avec des préfixes spécifiques, LINQ to XML tentera d’honorer les préfixes d’espace de noms lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="dcf63-115">If you declare the namespaces with specific prefixes, LINQ to XML will attempt to honor the namespace prefixes when serializing.</span></span>

<span data-ttu-id="dcf63-116">Pour créer un attribut qui déclare un espace de noms avec un préfixe, vous devez créer un attribut où l'espace de noms du nom de l'attribut est <xref:System.Xml.Linq.XNamespace.Xmlns%2A> et le nom de l'attribut est le préfixe d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="dcf63-116">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="dcf63-117">La valeur de l'attribut est l'URI de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="dcf63-117">The value of the attribute is the URI of the namespace.</span></span>

## <a name="example-create-two-namespaces-that-have-prefixes"></a><span data-ttu-id="dcf63-118">Exemple : créer deux espaces de noms qui ont des préfixes</span><span class="sxs-lookup"><span data-stu-id="dcf63-118">Example: Create two namespaces that have prefixes</span></span>

<span data-ttu-id="dcf63-119">Cet exemple déclare deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="dcf63-119">This example declares two namespaces.</span></span> <span data-ttu-id="dcf63-120">Elle spécifie le préfixe `aw` de l' `http://www.adventure-works.com` espace de noms et le préfixe `fc` de l' `www.fourthcoffee.com` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="dcf63-120">It specifies the prefix `aw` for the `http://www.adventure-works.com` namespace, and the prefix `fc` for the `www.fourthcoffee.com` namespace.</span></span>

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

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="dcf63-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcf63-121">See also</span></span>

- [<span data-ttu-id="dcf63-122">Vue d’ensemble des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="dcf63-122">Namespaces overview</span></span>](namespaces-overview.md)
