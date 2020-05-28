---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144477"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà

À compter de .NET 5,0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> lève une exception <xref:System.InvalidOperationException> au lieu d’un <xref:System.ArgumentException> si l’ensemble de compteurs existe déjà.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework et .NET Core 1,0 à 3,1, vous pouvez créer une instance de l’ensemble de compteurs en appelant <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> . Toutefois, si l’ensemble de compteurs existe déjà, la méthode lève une <xref:System.ArgumentException> exception.

Dans .NET 5,0 et versions ultérieures, lorsque vous appelez <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> et que l’ensemble de compteurs existe, une <xref:System.InvalidOperationException> exception est levée.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 5

#### <a name="recommended-action"></a>Action recommandée

Si vous interceptez des <xref:System.ArgumentException> exceptions dans votre application lors de l’appel de <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> , envisagez également d’intercepter les <xref:System.InvalidOperationException> exceptions.

> [!NOTE]
> L’interception des <xref:System.ArgumentException> exceptions n’est pas recommandée.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
