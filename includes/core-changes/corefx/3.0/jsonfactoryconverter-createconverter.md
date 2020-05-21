---
ms.openlocfilehash: 43da6233b70927e7320874772976b9e93a0bd69f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721376"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Signature de JsonFactoryConverter. CreateConverter modifiée

Pour faciliter la composition des <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, la <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> méthode a été rendue publique et reçoit un deuxième argument de type <xref:System.Text.Json.JsonSerializerOptions> .

#### <a name="change-description"></a>Description de la modification

La signature de la `CreateConverter` méthode dans .net Core antérieure à la version 3,0 Preview 8 était la suivante :

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

Dans .NET Core 3,0 Preview 8 et versions ultérieures, il s’agit de :

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Avant cette modification, il était difficile de composer des convertisseurs de fabrique scellés, car il n’existait pas de moyen simple de l’en faire <xref:System.Text.Json.Serialization.JsonConverter%601> . Rendre la méthode de fabrique publique et transmettre également l' <xref:System.Text.Json.JsonSerializerOptions> autorisation actuelle pour une composition bien plus flexible.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

Les classes dérivées doivent être mises à jour et recompilées.

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

#### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
