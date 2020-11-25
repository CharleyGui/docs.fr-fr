---
title: 'Modification avec rupture : WinForms et les applications WPF utilisent Microsoft. NET. Sdk'
description: Découvrez la modification avec rupture dans .NET 5,0 où les applications Windows Forms et Windows Presentation Framework utilisent désormais le kit de développement logiciel (SDK) .NET au lieu du kit de développement logiciel (SDK) .NET Core WinForms et WPF SDK.
ms.date: 09/18/2020
ms.openlocfilehash: 5f25be44c390abc173f155351d8cb007a6b370b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761106"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a>WinForms et les applications WPF utilisent Microsoft. NET. Sdk

Les applications Windows Forms et Windows Presentation Framework (WPF) utilisent désormais le kit de développement logiciel (SDK) .NET ( `Microsoft.NET.Sdk` ) au lieu de .net Core WinForms et du SDK WPF ( `Microsoft.NET.Sdk.WindowsDesktop` ).

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET Core, les applications WinForms et WPF utilisaient un [Kit de développement logiciel (SDK](../../../project-sdk/overview.md) ) de projet distinct ( `Microsoft.NET.Sdk.WindowsDesktop` ). À compter de .NET 5,0, le kit de développement logiciel (SDK) WinForms et WPF a été unifié avec le kit de développement logiciel (SDK `Microsoft.NET.Sdk` ) .net. En outre, les nouveaux [monikers de Framework cible (TFM)](../../../../standard/frameworks.md) remplacent `netcoreapp` et `netstandard` dans .net 5. L’exemple suivant montre les modifications que vous devez apporter pour un fichier projet WPF lors du reciblage vers .NET 5,0 ou version ultérieure.

Dans les versions précédentes de .NET Core :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Dans .NET 5,0 et versions ultérieures :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a>Version introduite

.NET 5,0

## <a name="recommended-action"></a>Action recommandée

Dans votre fichier de projet WPF ou Windows Forms :

- Mettez à jour l' `Sdk` attribut avec la valeur `Microsoft.NET.Sdk` .
- Mettez à jour la `TargetFramework` propriété avec la valeur `net5.0-windows` .

## <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
