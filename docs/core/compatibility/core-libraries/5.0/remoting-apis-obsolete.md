---
title: 'Modification avec rupture : les API de communication à distance sont obsolètes'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où certaines API liées à la communication à distance sont marquées comme obsolètes et génèrent un avertissement avec un ID de diagnostic personnalisé.
ms.date: 11/01/2020
ms.openlocfilehash: 5687b1471028b077674cfd31cb77ce95dc51bef5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760987"
---
# <a name="remoting-apis-are-obsolete"></a>Les API de communication à distance sont obsolètes

Certaines API liées à la communication à distance sont marquées comme obsolètes et génèrent un `SYSLIB0010` avertissement au moment de la compilation. Ces API peuvent être supprimées dans une future version de .NET.

## <a name="change-description"></a>Description de la modification

Les API de communication à distance suivantes sont marquées comme obsolètes.

| API | Marqué comme obsolète dans... |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | 5,0 RC1 |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | 5,0 RC1 |

Dans .NET Framework 2. x-4. x, les <xref:System.MarshalByRefObject.GetLifetimeService> <xref:System.MarshalByRefObject.InitializeLifetimeService> méthodes et contrôlent la durée de vie des instances impliquées dans .NET Remoting. Dans .NET Core 2. x-3. x, ces méthodes lèvent toujours une <xref:System.PlatformNotSupportedException> au moment de l’exécution.

Dans .NET 5,0 et versions ultérieures, <xref:System.MarshalByRefObject.GetLifetimeService> les <xref:System.MarshalByRefObject.InitializeLifetimeService> méthodes et sont marquées comme obsolètes comme avertissements, mais continuent à lever une <xref:System.PlatformNotSupportedException> au moment de l’exécution.

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

Il s’agit d’une modification uniquement au moment de la compilation. Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.

## <a name="reason-for-change"></a>Motif de modification

[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) est une technologie héritée. Il permet l’instanciation d’un objet dans un autre processus (peut-être même sur un autre ordinateur) et l’interaction avec cet objet comme s’il s’agissait d’une instance d’objet .NET en cours de traitement ordinaire. L’infrastructure .NET Remoting existe uniquement dans .NET Framework 2. x-4. x. .NET Core et .NET 5,0 et versions ultérieures ne prennent pas en charge .NET Remoting, et les API de communication à distance n’existent pas ou lèvent toujours des exceptions sur ces runtimes.

Pour aider les développeurs à s’éloigner de ces API, nous avons Obsoleting les API liées à la communication à distance. Ces API peuvent être supprimées entièrement dans une future version de .NET.

## <a name="version-introduced"></a>Version introduite

.NET 5,0

## <a name="recommended-action"></a>Action recommandée

- Envisagez d’utiliser des services REST WCF ou HTTP pour communiquer avec des objets dans d’autres applications ou sur plusieurs ordinateurs. Pour plus d’informations, consultez [.NET Framework technologies indisponibles sur .net Core](../../../porting/net-framework-tech-unavailable.md).

- Si vous devez continuer à utiliser les API obsolètes, vous pouvez supprimer l' `SYSLIB0010` avertissement dans le code.

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  Vous pouvez également supprimer l’avertissement dans votre fichier projet, ce qui désactive l’avertissement pour tous les fichiers sources du projet.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  La suppression `SYSLIB0010` désactive uniquement les avertissements obsoletion de l’API de communication à distance. Il ne désactive pas les autres avertissements. En outre, il ne modifie pas le comportement de l’exécution codé en continu de Always levant <xref:System.PlatformNotSupportedException> .

## <a name="affected-apis"></a>API affectées

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
