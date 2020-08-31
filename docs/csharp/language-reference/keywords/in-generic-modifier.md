---
description: in (modificateur générique) - Référence C#
title: in (modificateur générique) - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: feae17be7bdf29f6bc90e8c85b3878d4714699f4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118453"
---
# <a name="in-generic-modifier-c-reference"></a>in (modificateur générique) (Référence C#)

Pour les paramètres de type générique, le mot clé `in` spécifie que le paramètre de type est contravariant. Vous pouvez utiliser le mot clé `in` dans les interfaces et délégués génériques.

La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces contravariantes, ainsi que la conversion implicite des types délégués. La covariance et la contravariance des paramètres de type générique sont prises en charge pour les types référence, mais pas pour les types valeur.

Un type peut être déclaré comme étant contravariant dans une interface ou un délégué générique uniquement s’il définit le type des paramètres d’une méthode et non le type de retour d’une méthode. Les paramètres `In`, `ref` et `out` doivent être invariants, ce qui signifie qu’ils sont ni covariants ni contravariants.

Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface. Par exemple, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez attribuer un objet du type `IComparer<Person>` à un objet du type `IComparer<Employee>` sans utiliser de méthode de conversion spéciale si `Employee` hérite `Person`.

Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.

Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Interface générique contravariante

L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Délégué générique contravariant

L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant. Il montre également comment convertir implicitement un type délégué.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [à](out-generic-modifier.md)
- [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modificateurs](index.md)
