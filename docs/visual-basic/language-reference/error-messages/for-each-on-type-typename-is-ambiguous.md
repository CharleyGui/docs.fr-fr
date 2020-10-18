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
# <a name="bc32096-for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="95daa-102">BC32096 : 'for each’sur le type' \<typename> 'est ambigu, car le type implémente plusieurs instanciations de’System. Collections. Generic. IEnumerable (Of T) '</span><span class="sxs-lookup"><span data-stu-id="95daa-102">BC32096: 'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>

<span data-ttu-id="95daa-103">Une `For Each` instruction spécifie une variable d’itérateur qui a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="95daa-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>

 <span data-ttu-id="95daa-104">La variable d’itérateur doit être d’un type qui implémente <xref:System.Collections.IEnumerable?displayProperty=nameWithType> l' <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface ou dans l’un des `Collections` espaces de noms de l' .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95daa-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="95daa-105">Une classe peut implémenter plusieurs interfaces génériques construites, à l’aide d’un argument de type différent pour chaque construction.</span><span class="sxs-lookup"><span data-stu-id="95daa-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="95daa-106">Si une classe qui procède de cette façon est utilisée pour la variable d’itérateur, cette variable a plusieurs <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="95daa-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="95daa-107">Dans ce cas, Visual Basic ne peut pas choisir la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="95daa-107">In such a case, Visual Basic cannot choose which method to call.</span></span>

 <span data-ttu-id="95daa-108">**ID d’erreur :** BC32096</span><span class="sxs-lookup"><span data-stu-id="95daa-108">**Error ID:** BC32096</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="95daa-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="95daa-109">To correct this error</span></span>

- <span data-ttu-id="95daa-110">Utilisez un opérateur [DirectCast](../operators/directcast-operator.md) ou un [opérateur TryCast](../operators/trycast-operator.md) pour effectuer un cast du type de variable d’itérateur vers l’interface définissant la <xref:System.Collections.IEnumerable.GetEnumerator%2A> méthode que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="95daa-110">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>

## <a name="see-also"></a><span data-ttu-id="95daa-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95daa-111">See also</span></span>

- [<span data-ttu-id="95daa-112">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="95daa-112">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="95daa-113">Interfaces</span><span class="sxs-lookup"><span data-stu-id="95daa-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
