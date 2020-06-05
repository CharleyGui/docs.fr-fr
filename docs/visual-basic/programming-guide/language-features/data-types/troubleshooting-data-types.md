---
title: Dépannage des types de données
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 239e1c2f908a9023aeca6e92aff4633b60f27b69
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393401"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Dépannage des types de données (Visual Basic)

Cette page répertorie certains problèmes courants qui peuvent se produire lorsque vous effectuez des opérations sur des types de données intrinsèques.

## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Les expressions à virgule flottante ne sont pas considérées comme égales

Lorsque vous travaillez avec des nombres à virgule flottante ([type de données unique](../../../language-reference/data-types/single-data-type.md) et [type de données double](../../../language-reference/data-types/double-data-type.md)), n’oubliez pas qu’ils sont stockés sous forme de fractions binaires. Cela signifie qu’elles ne peuvent pas contenir une représentation exacte d’une quantité qui n’est pas une fraction binaire (au format k/(2 ^ n) où k et n sont des entiers). Par exemple, 0,5 (= 1/2) et 0,3125 (= 5/16) peuvent être conservés comme valeurs précises, alors que 0,2 (= 1/5) et 0,3 (= 3/10) peuvent uniquement être des approximations.

En raison de ce imprécision, vous ne pouvez pas vous reposer sur des résultats exacts lorsque vous utilisez des valeurs à virgule flottante. En particulier, deux valeurs théoriquement égales peuvent avoir des représentations légèrement différentes.

| Pour comparer les quantités à virgule flottante |
|---|
|1. Calculez la valeur absolue de la différence en utilisant la <xref:System.Math.Abs%2A> méthode de la <xref:System.Math> classe dans l' <xref:System> espace de noms.<br />2. Déterminez une différence maximale acceptable, de sorte que vous pouvez considérer les deux quantités comme étant égales pour des raisons pratiques si leur différence n’est pas supérieure.<br />3. Comparez la valeur absolue de la différence à la différence acceptable.|

L’exemple suivant montre à la fois une comparaison incorrecte et correcte de deux `Double` valeurs.

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

L’exemple précédent utilise la <xref:System.Double.ToString%2A> méthode de la <xref:System.Double> structure afin qu’il puisse spécifier une meilleure précision que le `CStr` mot clé utilise. La valeur par défaut est 15 chiffres, mais le format « G17 » l’étend jusqu’à 17 chiffres.

## <a name="mod-operator-does-not-return-accurate-result"></a>L’opérateur mod ne retourne pas de résultat exact

En raison du imprécision de stockage à virgule flottante, l' [opérateur mod](../../../language-reference/operators/mod-operator.md) peut retourner un résultat inattendu lorsqu’au moins l’un des opérandes est à virgule flottante.

Le [type de données decimal](../../../language-reference/data-types/decimal-data-type.md) n’utilise pas la représentation à virgule flottante. De nombreux nombres qui sont inexacts dans `Single` et `Double` sont exacts dans `Decimal` (par exemple 0,2 et 0,3). Bien que l’arithmétique soit plus lente dans `Decimal` que dans le calcul à virgule flottante, il peut être utile de réduire les performances pour obtenir une meilleure précision.

|Pour rechercher le reste entier des quantités à virgule flottante|
|---|
|1. déclarez les variables en tant que `Decimal` .<br />2. Utilisez le caractère de type littéral `D` pour forcer des littéraux `Decimal` , si leurs valeurs sont trop élevées pour le `Long` type de données.|

L’exemple suivant illustre le imprécision potentiel des opérandes à virgule flottante.

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

L’exemple précédent utilise la <xref:System.Double.ToString%2A> méthode de la <xref:System.Double> structure afin qu’il puisse spécifier une meilleure précision que le `CStr` mot clé utilise. La valeur par défaut est 15 chiffres, mais le format « G17 » l’étend jusqu’à 17 chiffres.

Comme `zeroPointTwo` est `Double` , sa valeur pour 0,2 est une fraction binaire à répétition infinie avec une valeur stockée de 0.20000000000000001. La Division de 2,0 par cette quantité produit 9.9999999999999995 avec un reste de 0.19999999999999991.

Dans l’expression pour `decimalRemainder` , le caractère de type de littéral `D` force les deux opérandes à `Decimal` , et 0,2 a une représentation précise. Par conséquent, l' `Mod` opérateur produit le reste attendu de 0,0.

Notez qu’il n’est pas suffisant de déclarer `decimalRemainder` en tant que `Decimal` . Vous devez également forcer les littéraux sur `Decimal` , ou ils utilisent `Double` par défaut et `decimalRemainder` reçoivent la même valeur inexacte que `doubleRemainder` .

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Le type booléen ne convertit pas correctement le type numérique

Les valeurs de [type de données Boolean](../../../language-reference/data-types/boolean-data-type.md) ne sont pas stockées sous forme de nombres, et les valeurs stockées ne sont pas destinées à être équivalentes aux nombres. Pour la compatibilité avec les versions antérieures, Visual Basic fournit des mots clés de conversion ([fonction CType](../../../language-reference/functions/ctype-function.md),, `CBool` , etc `CInt` .) pour effectuer une conversion entre `Boolean` des types numériques et. Toutefois, d’autres langages effectuent parfois ces conversions différemment, comme les méthodes .NET Framework.

Vous ne devez jamais écrire du code qui s’appuie sur des valeurs numériques équivalentes pour `True` et `False` . Dans la mesure du possible, limitez l’utilisation des `Boolean` variables aux valeurs logiques pour lesquelles elles sont conçues. Si vous devez mélanger `Boolean` des valeurs et des valeurs numériques, assurez-vous que vous comprenez la méthode de conversion que vous sélectionnez.

