---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656334"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="a3293-101">WinForms et les applications WPF utilisent Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="a3293-101">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="a3293-102">Les applications Windows Forms et Windows Presentation Framework (WPF) utilisent désormais le kit de développement logiciel (SDK) .NET ( `Microsoft.NET.Sdk` ) au lieu de .net Core WinForms et du SDK WPF ( `Microsoft.NET.Sdk.WindowsDesktop` ).</span><span class="sxs-lookup"><span data-stu-id="a3293-102">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

#### <a name="change-description"></a><span data-ttu-id="a3293-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="a3293-103">Change description</span></span>

<span data-ttu-id="a3293-104">Dans les versions précédentes de .NET Core, les applications WinForms et WPF utilisaient un [Kit de développement logiciel (SDK](../../../../docs/core/project-sdk/overview.md) ) de projet distinct ( `Microsoft.NET.Sdk.WindowsDesktop` ).</span><span class="sxs-lookup"><span data-stu-id="a3293-104">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="a3293-105">À compter de .NET 5,0, le kit de développement logiciel (SDK) WinForms et WPF a été unifié avec le kit de développement logiciel (SDK `Microsoft.NET.Sdk` ) .net.</span><span class="sxs-lookup"><span data-stu-id="a3293-105">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="a3293-106">En outre, les nouveaux [monikers de Framework cible (TFM)](../../../../docs/standard/frameworks.md) remplacent `netcoreapp` et `netstandard` dans .net 5.</span><span class="sxs-lookup"><span data-stu-id="a3293-106">In addition, new [target framework monikers (TFM)](../../../../docs/standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="a3293-107">L’exemple suivant montre les modifications que vous devez apporter pour un fichier projet WPF lors du reciblage vers .NET 5,0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a3293-107">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="a3293-108">Dans les versions précédentes de .NET Core :</span><span class="sxs-lookup"><span data-stu-id="a3293-108">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="a3293-109">Dans .NET 5,0 et versions ultérieures :</span><span class="sxs-lookup"><span data-stu-id="a3293-109">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

#### <a name="version-introduced"></a><span data-ttu-id="a3293-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a3293-110">Version introduced</span></span>

<span data-ttu-id="a3293-111">.NET 5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="a3293-111">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a3293-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a3293-112">Recommended action</span></span>

<span data-ttu-id="a3293-113">Dans votre fichier de projet WPF ou Windows Forms :</span><span class="sxs-lookup"><span data-stu-id="a3293-113">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="a3293-114">Mettez à jour l' `Sdk` attribut avec la valeur `Microsoft.NET.Sdk` .</span><span class="sxs-lookup"><span data-stu-id="a3293-114">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="a3293-115">Mettez à jour la `TargetFramework` propriété avec la valeur `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="a3293-115">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

#### <a name="category"></a><span data-ttu-id="a3293-116">Category</span><span class="sxs-lookup"><span data-stu-id="a3293-116">Category</span></span>

- <span data-ttu-id="a3293-117">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a3293-117">Windows Forms</span></span>
- <span data-ttu-id="a3293-118">Windows Presentation Framework (WPF)</span><span class="sxs-lookup"><span data-stu-id="a3293-118">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a3293-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="a3293-119">Affected APIs</span></span>

<span data-ttu-id="a3293-120">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="a3293-120">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
