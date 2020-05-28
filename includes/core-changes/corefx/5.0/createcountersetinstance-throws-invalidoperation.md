---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144477"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="ae120-101">CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà</span><span class="sxs-lookup"><span data-stu-id="ae120-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="ae120-102">À compter de .NET 5,0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> lève une exception <xref:System.InvalidOperationException> au lieu d’un <xref:System.ArgumentException> si l’ensemble de compteurs existe déjà.</span><span class="sxs-lookup"><span data-stu-id="ae120-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ae120-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ae120-103">Change description</span></span>

<span data-ttu-id="ae120-104">Dans .NET Framework et .NET Core 1,0 à 3,1, vous pouvez créer une instance de l’ensemble de compteurs en appelant <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae120-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="ae120-105">Toutefois, si l’ensemble de compteurs existe déjà, la méthode lève une <xref:System.ArgumentException> exception.</span><span class="sxs-lookup"><span data-stu-id="ae120-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="ae120-106">Dans .NET 5,0 et versions ultérieures, lorsque vous appelez <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> et que l’ensemble de compteurs existe, une <xref:System.InvalidOperationException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="ae120-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ae120-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ae120-107">Version introduced</span></span>

<span data-ttu-id="ae120-108">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="ae120-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ae120-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ae120-109">Recommended action</span></span>

<span data-ttu-id="ae120-110">Si vous interceptez des <xref:System.ArgumentException> exceptions dans votre application lors de l’appel de <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> , envisagez également d’intercepter les <xref:System.InvalidOperationException> exceptions.</span><span class="sxs-lookup"><span data-stu-id="ae120-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="ae120-111">L’interception des <xref:System.ArgumentException> exceptions n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="ae120-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="ae120-112">Category</span><span class="sxs-lookup"><span data-stu-id="ae120-112">Category</span></span>

<span data-ttu-id="ae120-113">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae120-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ae120-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="ae120-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
