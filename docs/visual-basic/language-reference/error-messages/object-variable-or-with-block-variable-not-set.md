---
title: Variable objet ou variable bloc With non définie
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 0264a4235a056c93edb703ec2ef70e7124e0df4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873623"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>Variable objet ou variable bloc With non définie

Une variable objet non valide est référencée.   Cette erreur peut se produire pour plusieurs raisons :

- Une variable a été déclarée sans spécifier de type. Si une variable est déclarée sans spécifier de type, la valeur par défaut est type `Object` .

    Par exemple, une variable déclarée avec est `Dim x` de type `Object;` , une variable déclarée avec est `Dim x As String` de type `String` .

    > [!TIP]
    > L' `Option Strict` instruction interdit le typage implicite qui produit un `Object` type. Si vous omettez le type, une erreur de compilation se produit. Consultez [Option Strict Statement](../statements/option-strict-statement.md).

- Vous tentez de référencer un objet qui a été défini sur `Nothing` .

- Vous tentez d’accéder à un élément d’une variable tableau qui n’a pas été correctement déclarée.

    Par exemple, un tableau déclaré comme `products() As String` déclenchera l’erreur si vous tentez de référencer un élément du tableau `products(3) = "Widget"` . Le tableau n’a pas d’éléments et est traité comme un objet.

- Vous tentez d’accéder au code dans un `With...End With` bloc avant que le bloc n’ait été initialisé.   Un `With...End With` bloc doit être initialisé en exécutant le point d' `With` entrée de l’instruction.

> [!NOTE]
> Dans les versions antérieures de Visual Basic ou VBA, cette erreur était également déclenchée en affectant une valeur à une variable sans utiliser le `Set` mot clé ( `x = "name"` au lieu de `Set x = "name"` ). Le `Set` mot clé n’est plus valide dans Visual Basic .net.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Affectez `Option Strict` `On` la valeur en ajoutant le code suivant au début du fichier :

    ```vb
    Option Strict On
    ```

    Quand vous exécutez le projet, une erreur de compilation s’affiche dans le **liste d’erreurs** pour toute variable qui a été spécifiée sans type.

2. Si vous ne souhaitez pas activer `Option Strict` , recherchez dans votre code toutes les variables qui ont été spécifiées sans type ( `Dim x` au lieu de `Dim x As String` ) et ajoutez le type prévu à la déclaration.

3. Assurez-vous que vous ne faites pas référence à une variable objet qui a été définie sur `Nothing` .  Recherchez le mot clé dans votre code `Nothing` et modifiez votre code afin que l’objet ne soit pas défini sur `Nothing` jusqu’à ce que vous l’ayez référencé.

4. Assurez-vous que toutes les variables de tableau sont dimensionnées avant d’y accéder. Vous pouvez affecter une dimension lors de la création initiale du tableau ( `Dim x(5) As String` au lieu de `Dim x() As String` ), ou utiliser le `ReDim` mot clé pour définir les dimensions du tableau avant d’y accéder.

5. Assurez-vous que votre `With` bloc est initialisé en exécutant le point d’entrée de l' `With` instruction.

## <a name="see-also"></a>Voir aussi

- [Déclaration des variables objets](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim (instruction)](../statements/redim-statement.md)
- [With...End With (instruction)](../statements/with-end-with-statement.md)
