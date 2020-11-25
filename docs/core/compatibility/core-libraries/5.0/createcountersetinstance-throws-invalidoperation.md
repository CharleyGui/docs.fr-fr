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
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>CounterSet. CreateCounterSetInstance lève désormais une exception InvalidOperationException si l’instance existe déjà

À compter de .NET 5,0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> lève une exception <xref:System.InvalidOperationException> au lieu d’un <xref:System.ArgumentException> si l’ensemble de compteurs existe déjà.

## <a name="change-description"></a>Description de la modification

Dans .NET Framework et .NET Core 1,0 à 3,1, vous pouvez créer une instance de l’ensemble de compteurs en appelant <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> . Toutefois, si l’ensemble de compteurs existe déjà, la méthode lève une <xref:System.ArgumentException> exception.

Dans .NET 5,0 et versions ultérieures, lorsque vous appelez <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> et que l’ensemble de compteurs existe, une <xref:System.InvalidOperationException> exception est levée.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Si vous interceptez des <xref:System.ArgumentException> exceptions dans votre application lors de l’appel de <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> , envisagez également d’intercepter les <xref:System.InvalidOperationException> exceptions.

> [!NOTE]
> L’interception des <xref:System.ArgumentException> exceptions n’est pas recommandée.

## <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
