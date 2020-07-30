---
title: Comment définir l’égalité des valeurs pour un type-guide de programmation C#
description: Découvrez comment définir l’égalité des valeurs pour un type. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: cf4449618c2b57f21855354f2250d41a403b4d57
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381643"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Comment définir l’égalité des valeurs pour un type (Guide de programmation C#)

Quand vous définissez une classe ou un struct, vous décidez s’il est judicieux de créer une définition personnalisée de l’égalité des valeurs (ou équivalence) pour le type. En général, vous implémentez l’égalité des valeurs quand des objets du type sont supposés être ajoutés à une collection quelconque, ou quand leur objectif principal est de stocker un ensemble de champs ou propriétés. Vous pouvez baser votre définition de l’égalité des valeurs sur une comparaison de tous les champs et propriétés du type, ou vous pouvez la baser sur un sous-ensemble.

Dans les deux cas, et dans les classes et les structs, votre implémentation doit suivre les cinq garanties d’équivalence (pour les règles suivantes, supposez que `x` , `y` et ne `z` sont pas null) :  
  
1. `x.Equals(x)` retourne `true`. Il s’agit de la propriété réflexive.  
  
2. `x.Equals(y)` retourne la même valeur que `y.Equals(x)`. Il s’agit de la propriété symétrique.  
  
3. si `(x.Equals(y) && y.Equals(z))` retourne `true`, `x.Equals(z)` retourne `true`. Il s’agit de la propriété transitive.  
  
4. Les appels successifs de `x.Equals(y)` retournent la même valeur tant que les objets référencés par x et y ne sont pas modifiés.  
  
5. Toute valeur non NULL n’est pas égale à null. Toutefois, le CLR vérifie la valeur NULL sur tous les appels de méthode et lève une `NullReferenceException` si la `this` référence aurait la valeur null. Par conséquent, `x.Equals(y)` lève une exception lorsque `x` a la valeur null. Cela arrête les règles 1 ou 2, en fonction de l’argument de `Equals` .

 Tout struct que vous définissez a déjà une implémentation par défaut de l’égalité des valeurs dont il hérite de la substitution <xref:System.ValueType?displayProperty=nameWithType> de la méthode <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. Cette implémentation utilise la réflexion pour examiner tous les champs et propriétés du type. Bien que cette implémentation produise des résultats corrects, elle est relativement lente par rapport à une implémentation personnalisée que vous écrivez spécifiquement pour le type.  
  
 Les détails d’implémentation pour l’égalité des valeurs sont différents pour les classes et les structs. Toutefois, les classes et les structs nécessitent tous deux les mêmes étapes de base pour l’implémentation de l’égalité :  
  
1. Substituez la méthode [virtual](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. Dans la plupart des cas, votre implémentation de `bool Equals( object obj )` doit simplement appeler la méthode `Equals` propre au type qui est l’implémentation de l’interface <xref:System.IEquatable%601?displayProperty=nameWithType>. (Voir l’étape 2.)  
  
2. Implémentez l’interface <xref:System.IEquatable%601?displayProperty=nameWithType> en fournissant une méthode `Equals` propre au type. C’est ici qu’est effectuée la comparaison d’équivalence. Par exemple, vous pouvez décider de définir l’égalité en comparant seulement un ou deux champs de votre type. Ne levez pas d'exceptions à partir de la méthode `Equals`. Pour les classes uniquement : cette méthode doit examiner uniquement les champs qui sont déclarés dans la classe. Elle doit appeler `base.Equals` pour examiner les champs qui sont dans la classe de base. (Ne faites pas cela si le type hérite directement d’<xref:System.Object>, car l’implémentation <xref:System.Object> de <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> effectue une vérification de l’égalité de référence.)  
  
3. Facultatif mais recommandé : Surchargez les [==](../../language-reference/operators/equality-operators.md#equality-operator-) opérateurs et [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) .  
  
4. Substituez <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> pour que deux objets ayant une égalité des valeurs produisent le même code de hachage.  
  
5. Facultatif : pour prendre en charge les définitions pour « supérieur à » ou « inférieur à », implémentez l' <xref:System.IComparable%601> interface pour votre type, et surchargez également les [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) opérateurs et.  
  
 Le premier exemple qui suit illustre une implémentation de classe. Le deuxième exemple illustre une implémentation de struct.  

## <a name="example"></a>Exemple

 L’exemple suivant montre comment implémenter l’égalité des valeurs dans une classe (type référence).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 Sur les classes (types référence), l’implémentation par défaut des deux méthodes <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> effectue une comparaison d’égalité de référence, et non une vérification de l’égalité des valeurs. Quand un implémenteur substitue la méthode virtuelle, l’objectif est de lui donner une sémantique d’égalité des valeurs.  
  
 Les opérateurs `==` et `!=` peuvent être utilisés avec des classes, même si la classe ne les surcharge pas. Toutefois, le comportement par défaut consiste à effectuer une vérification de l’égalité de référence. Dans une classe, si vous surchargez la méthode `Equals`, vous devez surcharger les opérateurs `==` et `!=`, mais cela n’est pas obligatoire.  

## <a name="example"></a>Exemple

 L’exemple suivant montre comment implémenter l’égalité des valeurs dans un struct (type valeur) :  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Pour les structs, l’implémentation par défaut de <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (qui est la version substituée dans <xref:System.ValueType?displayProperty=nameWithType>) effectue une vérification de l’égalité des valeurs à l’aide de la réflexion pour comparer les valeurs de chaque champ dans le type. Quand un implémenteur substitue la méthode `Equals` virtuelle dans un struct, l’objectif est de fournir un moyen plus efficace d’effectuer la vérification de l’égalité des valeurs, et éventuellement de baser la comparaison sur un sous-ensemble des propriétés ou du champ du struct.  
  
 Les [==](../../language-reference/operators/equality-operators.md#equality-operator-) opérateurs et [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) ne peuvent pas fonctionner sur un struct, sauf si le struct les surcharge explicitement.  
  
## <a name="see-also"></a>Voir aussi

- [Comparaisons d’égalité](equality-comparisons.md)
- [Guide de programmation C#](../index.md)
