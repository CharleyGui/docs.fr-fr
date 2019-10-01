---
title: L'attribut 'Extension' ne peut être appliqué qu'aux déclarations 'Module', 'Sub' ou 'Function'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 95a67a552efacf9e77dc3ebc3e0187817a6d82e2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698583"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>L'attribut 'Extension' ne peut être appliqué qu'aux déclarations 'Module', 'Sub' ou 'Function'
La seule façon d’étendre un type de données dans Visual Basic consiste à définir une méthode d’extension dans un module standard. La méthode d’extension peut être une procédure `Sub` ou une procédure `Function`. Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension, `<Extension()>`, à partir de l’espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Éventuellement, un module qui contient une méthode d’extension peut être marqué de la même façon. Aucune autre utilisation de l’attribut d’extension n’est valide.  
  
 **ID d’erreur :** BC36550  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez l’attribut d’extension.  
  
- Reconcevez votre extension en tant que méthode, définie dans un module englobant.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit une méthode `Print` pour le type de données `String`.  
  
```vb  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Méthodes d’extension](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)
