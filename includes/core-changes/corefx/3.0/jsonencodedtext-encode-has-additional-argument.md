---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021676"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="3a0cc-101">Les méthodes JsonEncodedText.Encode ont un argument JavaScriptEncoder supplémentaire</span><span class="sxs-lookup"><span data-stu-id="3a0cc-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="3a0cc-102">En commençant par .NET Core 3.0 Aperçu 8, les <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> méthodes contiennent un argument facultatif. <xref:System.Text.Encodings.Web.JavaScriptEncoder></span><span class="sxs-lookup"><span data-stu-id="3a0cc-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a0cc-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3a0cc-103">Change description</span></span>

<span data-ttu-id="3a0cc-104">.NET Core 3.0 comprend un nouveau type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty-nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3a0cc-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3a0cc-105">En commençant par .NET Core 3.0 Aperçu <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8, la signature de <xref:System.Text.Encodings.Web.JavaScriptEncoder> toutes les surcharges de méthode a changé pour inclure un paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="3a0cc-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="3a0cc-106">Cette modification a été apportée pour permettre un encoder différent ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3a0cc-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="3a0cc-107">La signature `Encode` des méthodes dans .NET Core 3.0 Aperçu 7 est:</span><span class="sxs-lookup"><span data-stu-id="3a0cc-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="3a0cc-108">La signature des `Encode` mêmes méthodes dans .NET Core 3.0 Aperçu 8 et les versions ultérieures est:</span><span class="sxs-lookup"><span data-stu-id="3a0cc-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="3a0cc-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3a0cc-109">Version introduced</span></span>

<span data-ttu-id="3a0cc-110">.NET Core 3.0 Aperçu 8</span><span class="sxs-lookup"><span data-stu-id="3a0cc-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a0cc-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3a0cc-111">Recommended action</span></span>

<span data-ttu-id="3a0cc-112">Il s’agit d’un changement de rupture binaire seulement; une recompile contre .NET Core 3.0 Aperçu 8 ou une version ultérieure permettra de résoudre tous les problèmes d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3a0cc-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="3a0cc-113">Category</span><span class="sxs-lookup"><span data-stu-id="3a0cc-113">Category</span></span>

<span data-ttu-id="3a0cc-114">Core .NET bibliothèques</span><span class="sxs-lookup"><span data-stu-id="3a0cc-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a0cc-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="3a0cc-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