### <a name="conversion-in-visual-basic"></a>Conversion en Visual Basic

Lorsque vous utilisez les `CType` `CBool` Mots clés de conversion ou pour convertir des types de données numériques en `Boolean` , 0 devient `False` et toutes les autres valeurs deviennent `True` . Lorsque vous convertissez des `Boolean` valeurs en types numériques à l’aide des mots clés de conversion, `False` devient 0 et `True` devient-1.

### <a name="conversion-in-the-framework"></a>Conversion dans le Framework

La <xref:System.Convert.ToInt32%2A> méthode de la <xref:System.Convert> classe de l' <xref:System> espace de noms est convertie `True` en + 1.

Si vous devez convertir une `Boolean` valeur en un type de données numérique, soyez prudent quant à la méthode de conversion que vous utilisez.

## <a name="character-literal-generates-compiler-error"></a>Le littéral de caractère génère une erreur du compilateur

En l’absence de caractères de type, Visual Basic utilise des types de données par défaut pour les littéraux. Le type par défaut d’un littéral de caractère, placé entre guillemets ( `" "` ), est `String` .

Le `String` type de données ne s’étend pas au [type de données char](../../../language-reference/data-types/char-data-type.md). Cela signifie que si vous souhaitez assigner un littéral à une `Char` variable, vous devez effectuer une conversion restrictive ou forcer le littéral au `Char` type.

|Pour créer un littéral de caractère à assigner à une variable ou une constante|
|---|
|1. déclarez la variable ou la constante comme `Char` .<br />2. Placez la valeur de caractère entre guillemets ( `" "` ).<br />3. Suivez le guillemet double fermant avec le caractère de type `C` de littéral pour forcer le littéral `Char` . Cela est nécessaire si le commutateur de vérification de type ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) est `On` , et il est souhaitable dans tous les cas.|

L’exemple suivant montre les assignations infructueuses et réussies d’un littéral à une `Char` variable.

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

Il y a toujours un risque d’utiliser des conversions restrictives, car elles peuvent échouer au moment de l’exécution. Par exemple, une conversion de `String` en `Char` peut échouer si la `String` valeur contient plusieurs caractères. Par conséquent, il est préférable d’utiliser le `C` caractère de type.

## <a name="string-conversion-fails-at-run-time"></a>La conversion de chaîne échoue au moment de l’exécution

Le [type de données String](../../../language-reference/data-types/string-data-type.md) participe à très peu de conversions étendues. `String`s’étend uniquement à lui-même et `Object` , et seuls `Char` et `Char()` (un `Char` tableau) s’étendent à `String` . Cela est dû au fait que `String` les variables et les constantes peuvent contenir des valeurs que d’autres types de données ne peuvent pas contenir.

Quand le commutateur de vérification de type ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) est `On` , le compilateur n’autorise pas toutes les conversions restrictives implicites. Cela comprend ceux qui impliquent `String` . Votre code peut toujours utiliser des mots clés de conversion, tels que `CStr` et la [fonction CType](../../../language-reference/functions/ctype-function.md), qui dirigent le .NET Framework à tenter la conversion.

> [!NOTE]
> L’erreur de conversion restrictive est supprimée pour les conversions des éléments d’une `For Each…Next` collection vers la variable de contrôle de boucle. Pour plus d’informations et d’exemples, consultez la section « conversions restrictives » dans [for each... Instruction suivante](../../../language-reference/statements/for-each-next-statement.md).

### <a name="narrowing-conversion-protection"></a>Protection de la conversion restrictive

L’inconvénient des conversions restrictives réside dans le fait qu’elles peuvent échouer au moment de l’exécution. Par exemple, si une `String` variable contient une valeur autre que « true » ou « false », elle ne peut pas être convertie en `Boolean` . S’il contient des caractères de ponctuation, la conversion en un type numérique échoue. À moins que vous sachiez que votre `String` variable contient toujours des valeurs que le type de destination peut accepter, vous ne devez pas essayer de convertir.

Si vous devez `String` effectuer une conversion de vers un autre type de données, la procédure la plus sûre consiste à encadrer la tentative de conversion dans le [bloc try... Catch... Finally, instruction](../../../language-reference/statements/try-catch-finally-statement.md). Cela vous permet de gérer un échec au moment de l’exécution.

### <a name="character-arrays"></a>Tableaux de caractères

Un unique `Char` et un tableau d' `Char` éléments s’étendent tous deux à `String` . Toutefois, `String` n’est pas étendu à `Char()` . Pour convertir une `String` valeur en `Char` tableau, vous pouvez utiliser la <xref:System.String.ToCharArray%2A> méthode de la <xref:System.String?displayProperty=nameWithType> classe.

### <a name="meaningless-values"></a>Valeurs sans signification

En général, les `String` valeurs ne sont pas significatives dans les autres types de données, et la conversion est extrêmement artificielle et dangereuse. Dans la mesure du possible, limitez l’utilisation des `String` variables aux séquences de caractères pour lesquelles elles sont conçues. Vous ne devez jamais écrire du code qui s’appuie sur des valeurs équivalentes dans d’autres types.

## <a name="see-also"></a>Voir aussi

- [Types de données](index.md)
- [Caractères de type](type-characters.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Conversions de type en Visual Basic](type-conversions.md)
- [Types de données](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
- [Utilisation efficace des types de données](efficient-use-of-data-types.md)
