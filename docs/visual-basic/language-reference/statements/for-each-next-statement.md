---
title: For Each...Next, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: f56e5defa2328011d222bfca05334b610e805055
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332787"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next, instruction (Visual Basic)

Répète un groupe d’instructions pour chaque élément d’une collection.

## <a name="syntax"></a>Syntaxe

```vb
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>Composants

|Terme|Définition|
|---|---|
|`element`|Obligatoire dans l’instruction `For Each`. Facultatif dans l’instruction `Next`. Variable. Utilisé pour itérer au sein des éléments de la collection.|
|`datatype`|Facultatif si [`Option Infer`](option-infer-statement.md) est activé (valeur par défaut) ou `element` est déjà déclaré ; obligatoire si `Option Infer` est désactivé et `element` n’est pas déjà déclaré. Type de données de l' `element`.|
|`group`|Requis. Variable avec un type qui est un type de collection ou un objet. Fait référence à la collection sur laquelle les `statements` doivent être répétées.|
|`statements`|Ce paramètre est facultatif. Une ou plusieurs instructions entre `For Each` et `Next` qui s’exécutent sur chaque élément dans `group`.|
|`Continue For`|Ce paramètre est facultatif. Transfère le contrôle au début de la boucle `For Each`.|
|`Exit For`|Ce paramètre est facultatif. Transfère le contrôle hors de la boucle de `For Each`.|
|`Next`|Requis. Termine la définition de la boucle `For Each`.|

## <a name="simple-example"></a>Exemple simple

Utilisez une boucle `For Each`...`Next` lorsque vous souhaitez répéter un ensemble d’instructions pour chaque élément d’une collection ou d’un tableau.

> [!TIP]
> [Pour... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) fonctionne bien lorsque vous pouvez associer chaque itération d’une boucle à une variable de contrôle et déterminer les valeurs initiale et finale de cette variable. Toutefois, lorsque vous travaillez avec une collection, le concept de valeurs initiales et finales n’est pas significatif et vous ne connaissez pas nécessairement le nombre d’éléments de la collection. Dans ce genre de cas, une boucle `For Each`...`Next` est souvent un meilleur choix.

Dans l’exemple suivant, l' `For Each`...`Next` l’instruction itère au sein de tous les éléments d’une collection de listes.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Pour obtenir plus d’exemples, consultez [Collections](../../../standard/collections/index.md) et [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Boucles imbriquées

Vous pouvez imbriquer des boucles `For Each` en plaçant une boucle dans une autre.

L’exemple suivant illustre une `For Each`imbriquée...`Next` Celles.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Lorsque vous imbriquez des boucles, chaque boucle doit avoir une variable `element` unique.

Vous pouvez également imbriquer différents genres de structures de contrôle dans les deux. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Quitter pour et continuer pour

L’instruction [Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) force l’exécution à quitter l' `For`...`Next` effectue une boucle et transfère le contrôle à l’instruction qui suit l’instruction `Next`.

L’instruction `Continue For` transfère immédiatement le contrôle à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction continue](../../../visual-basic/language-reference/statements/continue-statement.md).

L’exemple suivant montre comment utiliser les instructions `Continue For` et `Exit For`.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Vous pouvez placer n’importe quel nombre d’instructions `Exit For` dans une boucle `For Each`. Lorsqu’elle est utilisée dans des boucles `For Each` imbriquées, `Exit For` provoque l’arrêt de l’exécution de la boucle la plus profonde et transfère le contrôle au niveau supérieur d’imbrication suivant.

`Exit For` est souvent utilisé après une évaluation d’une condition, par exemple dans une structure `If`...`Then`...`Else`. Vous pouvez utiliser `Exit For` pour les conditions suivantes :

- La poursuite de l’itération est inutile ou impossible. Cela peut être dû à une valeur erronée ou à une demande d’arrêt.

- Une exception est interceptée dans une `Try`...`Catch`...`Finally`. Vous pouvez utiliser `Exit For` à la fin du bloc `Finally`.

- Il s’agit d’une boucle sans fin, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini. Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour échapper à la boucle. Pour plus d’informations, consultez [do... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>Itérateurs

Vous utilisez un *itérateur* pour exécuter une itération personnalisée sur une collection. Un itérateur peut être une fonction ou un accesseur `Get`. Elle utilise une instruction `Yield` pour retourner chaque élément de la collection un par un.

Vous appelez un itérateur à l’aide d’une instruction `For Each...Next`. Chaque itération de la boucle `For Each` appelle l’itérateur. Quand une instruction `Yield` est atteinte dans l’itérateur, l’expression dans l’instruction `Yield` est retournée, et l’emplacement actuel dans le code est conservé. L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.

L’exemple suivant utilise une fonction d’itérateur. La fonction Iterator a une instruction `Yield` qui se trouve à l’intérieur d’une instruction [for... Next](../../../visual-basic/language-reference/statements/for-next-statement.md) . Dans la méthode `ListEvenNumbers`, chaque itération du corps d’instruction `For Each` crée un appel à la fonction d’itérateur, qui passe à l’instruction de `Yield` suivante.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md), [instruction yield](../../../visual-basic/language-reference/statements/yield-statement.md)et [iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Implémentation technique

Quand un `For Each`...`Next` l’instruction s’exécute, Visual Basic évalue la collection une seule fois, avant le démarrage de la boucle. Si votre bloc d’instructions change `element` ou `group`, ces modifications n’affectent pas l’itération de la boucle.

Lorsque tous les éléments de la collection ont été assignés successivement à `element`, la boucle `For Each` s’arrête et le contrôle passe à l’instruction qui suit l’instruction `Next`.

Si l' [Option Infer](option-infer-statement.md) est définie sur on (paramètre par défaut), le compilateur Visual Basic peut déduire le type de données de `element`. Si elle est désactivée et `element` n’a pas été déclarée en dehors de la boucle, vous devez la déclarer dans l’instruction `For Each`. Pour déclarer explicitement le type de données de `element`, utilisez une clause `As`. À moins que le type de données de l’élément ne soit défini en dehors de la construction `For Each`...`Next`, son étendue est le corps de la boucle. Notez que vous ne pouvez pas déclarer `element` à la fois à l’extérieur et à l’intérieur de la boucle.

Vous pouvez éventuellement spécifier `element` dans l’instruction `Next`. Cela améliore la lisibilité de votre programme, surtout si vous avez imbriqué des boucles de `For Each`. Vous devez spécifier la même variable que celle qui apparaît dans l’instruction `For Each` correspondante.

Vous souhaiterez peut-être éviter de modifier la valeur de `element` à l’intérieur d’une boucle. Cela peut compliquer la lecture et le débogage de votre code. La modification de la valeur de `group` n’affecte pas la collection ou ses éléments, qui ont été déterminés lors de la première entrée de la boucle.

Lorsque vous imbriquez des boucles, si une instruction `Next` d’un niveau d’imbrication externe est rencontrée avant la `Next` d’un niveau interne, le compilateur signale une erreur. Toutefois, le compilateur peut détecter cette erreur qui se chevauche uniquement si vous spécifiez `element` dans chaque instruction `Next`.

Si votre code dépend de la traversée d’une collection dans un ordre particulier, une boucle `For Each`...`Next` n’est pas le meilleur choix, sauf si vous connaissez les caractéristiques de l’objet énumérateur exposé par la collection. L’ordre de traversée n’est pas déterminé par Visual Basic, mais par la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> de l’objet énumérateur. Par conséquent, vous pouvez ne pas être en mesure de prédire quel élément de la collection est le premier à être retourné dans `element`, ou qui est le suivant à retourner après un élément donné. Vous pouvez obtenir des résultats plus fiables à l’aide d’une structure de boucle différente, par exemple `For`...`Next` ou `Do`...`Loop`.

Le Runtime doit pouvoir convertir les éléments de `group` en `element`. L’instruction [`Option Strict`] contrôle si les conversions étendues et restrictives sont autorisées (`Option Strict` est désactivé, sa valeur par défaut) ou si seules les conversions étendues sont autorisées (`Option Strict` est activé). Pour plus d’informations, consultez [conversions restrictives](#narrowing-conversions).

Le type de données de `group` doit être un type référence qui fait référence à une collection ou à un tableau qui est énumérable. Le plus souvent, cela signifie que `group` fait référence à un objet qui implémente l’interface <xref:System.Collections.IEnumerable> de l’espace de noms `System.Collections` ou de l’interface <xref:System.Collections.Generic.IEnumerable%601> de l’espace de noms `System.Collections.Generic`. `System.Collections.IEnumerable` définit la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>, qui retourne un objet énumérateur pour la collection. L’objet énumérateur implémente l’interface `System.Collections.IEnumerator` de l’espace de noms `System.Collections` et expose la propriété <xref:System.Collections.IEnumerator.Current%2A> et les méthodes <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.MoveNext%2A>. Visual Basic les utilise pour parcourir la collection.

### <a name="narrowing-conversions"></a>Conversions restrictives

Lorsque `Option Strict` a la valeur `On`, les conversions restrictives entraînent généralement des erreurs de compilation. Toutefois, dans une instruction `For Each`, les conversions des éléments de `group` en `element` sont évaluées et exécutées au moment de l’exécution, et les erreurs du compilateur causées par les conversions restrictives sont supprimées.

Dans l’exemple suivant, l’assignation de `m` comme valeur initiale pour `n` ne se compile pas lorsque `Option Strict` est activé, car la conversion d’une `Long` en `Integer` est une conversion restrictive. Toutefois, dans l’instruction `For Each`, aucune erreur du compilateur n’est signalée, même si l’assignation à `number` requiert la même conversion de `Long` à `Integer`. Dans l’instruction `For Each` qui contient un grand nombre, une erreur d’exécution se produit lorsque <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> est appliqué au grand nombre.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Appels IEnumerator

Lorsque l’exécution d’une boucle `For Each`...`Next` démarre, Visual Basic vérifie que `group` fait référence à un objet de collection valide. Si ce n’est pas le cas, une exception est levée. Sinon, elle appelle la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> et la propriété <xref:System.Collections.IEnumerator.Current%2A> de l’objet énumérateur pour retourner le premier élément. Si `MoveNext` indique qu’il n’y a pas d’élément suivant, autrement dit, si la collection est vide, la boucle `For Each` s’arrête et le contrôle passe à l’instruction qui suit l’instruction `Next`. Dans le cas contraire, Visual Basic définit `element` sur le premier élément et exécute le bloc d’instructions.

Chaque fois que Visual Basic rencontre l’instruction `Next`, il retourne à l’instruction `For Each`. Là encore, il appelle `MoveNext` et `Current` pour retourner l’élément suivant, puis il exécute le bloc ou arrête la boucle en fonction du résultat. Ce processus se poursuit jusqu’à ce que `MoveNext` indique qu’il n’y a pas d’élément suivant ou qu’une instruction `Exit For` est rencontrée.

**Modification de la collection.** L’objet énumérateur retourné par <xref:System.Collections.IEnumerable.GetEnumerator%2A> ne vous permet généralement pas de modifier la collection en ajoutant, en supprimant, en remplaçant ou en réordonnant des éléments. Si vous modifiez la collection après avoir lancé une boucle `For Each`...`Next`, l’objet énumérateur devient non valide et la tentative suivante d’accès à un élément provoque une exception <xref:System.InvalidOperationException>.

Toutefois, ce blocage de modification n’est pas déterminé par Visual Basic, mais plutôt par l’implémentation de l’interface <xref:System.Collections.IEnumerable>. Il est possible d’implémenter `IEnumerable` de manière à permettre la modification pendant l’itération. Si vous envisagez d’effectuer une telle modification dynamique, assurez-vous que vous comprenez les caractéristiques de l’implémentation de `IEnumerable` sur le regroupement que vous utilisez.

**Modification des éléments de la collection.** La propriété <xref:System.Collections.IEnumerator.Current%2A> de l’objet énumérateur est [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)et retourne une copie locale de chaque élément de la collection. Cela signifie que vous ne pouvez pas modifier les éléments eux-mêmes dans une boucle `For Each`...`Next`. Toute modification que vous effectuez affecte uniquement la copie locale à partir de `Current` et n’est pas reflétée dans la collection sous-jacente. Toutefois, si un élément est un type référence, vous pouvez modifier les membres de l’instance vers laquelle il pointe. L’exemple suivant modifie le membre `BackColor` de chaque élément `thisControl`. Toutefois, vous ne pouvez pas modifier `thisControl` lui-même.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

L’exemple précédent peut modifier le membre `BackColor` de chaque élément `thisControl`, bien qu’il ne puisse pas modifier `thisControl` lui-même.

**Parcours des tableaux.** Étant donné que la classe <xref:System.Array> implémente l’interface <xref:System.Collections.IEnumerable>, tous les tableaux exposent la méthode <xref:System.Array.GetEnumerator%2A>. Cela signifie que vous pouvez effectuer une itération au sein d’un tableau avec une boucle `For Each`...`Next`. Toutefois, vous ne pouvez lire que les éléments du tableau. Vous ne pouvez pas les modifier.

## <a name="example"></a>Exemple

L’exemple suivant répertorie tous les dossiers dans le dossier C:\ Répertoire à l’aide de la classe <xref:System.IO.DirectoryInfo>.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Exemple

L’exemple suivant illustre une procédure de tri d’une collection. L’exemple trie les instances d’une classe `Car` qui sont stockées dans une <xref:System.Collections.Generic.List%601>. La classe `Car` implémente l’interface <xref:System.IComparable%601>, ce qui implique l’implémentation de la méthode <xref:System.IComparable%601.CompareTo%2A>.

Chaque appel à la méthode <xref:System.IComparable%601.CompareTo%2A> effectue une comparaison unique qui est utilisée pour le tri. Le code écrit par l’utilisateur dans la méthode `CompareTo` retourne une valeur pour chaque comparaison de l’objet actuel avec un autre objet. La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux. Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».

Dans la méthode `ListCars`, l’instruction `cars.Sort()` trie la liste. Cet appel à la méthode <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> entraîne l’appel automatique de la méthode `CompareTo` pour les objets `Car` dans `List`.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Voir aussi

- [Regroupements](../../../standard/collections/index.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Initialiseurs d’objets : types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)
