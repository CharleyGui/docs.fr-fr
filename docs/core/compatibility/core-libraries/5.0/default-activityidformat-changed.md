---
title: 'Modification avec rupture : le ActivityIdFormat par défaut est W3C'
description: En savoir plus sur le changement critique .NET 5,0 dans les bibliothèques .NET de base où le ActivityIdFormat par défaut est désormais W3C.
ms.date: 11/01/2020
ms.openlocfilehash: 77ee705ac18065c84ddeab3127e01b6a40c3b84d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761070"
---
# <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="b4adb-103">Le ActivityIdFormat par défaut est W3C</span><span class="sxs-lookup"><span data-stu-id="b4adb-103">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="b4adb-104">Le format d’identificateur par défaut pour Activity ( <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> ) est Now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b4adb-104">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="change-description"></a><span data-ttu-id="b4adb-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="b4adb-105">Change description</span></span>

<span data-ttu-id="b4adb-106">Le format de l’ID d’activité W3C a été introduit dans .NET Core 3,0 comme alternative au format d’ID hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="b4adb-106">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="b4adb-107">Toutefois, pour préserver la compatibilité, le format W3C n’a pas effectué la valeur par défaut tant que .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="b4adb-107">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="b4adb-108">La valeur par défaut a été modifiée dans .NET 5,0, car le [format W3C a été ratifié et a](https://www.w3.org/TR/trace-context/) obtenu une traction sur plusieurs implémentations de langage.</span><span class="sxs-lookup"><span data-stu-id="b4adb-108">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="b4adb-109">Si votre application cible une plateforme autre que .NET 5,0 ou une version ultérieure, elle rencontre l’ancien comportement, où <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> est le format par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4adb-109">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="b4adb-110">Cette valeur par défaut s’applique aux plateformes Net45 +, netstandard 1.1 + et netcoreapp (1. x, 2. x et 3. x).</span><span class="sxs-lookup"><span data-stu-id="b4adb-110">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="b4adb-111">Dans .NET 5,0 et versions ultérieures, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> a la valeur <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b4adb-111">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b4adb-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b4adb-112">Version introduced</span></span>

<span data-ttu-id="b4adb-113">5.0</span><span class="sxs-lookup"><span data-stu-id="b4adb-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b4adb-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b4adb-114">Recommended action</span></span>

<span data-ttu-id="b4adb-115">Si votre application est indépendante de l’identificateur utilisé pour le traçage distribué, aucune action n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b4adb-115">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="b4adb-116">Des bibliothèques telles que ASP.NET Core et <xref:System.Net.Http.HttpClient> peuvent utiliser ou propager les deux versions du <xref:System.Diagnostics.ActivityIdFormat> .</span><span class="sxs-lookup"><span data-stu-id="b4adb-116">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="b4adb-117">Si vous avez besoin d’une interopérabilité avec les systèmes existants ou si les systèmes actuels s’appuient sur le format de l’identificateur, vous pouvez conserver l’ancien comportement en affectant à la valeur <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b4adb-117">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4adb-118">Vous pouvez également définir un commutateur AppContext de l’une des trois façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="b4adb-118">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="b4adb-119">Dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="b4adb-119">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="b4adb-120">Dans le fichier *runtimeconfig.js* .</span><span class="sxs-lookup"><span data-stu-id="b4adb-120">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="b4adb-121">Via une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="b4adb-121">Through an environment variable.</span></span>

  <span data-ttu-id="b4adb-122">Défini `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` sur `true` ou 1.</span><span class="sxs-lookup"><span data-stu-id="b4adb-122">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b4adb-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="b4adb-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
