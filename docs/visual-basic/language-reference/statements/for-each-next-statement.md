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
ms.openlocfilehash: 5c2332b7371ec4ac7b5cfc0681466536d49bb7be
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026074"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next, instruction (Visual Basic)
Répète un groupe d’instructions pour chaque élément dans une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`element`|Requis dans le `For Each` instruction. Facultatif dans la `Next` instruction. variable. Utilisé pour itérer sur les éléments de la collection.|  
|`datatype`|Facultatif si [ `Option Infer` ](option-infer-statement.md) est activée (valeur par défaut) ou `element` est déjà déclaré ; obligatoire si `Option Infer` est désactivée et `element` n’est pas déjà déclaré. Type de données de l' `element`.|  
|`group`|Obligatoire. Une variable avec un type qui est un type de collection ou un objet. Fait référence à la collection sur laquelle le `statements` doivent être répétées.|  
|`statements`|Facultatif. Une ou plusieurs instructions entre `For Each` et `Next` qui s’exécutent sur chaque élément dans `group`.|  
|`Continue For`|Facultatif. Transfère le contrôle au début de la `For Each` boucle.|  
|`Exit For`|Facultatif. Transfère le contrôle de la `For Each` boucle.|  
|`Next`|Obligatoire. Termine la définition de la `For Each` boucle.|  
  
## <a name="simple-example"></a>Exemple simple  
 Utilisez un `For Each`... `Next` boucle lorsque vous souhaitez répéter un ensemble d’instructions pour chaque élément d’une collection ou un tableau.  
  
