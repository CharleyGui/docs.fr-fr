---
title: Étendue
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 1bee904996257474b7457b2aefb1f17d250933cb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410732"
---
# <a name="scope-in-visual-basic"></a>Portée dans Visual Basic

La *portée* d’un élément déclaré est le jeu de tout le code qui peut faire référence à celui-ci sans qualifier son nom ou le rendre disponible via une [instruction Imports (espace de noms et type .net)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md). Un élément peut avoir la portée à l’un des niveaux suivants :

|Level|Description|
|-----------|-----------------|
|Portée de bloc|Disponible uniquement dans le bloc de code dans lequel il est déclaré|
|Portée de la procédure|Disponible pour tout le code dans la procédure dans laquelle il est déclaré|
|Portée du module|Disponible pour tout le code au sein du module, de la classe ou de la structure dans laquelle il est déclaré|
|Portée espace de noms|Disponible pour l’ensemble du code dans l’espace de noms dans lequel il est déclaré|

Ces niveaux de la portée progressent du plus étroit (bloc) au plus large (espace de noms), où l’étendue la plus *étroite* correspond au plus petit ensemble de code qui peut faire référence à l’élément sans qualification. Pour plus d’informations, consultez « niveaux d’étendue » dans cette page.

## <a name="specifying-scope-and-defining-variables"></a>Spécification de l’étendue et définition de variables

Vous spécifiez l’étendue d’un élément lorsque vous le déclarez. L’étendue peut dépendre des facteurs suivants :

- Région (bloc, procédure, module, classe ou structure) dans laquelle vous déclarez l’élément

- Espace de noms contenant la déclaration de l’élément.

- Le niveau d’accès que vous déclarez pour l’élément

Soyez vigilant lorsque vous définissez des variables portant le même nom mais avec une étendue différente, car cela peut entraîner des résultats inattendus. Pour plus d'informations, consultez [References to Declared Elements](references-to-declared-elements.md).

## <a name="levels-of-scope"></a>Niveaux d’étendue

Un élément de programmation est disponible dans l’ensemble de la région dans laquelle vous le déclarez. Tout le code dans la même région peut faire référence à l’élément sans qualifier son nom.

### <a name="block-scope"></a>Portée de bloc

Un bloc est un ensemble d’instructions placées dans des instructions de déclaration de début et de fin, comme suit :

- `Do` et `Loop`

- `For`[ `Each` ] et`Next`

- `If` et `End If`

- `Select` et `End Select`

- `SyncLock` et `End SyncLock`

- `Try` et `End Try`

- `While` et `End While`

- `With` et `End With`

Si vous déclarez une variable dans un bloc, vous pouvez l’utiliser uniquement dans ce bloc. Dans l’exemple suivant, la portée de la variable de type entier `cube` est le bloc entre `If` et `End If` , et vous ne pouvez plus faire référence à `cube` lorsque l’exécution passe en dehors du bloc.

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> Même si l’étendue d’une variable est limitée à un bloc, sa durée de vie est toujours celle de la procédure entière. Si vous entrez le bloc plus d’une fois pendant la procédure, chaque variable de bloc conserve sa valeur précédente. Pour éviter des résultats inattendus dans ce cas, il est préférable d’initialiser les variables de bloc au début du bloc.

### <a name="procedure-scope"></a>Portée de la procédure

Un élément déclaré dans une procédure n’est pas disponible en dehors de cette procédure. Seule la procédure qui contient la déclaration peut l’utiliser. Les variables à ce niveau sont également appelées *variables locales*. Vous les déclarez avec l' [instruction Dim](../../../language-reference/statements/dim-statement.md), avec ou sans le mot clé [static](../../../language-reference/modifiers/static.md) .

La portée de la procédure et du bloc sont étroitement liées. Si vous déclarez une variable à l’intérieur d’une procédure mais en dehors d’un bloc au sein de cette procédure, vous pouvez considérer la variable comme ayant une portée de bloc, où le bloc correspond à la procédure entière.

> [!NOTE]
> Tous les éléments locaux, même s’il s’agit de `Static` variables, sont privés pour la procédure dans laquelle ils apparaissent. Vous ne pouvez pas déclarer d’élément à l’aide du mot clé [public](../../../language-reference/modifiers/public.md) dans une procédure.

### <a name="module-scope"></a>Portée du module

Pour plus de commodité, le *niveau de module* à simple terme s’applique de la même manière aux modules, aux classes et aux structures. Vous pouvez déclarer des éléments à ce niveau en plaçant l’instruction de déclaration en dehors d’une procédure ou d’un bloc, mais au sein du module, de la classe ou de la structure.

