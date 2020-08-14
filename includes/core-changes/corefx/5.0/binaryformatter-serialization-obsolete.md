---
ms.openlocfilehash: 7cb146d19486618a4cee9976abe2220ea4b72790
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88204044"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET

`Serialize` les `Deserialize` méthodes et sur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , <xref:System.Runtime.Serialization.Formatter> et <xref:System.Runtime.Serialization.IFormatter> sont désormais obsolètes. En outre, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> la sérialisation est interdite par défaut pour les applications ASP.net.

#### <a name="change-description"></a>Description de la modification

En raison de [failles de sécurité](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) dans <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , les méthodes suivantes sont désormais obsolètes. En outre, dans les applications ASP.NET Core 5,0 et versions ultérieures, elles lèvent un <xref:System.NotSupportedException> , sauf si l’application Web a réactivé la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> fonctionnalité.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

Ces méthodes sont marquées comme obsolètes dans le cadre d’un effort visant à réduire l’utilisation de au <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sein de l’écosystème .net.

Les méthodes de sérialisation suivantes sont également obsolètes, mais n’ont pas de changements de comportement :

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="recommended-action"></a>Action recommandée

- Arrêtez l’utilisation <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> de dans votre code. Au lieu de cela, envisagez d’utiliser <xref:System.Text.Json.JsonSerializer> ou <xref:System.Xml.Serialization.XmlSerializer> . Pour plus d’informations, consultez le Guide de la [sécurité BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).

- Vous pouvez supprimer temporairement l' <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> avertissement au moment de la compilation, qui est `SYSLIB0011` . Nous vous recommandons d’évaluer minutieusement votre code pour déterminer les risques avant de choisir cette option. Le moyen le plus simple de supprimer les avertissements est d’entourer le site d’appel individuel à l’aide de `#pragma` directives.

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  Vous pouvez également supprimer l’avertissement dans le fichier projet.

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  Si vous supprimez l’avertissement dans le fichier projet, l’avertissement est supprimé pour tous les fichiers de code du projet. La suppression de SYSLIB0011 ne supprime pas les avertissements causés par l’utilisation d’autres API obsolètes.

- Pour continuer à utiliser <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dans les applications ASP.net, vous pouvez la réactiver dans le fichier projet. Toutefois, il est vivement recommandé de ne pas le faire. Pour plus d’informations, consultez le Guide de la [sécurité BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

Pour plus d’informations sur les actions recommandées, consultez [résolution des erreurs BinaryFormatter obsoletion et des erreurs de désactivation](https://aka.ms/binaryformatter).

#### <a name="category"></a>Category

- Bibliothèques .NET Core
- ASP.NET

#### <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
