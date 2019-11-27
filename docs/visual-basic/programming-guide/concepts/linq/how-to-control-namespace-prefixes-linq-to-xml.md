---
title: 'Comment : contrôler les préfixes d’espaces de noms (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 5ba415452a8671466c3a4c71a88731e5bd3cda60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348375"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="23d4b-102">Comment : contrôler les préfixes d'espaces de noms (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="23d4b-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="23d4b-103">Cette rubrique décrit comment contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="23d4b-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d4b-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="23d4b-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="23d4b-105">Description</span><span class="sxs-lookup"><span data-stu-id="23d4b-105">Description</span></span>  
 <span data-ttu-id="23d4b-106">Cet exemple déclare deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="23d4b-106">This example declares two namespaces.</span></span> <span data-ttu-id="23d4b-107">Il spécifie que l’espace de noms `http://www.adventure-works.com` a le préfixe `aw`et que l’espace de noms `www.fourthcoffee.com` a le préfixe de `fc`.</span><span class="sxs-lookup"><span data-stu-id="23d4b-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="23d4b-108">Code</span><span class="sxs-lookup"><span data-stu-id="23d4b-108">Code</span></span>  
  
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
  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="23d4b-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="23d4b-109">Comments</span></span>  
 <span data-ttu-id="23d4b-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="23d4b-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23d4b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23d4b-111">See also</span></span>

- [<span data-ttu-id="23d4b-112">Vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23d4b-112">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
