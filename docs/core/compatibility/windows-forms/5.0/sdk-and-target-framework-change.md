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
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="9a2de-103">WinForms et les applications WPF utilisent Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="9a2de-103">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="9a2de-104">Les applications Windows Forms et Windows Presentation Framework (WPF) utilisent désormais le kit de développement logiciel (SDK) .NET ( `Microsoft.NET.Sdk` ) au lieu de .net Core WinForms et du SDK WPF ( `Microsoft.NET.Sdk.WindowsDesktop` ).</span><span class="sxs-lookup"><span data-stu-id="9a2de-104">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

## <a name="change-description"></a><span data-ttu-id="9a2de-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="9a2de-105">Change description</span></span>

<span data-ttu-id="9a2de-106">Dans les versions précédentes de .NET Core, les applications WinForms et WPF utilisaient un [Kit de développement logiciel (SDK](../../../project-sdk/overview.md) ) de projet distinct ( `Microsoft.NET.Sdk.WindowsDesktop` ).</span><span class="sxs-lookup"><span data-stu-id="9a2de-106">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="9a2de-107">À compter de .NET 5,0, le kit de développement logiciel (SDK) WinForms et WPF a été unifié avec le kit de développement logiciel (SDK `Microsoft.NET.Sdk` ) .net.</span><span class="sxs-lookup"><span data-stu-id="9a2de-107">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="9a2de-108">En outre, les nouveaux [monikers de Framework cible (TFM)](../../../../standard/frameworks.md) remplacent `netcoreapp` et `netstandard` dans .net 5.</span><span class="sxs-lookup"><span data-stu-id="9a2de-108">In addition, new [target framework monikers (TFM)](../../../../standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="9a2de-109">L’exemple suivant montre les modifications que vous devez apporter pour un fichier projet WPF lors du reciblage vers .NET 5,0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9a2de-109">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="9a2de-110">Dans les versions précédentes de .NET Core :</span><span class="sxs-lookup"><span data-stu-id="9a2de-110">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="9a2de-111">Dans .NET 5,0 et versions ultérieures :</span><span class="sxs-lookup"><span data-stu-id="9a2de-111">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a><span data-ttu-id="9a2de-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9a2de-112">Version introduced</span></span>

<span data-ttu-id="9a2de-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="9a2de-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9a2de-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9a2de-114">Recommended action</span></span>

<span data-ttu-id="9a2de-115">Dans votre fichier de projet WPF ou Windows Forms :</span><span class="sxs-lookup"><span data-stu-id="9a2de-115">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="9a2de-116">Mettez à jour l' `Sdk` attribut avec la valeur `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="9a2de-116">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="9a2de-117">Mettez à jour la `TargetFramework` propriété avec la valeur `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="9a2de-117">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9a2de-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="9a2de-118">Affected APIs</span></span>

<span data-ttu-id="9a2de-119">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="9a2de-119">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
