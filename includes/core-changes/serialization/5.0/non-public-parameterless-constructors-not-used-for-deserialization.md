---
ms.openlocfilehash: 572ebc47d26e30738fc4e5b8a8fab1f2643e3d83
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997708"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="ca96b-101">Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation</span><span class="sxs-lookup"><span data-stu-id="ca96b-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="ca96b-102">Pour garantir la cohérence entre tous les monikers du Framework cible (TFM) pris en charge, les constructeurs non publics et sans paramètre ne sont plus utilisés pour la désérialisation avec <xref:System.Text.Json.JsonSerializer> , par défaut.</span><span class="sxs-lookup"><span data-stu-id="ca96b-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ca96b-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ca96b-103">Change description</span></span>

<span data-ttu-id="ca96b-104">Sur .NET Core 3,0 et 3,1, les constructeurs internes et privés peuvent être utilisés pour la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="ca96b-104">On .NET Core 3.0 and 3.1, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="ca96b-105">Sur .NET Standard 2,0 et 2,1, les constructeurs internes et privés ne sont pas autorisés, et une <xref:System.MissingMethodException> exception est levée si aucun constructeur sans paramètre public n’est défini.</span><span class="sxs-lookup"><span data-stu-id="ca96b-105">On .NET Standard 2.0 and 2.1, internal and private constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="ca96b-106">À compter de .NET 5,0, les constructeurs non publics, y compris les constructeurs sans paramètre, sont ignorés par défaut par le sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="ca96b-106">Starting in .NET 5.0, non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="ca96b-107">Le sérialiseur utilise l’un des constructeurs suivants pour la désérialisation :</span><span class="sxs-lookup"><span data-stu-id="ca96b-107">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="ca96b-108">Constructeur public annoté avec <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ca96b-108">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="ca96b-109">Constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="ca96b-109">Public parameterless constructor.</span></span>
- <span data-ttu-id="ca96b-110">Constructeur public paramétré (s’il s’agit du seul constructeur public présent).</span><span class="sxs-lookup"><span data-stu-id="ca96b-110">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="ca96b-111">Si aucun de ces constructeurs n’est disponible, une <xref:System.NotSupportedException> exception est levée si vous tentez de désérialiser le type.</span><span class="sxs-lookup"><span data-stu-id="ca96b-111">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ca96b-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ca96b-112">Version introduced</span></span>

<span data-ttu-id="ca96b-113">5.0</span><span class="sxs-lookup"><span data-stu-id="ca96b-113">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ca96b-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="ca96b-114">Reason for change</span></span>

- <span data-ttu-id="ca96b-115">Pour appliquer un comportement cohérent entre tous les monikers du Framework cible (TFM) <xref:System.Text.Json?displayProperty=fullName> générés par (.net Core 3,0 et versions ultérieures, ainsi que les .NET Standard 2,0 et 2,1)</span><span class="sxs-lookup"><span data-stu-id="ca96b-115">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions, and .NET Standard 2.0 and 2.1)</span></span>
- <span data-ttu-id="ca96b-116">Étant donné que <xref:System.Text.Json.JsonSerializer> ne doit pas appeler la surface d’exposition non publique d’un type, qu’il s’agisse d’un constructeur, d’une propriété ou d’un champ.</span><span class="sxs-lookup"><span data-stu-id="ca96b-116">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ca96b-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ca96b-117">Recommended action</span></span>

- <span data-ttu-id="ca96b-118">Si vous êtes propriétaire du type et que cela est faisable, rendez le constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="ca96b-118">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="ca96b-119">Sinon, implémentez un `JsonConverter<T>` pour le type et contrôlez le comportement de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="ca96b-119">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="ca96b-120">Category</span><span class="sxs-lookup"><span data-stu-id="ca96b-120">Category</span></span>

<span data-ttu-id="ca96b-121">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="ca96b-121">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ca96b-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="ca96b-122">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
