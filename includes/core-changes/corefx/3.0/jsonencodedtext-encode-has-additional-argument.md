---
ms.openlocfilehash: d90996ae1b87cdea815daf979bece094d8602f70
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721682"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Les méthodes JsonEncodedText. Encode ont un argument JavaScriptEncoder supplémentaire

À compter de .NET Core 3,0 Preview 8, les <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> méthodes contiennent un <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument facultatif.

#### <a name="change-description"></a>Description de la modification

.NET Core 3,0 comprend un nouveau type, XREF : System. Text. JSON. JsonEncodedText. Encode% 2A ? displayProperty = nameWithType>. À compter de .NET Core 3,0 Preview 8, la signature de toutes les <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> surcharges de méthode a changé pour inclure un <xref:System.Text.Encodings.Web.JavaScriptEncoder> paramètre facultatif. Cette modification a été apportée pour autoriser un encodeur différent ou personnalisé.

La signature des `Encode` méthodes dans .net Core 3,0 Preview 7 est la suivante :

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

La signature des mêmes `Encode` méthodes dans .net Core 3,0 Preview 8 et versions ultérieures est la suivante :

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

#### <a name="version-introduced"></a>Version introduite

.NET Core 3,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

Il s’agit uniquement d’une modification avec rupture binaire. une recompilation sur .NET Core 3,0 Preview 8 ou une version ultérieure corrige tous les problèmes d’exécution.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
