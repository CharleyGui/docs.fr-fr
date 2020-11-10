---
title: "NETSDK1071 : PackageReference à' {0} 'a spécifié une version de `{1}` ."
description: Comment résoudre le problème d’un PackageReference sur un sous-package inclus avec une version de l’infrastructure.
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 852232cba04bb93a17872280e10848c2896991ae
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445784"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a>NETSDK1071 : PackageReference avec version explicite vers un repackage qui serait inclus dans le Framework.

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net 5.0.100 et versions ultérieures

Lorsque le kit de développement logiciel (SDK) .NET émet un avertissement NETSDK1071, il peut y avoir un conflit de version entre la version d’un PackageReference spécifié dans un et la version de ce dernier, comme référencé implicitement via une propriété TargetFramework :

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

Dans la mesure où la « TargetFramework » insère automatiquement une version du produit, les versions sont en conflit si elles diffèrent.

Pour résoudre ce problème :

1. Envisagez, quand vous ciblez .NET Core ou .NET Standard, d’éviter les références explicites à `Microsoft.NETCore.App` ou `NETStandard.Library` dans votre fichier projet.
2. Si vous avez besoin d’une version spécifique du runtime lorsque vous ciblez .NET Core, utilisez la `<RuntimeFrameworkVersion>` propriété au lieu de référencer directement le repackage. Par exemple, cela peut se produire si vous utilisez des [déploiements autonomes](../../deploying/index.md#publish-self-contained) et que vous avez besoin d’un correctif spécifique du runtime LTS 1.0.0.
3. Si vous avez besoin d’une version spécifique de `NetStandard.Library` lorsque vous ciblez .NET standard, vous pouvez utiliser la `<NetStandardImplicitPackageVersion>` propriété et la définir sur la version dont vous avez besoin.
4. N’eplicitly pas d’ajouter ou de mettre à jour des références à `Microsoft.NETCore.App` ou `NETSTandard.Library` dans des projets .NET Framework. NuGet installe automatiquement toute version de dont `NETStandard.Library` vous avez besoin lors de l’utilisation d’un package NuGet .NET standard.
5. Ne spécifiez pas de version pour `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All` lors de l’utilisation de .net Core 2.1 +, car le kit SDK .net Core sélectionne automatiquement la version appropriée. (Remarque : cela fonctionne uniquement quand vous ciblez .NET Core 2,1 si le projet utilise également `Microsoft.NET.Sdk.Web` . Ce problème a été résolu dans le kit de développement logiciel (SDK) .NET Core 2,2.)
6. Si vous souhaitez que l’avertissement disparaissent, vous pouvez également le désactiver :

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
