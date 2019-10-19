---
title: L'attribut 'Extension' ne peut être appliqué qu'aux déclarations 'Module', 'Sub' ou 'Function'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 2ed3a10cdf941bb8d1d7c00379736e04e8cad4d7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583183"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>L'attribut 'Extension' ne peut être appliqué qu'aux déclarations 'Module', 'Sub' ou 'Function'

La seule façon d’étendre un type de données dans Visual Basic consiste à définir une méthode d’extension dans un module standard. La méthode d’extension peut être une procédure `Sub` ou `Function`. Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension, `<Extension()>`, à partir de l’espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Éventuellement, un module qui contient une méthode d’extension peut être marqué de la même façon. Aucune autre utilisation de l’attribut d’extension n’est valide.

**ID d’erreur :** BC36550

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez l’attribut d’extension.

- Reconcevez votre extension en tant que méthode, définie dans un module englobant.

## <a name="example"></a>Exemple

L’exemple suivant définit une méthode de `Print` pour le type de données `String`.

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
