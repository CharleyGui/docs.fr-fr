---
ms.openlocfilehash: 4aef35502fc93cbf0399e3c8d0932338829d6c07
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517349"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a>BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException

La <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode réencapsule maintenant certains objets d’exception à l’intérieur d’un <xref:System.Runtime.Serialization.SerializationException> avant de propager l’exception à l’appelant.

#### <a name="change-description"></a>Description de la modification

Auparavant, la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode permettait des exceptions arbitraires, telles que <xref:System.ArgumentNullException> , pour propager la pile jusqu’à ses appelants.

Dans .NET 5,0 et versions ultérieures, la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode intercepte de manière plus agressive les exceptions qui se produisent en raison d’opérations de désérialisation non valides et les encapsule dans un <xref:System.Runtime.Serialization.SerializationException> .

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 1

#### <a name="recommended-action"></a>Action recommandée

Dans la plupart des cas, vous n’avez aucune action à effectuer. Toutefois, si votre site d’appel dépend d’une exception particulière levée, vous pouvez désencapsuler l’exception du externe <xref:System.Runtime.Serialization.SerializationException> , comme illustré dans l’exemple suivant.

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx)
{
    if (serEx.InnerException is MyException myEx)
    {
        // Handle 'myEx' here in case it was wrapped in SerializationException.
    }
    else
    {
        throw;
    }
}
```

#### <a name="category"></a>Category

Sérialisation

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
