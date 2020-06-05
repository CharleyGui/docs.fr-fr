---
title: For Each...Next (instruction)
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
ms.openlocfilehash: 0feb938121a97b06509b472652e6a753841ab2b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404652"
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

## <a name="parts"></a>Éléments

|Terme|Définition|
|---|---|
|`element`|Obligatoire dans l' `For Each` instruction. Facultatif dans l' `Next` instruction. Variable. Utilisé pour itérer au sein des éléments de la collection.|
|`datatype`|Facultatif si [`Option Infer`](option-infer-statement.md) est activé (valeur par défaut) ou si est `element` déjà déclaré ; obligatoire si `Option Infer` est désactivé et `element` n’est pas déjà déclaré. Le type de données `element`.|
|`group`|Obligatoire. Variable avec un type qui est un type de collection ou un objet. Fait référence à la collection sur laquelle le `statements` doit être répété.|
|`statements`|Facultatif. Une ou plusieurs instructions entre `For Each` et `Next` qui s’exécutent sur chaque élément dans `group` .|
|`Continue For`|Facultatif. Transfère le contrôle au début de la `For Each` boucle.|
|`Exit For`|Facultatif. Transfère le contrôle hors de la `For Each` boucle.|
|`Next`|Obligatoire. Termine la définition de la `For Each` boucle.|

## <a name="simple-example"></a>Exemple simple

Utilisez une `For Each` boucle... `Next` lorsque vous souhaitez répéter un ensemble d’instructions pour chaque élément d’une collection ou d’un tableau.

> [!TIP]
> [Pour... L’instruction suivante](for-next-statement.md) fonctionne bien lorsque vous pouvez associer chaque itération d’une boucle à une variable de contrôle et déterminer les valeurs initiale et finale de cette variable. Toutefois, lorsque vous travaillez avec une collection, le concept de valeurs initiales et finales n’est pas significatif et vous ne connaissez pas nécessairement le nombre d’éléments de la collection. Dans ce genre de cas, une `For Each` boucle... `Next` est souvent un meilleur choix.