Lorsque vous faites une déclaration au niveau du module, le niveau d’accès que vous choisissez détermine l’étendue. L’espace de noms qui contient le module, la classe ou la structure affecte également la portée.

Les éléments pour lesquels vous déclarez le niveau d’accès [privé](../../../language-reference/modifiers/private.md) sont disponibles pour chaque procédure dans ce module, mais pas pour le code d’un autre module. L' `Dim` instruction au niveau du module est définie par défaut sur `Private` si vous n’utilisez pas de mots clés de niveau d’accès. Toutefois, vous pouvez rendre l’étendue et le niveau d’accès plus évidents à l’aide du `Private` mot clé dans l' `Dim` instruction.

Dans l’exemple suivant, toutes les procédures définies dans le module peuvent faire référence à la variable de chaîne `strMsg` . Lorsque la deuxième procédure est appelée, elle affiche le contenu de la variable de chaîne `strMsg` dans une boîte de dialogue.

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a>Portée espace de noms

Si vous déclarez un élément au niveau du module à l’aide du mot clé [Friend](../../../language-reference/modifiers/friend.md) ou [public](../../../language-reference/modifiers/public.md) , il devient disponible pour toutes les procédures dans l’espace de noms dans lequel l’élément est déclaré. Avec la modification suivante apporte à l’exemple précédent, la variable de chaîne `strMsg` peut être référencée par du code n’importe où dans l’espace de noms de sa déclaration.

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

La portée espace de noms comprend des espaces de noms imbriqués. Un élément disponible à partir d’un espace de noms est également disponible à partir de n’importe quel espace de noms imbriqué dans cet espace de noms.

Si votre projet ne contient pas d' [instruction d’espace de noms](../../../language-reference/statements/namespace-statement.md), tous les éléments du projet se trouvent dans le même espace de noms. Dans ce cas, l’étendue de l’espace de noms peut être considérée comme la portée du projet. `Public`les éléments d’un module, d’une classe ou d’une structure sont également disponibles pour tous les projets qui font référence à leur projet.

## <a name="choice-of-scope"></a>Choix de l’étendue

Lorsque vous déclarez une variable, gardez à l’esprit les points suivants lorsque vous choisissez son étendue.

### <a name="advantages-of-local-variables"></a>Avantages des variables locales

Les variables locales sont un bon choix pour tout type de calcul temporaire, pour les raisons suivantes :

- **Évitement des conflits de noms.** Les noms de variables locales ne sont pas susceptibles d’être en conflit. Par exemple, vous pouvez créer plusieurs procédures différentes contenant une variable appelée `intTemp` . Tant que chaque `intTemp` est déclarée en tant que variable locale, chaque procédure reconnaît uniquement sa propre version de `intTemp` . Toute procédure peut modifier la valeur de son local `intTemp` sans affecter les `intTemp` variables dans d’autres procédures.

- **Consommation de mémoire.** Les variables locales consomment de la mémoire uniquement lorsque leur procédure est en cours d’exécution. Leur mémoire est libérée lorsque la procédure retourne au code appelant. En revanche, les variables [partagées](../../../language-reference/modifiers/shared.md) et [statiques](../../../language-reference/modifiers/static.md) consomment des ressources mémoire jusqu’à ce que votre application cesse de s’exécuter. Utilisez-les uniquement lorsque cela est nécessaire. Les *variables d’instance* consomment de la mémoire, tandis que leur instance continue à exister, ce qui les rend moins efficaces que les variables locales, mais potentiellement plus efficaces que les `Shared` variables ou `Static` .

### <a name="minimizing-scope"></a>Réduire l’étendue

En général, lors de la déclaration d’une variable ou d’une constante, il est recommandé de faire de la portée le plus étroit possible (la portée de bloc est la plus étroite). Cela permet d’économiser de la mémoire et réduit les chances que votre code fasse référence à la mauvaise variable. De même, vous devez déclarer une variable comme étant [statique](../../../language-reference/modifiers/static.md) uniquement lorsqu’il est nécessaire de conserver sa valeur entre les appels de procédure.

## <a name="see-also"></a>Voir aussi

- [Caractéristiques des éléments déclarés](declared-element-characteristics.md)
- [Comment : contrôler la portée d'une variable](how-to-control-the-scope-of-a-variable.md)
- [Durée de vie dans Visual Basic](lifetime.md)
- [Niveaux d’accès dans Visual Basic](access-levels.md)
- [References to Declared Elements](references-to-declared-elements.md)
- [Déclaration de variable](../variables/variable-declaration.md)
