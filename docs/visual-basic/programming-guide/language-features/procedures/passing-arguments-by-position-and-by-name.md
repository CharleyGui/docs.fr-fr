---
title: Passage des arguments par position et par nom
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364030"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passage des arguments par position et par nom (Visual Basic)

Quand vous appelez une `Sub` `Function` procédure ou, vous pouvez passer des arguments *par position* , dans l’ordre dans lequel ils apparaissent dans la définition de la procédure, ou vous pouvez les passer *par nom*, sans tenir compte de la position.

Quand vous transmettez un argument par nom, vous spécifiez le nom déclaré de l’argument suivi d’un signe deux-points et d’un signe égal ( `:=` ), suivi de la valeur de l’argument. Vous pouvez fournir des arguments nommés dans n’importe quel ordre.

Par exemple, la `Sub` procédure suivante accepte trois arguments :

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Lorsque vous appelez cette procédure, vous pouvez fournir les arguments par position, par nom ou à l’aide d’une combinaison des deux.

## <a name="passing-arguments-by-position"></a>Passage des arguments par position

Vous pouvez appeler la `Display` méthode avec ses arguments passés par position et délimités par des virgules, comme indiqué dans l’exemple suivant :

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Si vous omettez un argument facultatif dans une liste d’arguments positionnels, vous devez conserver son emplacement avec une virgule. L’exemple suivant appelle la `Display` méthode sans l' `age` argument :

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Passage d’arguments par nom

Vous pouvez également appeler `Display` avec les arguments passés par nom, également délimités par des virgules, comme indiqué dans l’exemple suivant :

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Le passage d’arguments par nom de cette façon est particulièrement utile lorsque vous appelez une procédure qui a plusieurs arguments facultatifs. Si vous fournissez des arguments par nom, il n’est pas nécessaire d’utiliser des virgules consécutives pour indiquer les arguments positionnels manquants. Le passage d’arguments par nom facilite également le suivi des arguments que vous passez et de ceux que vous omettez.

## <a name="mixing-arguments-by-position-and-by-name"></a>Combinaison d’arguments par position et par nom

Vous pouvez fournir des arguments par position et par nom dans un appel de procédure unique, comme indiqué dans l’exemple suivant :

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

Dans l’exemple précédent, aucune virgule supplémentaire n’est nécessaire pour contenir la place de l' `age` argument omis, car `birth` est passé par nom.

Dans les versions de Visual Basic antérieures à 15,5, lorsque vous fournissez des arguments à l’aide d’un mélange de position et de nom, les arguments positionnels doivent être placés en premier. Une fois que vous avez fourni un argument par nom, tous les arguments restants doivent être passés par nom.  Par exemple, l’appel suivant à la `Display` méthode affiche erreur du compilateur [BC30241 : argument nommé attendu](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

À compter de Visual Basic 15,5, les arguments positionnels peuvent suivre les arguments nommés si les arguments de position de fin se trouvent dans la position correcte. S’il est compilé sous Visual Basic 15,5, l’appel précédent à la `Display` méthode se compile correctement et ne génère plus d’erreur de compilateur [BC30241](../../../misc/bc30241.md).

Cette capacité à mélanger et à faire correspondre des arguments nommés et positionnels dans n’importe quel ordre est particulièrement utile lorsque vous souhaitez utiliser un argument nommé pour rendre votre code plus lisible. Par exemple, le `Person` constructeur de classe suivant requiert deux arguments de type `Person` , tous deux pouvant être `Nothing` .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

L’utilisation d’arguments nommés et positionnels mixtes permet d’effacer l’objectif du code lorsque la valeur des `father` `mother` arguments et est `Nothing` :

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Pour suivre les arguments positionnels avec les arguments nommés, vous devez ajouter l’élément suivant à votre fichier de projet d’Visual Basic ( \* . vbproj) :

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Pour plus d’informations, consultez [définition de la version du langage Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrictions relatives à la fourniture d’arguments par nom

Vous ne pouvez pas passer d’arguments par nom pour éviter d’entrer les arguments requis. Vous pouvez omettre uniquement les arguments facultatifs.

Vous ne pouvez pas passer un tableau de paramètres par nom. En effet, lorsque vous appelez la procédure, vous fournissez un nombre indéfini d’arguments séparés par des virgules pour le tableau de paramètres, et le compilateur ne peut pas associer plusieurs arguments à un seul nom.

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Tableaux de paramètres](./parameter-arrays.md)
- [Facultatif](../../../language-reference/modifiers/optional.md)
- [ParamArray](../../../language-reference/modifiers/paramarray.md)
