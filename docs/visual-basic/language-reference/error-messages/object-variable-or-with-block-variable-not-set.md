---
title: Variable objet ou variable bloc With non définie
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040557"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Variable objet ou variable bloc With non définie
Une variable objet non valide est référencée.   Cette erreur peut se produire pour plusieurs raisons :

- Une variable a été déclarée sans spécifier de type. Si une variable est déclarée sans spécifier de type, la valeur par défaut `Object`est type.

    Par exemple, une variable déclarée `Dim x` avec est de type `Object;` , une variable déclarée avec `Dim x As String` est de `String`type.

    > [!TIP]
    > L' `Option Strict` instruction interdit le typage implicite qui produit un `Object` type. Si vous omettez le type, une erreur de compilation se produit. Consultez [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).

- Vous tentez de référencer un objet qui a été défini `Nothing`sur.

- Vous tentez d’accéder à un élément d’une variable tableau qui n’a pas été correctement déclarée.

    Par exemple, un tableau déclaré comme `products() As String` déclenchera l’erreur si vous tentez de référencer un élément du `products(3) = "Widget"`tableau. Le tableau n’a pas d’éléments et est traité comme un objet.

- Vous tentez d’accéder au code dans `With...End With` un bloc avant que le bloc n’ait été initialisé.   Un `With...End With` bloc doit être initialisé en exécutant le point d' `With` entrée de l’instruction.

> [!NOTE]
> Dans les versions antérieures de Visual Basic ou VBA, cette erreur était également déclenchée en affectant une valeur à une variable sans `Set` utiliser le`x = "name"` mot clé `Set x = "name"`(au lieu de). Le `Set` mot clé n’est plus valide dans Visual Basic .net.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Affectez la valeur `Option Strict` enajoutantlecodesuivantaudébutdufichier:`On`

    ```vb
    Option Strict On
    ```

    Quand vous exécutez le projet, une erreur de compilation s’affiche dans le **liste d’erreurs** pour toute variable qui a été spécifiée sans type.

2. Si vous ne souhaitez pas activer `Option Strict`, recherchez dans votre code toutes les variables qui ont été spécifiées sans`Dim x` type ( `Dim x As String`au lieu de) et ajoutez le type prévu à la déclaration.

3. Assurez-vous que vous ne faites pas référence à une variable objet `Nothing`qui a été définie sur.  Recherchez le mot clé `Nothing`dans votre code et modifiez votre code afin que l’objet ne soit pas défini sur `Nothing` jusqu’à ce que vous l’ayez référencé.

4. Assurez-vous que toutes les variables de tableau sont dimensionnées avant d’y accéder. Vous pouvez affecter une dimension lors de la création initiale du tableau (`Dim x(5) As String` au lieu `Dim x() As String`de), ou utiliser `ReDim` le mot clé pour définir les dimensions du tableau avant d’y accéder.

5. Assurez- `With` vous que votre bloc est initialisé en exécutant `With` le point d’entrée de l’instruction.

## <a name="see-also"></a>Voir aussi

- [Déclaration des variables objets](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With (instruction)](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
