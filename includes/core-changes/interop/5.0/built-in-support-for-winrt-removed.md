---
ms.openlocfilehash: 47c676122df4f0990949a7bfbcd7af8c6144d870
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160535"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="04ae8-101">La prise en charge intégrée de WinRT est supprimée de .NET</span><span class="sxs-lookup"><span data-stu-id="04ae8-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="04ae8-102">La prise en charge intégrée de la consommation des API [Windows Runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) dans .net est supprimée.</span><span class="sxs-lookup"><span data-stu-id="04ae8-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="04ae8-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="04ae8-103">Version introduced</span></span>

<span data-ttu-id="04ae8-104">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="04ae8-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="04ae8-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="04ae8-105">Change description</span></span>

<span data-ttu-id="04ae8-106">Auparavant, CoreCLR pouvait consommer des [fichiers de métadonnées Windows (WinMD)](/uwp/winrt-cref/winmd-files) pour l’activité et l’utilisation des types WinRT.</span><span class="sxs-lookup"><span data-stu-id="04ae8-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="04ae8-107">À compter de .NET 5,0, CoreCLR ne peut plus consommer les fichiers WinMD directement.</span><span class="sxs-lookup"><span data-stu-id="04ae8-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="04ae8-108">Si vous tentez de référencer un assembly non pris en charge, vous obtiendrez un <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="04ae8-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="04ae8-109">Si vous activez une classe WinRT, vous obtenez un <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="04ae8-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="04ae8-110">Cette modification avec rupture a été effectuée pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="04ae8-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="04ae8-111">Par conséquent, WinRT peut être développé et amélioré séparément du Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="04ae8-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="04ae8-112">Pour la symétrie avec les systèmes d’interopérabilité fournis pour d’autres systèmes d’exploitation, tels que iOS et Android.</span><span class="sxs-lookup"><span data-stu-id="04ae8-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="04ae8-113">Pour tirer parti d’autres fonctionnalités .NET, telles que les fonctionnalités C#, la liaison de langage intermédiaire (IL) et la compilation à l’avance (AOA).</span><span class="sxs-lookup"><span data-stu-id="04ae8-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="04ae8-114">Pour simplifier le code base du Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="04ae8-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="04ae8-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="04ae8-115">Recommended action</span></span>

- <span data-ttu-id="04ae8-116">Supprimez les références au [package Microsoft. Windows. Sdk. Contracts](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span><span class="sxs-lookup"><span data-stu-id="04ae8-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span></span>  <span data-ttu-id="04ae8-117">Au lieu de cela, spécifiez la version des API Windows auxquelles vous souhaitez accéder via la `TargetFramework` propriété du projet.</span><span class="sxs-lookup"><span data-stu-id="04ae8-117">Instead, specify the version of the Windows APIs that you want to access via the `TargetFramework` property of the project.</span></span>  <span data-ttu-id="04ae8-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="04ae8-118">For example:</span></span>

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- <span data-ttu-id="04ae8-119">Utilisez la chaîne de l’outil [C#/WinRT](/windows/uwp/csharp-winrt/) pour générer ou personnaliser les types et les API WinRT pour .net 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="04ae8-119">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types for .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="04ae8-120">Category</span><span class="sxs-lookup"><span data-stu-id="04ae8-120">Category</span></span>

<span data-ttu-id="04ae8-121">Interop</span><span class="sxs-lookup"><span data-stu-id="04ae8-121">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="04ae8-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="04ae8-122">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
