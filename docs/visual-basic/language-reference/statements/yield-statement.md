---
title: yield, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352726"
---
# <a name="yield-statement-visual-basic"></a>yield, instruction (Visual Basic)
Envoie l’élément suivant d’une collection à une instruction `For Each...Next`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Terme|Définition|  
|---|---|  
|`expression`|Requis. Expression implicitement convertible en type de la fonction d’itérateur ou de `Get` accesseur qui contient l’instruction `Yield`.|  
  
## <a name="remarks"></a>Notes  
 L’instruction `Yield` retourne un élément d’une collection à la fois. L’instruction `Yield` est incluse dans une fonction d’itérateur ou un accesseur `Get` qui effectue des itérations personnalisées sur une collection.  
  
 Vous consommez une fonction d’itérateur à l’aide [d’une... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ou requête LINQ. Chaque itération de la boucle `For Each` appelle la fonction d’itérateur. Quand une instruction `Yield` est atteinte dans la fonction Iterator, `expression` est retourné et l’emplacement actuel dans le code est conservé. L'exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d'itérateur sera appelée.  
  
 Une conversion implicite doit exister du type de `expression` dans l’instruction `Yield` au type de retour de l’itérateur.  
  
 Vous pouvez utiliser une instruction `Exit Function` ou `Return` pour terminer l’itération.  
  
 « Yield » n’est pas un mot réservé et a une signification spéciale uniquement lorsqu’il est utilisé dans une fonction de `Iterator` ou un accesseur `Get`.  
  
 Pour plus d’informations sur les fonctions d’itérateur et les accesseurs `Get`, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="iterator-functions-and-get-accessors"></a>Fonctions d’itérateur et accesseurs d’extraction  
 La déclaration d’une fonction d’itérateur ou d’un accesseur `Get` doit remplir les conditions suivantes :  
  
- Il doit inclure un modificateur [iterator](../../../visual-basic/language-reference/modifiers/iterator.md) .  
  
- Le type de retour doit être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
- Il ne peut pas avoir de paramètres de `ByRef`.  
  
 Une fonction d’itérateur ne peut pas se produire dans un événement, un constructeur d’instance, un constructeur statique ou un destructeur statique.  
  
 Une fonction d’itérateur peut être une fonction anonyme. Pour plus d’informations, consultez [Itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 Une instruction `Yield` peut se trouver à l’intérieur d’un bloc `Try` d’une instruction [try... Catch... Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Un bloc `Try` qui a une instruction `Yield` peut avoir des blocs `Catch` et peut avoir un bloc `Finally`.  
  
 Une instruction `Yield` ne peut pas se trouver à l’intérieur d’un bloc `Catch` ou d’un bloc `Finally`.  
  
 Si le corps de `For Each` (en dehors de la fonction d’itérateur) lève une exception, un bloc `Catch` dans la fonction d’itérateur n’est pas exécuté, mais un bloc `Finally` dans la fonction d’itérateur est exécuté. Un bloc de `Catch` à l’intérieur d’une fonction d’itérateur intercepte uniquement les exceptions qui se produisent à l’intérieur de la fonction d’itérateur.  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Le code suivant retourne un `IEnumerable (Of String)` à partir d’une fonction d’itérateur, puis itère au sein des éléments du `IEnumerable (Of String)`.  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 L’appel à `MyIteratorFunction` n’exécute pas le corps de la fonction. À la place, l'appel retourne `IEnumerable(Of String)` dans la variable `elements`.  
  
 Dans une itération de la boucle `For Each`, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> est appelée pour `elements`. Cet appel exécute le corps de `MyIteratorFunction` jusqu'à ce que l'instruction `Yield` suivante soit atteinte. L’instruction `Yield` retourne une expression qui détermine non seulement la valeur de la variable `element` pour la consommation par le corps de la boucle, mais également la propriété <xref:System.Collections.Generic.IEnumerator%601.Current%2A> des éléments, qui est un `IEnumerable (Of String)`.  
  
 À chaque itération suivante de la boucle `For Each`, l'exécution du corps de l'itérateur reprend à partir de l'emplacement où elle s'est interrompue, et s'arrête encore lorsqu'elle atteint une instruction `Yield`. La boucle `For Each` se termine lorsque la fin de la fonction d’itérateur ou d’une instruction `Return` ou `Exit Function` est atteinte.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient une instruction `Yield` qui se trouve à l’intérieur d’une instruction [for... Next](../../../visual-basic/language-reference/statements/for-next-statement.md) . Chaque itération de [pour chaque](../../../visual-basic/language-reference/statements/for-each-next-statement.md) corps d’instruction dans `Main` crée un appel à la fonction d’itérateur `Power`. Chaque appel à la fonction d'itérateur continue vers l'exécution suivante de l'instruction `Yield`, qui se produit pendant l'itération suivante de la boucle `For…Next`.  
  
 Le type de retour de la méthode Iterator est <xref:System.Collections.Generic.IEnumerable%601>, un type interface itérateur. Lorsque la méthode Iterator est appelée, elle retourne un objet énumérable contenant les puissances d'un nombre.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre un accesseur `Get` qui est un itérateur. La déclaration de propriété comprend un modificateur de `Iterator`.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Pour obtenir des exemples supplémentaires, consultez [itérateurs](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Voir aussi

- [Instructions](../../../visual-basic/language-reference/statements/index.md)
