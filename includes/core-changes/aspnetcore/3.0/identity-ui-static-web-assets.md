---
ms.openlocfilehash: 8d7942ef6c36c01a9ae7ae2a9739f26dfcda5813
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394357"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="6dd71-101">Identité : l’interface utilisateur utilise la fonctionnalité de ressources Web statiques</span><span class="sxs-lookup"><span data-stu-id="6dd71-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="6dd71-102">ASP.NET Core 3,0 a introduit une fonctionnalité de ressources Web statiques et l’interface utilisateur de l’identité l’a adoptée.</span><span class="sxs-lookup"><span data-stu-id="6dd71-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6dd71-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="6dd71-103">Change description</span></span>

<span data-ttu-id="6dd71-104">En raison de l’interface utilisateur d’identité adoptant la fonctionnalité de ressources Web statiques :</span><span class="sxs-lookup"><span data-stu-id="6dd71-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="6dd71-105">La sélection de l’infrastructure s’effectue à l’aide de la propriété `IdentityUIFrameworkVersion` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6dd71-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="6dd71-106">Bootstrap 4 est l’infrastructure d’interface utilisateur par défaut pour l’interface utilisateur d’identité.</span><span class="sxs-lookup"><span data-stu-id="6dd71-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="6dd71-107">Le bootstrap 3 a atteint la fin de vie et vous devez envisager une migration vers une version prise en charge.</span><span class="sxs-lookup"><span data-stu-id="6dd71-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6dd71-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6dd71-108">Version introduced</span></span>

<span data-ttu-id="6dd71-109">3,0</span><span class="sxs-lookup"><span data-stu-id="6dd71-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6dd71-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="6dd71-110">Old behavior</span></span>

<span data-ttu-id="6dd71-111">L’infrastructure d’interface utilisateur par défaut pour l’interface utilisateur d’identité était **bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="6dd71-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="6dd71-112">L’infrastructure de l’interface utilisateur peut être configurée à l’aide d’un paramètre de l’appel de méthode `AddIdentityUI` dans `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="6dd71-112">The UI framework could be configured using a parameter to the `AddIdentityUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6dd71-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="6dd71-113">New behavior</span></span>

<span data-ttu-id="6dd71-114">L’infrastructure d’interface utilisateur par défaut pour l’interface utilisateur d’identité est **bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="6dd71-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="6dd71-115">L’infrastructure d’interface utilisateur doit être configurée dans votre fichier projet, plutôt que dans l’appel de méthode `AddIdentityUI`.</span><span class="sxs-lookup"><span data-stu-id="6dd71-115">The UI framework must be configured in your project file, instead of in the `AddIdentityUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6dd71-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6dd71-116">Reason for change</span></span>

<span data-ttu-id="6dd71-117">L’adoption de la fonctionnalité de ressources Web statiques nécessitait le déplacement de la configuration de l’infrastructure d’interface utilisateur vers MSBuild.</span><span class="sxs-lookup"><span data-stu-id="6dd71-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="6dd71-118">La décision sur l’infrastructure à incorporer est une décision au moment de la génération, et non une décision d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6dd71-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6dd71-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6dd71-119">Recommended action</span></span>

<span data-ttu-id="6dd71-120">Passez en revue l’interface utilisateur de votre site pour vous assurer que les nouveaux composants bootstrap 4 sont compatibles.</span><span class="sxs-lookup"><span data-stu-id="6dd71-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="6dd71-121">Si nécessaire, utilisez la propriété MSBuild `IdentityUIFrameworkVersion` pour revenir à bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="6dd71-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="6dd71-122">Ajoutez la propriété à un élément `<PropertyGroup>` dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="6dd71-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="6dd71-123">Category</span><span class="sxs-lookup"><span data-stu-id="6dd71-123">Category</span></span>

<span data-ttu-id="6dd71-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6dd71-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6dd71-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="6dd71-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)`

-->
