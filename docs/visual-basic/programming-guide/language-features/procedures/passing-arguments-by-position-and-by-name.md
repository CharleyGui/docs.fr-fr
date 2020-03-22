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
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400854"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passage des arguments par position et par nom (Visual Basic)

Lorsque vous `Sub` appelez `Function` un ou une procédure, vous pouvez passer des arguments *par position* — dans l’ordre dans lequel ils apparaissent dans la définition de la procédure — ou vous pouvez les passer par *leur nom,* sans égard à la position.

Lorsque vous passez un argument par nom, vous spécifiez le nom`:=`déclaré de l’argument suivi d’un côlon et d’un signe égal ( ), suivi de la valeur de l’argument. Vous pouvez fournir des arguments nommés dans n’importe quel ordre.

Par exemple, `Sub` la procédure suivante prend trois arguments :

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Lorsque vous appelez cette procédure, vous pouvez fournir les arguments par position, par nom, ou en utilisant un mélange des deux.

## <a name="passing-arguments-by-position"></a>Arguments de passage par position

Vous pouvez `Display` appeler la méthode avec ses arguments adoptés par position et délimités par des virgules, comme le montre l’exemple suivant:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Si vous ometez un argument facultatif dans une liste d’arguments positionnel, vous devez tenir sa place avec une virgule. L’exemple suivant `Display` appelle `age` la méthode sans l’argument :

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Arguments de passage par nom

Alternativement, vous `Display` pouvez appeler avec les arguments passés par leur nom, également délimités par des virgules, comme le montre l’exemple suivant:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Passer des arguments par nom de cette façon est particulièrement utile lorsque vous appelez une procédure qui a plus d’un argument facultatif. Si vous fournissez des arguments par nom, vous n’avez pas à utiliser des virgules consécutives pour désigner les arguments de position manquants. Passer des arguments par leur nom permet également de garder plus facilement une trace des arguments que vous passez et ceux que vous omettez.

## <a name="mixing-arguments-by-position-and-by-name"></a>Mélanger les arguments par position et par nom

Vous pouvez fournir des arguments par position et par nom dans un seul appel de procédure, comme le montre l’exemple suivant :

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

Dans l’exemple précédent, aucune virgule supplémentaire n’est nécessaire pour tenir la place de l’argument omis, `age` puisque `birth` est passé par son nom.

Dans les versions de Visual Basic avant 15,5, lorsque vous fournissez des arguments par un mélange de position et de nom, les arguments de position doivent tous passer en premier. Une fois que vous fournissez un argument par nom, tous les arguments restants doivent tous être adoptés par leur nom.  Par exemple, l’appel `Display` suivant à la méthode affiche l’erreur de compilateur [BC30241: Argument nommé prévu](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

En commençant par Visual Basic 15.5, les arguments de position peuvent suivre les arguments nommés si les arguments de position de fin sont dans la bonne position. S’il est compilé sous Visual Basic 15.5, l’appel précédent à la `Display` méthode compile avec succès et ne génère plus d’erreur de compilateur [BC30241](../../../misc/bc30241.md).

Cette capacité de mélanger et assortir les arguments nommés et de position dans n’importe quel ordre est particulièrement utile lorsque vous voulez utiliser un argument nommé pour rendre votre code plus lisible. Par exemple, `Person` le constructeur de classe `Person`suivant nécessite deux `Nothing`arguments de type, qui peuvent tous deux être .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

L’utilisation d’arguments mixtes nommés et de position permet `father` `mother` de `Nothing`rendre l’intention du code claire lorsque la valeur de la et des arguments est :

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Pour suivre les arguments de position avec les arguments nommés,\*vous devez ajouter l’élément suivant à votre projet Visual Basic (.vbproj) fichier:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Pour plus d’informations voir [le réglage de la version visuelle de la langue de base](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrictions sur l’approvisionnement des arguments par nom

Vous ne pouvez pas passer des arguments par nom pour éviter d’entrer les arguments requis. Vous ne pouvez omettre que les arguments facultatifs.

Vous ne pouvez pas passer un tableau de paramètres par nom. C’est parce que lorsque vous appelez la procédure, vous fournissez un nombre indéfini d’arguments comma-séparés pour le tableau de paramètres, et le compilateur ne peut pas associer plus d’un argument avec un seul nom.

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Comment : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)
- [Passage des arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)
- [Paramètres facultatifs](./optional-parameters.md)
- [Paramètres Arrays](./parameter-arrays.md)
- [Optionnel](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
