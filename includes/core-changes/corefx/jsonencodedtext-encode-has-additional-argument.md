---
ms.openlocfilehash: 101740e828589d7d210527e3db82a1c949a6e0fd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117110"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="c0277-101">Les méthodes JsonEncodedText. Encode ont un argument JavaScriptEncoder supplémentaire</span><span class="sxs-lookup"><span data-stu-id="c0277-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="c0277-102">À compter de .net Core 3,0 Preview 8, <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> les méthodes contiennent un <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="c0277-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span> 

#### <a name="details"></a><span data-ttu-id="c0277-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c0277-103">Details</span></span>

<span data-ttu-id="c0277-104">.NET Core 3,0 comprend un nouveau type, XREF : System. Text. JSON. JsonEncodedText. Encode% 2A ? displayProperty = nameWithType >.</span><span class="sxs-lookup"><span data-stu-id="c0277-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0277-105">À compter de .net Core 3,0 Preview 8, la signature de <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> toutes les surcharges de méthode a changé pour <xref:System.Text.Encodings.Web.JavaScriptEncoder> inclure un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="c0277-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="c0277-106">Cette modification a été apportée pour autoriser un encodeur différent ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c0277-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="c0277-107">La signature des `Encode` méthodes dans .net Core 3,0 Preview 7 est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c0277-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

<span data-ttu-id="c0277-108">La signature des mêmes `Encode` méthodes dans .net Core 3,0 Preview 8 et versions ultérieures est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c0277-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a><span data-ttu-id="c0277-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c0277-109">Version introduced</span></span>

<span data-ttu-id="c0277-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="c0277-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c0277-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c0277-111">Recommended action</span></span>

<span data-ttu-id="c0277-112">Il s’agit uniquement d’une modification avec rupture binaire. une recompilation sur .NET Core 3,0 Preview 8 ou une version ultérieure corrige tous les problèmes d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c0277-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="c0277-113">Category</span><span class="sxs-lookup"><span data-stu-id="c0277-113">Category</span></span>

<span data-ttu-id="c0277-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c0277-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c0277-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="c0277-115">Affected APIs</span></span>

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs 

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->