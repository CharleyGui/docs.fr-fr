---
title: 'Procédure : Préfixes d’espaces de noms de contrôle (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 2b89b49aa76df526c08143cad49685386ffd5e7c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709819"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="8c2c2-102">Procédure : Préfixes d’espaces de noms de contrôle (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8c2c2-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="8c2c2-103">Cette rubrique décrit comment contrôler les préfixes d'espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c2c2-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="8c2c2-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8c2c2-105">Description</span><span class="sxs-lookup"><span data-stu-id="8c2c2-105">Description</span></span>  
 <span data-ttu-id="8c2c2-106">Cet exemple déclare deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-106">This example declares two namespaces.</span></span> <span data-ttu-id="8c2c2-107">Il spécifie que `http://www.adventure-works.com` l’espace de noms `aw`a le préfixe `www.fourthcoffee.com` et que l’espace de `fc`noms a le préfixe.</span><span class="sxs-lookup"><span data-stu-id="8c2c2-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8c2c2-108">Code</span><span class="sxs-lookup"><span data-stu-id="8c2c2-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8c2c2-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="8c2c2-109">Comments</span></span>  
 <span data-ttu-id="8c2c2-110">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8c2c2-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c2c2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c2c2-111">See also</span></span>

- [<span data-ttu-id="8c2c2-112">Vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c2c2-112">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
