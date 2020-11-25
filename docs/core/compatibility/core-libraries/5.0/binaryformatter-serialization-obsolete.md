---
title: 'Modification avec rupture : les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où les méthodes de sérialisation et de désérialisation sur BinaryFormatter, Formatter et IFormatter sont obsolètes.
ms.date: 11/01/2020
ms.openlocfilehash: 5807a7d4e6beab26b9848b803922396dd893075b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761021"
---
# <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>Les méthodes de sérialisation BinaryFormatter sont obsolètes et interdites dans les applications ASP.NET

`Serialize` les `Deserialize` méthodes et sur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , <xref:System.Runtime.Serialization.Formatter> et <xref:System.Runtime.Serialization.IFormatter> sont désormais obsolètes en tant qu’avertissement. En outre, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> la sérialisation est interdite par défaut pour les applications ASP.net.

## <a name="change-description"></a>Description de la modification

En raison de [failles de sécurité](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) dans <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , les méthodes suivantes sont désormais obsolètes et produisent un avertissement au moment de la compilation avec l’ID `SYSLIB0011` . En outre, dans les applications ASP.NET Core 5,0 et versions ultérieures, elles lèvent un <xref:System.NotSupportedException> , sauf si l’application Web a réactivé la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> fonctionnalité.

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

Les méthodes de sérialisation suivantes sont également obsolètes et génèrent un avertissement `SYSLIB0011` , mais n’ont pas de changements de comportement :

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="reason-for-change"></a>Motif de modification

Ces méthodes sont marquées comme obsolètes dans le cadre d’un effort visant à réduire l’utilisation de au <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sein de l’écosystème .net.

## <a name="recommended-action"></a>Action recommandée

- Arrêtez l’utilisation <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> de dans votre code. Au lieu de cela, envisagez d’utiliser <xref:System.Text.Json.JsonSerializer> ou <xref:System.Xml.Serialization.XmlSerializer> . Pour plus d’informations, consultez le Guide de la [sécurité BinaryFormatter](../../../../standard/serialization/binaryformatter-security-guide.md).

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

  Si vous supprimez l’avertissement dans le fichier projet, l’avertissement est supprimé pour tous les fichiers de code du projet. La suppression `SYSLIB0011` ne supprime pas les avertissements causés par l’utilisation d’autres API obsolètes.

- Pour continuer à utiliser <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dans les applications ASP.net, vous pouvez la réactiver dans le fichier projet. Toutefois, il est vivement recommandé de ne pas le faire. Pour plus d’informations, consultez le Guide de la [sécurité BinaryFormatter](../../../../standard/serialization/binaryformatter-security-guide.md).

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

Pour plus d’informations sur les actions recommandées, consultez [résolution des erreurs BinaryFormatter obsoletion et des erreurs de désactivation](https://aka.ms/binaryformatter).

## <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET Core

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
