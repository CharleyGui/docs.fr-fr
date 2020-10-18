---
title: L'attribut 'Extension' ne peut être appliqué qu'aux déclarations 'Module', 'Sub' ou 'Function'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: bd4d14721b93800831dbce897535b4f5956fe9c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160748"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>BC36550 : l’attribut’extension’ne peut être appliqué qu’aux déclarations’module', 'Sub’ou’Function'

La seule façon d’étendre un type de données dans Visual Basic consiste à définir une méthode d’extension dans un module standard. La méthode d’extension peut être une `Sub` procédure ou une `Function` procédure. Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension, `<Extension()>` , à partir de l' <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> espace de noms. Éventuellement, un module qui contient une méthode d’extension peut être marqué de la même façon. Aucune autre utilisation de l’attribut d’extension n’est valide.

**ID d’erreur :** BC36550

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez l’attribut d’extension.

- Reconcevez votre extension en tant que méthode, définie dans un module englobant.

## <a name="example"></a> Exemple

L’exemple suivant définit une `Print` méthode pour le `String` type de données.

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

- [Vue d’ensemble des attributs](../../programming-guide/concepts/attributes/index.md)
- [Méthodes d’extension](../../programming-guide/language-features/procedures/extension-methods.md)
- [Module, instruction](../statements/module-statement.md)
