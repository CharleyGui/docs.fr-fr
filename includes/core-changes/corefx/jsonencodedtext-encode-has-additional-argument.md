---
ms.openlocfilehash: 101740e828589d7d210527e3db82a1c949a6e0fd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117110"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Les méthodes JsonEncodedText. Encode ont un argument JavaScriptEncoder supplémentaire

À compter de .net Core 3,0 Preview 8, <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> les méthodes contiennent un <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument facultatif. 

#### <a name="details"></a>Détails

.NET Core 3,0 comprend un nouveau type, XREF : System. Text. JSON. JsonEncodedText. Encode% 2A ? displayProperty = nameWithType >. À compter de .net Core 3,0 Preview 8, la signature de <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> toutes les surcharges de méthode a changé pour <xref:System.Text.Encodings.Web.JavaScriptEncoder> inclure un paramètre facultatif. Cette modification a été apportée pour autoriser un encodeur différent ou personnalisé.

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

CoreFx

#### <a name="affected-apis"></a>API affectées

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs 

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->