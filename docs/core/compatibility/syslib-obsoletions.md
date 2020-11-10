---
title: Fonctionnalités obsolètes dans .NET 5 +
description: Découvrez les API qui sont marquées comme obsolètes dans .NET 5,0 et versions ultérieures qui génèrent des avertissements du compilateur SYSLIB.
ms.date: 10/20/2020
ms.openlocfilehash: aa5716ba8fe46c7c4ae2faafe7cc963551eecef7
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440762"
---
# <a name="obsolete-features-in-net-5"></a>Fonctionnalités obsolètes dans .NET 5

À compter de .NET 5,0, certaines API qui viennent d’être marquées comme obsolètes utilisent deux nouvelles propriétés sur <xref:System.ObsoleteAttribute> .

- La <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> propriété indique au compilateur de générer des avertissements de génération à l’aide d’un ID de diagnostic personnalisé. L’ID personnalisé permet de supprimer l’avertissement obsoletion spécifiquement et séparément les uns des autres. Dans le cas de .NET 5 + obsoletions, le format de l’ID de diagnostic personnalisé est `SYSLIBxxxx` .

- La <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> propriété indique au compilateur d’inclure un lien d’URL pour en savoir plus sur le obsoletion.

Si vous rencontrez des avertissements ou des erreurs de build en raison de l’utilisation d’une API obsolète, suivez les instructions spécifiques fournies pour l’ID de diagnostic figurant dans la section [référence](#reference) . Les avertissements ou les erreurs pour ces obsoletions *ne peuvent pas* être supprimés à l’aide de l' [ID de diagnostic standard (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) pour les types ou membres obsolètes ; Utilisez les valeurs d’ID de diagnostic personnalisées à la `SYSLIBxxxx` place. Pour plus d’informations, consultez [supprimer des avertissements](#suppress-warnings).

## <a name="reference"></a>Informations de référence

Le tableau suivant fournit un index des `SYSLIBxxxx` obsoletions dans .net 5 +.

| ID de diagnostic | Description |
| - | - |
| [SYSLIB0001](syslib0001.md) | L’encodage UTF-7 n’est pas sécurisé et ne doit pas être utilisé. Envisagez plutôt d’utiliser UTF-8. |
| [SYSLIB0002](syslib0002.md) | <xref:System.Security.Permissions.PrincipalPermissionAttribute> n’est pas respecté par le runtime et ne doit pas être utilisé. |
| [SYSLIB0003](syslib0003.md) | La sécurité d’accès du code (CAS) n’est pas prise en charge ou respectée par le Runtime. |
| [SYSLIB0004](syslib0004.md) | La fonctionnalité de région d’exécution limitée n’est pas prise en charge. |
| [SYSLIB0005](syslib0005.md) | Le Global Assembly Cache (GAC) n’est pas pris en charge. |
| [SYSLIB0006](syslib0006.md) | <xref:System.Threading.Thread.Abort?displayProperty=nameWithType> n’est pas pris en charge et lève une exception <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0007](syslib0007.md) | L’implémentation par défaut de cet algorithme de chiffrement n’est pas prise en charge. |
| [SYSLIB0008](syslib0008.md) | L' <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API n’est pas prise en charge et lève une exception <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0009](syslib0009.md) | Les <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> méthodes et ne <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> sont pas prises en charge et lèvent <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0010](syslib0010.md) | Certaines API de communication à distance ne sont pas prises en charge et lèvent <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0011](syslib0011.md) | <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> la sérialisation est obsolète et ne doit pas être utilisée. |
| [SYSLIB0012](syslib0012.md) | <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> sont uniquement inclus pour la compatibilité .NET Framework. Utilisez <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> à la place. |

## <a name="suppress-warnings"></a>Supprimer les avertissements

Si vous devez utiliser les API obsolètes et `SYSLIBxxxx` que le diagnostic ne se présente pas comme une erreur, vous pouvez supprimer l’avertissement dans le code ou dans votre fichier projet.

Dans le code :

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

Fichier projet :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> La suppression des avertissements de cette façon ne désactive que les avertissements obsoletion que vous spécifiez. Il ne désactive pas les autres avertissements, y compris les avertissements obsoletion avec différents ID de diagnostic.
