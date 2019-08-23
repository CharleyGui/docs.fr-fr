---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 12c88db49dc7723fc269195e7d174bfa822c64d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963758"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Représente la valeur par défaut de n’importe quel type de données. Pour les types de référence, la valeur par `null` défaut est la référence. Pour les types valeur, la valeur par défaut varie selon que le type valeur est Nullable ou non.  
  
> [!NOTE]
> Pour les types valeur n’acceptant `Nothing` pas les valeurs null `null` , C#dans Visual Basic diffère de dans. Dans Visual Basic, si vous définissez une variable d’un type valeur qui n’autorise pas `Nothing`les valeurs NULL sur, la variable est définie sur la valeur par défaut pour son type déclaré. Dans C#, si vous assignez une variable d’un type valeur n’acceptant pas les valeurs NULL à `null`, une erreur de compilation se produit.  
  
## <a name="remarks"></a>Notes  
 `Nothing`représente la valeur par défaut d’un type de données. La valeur par défaut varie selon que la variable est d’un type valeur ou d’un type référence.  
  
 Une variable d’un *type valeur* contient directement sa valeur. Les types valeur incluent tous les types de `Boolean`données `Char`numériques `Date`,,,, toutes les structures et toutes les énumérations. Une variable d’un *type référence* stocke une référence à une instance de l’objet en mémoire. Les types référence incluent des classes, des tableaux, des délégués et des chaînes. Pour plus d'informations, consultez [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Si une variable est d’un type valeur, le comportement de `Nothing` varie selon que la variable est d’un type de données Nullable ou non. Pour représenter un type valeur Nullable, ajoutez un `?` modificateur au nom de type. L’assignation `null`à une variable Nullable affecte la valeur à. `Nothing` Pour plus d’informations et d’exemples, consultez [types valeur Nullable](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Si une variable est d’un type valeur qui n’accepte pas la valeur null `Nothing` , son assignation lui affecte la valeur par défaut pour son type déclaré. Si ce type contient des membres de variables, ils sont tous définis sur leurs valeurs par défaut. L’exemple suivant illustre cela pour les types scalaires.  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 Si une variable est d’un type référence, l’assignation `Nothing` à la variable la définit sur une `null` référence du type de la variable. Une variable qui est définie sur une `null` référence n’est pas associée à un objet. Cela est illustré par l'exemple suivant.  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 Lorsque vous vérifiez si une variable de référence (ou de type de `null`valeur Nullable) est `= Nothing` , `<> Nothing`n’utilisez pas ou. Utilisez `Is Nothing` toujours ou `IsNot Nothing`.  
  
 Pour les chaînes dans Visual Basic, la chaîne vide est `Nothing`égale à. Par conséquent `"" = Nothing` , a la valeur true.  
  
 L’exemple suivant illustre des comparaisons qui utilisent `Is` les `IsNot` opérateurs et.  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 Si vous déclarez une variable sans utiliser `As` de clause et que vous `Nothing`lui affectez la valeur, la `Object`variable a un type de. Un exemple est `Dim something = Nothing`. Une erreur de compilation se produit dans ce cas lorsque `Option Strict` est activé et `Option Infer` est désactivé.  
  
 Quand vous attribuez `Nothing` à une variable objet, elle ne fait plus référence à une instance d’objet. Si la variable avait précédemment fait l’appel d’une instance, sa `Nothing` définition sur ne met pas fin à l’instance elle-même. L’instance est arrêtée, et la mémoire et les ressources système qui lui sont associées sont libérées, uniquement après que le garbage collector (GC) a détecté qu’il n’y a aucune référence active restante.  
  
 `Nothing`diffère de l' <xref:System.DBNull> objet, qui représente une variante non initialisée ou une colonne de base de données inexistante.  
  
## <a name="see-also"></a>Voir aussi

- [Dim (instruction)](../../visual-basic/language-reference/statements/dim-statement.md)
- [Durée de vie d’un objet: Comment les objets sont créés et détruits](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Durée de vie dans Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is (opérateur)](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot (opérateur)](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Types valeur Nullable](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
