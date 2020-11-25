---
title: 'Modification avec rupture : CreateCounterSetInstance lève InvalidOperationException si l’instance existe déjà'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où CounterSet. CreateCounterSetInstance lève une exception différente si le compteur existe déjà.
ms.date: 11/01/2020
ms.openlocfilehash: 28042690b71f9b86e4e54748ec75467bbe232684
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761075"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="a953b-103">CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà</span><span class="sxs-lookup"><span data-stu-id="a953b-103">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="a953b-104">À compter de .NET 5,0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> lève une exception <xref:System.InvalidOperationException> au lieu d’un <xref:System.ArgumentException> si l’ensemble de compteurs existe déjà.</span><span class="sxs-lookup"><span data-stu-id="a953b-104">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

## <a name="change-description"></a><span data-ttu-id="a953b-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="a953b-105">Change description</span></span>

<span data-ttu-id="a953b-106">Dans .NET Framework et .NET Core 1,0 à 3,1, vous pouvez créer une instance de l’ensemble de compteurs en appelant <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> .</span><span class="sxs-lookup"><span data-stu-id="a953b-106">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="a953b-107">Toutefois, si l’ensemble de compteurs existe déjà, la méthode lève une <xref:System.ArgumentException> exception.</span><span class="sxs-lookup"><span data-stu-id="a953b-107">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="a953b-108">Dans .NET 5,0 et versions ultérieures, lorsque vous appelez <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> et que l’ensemble de compteurs existe, une <xref:System.InvalidOperationException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="a953b-108">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a953b-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a953b-109">Version introduced</span></span>

<span data-ttu-id="a953b-110">5.0</span><span class="sxs-lookup"><span data-stu-id="a953b-110">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a953b-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a953b-111">Recommended action</span></span>

<span data-ttu-id="a953b-112">Si vous interceptez des <xref:System.ArgumentException> exceptions dans votre application lors de l’appel de <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> , envisagez également d’intercepter les <xref:System.InvalidOperationException> exceptions.</span><span class="sxs-lookup"><span data-stu-id="a953b-112">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="a953b-113">L’interception des <xref:System.ArgumentException> exceptions n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="a953b-113">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a953b-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="a953b-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
