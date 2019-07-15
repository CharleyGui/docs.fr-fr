---
ms.openlocfilehash: b7953aab434de3b081f22acc43cf6c4a00ac0742
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858547"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>Un ConcurrentDictionary sérialisé dans .NET Framework 4.5 avec NetDataContractSerializer ne peut pas être désérialisé par .NET Framework 4.5.1 ni 4.5.2

|   |   |
|---|---|
|Détails|En raison des modifications internes apportées au type, les objets <xref:System.Collections.Concurrent.ConcurrentDictionary%602> qui sont sérialisés avec .NET Framework 4.5 à l’aide de <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> ne peuvent pas être désérialisés dans .NET Framework 4.5.1 ni .NET Framework 4.5.2. Notez toutefois que l’inverse fonctionne (c’est-à-dire sérialiser avec .NET Framework 4.5.x et désérialiser avec .NET Framework 4.5). De même, toutes les sérialisations interversions 4.x fonctionnent avec .NET Framework 4.6. La sérialisation et la désérialisation à l’aide d’une même version du .NET Framework ne sont pas affectées.|
|Suggestion|Si vous devez sérialiser et désérialiser un <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> entre .NET Framework 4.5 et .NET Framework 4.5.1/4.5.2, utilisez un autre sérialiseur tel que <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> au lieu de <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Étant donné que ce problème a été corrigé dans .NET Framework 4.6, vous pouvez aussi le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.|
|Portée|Mineur|
|Version|4.5.1|
|Type|Runtime|

