---
title: "'For Each' pour le type '<typename>' est ambigu, car le type implémente plusieurs instanciations de 'System.Collections.Generic.IEnumerable(Of T)'"
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 0f19836efeabcf1d9e5097667c719c1f7d99cbbb
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163465"
---
# <a name="bc32096-for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>BC32096 : 'for each’sur le type' \<typename> 'est ambigu, car le type implémente plusieurs instanciations de’System. Collections. Generic. IEnumerable (Of T) '

Une `For Each` instruction spécifie une variable d’itérateur qui a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthodes.

 La variable d’itérateur doit être d’un type qui implémente <xref:System.Collections.IEnumerable?displayProperty=nameWithType> l' <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface ou dans l’un des `Collections` espaces de noms de l' .NET Framework. Une classe peut implémenter plusieurs interfaces génériques construites, à l’aide d’un argument de type différent pour chaque construction. Si une classe qui procède de cette façon est utilisée pour la variable d’itérateur, cette variable a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthodes. Dans ce cas, Visual Basic ne peut pas choisir la méthode à appeler.

 **ID d’erreur :** BC32096

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Utilisez un opérateur [DirectCast](../operators/directcast-operator.md) ou un [opérateur TryCast](../operators/trycast-operator.md) pour effectuer un cast du type de variable d’itérateur vers l’interface définissant la <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthode que vous souhaitez utiliser.

## <a name="see-also"></a>Voir aussi

- [For Each...Next (instruction)](../statements/for-each-next-statement.md)
- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
