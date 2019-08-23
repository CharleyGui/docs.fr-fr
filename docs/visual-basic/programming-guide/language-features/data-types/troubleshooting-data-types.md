---
title: Dépannage des types de données (Visual Basic)
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
ms.openlocfilehash: 5b2cb0d5270b7e14c3462aeaf54942f939511fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933229"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Dépannage des types de données (Visual Basic)
Cette page répertorie certains problèmes courants qui peuvent se produire lorsque vous effectuez des opérations sur des types de données intrinsèques.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Les expressions à virgule flottante ne sont pas considérées comme égales  
 Lorsque vous travaillez avec des nombres à virgule flottante ([type de données unique](../../../../visual-basic/language-reference/data-types/single-data-type.md) et [type de données double](../../../../visual-basic/language-reference/data-types/double-data-type.md)), n’oubliez pas qu’ils sont stockés sous forme de fractions binaires. Cela signifie qu’elles ne peuvent pas contenir une représentation exacte d’une quantité qui n’est pas une fraction binaire (au format k/(2 ^ n) où k et n sont des entiers). Par exemple, 0,5 (= 1/2) et 0,3125 (= 5/16) peuvent être conservés comme valeurs précises, alors que 0,2 (= 1/5) et 0,3 (= 3/10) peuvent uniquement être des approximations.  
  
 En raison de ce imprécision, vous ne pouvez pas vous reposer sur des résultats exacts lorsque vous utilisez des valeurs à virgule flottante. En particulier, deux valeurs théoriquement égales peuvent avoir des représentations légèrement différentes.  
  
| Pour comparer les quantités à virgule flottante | 
|---| 
|1.  Calculez la valeur absolue de la différence à l' <xref:System.Math.Abs%2A> aide de la <xref:System.Math> méthode de la <xref:System> classe dans l’espace de noms.<br />2.  Déterminez une différence maximale acceptable, de sorte que vous pouvez considérer les deux quantités comme étant égales pour des raisons pratiques si leur différence n’est pas plus importante.<br />3.  Comparez la valeur absolue de la différence à la différence acceptable.|  
  
 L’exemple suivant montre à la fois une comparaison incorrecte et correcte de deux `Double` valeurs.  
  
 [!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]  
  
 L’exemple précédent utilise la <xref:System.Double.ToString%2A> méthode de la <xref:System.Double> structure afin qu’il puisse spécifier une meilleure précision que `CStr` le mot clé utilise. La valeur par défaut est 15 chiffres, mais le format «G17» l’étend jusqu’à 17 chiffres.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>L’opérateur mod ne retourne pas de résultat exact  
 En raison du imprécision de stockage à virgule flottante, l' [opérateur mod](../../../../visual-basic/language-reference/operators/mod-operator.md) peut retourner un résultat inattendu lorsqu’au moins l’un des opérandes est à virgule flottante.  
  
 Le [type de données decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) n’utilise pas la représentation à virgule flottante. De nombreux nombres qui sont inexacts `Double` dans `Single` et sont `Decimal` exacts dans (par exemple 0,2 et 0,3). Bien que l’arithmétique soit `Decimal` plus lente dans que dans le calcul à virgule flottante, il peut être utile de réduire les performances pour obtenir une meilleure précision.  
  
|Pour rechercher le reste entier des quantités à virgule flottante|  
|---|  
|1.  Déclarez les `Decimal`variables en tant que.<br />2.  Utilisez le caractère `D` de type de littéral pour forcer des `Decimal`littéraux, si leurs valeurs sont trop élevées pour `Long` le type de données.|  
  
 L’exemple suivant illustre le imprécision potentiel des opérandes à virgule flottante.  
  
 [!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]  
  
 L’exemple précédent utilise la <xref:System.Double.ToString%2A> méthode de la <xref:System.Double> structure afin qu’il puisse spécifier une meilleure précision que `CStr` le mot clé utilise. La valeur par défaut est 15 chiffres, mais le format «G17» l’étend jusqu’à 17 chiffres.  
  
 Comme `zeroPointTwo` est`Double`, sa valeur pour 0,2 est une fraction binaire à répétition infinie avec une valeur stockée de 0.20000000000000001. La Division de 2,0 par cette quantité produit 9.9999999999999995 avec un reste de 0.19999999999999991.  
  
 Dans l’expression pour `decimalRemainder`, le caractère `D` de type de littéral force les deux `Decimal`opérandes à, et 0,2 a une représentation précise. Par conséquent `Mod` , l’opérateur produit le reste attendu de 0,0.  
  
 Notez qu’il n’est pas suffisant de `decimalRemainder` déclarer `Decimal`en tant que. Vous devez également forcer les littéraux sur `Decimal`, ou ils utilisent `Double` par défaut et `decimalRemainder` reçoivent la même valeur inexacte `doubleRemainder`que.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Le type booléen ne convertit pas correctement le type numérique  
 Les valeurs de [type de données Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) ne sont pas stockées sous forme de nombres, et les valeurs stockées ne sont pas destinées à être équivalentes aux nombres. Pour la compatibilité avec les versions antérieures, Visual Basic fournit des mots clés de `CBool`conversion `CInt`([fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md),,, etc. `Boolean` ) pour effectuer une conversion entre des types numériques et. Toutefois, d’autres langages effectuent parfois ces conversions différemment, comme les méthodes .NET Framework.  
  
 Vous ne devez jamais écrire du code qui s’appuie sur des valeurs `True` numériques `False`équivalentes pour et. Dans la mesure du possible, limitez `Boolean` l’utilisation des variables aux valeurs logiques pour lesquelles elles sont conçues. Si vous devez mélanger `Boolean` des valeurs et des valeurs numériques, assurez-vous que vous comprenez la méthode de conversion que vous sélectionnez.  
  
