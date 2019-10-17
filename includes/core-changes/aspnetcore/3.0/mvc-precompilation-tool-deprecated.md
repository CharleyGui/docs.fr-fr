---
ms.openlocfilehash: 641233df165a1c2208a2185f2b6e99077f9a59d3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394225"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="d01e3-101">MVC : outil de précompilation déconseillé</span><span class="sxs-lookup"><span data-stu-id="d01e3-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="d01e3-102">Dans ASP.NET Core 1,1, le package `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (outil de précompilation MVC) a été introduit pour ajouter la prise en charge de la compilation au moment de la publication des fichiers Razor (fichiers *. cshtml* ).</span><span class="sxs-lookup"><span data-stu-id="d01e3-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="d01e3-103">Dans ASP.NET Core 2,1, le [Kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) a été introduit pour s’étendre sur les fonctionnalités de l’outil de précompilation.</span><span class="sxs-lookup"><span data-stu-id="d01e3-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="d01e3-104">Le kit de développement logiciel (SDK) Razor a ajouté la prise en charge de la compilation et de la publication des fichiers Razor.</span><span class="sxs-lookup"><span data-stu-id="d01e3-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="d01e3-105">Le kit de développement logiciel (SDK) vérifie l’exactitude des fichiers *. cshtml* au moment de la génération, tout en améliorant le temps de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="d01e3-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="d01e3-106">Le kit de développement logiciel (SDK) Razor est activé par défaut et aucun geste n’est nécessaire pour commencer à l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="d01e3-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="d01e3-107">Dans ASP.NET Core 3,0, l’outil de précompilation MVC ASP.NET Core 1,1-Era a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="d01e3-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="d01e3-108">Les versions antérieures du package continueront de recevoir des correctifs de sécurité et bogues importants dans la version corrective.</span><span class="sxs-lookup"><span data-stu-id="d01e3-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="d01e3-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d01e3-109">Version introduced</span></span>

<span data-ttu-id="d01e3-110">3,0</span><span class="sxs-lookup"><span data-stu-id="d01e3-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d01e3-111">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d01e3-111">Old behavior</span></span>

<span data-ttu-id="d01e3-112">Le package `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` a été utilisé pour précompiler les vues Razor MVC.</span><span class="sxs-lookup"><span data-stu-id="d01e3-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d01e3-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d01e3-113">New behavior</span></span>

<span data-ttu-id="d01e3-114">Le kit de développement logiciel (SDK) Razor prend en charge cette fonctionnalité en mode natif.</span><span class="sxs-lookup"><span data-stu-id="d01e3-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="d01e3-115">Le package `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` n’est plus mis à jour.</span><span class="sxs-lookup"><span data-stu-id="d01e3-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d01e3-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d01e3-116">Reason for change</span></span>

<span data-ttu-id="d01e3-117">Le kit de développement logiciel (SDK) Razor offre plus de fonctionnalités et vérifie l’exactitude des fichiers *. cshtml* au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="d01e3-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="d01e3-118">Le SDK améliore également le temps de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="d01e3-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d01e3-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d01e3-119">Recommended action</span></span>

<span data-ttu-id="d01e3-120">Pour les utilisateurs de ASP.NET Core 2,1 ou version ultérieure, mettez à jour pour utiliser la prise en charge native pour la précompilation dans le [Kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="d01e3-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="d01e3-121">Si des bogues ou des fonctionnalités manquantes empêchent la migration vers le kit de développement logiciel (SDK) Razor, ouvrez un problème dans [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span><span class="sxs-lookup"><span data-stu-id="d01e3-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="d01e3-122">Category</span><span class="sxs-lookup"><span data-stu-id="d01e3-122">Category</span></span>

<span data-ttu-id="d01e3-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d01e3-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d01e3-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="d01e3-124">Affected APIs</span></span>

<span data-ttu-id="d01e3-125">aucune.</span><span class="sxs-lookup"><span data-stu-id="d01e3-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
