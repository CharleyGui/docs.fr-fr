---
title: Overloads
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 44823b409cfa81dc889aabacf101fac90bf851e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351410"
---
# <a name="overloads-visual-basic"></a>Overloads (Visual Basic)

Spécifie qu'une propriété ou une procédure redéclare une ou plusieurs propriétés ou procédures existantes avec le même nom.

## <a name="remarks"></a>Notes

*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope. Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.

## <a name="rules"></a>Règles

- **Declaration Context.** You can use `Overloads` only in a property or procedure declaration statement.

- **Combined Modifiers.** You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.

- **Required Differences.** The *signature* in this declaration must be different from the signature of every property or procedure that it overloads. La signature comprend le nom de la propriété ou de la procédure ainsi que les éléments suivants :

  - le nombre de paramètres

  - l'ordre des paramètres

  - les types de données des paramètres

  - le nombre de paramètres de type (pour une procédure générique)

  - le type de retour (uniquement pour une procédure d'opérateur de conversion)

  Toutes les surcharges doivent avoir le même nom, mais chacune doit différer de toutes les autres à l'égard d'une ou de plusieurs des raisons ci-dessus. Cela permet au compilateur de distinguer la version à utiliser quand le code appelle la propriété ou la procédure.

- **Disallowed Differences.** La modification d'un ou de plusieurs des éléments suivants n'est pas valide pour la surcharge d'une propriété ou d'une procédure, parce qu'elles ne font pas partie de la signature :

  - elle retourne ou non une valeur (pour une procédure)

  - le type de données de la valeur de retour (sauf pour un opérateur de conversion)

  - les noms des paramètres ou des paramètres de type

  - les contraintes sur les paramètres de type (pour une procédure générique)

  - les mots clés de modificateur de paramètre (tels que `ByRef` ou `Optional`)

  - les mots clés de modificateur de propriété ou de procédure (tels que `Public` ou `Shared`)

- **Optional Modifier.** You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class. Toutefois, si vous utilisez `Overloads` dans l'une des déclarations, vous devez l'utiliser dans toutes.

- **Shadowing and Overloading.** `Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class. Quand vous utilisez `Overloads` de cette façon, vous déclarez la propriété ou la méthode avec le même nom et la même liste de paramètres que le membre de classe de base, et vous ne spécifiez pas le mot clé `Shadows`.

Si vous utilisez `Overrides`, le compilateur ajoute implicitement `Overloads` afin que vos API de bibliothèque fonctionnent plus facilement avec C#.

Le modificateur `Overloads` peut être utilisé dans les contextes suivants :

- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)

- [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)

- [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Surcharge de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Guide pratique : définir un opérateur de conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
