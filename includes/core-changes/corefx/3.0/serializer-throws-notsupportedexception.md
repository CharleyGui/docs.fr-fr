---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021664"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="03f03-101">Le type d’exception du sérialiseur `JsonException` JSON est passé de à`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="03f03-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="03f03-102">Dans .NET Core 3,0 Preview 6 à 8, le sérialiseur lève une exception <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="03f03-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="03f03-103">À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> exception à la place.</span><span class="sxs-lookup"><span data-stu-id="03f03-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="03f03-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="03f03-104">Change description</span></span>

<span data-ttu-id="03f03-105">Dans .NET Core 3,0 Preview 6 à Preview 8, le sérialiseur lève une exception <xref:System.Text.Json.JsonException> lorsqu’il a rencontré un type de collection dérivé non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="03f03-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="03f03-106">Un *type de collection dérivé non pris en charge* est un type de collection qui n’est pas attribuable à l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="03f03-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="03f03-107">Chaîne\<IDictionary, T></span><span class="sxs-lookup"><span data-stu-id="03f03-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="03f03-108">À compter de .NET Core 3,0 Preview 9, le sérialiseur lève une <xref:System.NotSupportedException> lorsqu’il rencontre un type de collection non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="03f03-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="03f03-109">Le nouveau type d’exception reflète mieux la raison pour laquelle l’opération de désérialisation échoue.</span><span class="sxs-lookup"><span data-stu-id="03f03-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03f03-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="03f03-110">Version introduced</span></span>

<span data-ttu-id="03f03-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="03f03-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="03f03-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="03f03-112">Recommended action</span></span>

<span data-ttu-id="03f03-113">Si vous intervenez <xref:System.Text.Json.JsonException> lors de la désérialisation, vous souhaiterez peut-être également prendre <xref:System.NotSupportedException>en compte l’interception.</span><span class="sxs-lookup"><span data-stu-id="03f03-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="03f03-114">Category</span><span class="sxs-lookup"><span data-stu-id="03f03-114">Category</span></span>

<span data-ttu-id="03f03-115">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="03f03-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03f03-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="03f03-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
