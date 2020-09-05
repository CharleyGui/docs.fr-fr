---
ms.openlocfilehash: 71cc7119710a2b381626dd9cf4ab66265eb3deba
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497320"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a><span data-ttu-id="52aba-101">SoapFormatter ne peut pas désérialiser Hashtable et les objets de collection ordonnée similaires</span><span class="sxs-lookup"><span data-stu-id="52aba-101">SoapFormatter cannot deserialize Hashtable and similar ordered collection objects</span></span>

#### <a name="details"></a><span data-ttu-id="52aba-102">Détails</span><span class="sxs-lookup"><span data-stu-id="52aba-102">Details</span></span>

<span data-ttu-id="52aba-103"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> ne garantit pas que les objets sérialisés dans une version du .NET Framework pourront être désérialisés correctement dans une autre version.</span><span class="sxs-lookup"><span data-stu-id="52aba-103">The <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version.</span></span> <span data-ttu-id="52aba-104">En effet, certaines collections ordonnées (comme <xref:System.Collections.Hashtable?displayProperty=fullName>) ont gagné de nouveaux membres entre les versions 4.0 et 4.5. De fait, les objets de ces types ne peuvent pas être désérialisés avec .NET Framework 4.0 s’ils ont été sérialisés avec .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="52aba-104">Specifically, some ordered collections (like <xref:System.Collections.Hashtable?displayProperty=fullName>) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET Framework 4.0 if they were serialized with .NET Framework 4.5.</span></span> <span data-ttu-id="52aba-105">Notez que si les données sérialisées sont sérialisées et désérialisées avec la même version du .NET Framework, aucun problème ne se produit.</span><span class="sxs-lookup"><span data-stu-id="52aba-105">Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="52aba-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="52aba-106">Suggestion</span></span>

<span data-ttu-id="52aba-107">La sérialisation <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> doit être remplacée par la sérialisation <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> ou <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> pour ne pas être affectée par les changements du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52aba-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serialization should be replaced with <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serialization or <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> to be resilient to .NET Framework changes.</span></span>

| <span data-ttu-id="52aba-108">Name</span><span class="sxs-lookup"><span data-stu-id="52aba-108">Name</span></span>    | <span data-ttu-id="52aba-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="52aba-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="52aba-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="52aba-110">Scope</span></span>   |<span data-ttu-id="52aba-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="52aba-111">Minor</span></span>|
|<span data-ttu-id="52aba-112">Version</span><span class="sxs-lookup"><span data-stu-id="52aba-112">Version</span></span>|<span data-ttu-id="52aba-113">4,5</span><span class="sxs-lookup"><span data-stu-id="52aba-113">4.5</span></span>|
|<span data-ttu-id="52aba-114">Type</span><span class="sxs-lookup"><span data-stu-id="52aba-114">Type</span></span>|<span data-ttu-id="52aba-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="52aba-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="52aba-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="52aba-116">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
