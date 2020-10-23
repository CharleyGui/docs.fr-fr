---
ms.openlocfilehash: 959d8cb6d3e52916f6777054f3e9b327dc8edb4e
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434928"
---
### <a name="global-assembly-cache-apis-are-obsolete"></a>Les API du global assembly cache sont obsolètes

.NET Core et .NET 5,0 et versions ultérieures éliminent le concept de Global Assembly Cache (GAC) qui était présent dans .NET Framework. Ainsi, toutes les API .NET Core et .NET 5 + qui gèrent le GAC échouent ou n’effectuent aucune opération.

Pour aider les développeurs à s’éloigner de ces API, certaines API liées au GAC sont marquées comme obsolètes et génèrent un `SYSLIB0005` avertissement au moment de la compilation. Ces API peuvent être supprimées dans une future version de .NET.

#### <a name="change-description"></a>Description de la modification

Les API suivantes sont marquées comme obsolètes.

| API | Marqué comme obsolète dans... |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | 5,0 RC1 |

Dans .NET Framework 2. x-4. x, la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété retourne `true` si l’assembly interrogé a été chargé à partir du GAC et `false` s’il a été chargé à partir d’un emplacement différent sur le disque. Dans .NET Core 2. x-3. x, <xref:System.Reflection.Assembly.GlobalAssemblyCache> retourne toujours `false` , ce qui reflète le fait que le GAC n’existe pas dans .net core.

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

Dans .NET 5,0 et versions ultérieures, la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété continue de retourner toujours `false` . Toutefois, l’accesseur Get de propriété est également marqué comme obsolète pour indiquer aux appelants qu’ils doivent arrêter d’accéder à la propriété. Les bibliothèques et les applications ne doivent pas utiliser l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> API pour effectuer des déterminations sur le comportement au moment de l’exécution, car elles sont toujours renvoyées `false` dans .net Core et .net 5,0 et versions ultérieures.

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

Il s’agit d’une modification uniquement au moment de la compilation. Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.

#### <a name="reason-for-change"></a>Motif de modification

Le Global Assembly Cache (GAC) n’existe pas en tant que concept dans .NET Core et .NET 5,0 et versions ultérieures.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0

#### <a name="recommended-action"></a>Action recommandée

- Si votre application interroge la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété, envisagez de supprimer l’appel. Si vous utilisez la <xref:System.Reflection.Assembly.GlobalAssemblyCache> valeur pour choisir entre un « assembly dans le GAC » et un « assembly qui n’est pas dans le GAC » au moment de l’exécution, reconsidérez si le workflow a toujours un sens pour une application .net Core ou .net 5.0 +.

- Si vous devez continuer à utiliser les API obsolètes, vous pouvez supprimer l' `SYSLIB0005` avertissement dans le code.

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  Vous pouvez également supprimer l’avertissement dans votre fichier projet, ce qui désactive l’avertissement pour tous les fichiers sources du projet.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  La suppression `SYSLIB0005` désactive uniquement l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> Avertissement obsoletion. Il ne désactive pas les autres avertissements.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
