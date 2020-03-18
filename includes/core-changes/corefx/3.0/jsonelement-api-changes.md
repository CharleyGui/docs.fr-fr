---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568167"
---
### <a name="jsonelement-api-changes"></a>Modifications de l’API JsonElement

En commençant par .NET Core 3.0 Aperçu 7, certaines <xref:System.Text.Json.JsonElement> API ont changé pour permettre une découverte plus facile et une plus grande utilisabilité.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 3.0 <xref:System.Text.Json.JsonElement> Aperçu 7, les API ont changé comme suit pour permettre une découverte plus facile et une plus grande utilisabilité.

1. Toutes `WriteProperty` les surcharges de <xref:System.Text.Json.JsonElement>méthode ont été supprimées de . Cela affecte le code tel que ce qui suit :

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

1. `WriteValue`a été <xref:System.Text.Json.JsonElement.WriteTo%2A>rebaptisé comme . Cela affecte le code tel que ce qui suit :

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>jette maintenant <xref:System.ArgumentNullException> un lorsque son `null`paramètre de méthode est .

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 7

#### <a name="recommended-action"></a>Action recommandée

Si votre code est affecté par ces modifications, vous pouvez faire ce qui suit :

- Il n’y a `WriteProperty` pas d’API de remplacement pour les surcharges dans <xref:System.Text.Json.JsonElement>. Au lieu de cela, <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> vous pouvez appeler <xref:System.Text.Json.JsonElement.WriteTo%2A> l’une des surcharges avec la méthode pour atteindre le même résultat. Par exemple :

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Renommer la `WriteValue` méthode <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>pour . Le paramètre de la méthode reste inchangé. Par exemple, le code précédent doit être modifié en ce qui suit :

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Gérer <xref:System.ArgumentNullException> les appels <xref:System.Text.Json.JsonElement.WriteTo%2A> dans la méthode.

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
