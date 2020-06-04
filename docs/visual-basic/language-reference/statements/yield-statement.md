---
title: Yield (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: cc89e6f9bc2ccb4fff9a9fe12cd190a6b2d212dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401366"
---
# <a name="yield-statement-visual-basic"></a>yield, instruction (Visual Basic)
Envoie l’élément suivant d’une collection à une `For Each...Next` instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Terme|Définition|  
|---|---|  
|`expression`|Obligatoire. Expression implicitement convertible en type de la fonction d’itérateur ou de l' `Get` accesseur qui contient l' `Yield` instruction.|  
  
## <a name="remarks"></a>Notes  
 L' `Yield` instruction retourne un élément d’une collection à la fois. L' `Yield` instruction est incluse dans une fonction ou un `Get` accesseur d’itérateur, qui effectue des itérations personnalisées sur une collection.  
  
 Vous consommez une fonction d’itérateur à l’aide [d’une... Instruction suivante](for-each-next-statement.md) ou requête LINQ. Chaque itération de la `For Each` boucle appelle la fonction d’itérateur. Quand une `Yield` instruction est atteinte dans la fonction Iterator, `expression` est retourné, et l’emplacement actuel dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.  
  
 Une conversion implicite doit exister du type de `expression` dans l' `Yield` instruction vers le type de retour de l’itérateur.  
  
 Vous pouvez utiliser une `Exit Function` `Return` instruction ou pour terminer l’itération.  
  
 « Yield » n’est pas un mot réservé et a une signification spéciale uniquement lorsqu’il est utilisé dans une `Iterator` fonction ou un `Get` accesseur.  
  
 Pour plus d’informations sur les fonctions et accesseurs d’itérateurs `Get` , consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Fonctions d’itérateur et accesseurs d’extraction  
 La déclaration d’une fonction ou d’un `Get` accesseur d’itérateur doit remplir les conditions suivantes :  
  
- Il doit inclure un modificateur [iterator](../modifiers/iterator.md) .  
  
- Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
- Il ne peut pas avoir de `ByRef` paramètres.  
  
 Une fonction d’itérateur ne peut pas se produire dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.  
  
 Une fonction d’itérateur peut être une fonction anonyme. Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 Une `Yield` instruction peut se trouver à l’intérieur `Try` d’un bloc d’une instruction [try... Catch... Finally, instruction](try-catch-finally-statement.md). Un `Try` bloc qui a une `Yield` instruction peut avoir des `Catch` blocs et peut avoir un `Finally` bloc.  
  
 Une `Yield` instruction ne peut pas être à l’intérieur d’un `Catch` bloc ou d’un `Finally` bloc.  
  
 Si le `For Each` corps (en dehors de la fonction d’itérateur) lève une exception, un `Catch` bloc de la fonction d’itérateur n’est pas exécuté, mais un `Finally` bloc dans la fonction d’itérateur est exécuté. Un `Catch` bloc à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction Iterator.  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Le code suivant retourne un `IEnumerable (Of String)` à partir d’une fonction d’itérateur, puis itère au sein des éléments de `IEnumerable (Of String)` .  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 L’appel à `MyIteratorFunction` n’exécute pas le corps de la fonction. À la place, l'appel retourne `IEnumerable(Of String)` dans la variable `elements`.  
  
 Dans une itération de la boucle `For Each`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`. Cet appel exécute le corps de `MyIteratorFunction` jusqu'à ce que l'instruction `Yield` suivante soit atteinte. L' `Yield` instruction retourne une expression qui détermine non seulement la valeur de la `element` variable pour la consommation par le corps de la boucle, mais également la <xref:System.Collections.Generic.IEnumerator%601.Current%2A> propriété des éléments, qui est un `IEnumerable (Of String)` .  
  
 À chaque itération suivante de la boucle `For Each`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `Yield`. La `For Each` boucle se termine lorsque la fin de la fonction d’itérateur ou d’une `Return` `Exit Function` instruction ou est atteinte.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient une `Yield` instruction qui se trouve à l’intérieur d’une instruction [for... Next](for-next-statement.md) . Chaque itération de [pour chaque](for-each-next-statement.md) corps d’instruction dans `Main` crée un appel à la `Power` fonction d’itérateur. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.  
  
 Le type de retour de la méthode Iterator est <xref:System.Collections.Generic.IEnumerable%601> , un type interface itérateur. Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre un accesseur `Get` qui est un itérateur. La déclaration de propriété comprend un `Iterator` modificateur.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Pour obtenir des exemples supplémentaires, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Voir aussi

- [Instructions](index.md)
