---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568218"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="693c8-101">Json serializer type `JsonException` d’exception changé de à`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="693c8-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="693c8-102">Dans .NET Core 3.0 Aperçu 6 à 8, le sérialisateur jetterait un <xref:System.Text.Json.JsonException> quand il a rencontré un type de collection dérivé non soutenu.</span><span class="sxs-lookup"><span data-stu-id="693c8-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="693c8-103">À partir de .NET Core 3.0 Aperçu 9, le sérialisateur jette à <xref:System.NotSupportedException> la place.</span><span class="sxs-lookup"><span data-stu-id="693c8-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="693c8-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="693c8-104">Change description</span></span>

<span data-ttu-id="693c8-105">Dans .NET Core 3.0 Aperçu 6 à travers Aperçu <xref:System.Text.Json.JsonException> 8, le sérialisateur jetterait un quand il a rencontré un type de collection dérivé non soutenu.</span><span class="sxs-lookup"><span data-stu-id="693c8-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="693c8-106">Un *type de collection dérivé non soutenu* est tout type de collection qui n’est pas attribué à l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="693c8-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="693c8-107">Chaîne iDictionnaire,T\<></span><span class="sxs-lookup"><span data-stu-id="693c8-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="693c8-108">En commençant par .NET Core 3.0 Aperçu 9, le sérialisateur lance un <xref:System.NotSupportedException> Lors de la rencontre d’un type de collection non soutenu.</span><span class="sxs-lookup"><span data-stu-id="693c8-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="693c8-109">Le nouveau type d’exception reflète mieux les raisons pour lesquelles l’opération de désétérialisation est défaillante.</span><span class="sxs-lookup"><span data-stu-id="693c8-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="693c8-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="693c8-110">Version introduced</span></span>

<span data-ttu-id="693c8-111">3.0 Aperçu 9</span><span class="sxs-lookup"><span data-stu-id="693c8-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="693c8-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="693c8-112">Recommended action</span></span>

<span data-ttu-id="693c8-113">Si vous attrapez <xref:System.Text.Json.JsonException> lors de deserialisation, vous <xref:System.NotSupportedException>voudrez peut-être envisager également attraper .</span><span class="sxs-lookup"><span data-stu-id="693c8-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="693c8-114">Category</span><span class="sxs-lookup"><span data-stu-id="693c8-114">Category</span></span>

<span data-ttu-id="693c8-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="693c8-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="693c8-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="693c8-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
