---
ms.openlocfilehash: 98893470b64de4abf7f04817871e3053bf25b86d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119302"
---
### <a name="jsonelement-api-changes"></a>Modifications de l’API JsonElement

À compter de .net Core 3,0 Preview 7, <xref:System.Text.Json.JsonElement> certaines API ont été modifiées pour permettre une découverte plus facile et une plus grande facilité d’utilisation.

#### <a name="change-description"></a>Modifier la description

Dans .net Core 3,0 Preview 7, <xref:System.Text.Json.JsonElement> les API ont été modifiées comme suit pour permettre une découverte plus facile et une plus grande facilité d’utilisation.

1. Toutes `WriteProperty` les surcharges de méthode ont <xref:System.Text.Json.JsonElement>été supprimées de. Cela affecte le code comme suit :

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

1. `WriteValue`a été renommé en <xref:System.Text.Json.JsonElement.WriteTo%2A>. Cela affecte le code comme suit :

```csharp
using (JsonDocument doc = JsonDocument.Parse(jsonString))
{
    JsonElement root = doc.RootElement;
    root.WriteValue(writer);
}

```

1. <xref:System.Text.Json.JsonElement.WriteTo%2A>lève désormais une <xref:System.ArgumentNullException> lorsque son paramètre de méthode est `null`.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 7

#### <a name="recommended-action"></a>Action recommandée

Si votre code est affecté par ces modifications, vous pouvez effectuer les opérations suivantes :

- Il n’existe aucune API de remplacement `WriteProperty` pour les surcharges dans. <xref:System.Text.Json.JsonElement> Au lieu de cela, vous pouvez appeler <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> l’une des surcharges <xref:System.Text.Json.JsonElement.WriteTo%2A> avec la méthode pour Achive le même résultat. Par exemple :

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- Renommez `WriteValue` la méthode <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>en. Le paramètre de la méthode reste inchangé. Par exemple, le code précédent doit être remplacé par ce qui suit :

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- Gérez les <xref:System.ArgumentNullException> dans les appels à <xref:System.Text.Json.JsonElement.WriteTo%2A> la méthode.

#### <a name="affected-apis"></a>API affectées

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
