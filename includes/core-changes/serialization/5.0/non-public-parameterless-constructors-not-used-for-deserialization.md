---
ms.openlocfilehash: 3692848a0cbd4bbbe3c7bb4d2c22a2b19de732e4
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050463"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="eeb58-101">Constructeurs non publics, sans paramètre, non utilisés pour la désérialisation</span><span class="sxs-lookup"><span data-stu-id="eeb58-101">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="eeb58-102">Pour garantir la cohérence entre tous les monikers du Framework cible (TFM) pris en charge, les constructeurs non publics et sans paramètre ne sont plus utilisés pour la désérialisation avec <xref:System.Text.Json.JsonSerializer> , par défaut.</span><span class="sxs-lookup"><span data-stu-id="eeb58-102">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eeb58-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="eeb58-103">Change description</span></span>

<span data-ttu-id="eeb58-104">LesSystem.Text.Jsautonomes [ sur les packages NuGet](https://www.nuget.org/packages/System.Text.Json/) qui prennent en charge .NET standard 2,0 et versions ultérieures, autrement dit, les versions 4.6.0-4.7.2, se comportent de façon incohérente avec le comportement intégré sur .net Core 3,0 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="eeb58-104">The standalone [System.Text.Json NuGet packages](https://www.nuget.org/packages/System.Text.Json/) that support .NET Standard 2.0 and higher, that is, versions 4.6.0-4.7.2, behave inconsistently with the built-in behavior on .NET Core 3.0 and 3.1.</span></span> <span data-ttu-id="eeb58-105">Sur .NET Core 3. x, les constructeurs internes et privés peuvent être utilisés pour la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eeb58-105">On .NET Core 3.x, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="eeb58-106">Dans les packages autonomes, les constructeurs non publics ne sont pas autorisés, et une <xref:System.MissingMethodException> exception est levée si aucun constructeur sans paramètre public n’est défini.</span><span class="sxs-lookup"><span data-stu-id="eeb58-106">In the standalone packages, non-public constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="eeb58-107">À compter de .NET 5,0 et System.Text.Jssur le package NuGet 5.0.0, le comportement est cohérent entre le package NuGet et les API intégrées.</span><span class="sxs-lookup"><span data-stu-id="eeb58-107">Starting with .NET 5.0 and System.Text.Json NuGet package 5.0.0, the behavior is consistent between the NuGet package and the built-in APIs.</span></span> <span data-ttu-id="eeb58-108">Les constructeurs non publics, y compris les constructeurs sans paramètre, sont ignorés par défaut par le sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="eeb58-108">Non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="eeb58-109">Le sérialiseur utilise l’un des constructeurs suivants pour la désérialisation :</span><span class="sxs-lookup"><span data-stu-id="eeb58-109">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="eeb58-110">Constructeur public annoté avec <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="eeb58-110">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="eeb58-111">Constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="eeb58-111">Public parameterless constructor.</span></span>
- <span data-ttu-id="eeb58-112">Constructeur public paramétré (s’il s’agit du seul constructeur public présent).</span><span class="sxs-lookup"><span data-stu-id="eeb58-112">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="eeb58-113">Si aucun de ces constructeurs n’est disponible, une <xref:System.NotSupportedException> exception est levée si vous tentez de désérialiser le type.</span><span class="sxs-lookup"><span data-stu-id="eeb58-113">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eeb58-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="eeb58-114">Version introduced</span></span>

<span data-ttu-id="eeb58-115">5.0</span><span class="sxs-lookup"><span data-stu-id="eeb58-115">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eeb58-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="eeb58-116">Reason for change</span></span>

- <span data-ttu-id="eeb58-117">Pour appliquer un comportement cohérent entre tous les monikers du Framework cible (TFM) <xref:System.Text.Json?displayProperty=fullName> générés par (.net Core 3,0 et versions ultérieures et .NET Standard 2,0)</span><span class="sxs-lookup"><span data-stu-id="eeb58-117">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions and .NET Standard 2.0)</span></span>
- <span data-ttu-id="eeb58-118">Étant donné que <xref:System.Text.Json.JsonSerializer> ne doit pas appeler la surface d’exposition non publique d’un type, qu’il s’agisse d’un constructeur, d’une propriété ou d’un champ.</span><span class="sxs-lookup"><span data-stu-id="eeb58-118">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eeb58-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="eeb58-119">Recommended action</span></span>

- <span data-ttu-id="eeb58-120">Si vous êtes propriétaire du type et que cela est faisable, rendez le constructeur sans paramètre public.</span><span class="sxs-lookup"><span data-stu-id="eeb58-120">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="eeb58-121">Sinon, implémentez un `JsonConverter<T>` pour le type et contrôlez le comportement de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="eeb58-121">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="eeb58-122">Category</span><span class="sxs-lookup"><span data-stu-id="eeb58-122">Category</span></span>

<span data-ttu-id="eeb58-123">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="eeb58-123">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eeb58-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="eeb58-124">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
