---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117088"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Signature de JsonFactoryConverter. CreateConverter modifiée

Pour faciliter la composition des <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, la <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> méthode a été rendue publique et reçoit un deuxième argument de type <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="details"></a>Détails

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

Avant cette modification, il était difficile de composer des convertisseurs de fabrique scellés, car il n’existait pas de moyen <xref:System.Text.Json.Serialization.JsonConverter%601> simple de l’en faire. Rendre la méthode de fabrique publique et transmettre également l' <xref:System.Text.Json.JsonSerializerOptions> autorisation actuelle pour une composition bien plus flexible.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

Les classes dérivées doivent être mises à jour et recompilées.

#### <a name="affected-apis"></a>API affectées

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
