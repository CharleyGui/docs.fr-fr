---
title: TryCast, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 8f0d4f612cd5a96e0b0ab7305c41e00790613cc8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406375"
---
# <a name="trycast-operator-visual-basic"></a>Opérateur TryCast (Visual Basic)
Introduit une opération de conversion de type qui ne lève pas d’exception.  
  
## <a name="remarks"></a>Notes  
 Si une tentative de conversion échoue, `CType` et `DirectCast` les deux génèrent une <xref:System.InvalidCastException> erreur. Cela peut nuire aux performances de votre application. `TryCast`retourne [Nothing](../nothing.md), de sorte qu’au lieu de devoir gérer une exception possible, vous devez uniquement tester le résultat retourné par rapport à `Nothing` .  
  
 Vous utilisez le `TryCast` mot clé de la même façon que vous utilisez la [fonction CType](../functions/ctype-function.md) et le mot clé d' [opérateur DirectCast](directcast-operator.md) . Vous fournissez une expression comme premier argument et un type à convertir en tant que deuxième argument. `TryCast`fonctionne uniquement sur les types référence, tels que les classes et les interfaces. Elle nécessite une relation d’héritage ou d’implémentation entre les deux types. Cela signifie qu’un type doit hériter de ou implémenter l’autre.  
  
## <a name="errors-and-failures"></a>Erreurs et échecs  
 `TryCast`génère une erreur du compilateur s’il détecte qu’il n’existe aucune relation d’héritage ou d’implémentation. Toutefois, l’absence d’erreur du compilateur ne garantit pas une conversion réussie. Si la conversion souhaitée est restrictive, elle peut échouer au moment de l’exécution. Dans ce cas, `TryCast` [ne retourne rien](../nothing.md).  
  
## <a name="conversion-keywords"></a>Mots clés de conversion  
 Une comparaison des mots clés de conversion de type est la suivante.  
  
|Mot clé|Types de données|Relation d’argument|Échec au moment de l’exécution|  
|---|---|---|---|  
|[CType Function](../functions/ctype-function.md)|Tous les types de données|La conversion étendue ou restrictive doit être définie entre les deux types de données|Lève<xref:System.InvalidCastException>|  
|[DirectCast, opérateur](directcast-operator.md)|Tous les types de données|Un type doit hériter de ou implémenter l’autre type|Lève<xref:System.InvalidCastException>|  
|`TryCast`|Types référence uniquement|Un type doit hériter de ou implémenter l’autre type|Retourne [Nothing](../nothing.md)|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