> [!TIP]
>  Un [pour... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) fonctionne bien lorsque vous pouvez associer chaque itération d’une boucle à une variable de contrôle et déterminer les valeurs initiale et finale de cette variable. Toutefois, lorsque vous êtes confronté à une collection, le concept de valeurs initiales et finales n’est pas explicite, et vous ne connaissez pas nécessairement le nombre d’éléments a la collection. Dans ce type de cas, un `For Each`... `Next` boucle est souvent un meilleur choix.  
  
 Dans l’exemple suivant, le `For Each`...`Next` instruction effectue une itération dans tous les éléments d’une collection de listes.  
  
 [!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]  
  
 Pour plus d’exemples, consultez [Collections](../../../standard/collections/index.md) et [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Boucles imbriquées  
 Vous pouvez imbriquer `For Each` boucles en plaçant une boucle à l’intérieur d’une autre.  
  
 L’exemple suivant illustre des structures `For Each`...`Next` structures.  
  
 [!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]  
  
 Lorsque vous imbriquez des boucles, chaque boucle doit posséder une valeur unique `element` variable.  
  
 Vous pouvez également imbriquer des différents types de structures de contrôle dans d’autres. Pour plus d’informations, consultez [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Quitter pour et continuer pour  
 Le [quitter pour](../../../visual-basic/language-reference/statements/exit-statement.md) instruction provoque l’exécution quitter le `For`...`Next` boucle et transfère le contrôle à l’instruction qui suit la `Next` instruction.  
  
 La `Continue For` instruction transfère le contrôle immédiatement à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 L’exemple suivant montre comment utiliser le `Continue For` et `Exit For` instructions.  
  
 [!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]  
  
 Vous pouvez placer un nombre quelconque de `Exit For` instructions dans un `For Each` boucle. Lorsqu’il est utilisé dans imbriqués `For Each` boucles, `Exit For` quitte le contrôle et transfère le plus profond pour le niveau d’imbrication supérieur suivant.  
  
 `Exit For` est souvent utilisé après l’évaluation d’une condition, par exemple, dans un `If`... `Then`... `Else` structure. Vous souhaiterez peut-être utiliser `Exit For` pour les conditions suivantes :  
  
- Pour continuer à effectuer une itération est inutile ou impossible. Cela peut résulter d’une valeur erronée ou une demande d’arrêt.  
  
- Une exception est interceptée dans un `Try`... `Catch`... `Finally`. Vous pouvez utiliser `Exit For` à la fin de la `Finally` bloc.  
  
- Il existe une boucle infinie, ce qui est une boucle qui pourrait s’exécuter de volumineux ou même infini de fois. Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour abandonner la boucle. Pour plus d’informations, consultez [faire... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Iterators  
 Vous utilisez un *itérateur* pour effectuer une itération personnalisée sur une collection. Un itérateur peut être une fonction ou un `Get` accesseur. Il utilise un `Yield` instruction pour retourner chaque élément de la collection un à la fois.  
  
 Vous appelez un itérateur en utilisant un `For Each...Next` instruction. Chaque itération de la boucle `For Each` appelle l’itérateur. Quand un `Yield` instruction est atteinte dans l’itérateur, l’expression dans la `Yield` instruction qui est renvoyé et l’emplacement actuel dans le code est conservé. L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.  
  
 L’exemple suivant utilise une fonction d’itérateur. La fonction d’itérateur a un `Yield` instruction qui se trouve dans un [pour... Suivant](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle. Dans le `ListEvenNumbers` (méthode), chaque itération de la `For Each` corps de l’instruction crée un appel à la fonction d’itérateur, qui passe à la prochaine `Yield` instruction.  
  
 [!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]  
  
 Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md), [instruction Yield](../../../visual-basic/language-reference/statements/yield-statement.md), et [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Quand un `For Each`...`Next` instruction s’exécute, Visual Basic évalue la collection qu’une seule fois, avant le démarrage de la boucle. Si votre bloc d’instructions change `element` ou `group`, ces modifications n’affectent pas l’itération de la boucle.  
  
 Lorsque tous les éléments dans la collection ont été assignés successivement à `element`, le `For Each` boucle s’arrête et le contrôle passe à l’instruction qui suit la `Next` instruction.  
 
Si [Option Infer](option-infer-statement.md) est (défini par défaut), le compilateur Visual Basic peut déduire le type de données `element`. Si elle est désactivée et `element` n’a pas été déclarée en dehors de la boucle, vous devez la déclarer dans le `For Each` instruction. Pour déclarer le type de données `element` explicitement, utilisez un `As` clause. À moins que le type de données de l’élément est défini en dehors du `For Each`... `Next` construction, sa portée est le corps de la boucle. Notez que vous ne pouvez pas déclarer `element` à la fois à l’extérieur et à l’intérieur de la boucle.
  
 Vous pouvez éventuellement spécifier `element` dans le `Next` instruction. Cela améliore la lisibilité de votre programme, en particulier si vous avez imbriqué `For Each` boucles. Vous devez spécifier la variable de même que celui qui s’affiche dans le correspondantes `For Each` instruction.  
  
 Vous souhaiterez peut-être éviter de modifier la valeur de `element` dans une boucle. Cela peut rendre plus difficile à lire et à déboguer votre code. Modification de la valeur de `group` n’affecte pas la collection ou ses éléments qui ont été déterminés lors de la première entrée de la boucle.  
  
 Lorsque vous êtes imbrication de boucles, si un `Next` d’un niveau d’imbrication externe est rencontrée avant le `Next` d’un niveau interne, le compilateur signale une erreur. Toutefois, le compilateur peut détecter cette erreur de chevauchement uniquement si vous spécifiez `element` dans chaque `Next` instruction.  
  
 Si votre code dépend du parcours d’une collection dans un ordre particulier, un `For Each`... `Next` boucle n’est pas le meilleur choix, sauf si vous connaissez les caractéristiques de l’objet énumérateur exposé par la collection. L’ordre de parcours n’est pas déterminé par Visual Basic, mais par le <xref:System.Collections.IEnumerator.MoveNext%2A> méthode de l’objet énumérateur. Par conséquent, vous ne peut-être pas capable de prédire que l’élément de la collection est le premier à être retournées dans `element`, ou qui est la suivante doit être retourné après un élément donné. Vous pouvez obtenir des résultats plus fiables à l’aide d’une structure de boucle différente, comme `For`... `Next` ou `Do`... `Loop`.  
  
Le runtime doit être en mesure de convertir les éléments dans `group` à `element`. Le [`Option Strict`] instruction contrôle si les conversions étendues et restrictives sont autorisées (`Option Strict` est désactivé, sa valeur par défaut), ou si seules les conversions étendues sont autorisées (`Option Strict` se trouve sur). Pour plus d’informations, consultez [les conversions restrictives](#narrowing-conversions).
  
 Le type de données de `group` doit être un type référence qui fait référence à une collection ou un tableau qui est énumérable. Plus souvent, cela signifie que `group` fait référence à un objet qui implémente le <xref:System.Collections.IEnumerable> interface de la `System.Collections` espace de noms ou le <xref:System.Collections.Generic.IEnumerable%601> interface de la `System.Collections.Generic` espace de noms. `System.Collections.IEnumerable` définit le <xref:System.Collections.IEnumerable.GetEnumerator%2A> (méthode), qui retourne un objet énumérateur pour la collection. L’objet énumérateur implémente le `System.Collections.IEnumerator` interface de la `System.Collections` espace de noms et expose le <xref:System.Collections.IEnumerator.Current%2A> propriété et la <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.MoveNext%2A> méthodes. Visual Basic utilise ces pour parcourir la collection.  
  
### <a name="narrowing-conversions"></a>conversions restrictives  
 Lorsque `Option Strict` a la valeur `On`, les conversions restrictives provoquent ordinairement des erreurs du compilateur. Dans un `For Each` instruction, toutefois, les conversions à partir des éléments dans `group` à `element` sont évaluées et exécutées au moment de l’exécution, et les erreurs du compilateur causées par les conversions restrictives sont supprimées.  
  
 Dans l’exemple suivant, l’attribution de `m` comme valeur initiale pour `n` ne se compile pas lorsque `Option Strict` est activé, car la conversion d’un `Long` à un `Integer` est une conversion restrictive. Dans le `For Each` instruction, toutefois, aucune erreur du compilateur n’est signalée, même si l’assignation à `number` nécessite la même conversion de `Long` à `Integer`. Dans le `For Each` instruction qui contient un grand nombre, une erreur d’exécution s’exécute lorsque <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> est appliqué pour le grand nombre.  
  
 [!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]  
  
### <a name="ienumerator-calls"></a>Appels IEnumerator  
 Lors de l’exécution d’un `For Each`... `Next` commence, Visual Basic vérifie que `group` fait référence à un objet de collection valide. Si ce n’est pas le cas, elle lève une exception. Sinon, elle appelle le <xref:System.Collections.IEnumerator.MoveNext%2A> (méthode) et le <xref:System.Collections.IEnumerator.Current%2A> propriété de l’objet énumérateur pour retourner le premier élément. Si `MoveNext` indique qu’il n’existe aucun élément suivant, autrement dit, si la collection est vide, le `For Each` boucle s’arrête et le contrôle passe à l’instruction qui suit la `Next` instruction. Sinon, Visual Basic définit `element` pour le premier élément et exécute le bloc d’instructions.  
  
 Chaque fois que Visual Basic rencontre le `Next` instruction, elle retourne à la `For Each` instruction. Il appelle de nouveau `MoveNext` et `Current` pour retourner l’élément suivant et à nouveau qu’il soit exécute le bloc ou arrête la boucle en fonction du résultat. Ce processus se poursuit jusqu'à ce que `MoveNext` indique qu’il n’existe aucun élément suivant ou un `Exit For` est rencontrée.  
  
 **Modification de la Collection.** L’objet énumérateur retourné par <xref:System.Collections.IEnumerable.GetEnumerator%2A> ne vous permettent de modifier la collection en ajoutant, supprimant, en remplaçant ou réorganisation d’éléments. Si vous modifiez la collection une fois que vous avez lancé un `For Each`... `Next` boucle, l’objet énumérateur devient non valide, et la prochaine tentative d’accès à un élément provoque une <xref:System.InvalidOperationException> exception.  
  
 Toutefois, ce blocage de modification n’est pas déterminé par Visual Basic, mais plutôt par l’implémentation de la <xref:System.Collections.IEnumerable> interface. Il est possible d’implémenter `IEnumerable` d’une façon qui autorise la modification pendant l’itération. Si vous comptez effectuer des modifications dynamiques de ce type, assurez-vous que vous comprenez les caractéristiques de la `IEnumerable` implémentation sur la collection que vous utilisez.  
  
 **Modification des éléments de la Collection.** Le <xref:System.Collections.IEnumerator.Current%2A> propriété de l’objet énumérateur est [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), et il retourne une copie locale de chaque élément de la collection. Cela signifie que vous ne pouvez pas modifier les éléments eux-mêmes dans un `For Each`... `Next` boucle. Toute modification apportée affecte uniquement la copie locale à partir de `Current` et n’est pas répercutée dans la collection sous-jacente. Toutefois, si un élément est un type référence, vous pouvez modifier les membres de l’instance vers laquelle il pointe. L’exemple suivant modifie le `BackColor` membre de chaque `thisControl` élément. Vous ne pouvez pas, toutefois, modifier `thisControl` lui-même.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 L’exemple précédent peut modifier le `BackColor` membre de chaque `thisControl` élément, bien qu’il ne peut pas modifier `thisControl` lui-même.  
  
 **Parcours de tableaux.** Étant donné que le <xref:System.Array> la classe implémente le <xref:System.Collections.IEnumerable> interface, tous les tableaux exposent la <xref:System.Array.GetEnumerator%2A> (méthode). Cela signifie que vous pouvez itérer au sein d’un tableau avec un `For Each`... `Next` boucle. Toutefois, vous pouvez lire uniquement les éléments du tableau. Vous ne pouvez pas les modifier.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant répertorie tous les dossiers dans le répertoire C:\ à l’aide de la <xref:System.IO.DirectoryInfo> classe.  
  
 [!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre une procédure de tri d’une collection. L’exemple trie les instances d’un `Car` classe qui sont stockés dans un <xref:System.Collections.Generic.List%601>. La classe `Car` implémente l’interface <xref:System.IComparable%601>, ce qui implique l’implémentation de la méthode <xref:System.IComparable%601.CompareTo%2A>.  
  
 Chaque appel à la <xref:System.IComparable%601.CompareTo%2A> méthode effectue une comparaison unique qui est utilisée pour le tri. Le code écrit par l’utilisateur dans la méthode `CompareTo` retourne une valeur pour chaque comparaison de l’objet actuel avec un autre objet. La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux. Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».  
  
 Dans la méthode `ListCars`, l’instruction `cars.Sort()` trie la liste. Cet appel à la méthode <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> entraîne l’appel automatique de la méthode `CompareTo` pour les objets `Car` dans `List`.  
  
 [!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]  
  
## <a name="see-also"></a>Voir aussi

- [Collections](../../../standard/collections/index.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Initialiseurs d’objets : Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md)
