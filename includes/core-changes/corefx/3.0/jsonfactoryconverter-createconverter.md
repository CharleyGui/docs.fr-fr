---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568175"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Signature de JsonFactoryConverter. CreateConverter modifiée

Pour faciliter la composition des classes <xref:System.Text.Json.Serialization.JsonConverterFactory>, la méthode <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> a été rendue publique et reçoit un deuxième argument de type <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="change-description"></a>Modifier la description

La signature de la méthode `CreateConverter` dans .NET Core antérieure à la version 3,0 Preview 8 était la suivante :

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

Avant cette modification, il était difficile de composer des convertisseurs de fabrique scellés, car il n’existait pas de moyen facile d’y <xref:System.Text.Json.Serialization.JsonConverter%601> parvenir. Rendre la méthode de fabrique publique et transmettre également le <xref:System.Text.Json.JsonSerializerOptions> actuel permet une composition bien plus flexible.

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
