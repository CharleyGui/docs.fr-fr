---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901689"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="3c85e-101">MVC : outil de précompilation déconseillé</span><span class="sxs-lookup"><span data-stu-id="3c85e-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="3c85e-102">Dans ASP.NET Core 1,1, le `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package (outil de précompilation Mvc) a été introduit pour ajouter la prise en charge de la compilation au moment de la publication des fichiers Razor (fichiers *. cshtml* ).</span><span class="sxs-lookup"><span data-stu-id="3c85e-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="3c85e-103">Dans ASP.NET Core 2,1, le [Kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) a été introduit pour s’étendre sur les fonctionnalités de l’outil de précompilation.</span><span class="sxs-lookup"><span data-stu-id="3c85e-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="3c85e-104">Le kit de développement logiciel (SDK) Razor a ajouté la prise en charge de la compilation et de la publication des fichiers Razor.</span><span class="sxs-lookup"><span data-stu-id="3c85e-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="3c85e-105">Le kit de développement logiciel (SDK) vérifie l’exactitude des fichiers *. cshtml* au moment de la génération, tout en améliorant le temps de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c85e-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="3c85e-106">Le kit de développement logiciel (SDK) Razor est activé par défaut et aucun geste n’est nécessaire pour commencer à l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="3c85e-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="3c85e-107">Dans ASP.NET Core 3,0, l’outil de précompilation MVC ASP.NET Core 1,1-Era a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="3c85e-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="3c85e-108">Les versions antérieures du package continueront de recevoir des correctifs de sécurité et bogues importants dans la version corrective.</span><span class="sxs-lookup"><span data-stu-id="3c85e-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3c85e-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3c85e-109">Version introduced</span></span>

<span data-ttu-id="3c85e-110">3.0</span><span class="sxs-lookup"><span data-stu-id="3c85e-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3c85e-111">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="3c85e-111">Old behavior</span></span>

<span data-ttu-id="3c85e-112">Le `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package a été utilisé pour précompiler les vues Razor Mvc.</span><span class="sxs-lookup"><span data-stu-id="3c85e-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3c85e-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="3c85e-113">New behavior</span></span>

<span data-ttu-id="3c85e-114">Le kit de développement logiciel (SDK) Razor prend en charge cette fonctionnalité en mode natif.</span><span class="sxs-lookup"><span data-stu-id="3c85e-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="3c85e-115">Le `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package n’est plus mis à jour.</span><span class="sxs-lookup"><span data-stu-id="3c85e-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3c85e-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="3c85e-116">Reason for change</span></span>

<span data-ttu-id="3c85e-117">Le kit de développement logiciel (SDK) Razor offre plus de fonctionnalités et vérifie l’exactitude des fichiers *. cshtml* au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="3c85e-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="3c85e-118">Le SDK améliore également le temps de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="3c85e-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3c85e-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3c85e-119">Recommended action</span></span>

<span data-ttu-id="3c85e-120">Pour les utilisateurs de ASP.NET Core 2,1 ou version ultérieure, mettez à jour pour utiliser la prise en charge native pour la précompilation dans le [Kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="3c85e-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="3c85e-121">Si des bogues ou des fonctionnalités manquantes empêchent la migration vers le kit de développement logiciel (SDK) Razor, ouvrez un problème dans [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="3c85e-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="3c85e-122">Category</span><span class="sxs-lookup"><span data-stu-id="3c85e-122">Category</span></span>

<span data-ttu-id="3c85e-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3c85e-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c85e-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="3c85e-124">Affected APIs</span></span>

<span data-ttu-id="3c85e-125">Aucun</span><span class="sxs-lookup"><span data-stu-id="3c85e-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
