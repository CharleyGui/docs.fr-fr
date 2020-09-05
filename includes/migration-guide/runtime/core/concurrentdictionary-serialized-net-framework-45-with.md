---
ms.openlocfilehash: 450bfc56c99a3df9be71be2ef7df6e4e12d4ed76
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496783"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a><span data-ttu-id="6336e-101">Un ConcurrentDictionary sérialisé dans .NET Framework 4.5 avec NetDataContractSerializer ne peut pas être désérialisé par .NET Framework 4.5.1 ni 4.5.2</span><span class="sxs-lookup"><span data-stu-id="6336e-101">A ConcurrentDictionary serialized in .NET Framework 4.5 with NetDataContractSerializer cannot be deserialized by .NET Framework 4.5.1 or 4.5.2</span></span>

#### <a name="details"></a><span data-ttu-id="6336e-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6336e-102">Details</span></span>

<span data-ttu-id="6336e-103">En raison des modifications internes apportées au type, les objets <xref:System.Collections.Concurrent.ConcurrentDictionary%602> qui sont sérialisés avec .NET Framework 4.5 à l’aide de <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> ne peuvent pas être désérialisés dans .NET Framework 4.5.1 ni .NET Framework 4.5.2. Notez toutefois que l’inverse fonctionne (c’est-à-dire sérialiser avec .NET Framework 4.5.x et désérialiser avec .NET Framework 4.5).</span><span class="sxs-lookup"><span data-stu-id="6336e-103">Due to internal changes to the type, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objects that are serialized with the .NET Framework 4.5 using the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> cannot be deserialized in the .NET Framework 4.5.1 or in the .NET Framework 4.5.2.Note that moving in the other direction (serializing with the .NET Framework 4.5.x and deserializing with the .NET Framework 4.5) works.</span></span> <span data-ttu-id="6336e-104">De même, toutes les sérialisations interversions 4.x fonctionnent avec .NET Framework 4.6. La sérialisation et la désérialisation à l’aide d’une même version du .NET Framework ne sont pas affectées.</span><span class="sxs-lookup"><span data-stu-id="6336e-104">Similarly, all 4.x cross-version serialization works with the .NET Framework 4.6.Serializing and deserializing with a single version of the .NET Framework is not affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6336e-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6336e-105">Suggestion</span></span>

<span data-ttu-id="6336e-106">Si vous devez sérialiser et désérialiser un <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> entre .NET Framework 4.5 et .NET Framework 4.5.1/4.5.2, utilisez un autre sérialiseur tel que <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> au lieu de <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>. Étant donné que ce problème a été corrigé dans .NET Framework 4.6, vous pouvez aussi le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6336e-106">If it is necessary to serialize and deserialize a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> between the .NET Framework 4.5 and .NET Framework 4.5.1/4.5.2, an alternate serializer like the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serializer should be used instead of the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>.Alternatively, because this issue is addressed in the .NET Framework 4.6, it may be solved by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="6336e-107">Name</span><span class="sxs-lookup"><span data-stu-id="6336e-107">Name</span></span>    | <span data-ttu-id="6336e-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="6336e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6336e-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="6336e-109">Scope</span></span>   |<span data-ttu-id="6336e-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="6336e-110">Minor</span></span>|
|<span data-ttu-id="6336e-111">Version</span><span class="sxs-lookup"><span data-stu-id="6336e-111">Version</span></span>|<span data-ttu-id="6336e-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6336e-112">4.5.1</span></span>|
|<span data-ttu-id="6336e-113">Type</span><span class="sxs-lookup"><span data-stu-id="6336e-113">Type</span></span>|<span data-ttu-id="6336e-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="6336e-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6336e-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="6336e-115">Affected APIs</span></span>

<span data-ttu-id="6336e-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="6336e-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
