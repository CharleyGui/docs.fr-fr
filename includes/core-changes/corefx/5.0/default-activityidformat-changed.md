---
ms.openlocfilehash: d75dc2caa3a002b9d34ac74f2c5c5e192281c0df
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281296"
---
### <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="e9591-101">Le ActivityIdFormat par défaut est W3C</span><span class="sxs-lookup"><span data-stu-id="e9591-101">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="e9591-102">Le format d’identificateur par défaut pour Activity ( <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> ) est Now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9591-102">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e9591-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e9591-103">Change description</span></span>

<span data-ttu-id="e9591-104">Le format de l’ID d’activité W3C a été introduit dans .NET Core 3,0 comme alternative au format d’ID hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="e9591-104">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="e9591-105">Toutefois, pour préserver la compatibilité, le format W3C n’a pas effectué la valeur par défaut tant que .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="e9591-105">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="e9591-106">La valeur par défaut a été modifiée dans .NET 5,0, car le [format W3C a été ratifié et a](https://www.w3.org/TR/trace-context/) obtenu une traction sur plusieurs implémentations de langage.</span><span class="sxs-lookup"><span data-stu-id="e9591-106">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="e9591-107">Si votre application cible une plateforme autre que .NET 5,0 ou une version ultérieure, elle rencontre l’ancien comportement, où <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> est le format par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9591-107">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="e9591-108">Cette valeur par défaut s’applique aux plateformes Net45 +, netstandard 1.1 + et netcoreapp (1. x, 2. x et 3. x).</span><span class="sxs-lookup"><span data-stu-id="e9591-108">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="e9591-109">Dans .NET 5,0 et versions ultérieures, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> a la valeur <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9591-109">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9591-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e9591-110">Version introduced</span></span>

<span data-ttu-id="e9591-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="e9591-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9591-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e9591-112">Recommended action</span></span>

<span data-ttu-id="e9591-113">Si votre application est indépendante de l’identificateur utilisé pour le traçage distribué, aucune action n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e9591-113">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="e9591-114">Des bibliothèques telles que ASP.NET Core et <xref:System.Net.Http.HttpClient> peuvent utiliser ou propager les deux versions du <xref:System.Diagnostics.ActivityIdFormat> .</span><span class="sxs-lookup"><span data-stu-id="e9591-114">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="e9591-115">Si vous avez besoin d’une interopérabilité avec les systèmes existants ou si les systèmes actuels s’appuient sur le format de l’identificateur, vous pouvez conserver l’ancien comportement en affectant à la valeur <xref:System.Diagnostics.Activity.DefaultIdFormat> <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9591-115">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9591-116">Vous pouvez également définir un commutateur AppContext de l’une des trois façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="e9591-116">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="e9591-117">Dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="e9591-117">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="e9591-118">Dans le fichier *runtimeconfig.js* .</span><span class="sxs-lookup"><span data-stu-id="e9591-118">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="e9591-119">Via une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="e9591-119">Through an environment variable.</span></span>

  <span data-ttu-id="e9591-120">Défini `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` sur `true` ou 1.</span><span class="sxs-lookup"><span data-stu-id="e9591-120">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

#### <a name="category"></a><span data-ttu-id="e9591-121">Category</span><span class="sxs-lookup"><span data-stu-id="e9591-121">Category</span></span>

<span data-ttu-id="e9591-122">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="e9591-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9591-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="e9591-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->
