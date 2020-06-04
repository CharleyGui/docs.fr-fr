---
title: Out (modificateur générique)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 28ae7d6fd51170aa822072fc2f5357443f51a353
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392091"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (modificateur générique) (Visual Basic)

Pour les paramètres de type générique, le `Out` mot clé spécifie que le type est covariant.

## <a name="remarks"></a>Notes

La covariance permet d’utiliser un type plus dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.

Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Règles

Vous pouvez utiliser le mot clé `Out` dans les interfaces et délégués génériques.

Dans une interface générique, un paramètre de type peut être déclaré covariant s’il satisfait aux conditions suivantes :

- Le paramètre de type est utilisé uniquement comme type de retour des méthodes d’interface, mais pas comme type des arguments de méthode.

    > [!NOTE]
    > Il existe une exception à cette règle. Si une interface covariante a un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type covariant comme paramètre de type générique pour ce délégué. Pour plus d’informations sur les délégués génériques covariants et contravariants, consultez [Variance dans les délégués](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Le paramètre de type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.

Dans un délégué générique, un paramètre de type peut être déclaré covariant s’il est utilisé uniquement comme type de retour de méthode et n’est pas utilisé pour les arguments de méthode.

La covariance et la contravariance sont prises en charge pour les types référence, mais pas pour les types valeur.

Dans Visual Basic, vous ne pouvez pas déclarer d’événements dans des interfaces covariants sans spécifier le type délégué. En outre, les interfaces covariantes ne peuvent pas avoir de classes imbriquées, d’énumérations ou de structures, mais elles peuvent avoir des interfaces imbriquées.

## <a name="behavior"></a>Comportement

Une interface qui possède un paramètre de type covariant permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés par le paramètre de type. Par exemple, comme dans le .NET Framework 4, dans <xref:System.Collections.Generic.IEnumerable%601>, le type T est covariant, vous pouvez assigner un objet du type `IEnumerable(Of String)` à un objet du type `IEnumerable(Of Object)` sans utiliser de méthode de conversion spéciale.

Un délégué covariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique plus dérivé.

## <a name="example"></a>Exemple

L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique covariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent une interface covariante.

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>Exemple

L’exemple de code suivant montre comment déclarer, instancier et appeler un délégué générique covariant. Il montre également comment vous pouvez utiliser la conversion implicite pour les types délégués.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>Voir aussi

- [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Dans](in-generic-modifier.md)
