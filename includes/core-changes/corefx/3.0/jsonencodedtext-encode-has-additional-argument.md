---
ms.openlocfilehash: f5ae4669c85ae4f5d57d88ab55f6e1c758a625a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147586"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Les méthodes JsonEncodedText.Encode ont un argument JavaScriptEncoder supplémentaire

En commençant par .NET Core 3.0 Aperçu 8, les <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> méthodes contiennent un argument facultatif. <xref:System.Text.Encodings.Web.JavaScriptEncoder>

#### <a name="change-description"></a>Description de la modification

.NET Core 3.0 comprend un nouveau type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty-nameWithType>. En commençant par .NET Core 3.0 Aperçu <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8, la signature de <xref:System.Text.Encodings.Web.JavaScriptEncoder> toutes les surcharges de méthode a changé pour inclure un paramètre optionnel. Cette modification a été apportée pour permettre un encoder différent ou personnalisé.

La signature `Encode` des méthodes dans .NET Core 3.0 Aperçu 7 est:

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

La signature des `Encode` mêmes méthodes dans .NET Core 3.0 Aperçu 8 et les versions ultérieures est:

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

.NET Core 3.0 Aperçu 8

#### <a name="recommended-action"></a>Action recommandée

Il s’agit d’un changement de rupture binaire seulement; une recompile contre .NET Core 3.0 Aperçu 8 ou une version ultérieure permettra de résoudre tous les problèmes d’exécution.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
