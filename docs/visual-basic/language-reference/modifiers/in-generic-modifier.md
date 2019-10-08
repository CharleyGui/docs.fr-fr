---
title: In (modificateur générique)-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004871"
---
# <a name="in-generic-modifier-visual-basic"></a>In (modificateur générique) (Visual Basic)

Pour les paramètres de type générique, le mot clé `In` spécifie que le paramètre de type est contravariant.

## <a name="remarks"></a>Notes

La contravariance permet d’utiliser un type moins dérivé que celui spécifié par le paramètre générique. Cela permet la conversion implicite des classes qui implémentent des interfaces variantes, ainsi que la conversion implicite des types délégués.

Pour plus d’informations, consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Règles

Vous pouvez utiliser le mot clé `In` dans les interfaces et délégués génériques.
  
Un paramètre de type peut être déclaré contravariant dans une interface ou un délégué générique s’il est utilisé uniquement comme type d’arguments de méthode et qu’il n’est pas utilisé comme type de retour de méthode. les paramètres `ByRef` ne peuvent pas être covariants ou contravariants.

La covariance et la contravariance sont prises en charge pour les types référence et ne sont pas prises en charge pour les types valeur.

Dans Visual Basic, vous ne pouvez pas déclarer d’événements dans les interfaces contravariant sans spécifier le type délégué. En outre, les interfaces contravariant ne peuvent pas avoir de classes imbriquées, d’énumérations ou de structures, mais elles peuvent avoir des interfaces imbriquées.

## <a name="behavior"></a>Comportement

Une interface qui possède un paramètre de type contravariant permet à ses méthodes d’accepter des arguments de types moins dérivés que ceux spécifiés par le paramètre de type d’interface. Par exemple, étant donné que dans .NET Framework 4, dans l’interface <xref:System.Collections.Generic.IComparer%601>, le type T est contravariant, vous pouvez assigner un objet du type `IComparer(Of Person)` à un objet du type `IComparer(Of Employee)` sans utiliser de méthode de conversion spéciale si `Employee` hérite de `Person`.

Un délégué contravariant peut être assigné à un autre délégué du même type, mais avec un paramètre de type générique moins dérivé.

## <a name="example---contravariant-generic-interface"></a>Exemple : interface générique contravariant

L’exemple suivant montre comment déclarer, étendre et implémenter une interface générique contravariante. Il montre également comment utiliser la conversion implicite pour les classes qui implémentent cette interface.

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a>Exemple : délégué générique contravariant

L’exemple de code suivant montre comment déclarer, instancier et invoquer un délégué générique contravariant. Il montre également comment convertir implicitement un type délégué.

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Variance dans les interfaces génériques](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Out](out-generic-modifier.md)
