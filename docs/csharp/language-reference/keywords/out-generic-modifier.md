---
title: out, mot clé (modificateur générique) - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 97ddae2efe55be89840f7a483c18d61259020283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713284"
---
# <a name="out-generic-modifier-c-reference"></a>out (modificateur générique) (référence C#)

Pour les paramètres de type générique, le mot clé `out` spécifie que le paramètre de type est covariant. Vous pouvez utiliser le mot clé `out` dans les interfaces et délégués génériques.

La covariance permet d’utiliser un type plus dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces covariantes, ainsi que la conversion implicite des types délégués. La covariance et la contravariance sont prises en charge pour les types référence, mais pas pour les types valeur.

Une interface qui possède un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type. Par exemple, comme dans le .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet du type `IEnumerable(Of String)` à un objet du type `IEnumerable(Of Object)` sans utiliser de méthode de conversion spéciale.

Un délégué covariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique plus dérivé.

Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="example---covariant-generic-interface"></a>Exemple - interface générique covariante

L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique covariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

Dans une interface générique, un paramètre de type peut être déclaré covariant s’il satisfait aux conditions suivantes :

- Le paramètre de type est utilisé uniquement comme type de retour des méthodes d’interface, mais pas comme type des arguments de méthode.

    > [!NOTE]
    > Il existe une exception à cette règle. Si une interface covariante a un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué. Pour plus d’informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Le paramètre de type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.

## <a name="example---covariant-generic-delegate"></a>Exemple - délégué générique covariant

L’exemple de code suivant montre comment déclarer, instancier et appeler un délégué générique covariant. Il montre également comment convertir implicitement des types délégués.

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

Dans un délégué générique, un type peut être déclaré comme étant covariant s’il est utilisé uniquement comme type de retour des méthodes, mais pas pour des arguments de méthode.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Dans](in-generic-modifier.md)
- [Modificateurs](index.md)
