---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237348"
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

Avant cette modification, il était difficile de composer des convertisseurs de fabrique scellés, car il n’existait pas de moyen facile d’en faire un <xref:System.Text.Json.Serialization.JsonConverter%601>. Rendre la méthode de fabrique publique et transmettre également le @no__t actuel-0 permet une composition bien plus flexible.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

Les classes dérivées doivent être mises à jour et recompilées.

#### <a name="affected-apis"></a>API affectées

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> .

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
