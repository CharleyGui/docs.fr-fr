---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041657"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="cbe31-101">Identité : L’interface utilisateur utilise la fonction d’actifs Web statiques</span><span class="sxs-lookup"><span data-stu-id="cbe31-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="cbe31-102">ASP.NET Core 3.0 a introduit une fonction d’actifs Web statiques, et Identity UI l’a adoptée.</span><span class="sxs-lookup"><span data-stu-id="cbe31-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cbe31-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="cbe31-103">Change description</span></span>

<span data-ttu-id="cbe31-104">À la suite de l’interface utilisateur Identity adoptant la fonction d’actifs Web statiques :</span><span class="sxs-lookup"><span data-stu-id="cbe31-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="cbe31-105">La sélection des cadres `IdentityUIFrameworkVersion` est effectuée en utilisant la propriété dans votre dossier de projet.</span><span class="sxs-lookup"><span data-stu-id="cbe31-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="cbe31-106">Bootstrap 4 est le cadre d’interface utilisateur par défaut pour l’interface utilisateur d’identité.</span><span class="sxs-lookup"><span data-stu-id="cbe31-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="cbe31-107">Bootstrap 3 a atteint la fin de la vie, et vous devriez envisager de migrer vers une version prise en charge.</span><span class="sxs-lookup"><span data-stu-id="cbe31-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cbe31-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="cbe31-108">Version introduced</span></span>

<span data-ttu-id="cbe31-109">3.0</span><span class="sxs-lookup"><span data-stu-id="cbe31-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cbe31-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="cbe31-110">Old behavior</span></span>

<span data-ttu-id="cbe31-111">Le cadre d’interface utilisateur par défaut pour l’interface utilisateur d’identité était **Bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="cbe31-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="cbe31-112">Le cadre d’interface utilisateur pourrait être `AddDefaultUI` configuré à l’aide d’un paramètre à la méthode appelez `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="cbe31-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cbe31-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="cbe31-113">New behavior</span></span>

<span data-ttu-id="cbe31-114">Le cadre d’interface utilisateur par défaut pour l’interface utilisateur d’identité est **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="cbe31-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="cbe31-115">Le cadre d’interface utilisateur doit être configuré `AddDefaultUI` dans votre fichier de projet, au lieu de l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="cbe31-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cbe31-116">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="cbe31-116">Reason for change</span></span>

<span data-ttu-id="cbe31-117">L’adoption de la fonction d’actifs Web statiques exigeait que la configuration du cadre d’interface utilisateur passe à MSBuild.</span><span class="sxs-lookup"><span data-stu-id="cbe31-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="cbe31-118">La décision sur le cadre à intégrer est une décision de prise de fonction, et non une décision en temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cbe31-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cbe31-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="cbe31-119">Recommended action</span></span>

<span data-ttu-id="cbe31-120">Examinez votre interface utilisateur de site pour vous assurer que les nouveaux composants Bootstrap 4 sont compatibles.</span><span class="sxs-lookup"><span data-stu-id="cbe31-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="cbe31-121">Si nécessaire, `IdentityUIFrameworkVersion` utilisez la propriété MSBuild pour revenir à Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="cbe31-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="cbe31-122">Ajoutez la propriété `<PropertyGroup>` à un élément de votre dossier de projet :</span><span class="sxs-lookup"><span data-stu-id="cbe31-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="cbe31-123">Category</span><span class="sxs-lookup"><span data-stu-id="cbe31-123">Category</span></span>

<span data-ttu-id="cbe31-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="cbe31-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cbe31-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="cbe31-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
