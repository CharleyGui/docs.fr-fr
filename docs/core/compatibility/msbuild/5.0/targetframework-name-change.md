---
title: 'Modification avec rupture : la modification de TargetFramework de netcoreapp à net'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où la valeur de la propriété de la propriété de la propriété MSBuild est passée de netcoreapp 3.1 à net 5.0.
ms.date: 10/17/2020
ms.openlocfilehash: c3b39a36548d58d6ed75fd8b1c84b0cccfc738f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760939"
---
# <a name="targetframework-change-from-netcoreapp-to-net"></a>Modification de TargetFramework de netcoreapp en net

La valeur de la propriété MSBuild est `TargetFramework` passée de `netcoreapp3.1` à `net5.0` . Cela peut interrompre le code qui s’appuie sur l’analyse de la valeur de `TargetFramework` .

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

Dans .NET Core 1,0-3,1, la valeur de la `TargetFramework` propriété MSBuild commence par `netcoreapp` , par exemple, `netcoreapp3.1` pour les applications qui ciblent .net Core 3,1. À compter de .NET 5,0, cette valeur est simplifiée pour commencer `net` , par exemple, pour `net5.0` .net 5,0.

Pour plus d’informations, consultez [l’avenir des .NET standard et des noms de](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) [Framework cibles dans .net 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).

## <a name="reason-for-change"></a>Motif de modification

- Simplifie la `TargetFramework` valeur.
- Permet aux projets d’inclure un `TargetPlatform` dans la `TargetFramework` propriété.

## <a name="recommended-action"></a>Action recommandée

Si vous avez une logique qui analyse la valeur de `TargetFramework` , vous devez la mettre à jour. Par exemple, la condition MSBuild suivante s’appuie sur la valeur de `TargetFramework` .

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

Pour cette exigence, vous pouvez mettre à jour le code pour comparer l’identificateur de Framework cible à la place.

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

## <a name="affected-apis"></a>API affectées

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