Dans l’exemple suivant, le `For Each` ...`Next` l’instruction itère au sein de tous les éléments d’une collection de listes.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Pour obtenir plus d’exemples, consultez [Collections](../../../standard/collections/index.md) et [tableaux](../../programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Nested Loops

Vous pouvez imbriquer `For Each` des boucles en plaçant une boucle dans une autre.

L’exemple suivant illustre l’imbrication de `For Each` ...`Next` celles.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Lorsque vous imbriquez des boucles, chaque boucle doit avoir une `element` variable unique.

Vous pouvez également imbriquer différents genres de structures de contrôle dans les deux. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Quitter pour et continuer pour

L’instruction [Exit for](exit-statement.md) provoque l’arrêt de l’exécution de `For` ...`Next` effectue une boucle et transfère le contrôle à l’instruction qui suit l' `Next` instruction.

L' `Continue For` instruction transfère immédiatement le contrôle à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction continue](continue-statement.md).

L’exemple suivant montre comment utiliser les `Continue For` instructions et `Exit For` .

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Vous pouvez placer n’importe quel nombre d' `Exit For` instructions dans une `For Each` boucle. Lorsqu’il est utilisé dans `For Each` les boucles imbriquées, l' `Exit For` exécution quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.

`Exit For`est souvent utilisé après une évaluation d’une condition, par exemple dans un `If` ... `Then` ...`Else` arborescence. Vous pouvez utiliser `Exit For` pour les conditions suivantes :

- La poursuite de l’itération est inutile ou impossible. Cela peut être dû à une valeur erronée ou à une demande d’arrêt.

- Une exception est interceptée dans `Try` ... `Catch` ...`Finally`. Vous pouvez utiliser `Exit For` à la fin du `Finally` bloc.

- Il s’agit d’une boucle sans fin, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini. Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour échapper la boucle. Pour plus d’informations, consultez [do... Instruction de boucle](do-loop-statement.md).

## <a name="iterators"></a>Iterators

Vous utilisez un *itérateur* pour exécuter une itération personnalisée sur une collection. Un itérateur peut être une fonction ou un `Get` accesseur. Elle utilise une `Yield` instruction pour retourner chaque élément de la collection un par un.

Vous appelez un itérateur à l’aide d’une `For Each...Next` instruction. Chaque itération de la boucle `For Each` appelle l’itérateur. Quand une `Yield` instruction est atteinte dans l’itérateur, l’expression dans l' `Yield` instruction est retournée, et l’emplacement actuel dans le code est conservé. L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.

L’exemple suivant utilise une fonction d’itérateur. La fonction Iterator a une `Yield` instruction qui se trouve à l’intérieur d’une instruction [for... Next](for-next-statement.md) . Dans la `ListEvenNumbers` méthode, chaque itération du `For Each` corps d’instruction crée un appel à la fonction d’itérateur, qui passe à l' `Yield` instruction suivante.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md), [instruction yield](yield-statement.md)et [iterator](../modifiers/iterator.md).

## <a name="technical-implementation"></a>Implémentation technique

Quand un `For Each` ...`Next` l’instruction s’exécute, Visual Basic évalue la collection une seule fois, avant le démarrage de la boucle. Si votre bloc d’instructions change `element` ou `group` , ces modifications n’affectent pas l’itération de la boucle.

Lorsque tous les éléments de la collection ont été assignés successivement à `element` , la `For Each` boucle s’arrête et le contrôle passe à l’instruction qui suit l' `Next` instruction.

Si l' [Option Infer](option-infer-statement.md) est définie sur on (paramètre par défaut), le compilateur Visual Basic peut déduire le type de données de `element` . Si elle est désactivée et `element` n’a pas été déclarée en dehors de la boucle, vous devez la déclarer dans l' `For Each` instruction. Pour déclarer explicitement le type de données `element` , utilisez une `As` clause. À moins que le type de données de l’élément ne soit défini en dehors de la `For Each` construction... `Next` , sa portée est le corps de la boucle. Notez que vous ne pouvez pas déclarer `element` à la fois à l’extérieur et à l’intérieur de la boucle.

Vous pouvez éventuellement spécifier `element` dans l' `Next` instruction. Cela améliore la lisibilité de votre programme, en particulier si vous avez des `For Each` boucles imbriquées. Vous devez spécifier la même variable que celle qui apparaît dans l’instruction correspondante `For Each` .

Vous souhaiterez peut-être éviter de modifier la valeur de `element` à l’intérieur d’une boucle. Cela peut compliquer la lecture et le débogage de votre code. La modification de la valeur de `group` n’affecte pas la collection ou ses éléments, qui ont été déterminés lors de la première entrée de la boucle.

Lorsque vous imbriquez des boucles, si une `Next` instruction d’un niveau d’imbrication externe est rencontrée avant le `Next` d’un niveau interne, le compilateur signale une erreur. Toutefois, le compilateur peut détecter cette erreur qui se chevauche uniquement si vous spécifiez `element` dans chaque `Next` instruction.

Si votre code dépend de la traversée d’une collection dans un ordre particulier, une `For Each` boucle... `Next` n’est pas le meilleur choix, sauf si vous connaissez les caractéristiques de l’objet énumérateur exposé par la collection. L’ordre de traversée n’est pas déterminé par Visual Basic, mais par la <xref:System.Collections.IEnumerator.MoveNext%2A> méthode de l’objet énumérateur. Par conséquent, vous pouvez ne pas être en mesure de prédire quel élément de la collection est le premier à retourner dans `element` , ou qui est le suivant à retourner après un élément donné. Vous pouvez obtenir des résultats plus fiables à l’aide d’une structure de boucle différente, telle que `For` ... `Next` ou `Do` ... `Loop` .

Le Runtime doit pouvoir convertir les éléments dans en `group` `element` . L' `Option Strict` instruction [] contrôle si les conversions étendues et restrictives sont autorisées ( `Option Strict` est désactivé, sa valeur par défaut) ou si seules les conversions étendues sont autorisées ( `Option Strict` est activé). Pour plus d’informations, consultez [conversions restrictives](#narrowing-conversions).

Le type de données de `group` doit être un type référence qui fait référence à une collection ou à un tableau qui est énumérable. Cela signifie généralement que `group` fait référence à un objet qui implémente l' <xref:System.Collections.IEnumerable> interface de l' `System.Collections` espace de noms ou l' <xref:System.Collections.Generic.IEnumerable%601> interface de l' `System.Collections.Generic` espace de noms. `System.Collections.IEnumerable`définit la <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthode, qui retourne un objet énumérateur pour la collection. L’objet énumérateur implémente l' `System.Collections.IEnumerator` interface de l' `System.Collections` espace de noms et expose la <xref:System.Collections.IEnumerator.Current%2A> propriété et les <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.MoveNext%2A> méthodes et. Visual Basic les utilise pour parcourir la collection.

### <a name="narrowing-conversions"></a>conversions restrictives

Lorsque `Option Strict` a la valeur `On` , les conversions restrictives provoquent normalement des erreurs de compilation. `For Each`Toutefois, dans une instruction, les conversions des éléments dans `group` vers `element` sont évaluées et exécutées au moment de l’exécution, et les erreurs du compilateur provoquées par les conversions restrictives sont supprimées.

Dans l’exemple suivant, l’assignation de `m` comme valeur initiale pour `n` ne se compile pas lorsque `Option Strict` est activé, car la conversion d’un `Long` en `Integer` est une conversion restrictive. Toutefois, dans l' `For Each` instruction, aucune erreur du compilateur n’est signalée, même si l’assignation à `number` requiert la même conversion de `Long` en `Integer` . Dans l' `For Each` instruction qui contient un grand nombre, une erreur d’exécution se produit lorsque <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> est appliqué au grand nombre.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Appels IEnumerator

Lorsque l’exécution d’une `For Each` boucle... `Next` démarre, Visual Basic vérifie que `group` fait référence à un objet de collection valide. Si ce n’est pas le cas, une exception est levée. Sinon, elle appelle la <xref:System.Collections.IEnumerator.MoveNext%2A> méthode et la <xref:System.Collections.IEnumerator.Current%2A> propriété de l’objet énumérateur pour retourner le premier élément. Si `MoveNext` indique qu’il n’y a pas d’élément suivant, autrement dit, si la collection est vide, la `For Each` boucle s’arrête et le contrôle passe à l’instruction qui suit l' `Next` instruction. Sinon, Visual Basic définit `element` sur le premier élément et exécute le bloc d’instructions.

Chaque fois que Visual Basic rencontre l' `Next` instruction, il retourne à l' `For Each` instruction. Là encore, il appelle `MoveNext` et `Current` retourne l’élément suivant, et il exécute à nouveau le bloc ou arrête la boucle en fonction du résultat. Ce processus se poursuit jusqu’à ce qu' `MoveNext` indique qu’il n’existe aucun élément suivant ou qu’une `Exit For` instruction soit rencontrée.

**Modification de la collection.** L’objet énumérateur retourné par <xref:System.Collections.IEnumerable.GetEnumerator%2A> normalement ne vous permet pas de modifier la collection en ajoutant, en supprimant, en remplaçant ou en réordonnant des éléments. Si vous modifiez la collection après avoir lancé une `For Each` boucle... `Next` , l’objet énumérateur devient non valide et la tentative suivante d’accès à un élément provoque une <xref:System.InvalidOperationException> exception.

Toutefois, ce blocage de modification n’est pas déterminé par Visual Basic, mais plutôt par l’implémentation de l' <xref:System.Collections.IEnumerable> interface. Il est possible d’implémenter `IEnumerable` de manière à permettre la modification pendant l’itération. Si vous envisagez d’effectuer une telle modification dynamique, assurez-vous que vous comprenez les caractéristiques de l' `IEnumerable` implémentation sur la collection que vous utilisez.

**Modification des éléments de la collection.** La <xref:System.Collections.IEnumerator.Current%2A> propriété de l’objet énumérateur est [ReadOnly](../modifiers/readonly.md)et retourne une copie locale de chaque élément de la collection. Cela signifie que vous ne pouvez pas modifier les éléments eux-mêmes dans une `For Each` boucle... `Next` . Toute modification que vous effectuez affecte uniquement la copie locale à partir de `Current` et n’est pas reflétée dans la collection sous-jacente. Toutefois, si un élément est un type référence, vous pouvez modifier les membres de l’instance vers laquelle il pointe. L’exemple suivant modifie le `BackColor` membre de chaque `thisControl` élément. Toutefois, vous ne pouvez pas le modifier `thisControl` .

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

L’exemple précédent peut modifier le `BackColor` membre de chaque `thisControl` élément, même s’il ne peut pas se modifier `thisControl` lui-même.

**Parcours des tableaux.** Étant donné que la <xref:System.Array> classe implémente l' <xref:System.Collections.IEnumerable> interface, tous les tableaux exposent la <xref:System.Array.GetEnumerator%2A> méthode. Cela signifie que vous pouvez effectuer une itération au sein d’un tableau avec une `For Each` boucle... `Next` . Toutefois, vous ne pouvez lire que les éléments du tableau. Vous ne pouvez pas les modifier.

## <a name="example"></a>Exemple

L’exemple suivant répertorie tous les dossiers dans le dossier C:\ dans le répertoire à l’aide de la <xref:System.IO.DirectoryInfo> classe.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Exemple

L’exemple suivant illustre une procédure de tri d’une collection. L’exemple trie les instances d’une `Car` classe qui sont stockées dans un <xref:System.Collections.Generic.List%601> . La classe `Car` implémente l’interface <xref:System.IComparable%601>, ce qui implique l’implémentation de la méthode <xref:System.IComparable%601.CompareTo%2A>.

Chaque appel à la <xref:System.IComparable%601.CompareTo%2A> méthode effectue une comparaison unique qui est utilisée pour le tri. Le code écrit par l’utilisateur dans la méthode `CompareTo` retourne une valeur pour chaque comparaison de l’objet actuel avec un autre objet. La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux. Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».

Dans la méthode `ListCars`, l’instruction `cars.Sort()` trie la liste. Cet appel à la méthode <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> entraîne l’appel automatique de la méthode `CompareTo` pour les objets `Car` dans `List`.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Voir aussi

- [Regroupements](../../../standard/collections/index.md)
- [For...Next (instruction)](for-next-statement.md)
- [Structures de boucle](../../programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While (instruction)](while-end-while-statement.md)
- [Do...Loop (instruction)](do-loop-statement.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Initialiseurs d'objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Initialiseurs de collection](../../programming-guide/language-features/collection-initializers/index.md)
- [Tableaux](../../programming-guide/language-features/arrays/index.md)
