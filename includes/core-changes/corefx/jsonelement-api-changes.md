---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237350"
---
### <a name="jsonelement-api-changes"></a>Modifications de l’API JsonElement

À compter de .NET Core 3,0 Preview 7, certaines API <xref:System.Text.Json.JsonElement> ont été modifiées pour permettre une découverte plus facile et une plus grande facilité d’utilisation.

#### <a name="change-description"></a>Modifier la description

Dans .NET Core 3,0 Preview 7, les API <xref:System.Text.Json.JsonElement> ont été modifiées comme suit pour permettre une découverte plus facile et une plus grande facilité d’utilisation.

1. Toutes les surcharges de méthode `WriteProperty` ont été supprimées de <xref:System.Text.Json.JsonElement>. Cela affecte le code comme suit :

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. `WriteValue` a été renommé en <xref:System.Text.Json.JsonElement.WriteTo%2A>. Cela affecte le code comme suit :

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A> lève désormais une <xref:System.ArgumentNullException> lorsque son paramètre de méthode est `null`.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 7

#### <a name="recommended-action"></a>Action recommandée

Si votre code est affecté par ces modifications, vous pouvez effectuer les opérations suivantes :

- Il n’existe aucune API de remplacement pour les surcharges `WriteProperty` dans <xref:System.Text.Json.JsonElement>. Au lieu de cela, vous pouvez appeler l’une des surcharges <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType>, ainsi que la méthode <xref:System.Text.Json.JsonElement.WriteTo%2A> pour Achive le même résultat. Exemple :

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Renommez la méthode `WriteValue` en <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>. Le paramètre de la méthode reste inchangé. Par exemple, le code précédent doit être remplacé par ce qui suit :

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Gérez le <xref:System.ArgumentNullException> dans les appels à la méthode <xref:System.Text.Json.JsonElement.WriteTo%2A>.

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
