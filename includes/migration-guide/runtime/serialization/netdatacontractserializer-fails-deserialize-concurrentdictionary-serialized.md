---
ms.openlocfilehash: eef5633ec8566f6d5216b7dca4387766cacb600d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620063"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer ne parvient pas à désérialiser un ConcurrentDictionary sérialisé avec une autre version de .NET

#### <a name="details"></a>Détails

Par conception, <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> peut être utilisé uniquement si les extrémités de sérialisation et de désérialisation partagent toutes deux les mêmes types CLR. Par conséquent, il n’est pas garanti qu’un objet sérialisé avec une version du .NET Framework puisse être désérialisé par une autre version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> est un type qui est connu pour ne pas désérialiser correctement si la sérialisation est effectuée avec .NET Framework 4.5 ou version antérieure et la désérialisation avec .NET Framework 4.5.1 ou version ultérieure.

#### <a name="suggestion"></a>Suggestion

Il existe un certain nombre de solutions de contournement possibles à ce problème :<ul><li>Mettez à niveau l’ordinateur de sérialisation pour utiliser également .NET Framework 4.5.1.</li><li>Utilisez <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> au lieu de <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>, car il n’attend pas les mêmes types CLR à la fois aux extrémités de sérialisation et de désérialisation.</li><li>Utilisez <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> au lieu de <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>, car il ne présente pas cette rupture particulière entre 4.5-&gt;4.5.1.</li></ul>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|
