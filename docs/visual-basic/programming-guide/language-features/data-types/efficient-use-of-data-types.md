---
title: Utilisation efficace des types de données (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 68371a9f8d4dcc5d0a2b67955d5e88943a83b085
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631109"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Utilisation efficace des types de données (Visual Basic)
Le type de données est affecté aux variables non déclarées et aux `Object` variables déclarées sans type de données. Cela facilite l’écriture rapide de programmes, mais peut entraîner une exécution plus lente.

## <a name="strong-typing"></a>Typage fort
 La spécification des types de données pour toutes vos variables est appelée *typage fort*. L’utilisation du typage fort présente plusieurs avantages:

- Il permet la prise en charge d’IntelliSense pour vos variables. Cela vous permet de voir leurs propriétés et d’autres membres au fur et à mesure que vous tapez dans le code.

- Elle tire parti de la vérification du type de compilateur. Cela permet d’intercepter les instructions qui peuvent échouer au moment de l’exécution en raison d’erreurs telles que le dépassement de capacité. Il intercepte également les appels aux méthodes sur les objets qui ne les prennent pas en charge.

- Cela permet d’accélérer l’exécution de votre code.

## <a name="most-efficient-data-types"></a>Types de données les plus efficaces
 Pour les variables qui ne contiennent jamais de fractions, les types de données intégraux sont plus efficaces que les types non intégraux. Dans Visual Basic, `Integer` et `UInteger` sont les types numériques les plus efficaces.

 Pour les nombres fractionnaires `Double` , est le type de données le plus efficace, car les processeurs sur les plateformes actuelles effectuent des opérations à virgule flottante en double précision. Toutefois, les opérations `Double` avec ne sont pas aussi rapides que les types intégraux `Integer`tels que.

## <a name="specifying-data-type"></a>Spécification du type de données
 Utilisez l' [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour déclarer une variable d’un type spécifique. Vous pouvez spécifier simultanément son niveau d’accès à l’aide du mot clé [public](../../../../visual-basic/language-reference/modifiers/public.md), [protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)ou [Private](../../../../visual-basic/language-reference/modifiers/private.md) , comme dans l’exemple suivant.

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>Conversion de caractères
 Les `AscW` fonctions `ChrW` et fonctionnent en Unicode. Vous devez les utiliser de préférence pour `Asc` et `Chr`, qui doit traduire à l’intérieur et à l’extérieur d’Unicode.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Types de données numériques](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Utilisation de la fonctionnalité IntelliSense](/visualstudio/ide/using-intellisense)
