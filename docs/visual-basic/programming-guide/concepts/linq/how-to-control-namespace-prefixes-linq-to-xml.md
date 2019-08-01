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
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Procédure : Préfixes d’espaces de noms de contrôle (Visual Basic) (LINQ to XML)
Cette rubrique décrit comment contrôler les préfixes d'espaces de noms.  
  
## <a name="example"></a>Exemples  
  
### <a name="description"></a>Description  
 Cet exemple déclare deux espaces de noms. Il spécifie que `http://www.adventure-works.com` l’espace de noms `aw`a le préfixe `www.fourthcoffee.com` et que l’espace de `fc`noms a le préfixe.  
  
### <a name="code"></a>Code  
  
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
  
### <a name="comments"></a>Commentaires  
 Cet exemple génère la sortie suivante :  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