### <a name="conversion-in-visual-basic"></a>Conversion en Visual Basic  
 Lorsque vous utilisez les `CType` mots `CBool` clés de conversion ou pour convertir des types `Boolean`de données numériques `False` en, 0 devient et `True`toutes les autres valeurs deviennent. Lorsque vous convertissez `Boolean` des valeurs en types numériques à l’aide des mots clés de `True` conversion, `False` devient 0 et devient-1.  
  
### <a name="conversion-in-the-framework"></a>Conversion dans le Framework  
 La <xref:System.Convert.ToInt32%2A> méthode de la <xref:System.Convert> <xref:System> classe`True` de l’espace de noms est convertie en + 1.  
  
 Si vous devez convertir une `Boolean` valeur en un type de données numérique, soyez prudent quant à la méthode de conversion que vous utilisez.  
  
## <a name="character-literal-generates-compiler-error"></a>Le littéral de caractère génère une erreur du compilateur  
 En l’absence de caractères de type, Visual Basic utilise des types de données par défaut pour les littéraux. Le type par défaut d’un littéral de caractère, placé entre guillemets (`" "`), est. `String`  
  
 Le `String` type de données ne s’étend pas au [type de données char](../../../../visual-basic/language-reference/data-types/char-data-type.md). Cela signifie que si vous souhaitez assigner un littéral à `Char` une variable, vous devez effectuer une conversion restrictive ou forcer le littéral `Char` au type.  

|Pour créer un littéral de caractère à assigner à une variable ou une constante|
|---|  
|1.  Déclarez la variable ou la `Char`constante en tant que.<br />2.  Placez la valeur de caractère entre guillemets`" "`().<br />3.  Suivez le guillemet double fermant avec le caractère `C` de type de littéral pour forcer le `Char`littéral. Cela est nécessaire si le commutateur de vérification de type ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `On`, et il est souhaitable dans tous les cas.|  
  
 L’exemple suivant montre les assignations infructueuses et réussies d’un `Char` littéral à une variable.  
  
 [!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]  
  
 Il y a toujours un risque d’utiliser des conversions restrictives, car elles peuvent échouer au moment de l’exécution. Par exemple, une conversion de `String` en `Char` peut échouer si `String` la valeur contient plusieurs caractères. Par conséquent, il est préférable d’utiliser le `C` caractère de type.  
  
## <a name="string-conversion-fails-at-run-time"></a>La conversion de chaîne échoue au moment de l’exécution  
 Le [type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md) participe à très peu de conversions étendues. `String`s’étend uniquement à lui- `Object`même et, `Char` et `Char()` seuls et `Char` (un tableau) `String`s’étendent à. Cela est dû `String` au fait que les variables et les constantes peuvent contenir des valeurs que d’autres types de données ne peuvent pas contenir.  
  
 Quand le commutateur de vérification de type ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est, le compilateur n' `On`autorise pas toutes les conversions restrictives implicites. Cela comprend ceux qui `String`impliquent. Votre code peut toujours utiliser des mots clés de `CStr` conversion, tels que et la [fonction CType](../../../../visual-basic/language-reference/functions/ctype-function.md), qui dirigent le .NET Framework à tenter la conversion.  
  
> [!NOTE]
> L’erreur de conversion restrictive est supprimée pour les conversions des éléments d’une `For Each…Next` collection vers la variable de contrôle de boucle. Pour plus d’informations et d’exemples, consultez la section «conversions restrictives» dans [for each... Instruction suivante](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Protection de la conversion restrictive  
 L’inconvénient des conversions restrictives réside dans le fait qu’elles peuvent échouer au moment de l’exécution. Par exemple, si une `String` variable contient une valeur autre que «true» ou «false», elle ne peut `Boolean`pas être convertie en. S’il contient des caractères de ponctuation, la conversion en un type numérique échoue. À moins que vous sachiez que votre variable contient toujours des `String` valeurs que le type de destination peut accepter, vous ne devez pas essayer de convertir.  
  
 Si vous devez effectuer une `String` conversion de vers un autre type de données, la procédure la plus sûre consiste à encadrer la tentative de conversion dans le [bloc try... Catch... Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Cela vous permet de gérer un échec au moment de l’exécution.  
  
### <a name="character-arrays"></a>Tableaux de caractères  
 Un unique `Char` et un tableau d' `Char` éléments s’étendent `String`tous deux à. Toutefois, `String` n’est pas étendu `Char()`à. Pour convertir une `String` valeur `Char` en tableau, vous pouvez utiliser la <xref:System.String.ToCharArray%2A> méthode de la <xref:System.String?displayProperty=nameWithType> classe.  
  
### <a name="meaningless-values"></a>Valeurs sans signification  
 En général, `String` les valeurs ne sont pas significatives dans les autres types de données, et la conversion est extrêmement artificielle et dangereuse. Dans la mesure du possible, limitez `String` l’utilisation des variables aux séquences de caractères pour lesquelles elles sont conçues. Vous ne devez jamais écrire du code qui s’appuie sur des valeurs équivalentes dans d’autres types.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
- [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Utilisation efficace des types de données](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
