---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147560"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter.CreateConverter signature changé

Pour faciliter la <xref:System.Text.Json.Serialization.JsonConverterFactory> composition <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> des classes, la méthode a été <xref:System.Text.Json.JsonSerializerOptions>rendue publique et a reçu un deuxième argument de type .

#### <a name="change-description"></a>Description de la modification

La signature `CreateConverter` de la méthode en .NET Core avant la version 3.0 Aperçu 8 était:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

Dans .NET Core 3.0 Aperçu 8 et versions ultérieures, il est:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Avant ce changement, il était difficile de composer des convertisseurs d’usine scellés, car il n’y avait pas <xref:System.Text.Json.Serialization.JsonConverter%601> de moyen facile d’en tirer. Rendre la méthode d’usine <xref:System.Text.Json.JsonSerializerOptions> publique et aussi passer le courant permettent une composition beaucoup plus flexible.

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 8

#### <a name="recommended-action"></a>Action recommandée

Les classes dérivées doivent être mises à jour et recompilées.

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
