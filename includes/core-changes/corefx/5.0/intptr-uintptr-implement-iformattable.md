---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024695"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a>IntPtr et UIntPtr implémentent IFormattable

<xref:System.IntPtr>et <xref:System.UIntPtr> implémentent désormais <xref:System.IFormattable> . Les fonctions qui vérifient <xref:System.IFormattable> la prise en charge peuvent maintenant retourner des résultats différents pour ces types, car ils peuvent passer un spécificateur de format et une culture.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.IntPtr> et <xref:System.UIntPtr> n’implémentent pas <xref:System.IFormattable> . Les fonctions qui recherchent <xref:System.IFormattable> peuvent revenir au simple appel à <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> ou, ce qui <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> signifie que les spécificateurs de format et les cultures ne sont pas respectés.

Dans .NET 5,0 et versions ultérieures, <xref:System.IntPtr> et <xref:System.UIntPtr> implémentent <xref:System.IFormattable> . Les fonctions qui vérifient <xref:System.IFormattable> la prise en charge peuvent maintenant retourner des résultats différents pour ces types, car ils peuvent passer un spécificateur de format et une culture.

Cette modification a un impact sur les scénarios tels que les chaînes interpolées et <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , entre autres.

#### <a name="reason-for-change"></a>Motif de modification

<xref:System.IntPtr>et <xref:System.UIntPtr> prennent désormais en charge le langage en C# via les `nint` `nuint` Mots clés et. Les types de stockage ont été mis à jour pour fournir une parité proche (dans la mesure du possible) avec des fonctionnalités exposées par d’autres types primitifs, tels que <xref:System.Int32?displayProperty=nameWithType> .

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 4

#### <a name="recommended-action"></a>Action recommandée

Si vous ne souhaitez pas qu’un spécificateur de format ou une culture personnalisée soit utilisé lors de l’affichage des valeurs de ces types, vous pouvez appeler les <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> surcharges et de `ToString()` .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
