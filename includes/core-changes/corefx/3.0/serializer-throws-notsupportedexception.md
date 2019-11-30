---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568218"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="f416d-101">Le type d’exception du sérialiseur JSON est passé de `JsonException` à `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="f416d-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="f416d-102">Dans .NET Core 3,0 Preview 6 à 8, le sérialiseur lève une <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f416d-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f416d-103">À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> à la place.</span><span class="sxs-lookup"><span data-stu-id="f416d-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f416d-104">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="f416d-104">Change description</span></span>

<span data-ttu-id="f416d-105">Dans .NET Core 3,0 Preview 6 jusqu’à Preview 8, le sérialiseur lève une <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f416d-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f416d-106">Un *type de collection dérivé non pris en charge* est un type de collection qui n’est pas attribuable à l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="f416d-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="f416d-107">IDictionary\<chaîne, T ></span><span class="sxs-lookup"><span data-stu-id="f416d-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="f416d-108">À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> lorsqu’il rencontre un type de collection non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f416d-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="f416d-109">Le nouveau type d’exception reflète mieux la raison pour laquelle l’opération de désérialisation échoue.</span><span class="sxs-lookup"><span data-stu-id="f416d-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f416d-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f416d-110">Version introduced</span></span>

<span data-ttu-id="f416d-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="f416d-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f416d-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f416d-112">Recommended action</span></span>

<span data-ttu-id="f416d-113">Si vous interceptez des <xref:System.Text.Json.JsonException> lors de la désérialisation, vous souhaiterez peut-être également intercepter les <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="f416d-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="f416d-114">Category</span><span class="sxs-lookup"><span data-stu-id="f416d-114">Category</span></span>

<span data-ttu-id="f416d-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="f416d-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f416d-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="f416d-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
