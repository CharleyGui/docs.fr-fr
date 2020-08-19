---
title: Surcharge d'opérateur
description: 'Découvrez comment surcharger les opérateurs arithmétiques dans une classe ou un type d’enregistrement et au niveau global en F #.'
ms.date: 08/15/2020
ms.openlocfilehash: fb86ceb95101fcc1f157ec9ba17a9d8145b11a91
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557579"
---
# <a name="operator-overloading"></a>Surcharge d'opérateur

Cette rubrique décrit comment surcharger les opérateurs arithmétiques dans une classe ou un type d’enregistrement, et au niveau global.

## <a name="syntax"></a>Syntaxe

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, *Operator-Symbol* est l’un des caractères `+` ,,,, `-` `*` `/` `=` , et ainsi de suite. La *liste de paramètres* spécifie les opérandes dans l’ordre dans lequel ils apparaissent dans la syntaxe habituelle pour cet opérateur. Le *corps de la méthode* construit la valeur résultante.

Les surcharges d’opérateur pour les opérateurs doivent être statiques. Les surcharges d’opérateur pour les opérateurs unaires, tels que `+` et `-` , doivent utiliser un tilde ( `~` ) dans le *symbole d’opérateur* pour indiquer que l’opérateur est un opérateur unaire et non un opérateur binaire, comme indiqué dans la déclaration suivante.

```fsharp
static member (~-) (v : Vector)
```

Le code suivant illustre une classe Vector qui n’a que deux opérateurs, l’un pour le moins unaire et l’autre pour la multiplication par un scalaire. Dans l’exemple, deux surcharges pour la multiplication scalaire sont nécessaires, car l’opérateur doit fonctionner indépendamment de l’ordre dans lequel le vecteur et la scalaire apparaissent.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Créer des opérateurs

Vous pouvez surcharger tous les opérateurs standard, mais vous pouvez également créer des opérateurs à partir de séquences de certains caractères. Les caractères d’opérateur autorisés sont `!` , `%` , `&` , `*` , `+` , `-` , `.` ,, `/` `<` , `=` , `>` , `?` , `@` ,, `^` `|` et `~` . Le `~` caractère a la signification particulière de la création d’un opérateur unaire et ne fait pas partie de la séquence de caractères de l’opérateur. Tous les opérateurs ne peuvent pas être rendus unaires.

Selon la séquence de caractères exacte que vous utilisez, votre opérateur aura une certaine priorité et associativité. L’associativité peut être de gauche à droite ou de droite à gauche et est utilisée chaque fois que des opérateurs du même niveau de priorité apparaissent sans parenthèses dans l’ordre.

Le caractère `.` d’opérateur n’affecte pas la précédence. ainsi, par exemple, si vous souhaitez définir votre propre version de la multiplication qui a la même priorité et associativité que la multiplication ordinaire, vous pouvez créer des opérateurs tels que `.*` .

Seuls les opérateurs `?` et `?<-` peuvent commencer par `?` .

Une table qui affiche la priorité de tous les opérateurs en F # est disponible dans [référence des symboles et des opérateurs](./symbol-and-operator-reference/index.md).

## <a name="overloaded-operator-names"></a>Noms des opérateurs surchargés

Quand le compilateur F # compile une expression d’opérateur, il génère une méthode qui a un nom généré par le compilateur pour cet opérateur. Il s’agit du nom qui s’affiche dans le langage MSIL (Microsoft Intermediate Language) pour la méthode et également dans la réflexion et IntelliSense. Normalement, vous n’avez pas besoin d’utiliser ces noms dans le code F #.

Le tableau suivant présente les opérateurs standard et leurs noms générés correspondants.

|Opérateur|Nom généré|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

Notez que l' `not` opérateur en F # n’est pas émis `op_Inequality` , car il ne s’agit pas d’un opérateur symbolique. Il s’agit d’une fonction qui émet un langage intermédiaire qui nie une expression booléenne.

D’autres combinaisons de caractères d’opérateur qui ne sont pas répertoriées ici peuvent être utilisées en tant qu’opérateurs et ont des noms qui sont composés en concaténant des noms pour les caractères individuels du tableau suivant. Par exemple, + ! devient `op_PlusBang` .

|Caractère d’opérateur|Nom|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>Opérateurs prefix et infixe

Les opérateurs de *préfixe* sont censés être placés devant un opérande ou des opérandes, à l’instar d’une fonction. Les opérateurs *infixes* sont censés être placés entre les deux opérandes.

Seuls certains opérateurs peuvent être utilisés comme opérateurs de préfixe. Certains opérateurs sont toujours des opérateurs de préfixe, d’autres peuvent être infixes ou préfixes, tandis que les autres sont toujours des opérateurs infixes. Les opérateurs qui commencent par `!` , except `!=` et l’opérateur `~` , ou les séquences répétées de `~` , sont toujours des opérateurs de préfixe. Les opérateurs,,,,,, `+` `-` `+.` et peuvent être des opérateurs de `-.` `&` `&&` `%` `%%` préfixe ou des opérateurs infixes. Vous pouvez distinguer la version préfixée de ces opérateurs de la version infix en ajoutant un `~` au début d’un opérateur préfixé lorsqu’il est défini. Le `~` n’est pas utilisé lorsque vous utilisez l’opérateur, uniquement lorsqu’il est défini.

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de la surcharge d’opérateur pour implémenter un type de fraction. Une fraction est représentée par un numérateur et un dénominateur. La fonction `hcf` est utilisée pour déterminer le facteur commun le plus élevé, qui est utilisé pour réduire les fractions.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Output:**

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Opérateurs au niveau global

Vous pouvez également définir des opérateurs au niveau global. Le code suivant définit un opérateur `+?` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

La sortie du code ci-dessus est `12` .

Vous pouvez redéfinir les opérateurs arithmétiques réguliers de cette manière, car les règles de portée pour F # dictent que les opérateurs nouvellement définis sont prioritaires sur les opérateurs intégrés.

Le mot clé `inline` est souvent utilisé avec les opérateurs globaux, qui sont souvent des petites fonctions qui sont mieux intégrées dans le code appelant. La création d’une fonction d’opérateur Inline permet également de travailler avec des paramètres de type résolus statiquement pour produire du code générique résolu statiquement. Pour plus d’informations, consultez [fonctions inline](./functions/inline-functions.md) et [paramètres de type résolus statiquement](./generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Voir aussi

- [Members](./members/index.md) (Membres)
