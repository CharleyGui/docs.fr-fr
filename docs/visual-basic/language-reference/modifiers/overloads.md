---
title: Surcharges
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
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392104"
---
# <a name="overloads-visual-basic"></a>Overloads (Visual Basic)

Spécifie qu'une propriété ou une procédure redéclare une ou plusieurs propriétés ou procédures existantes avec le même nom.

## <a name="remarks"></a>Notes

La *surcharge* consiste à fournir plusieurs définitions pour un nom de propriété ou de procédure donné dans la même portée. La redéclaration d’une propriété ou d’une procédure avec une signature différente est parfois appelée *masquage par signature*.

## <a name="rules"></a>Règles

- **Contexte de déclaration.** Vous pouvez utiliser `Overloads` uniquement dans une instruction de déclaration de propriété ou de procédure.

- **Modificateurs combinés.** Vous ne pouvez pas spécifier `Overloads` avec [Shadows](shadows.md) dans la même déclaration de procédure.

- **Différences requises.** La *signature* de cette déclaration doit être différente de la signature de chaque propriété ou procédure qu’elle surcharge. La signature comprend le nom de la propriété ou de la procédure ainsi que les éléments suivants :

  - le nombre de paramètres

  - l'ordre des paramètres

  - les types de données des paramètres

  - le nombre de paramètres de type (pour une procédure générique)

  - le type de retour (uniquement pour une procédure d'opérateur de conversion)

  Toutes les surcharges doivent avoir le même nom, mais chacune doit différer de toutes les autres à l'égard d'une ou de plusieurs des raisons ci-dessus. Cela permet au compilateur de distinguer la version à utiliser quand le code appelle la propriété ou la procédure.

- **Différences interdites.** La modification d'un ou de plusieurs des éléments suivants n'est pas valide pour la surcharge d'une propriété ou d'une procédure, parce qu'elles ne font pas partie de la signature :

  - elle retourne ou non une valeur (pour une procédure)

  - le type de données de la valeur de retour (sauf pour un opérateur de conversion)

  - les noms des paramètres ou des paramètres de type

  - les contraintes sur les paramètres de type (pour une procédure générique)

  - les mots clés de modificateur de paramètre (tels que `ByRef` ou `Optional`)

  - les mots clés de modificateur de propriété ou de procédure (tels que `Public` ou `Shared`)

- **Modificateur facultatif.** Vous n’avez pas besoin d’utiliser le `Overloads` modificateur lorsque vous définissez plusieurs propriétés ou procédures surchargées dans la même classe. Toutefois, si vous utilisez `Overloads` dans l'une des déclarations, vous devez l'utiliser dans toutes.

- **Occultation et surcharge.** `Overloads`peut également être utilisé pour occulter un membre existant ou un ensemble de membres surchargés dans une classe de base. Quand vous utilisez `Overloads` de cette façon, vous déclarez la propriété ou la méthode avec le même nom et la même liste de paramètres que le membre de classe de base, et vous ne spécifiez pas le mot clé `Shadows`.

Si vous utilisez `Overrides`, le compilateur ajoute implicitement `Overloads` afin que vos API de bibliothèque fonctionnent plus facilement avec C#.

Le modificateur `Overloads` peut être utilisé dans les contextes suivants :

- [Function (instruction)](../statements/function-statement.md)

- [Operator Statement](../statements/operator-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Sub (instruction)](../statements/sub-statement.md)

## <a name="see-also"></a>Voir aussi

- [Shadows](shadows.md)
- [Surcharge de procédure](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Procédures d'opérateur](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Guide pratique : définir un opérateur de conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
