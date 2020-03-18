---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901689"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="88bab-101">MVC : Outil de précomplification déprécié</span><span class="sxs-lookup"><span data-stu-id="88bab-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="88bab-102">Dans ASP.NET Core 1.1, `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` le paquet (outil de précomplation MVC) a été introduit pour ajouter de la prise en charge de la compilation en temps de publication des fichiers Razor (fichiers *.cshtml).*</span><span class="sxs-lookup"><span data-stu-id="88bab-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="88bab-103">Dans ASP.NET Core 2.1, le [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) a été introduit pour étendre les fonctionnalités de l’outil de précomplation.</span><span class="sxs-lookup"><span data-stu-id="88bab-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="88bab-104">Le Razor SDK a ajouté un support pour la compilation des fichiers Razor.</span><span class="sxs-lookup"><span data-stu-id="88bab-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="88bab-105">Le SDK vérifie la justesse des fichiers *.cshtml* au moment de la construction tout en améliorant le temps de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="88bab-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="88bab-106">Le Razor SDK est allumé par défaut, et aucun geste n’est nécessaire pour commencer à l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="88bab-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="88bab-107">Dans ASP.NET Core 3.0, l’outil ASP.NET de précomplation MVC de l’ère Core 1.1 a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="88bab-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="88bab-108">Les versions plus tôt de paquet continueront à recevoir des corrections importantes de bogue et de sécurité dans la version de correction.</span><span class="sxs-lookup"><span data-stu-id="88bab-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="88bab-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="88bab-109">Version introduced</span></span>

<span data-ttu-id="88bab-110">3.0</span><span class="sxs-lookup"><span data-stu-id="88bab-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="88bab-111">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="88bab-111">Old behavior</span></span>

<span data-ttu-id="88bab-112">Le `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paquet a été utilisé pour pré-compiler des vues de rasoir de MVC.</span><span class="sxs-lookup"><span data-stu-id="88bab-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="88bab-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="88bab-113">New behavior</span></span>

<span data-ttu-id="88bab-114">Le Razor SDK prend en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="88bab-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="88bab-115">Le `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paquet n’est plus mis à jour.</span><span class="sxs-lookup"><span data-stu-id="88bab-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="88bab-116">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="88bab-116">Reason for change</span></span>

<span data-ttu-id="88bab-117">Le Razor SDK fournit plus de fonctionnalités et vérifie la justesse des fichiers *.cshtml* au moment de la construction.</span><span class="sxs-lookup"><span data-stu-id="88bab-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="88bab-118">Le SDK améliore également le temps de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="88bab-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="88bab-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="88bab-119">Recommended action</span></span>

<span data-ttu-id="88bab-120">Pour les utilisateurs de ASP.NET Core 2.1 ou plus tard, mettre à jour pour utiliser le support natif pour la précomplation dans le [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="88bab-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="88bab-121">Si des bogues ou des fonctionnalités manquantes empêchent la migration vers le Razor SDK, ouvrez un problème à [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="88bab-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="88bab-122">Category</span><span class="sxs-lookup"><span data-stu-id="88bab-122">Category</span></span>

<span data-ttu-id="88bab-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="88bab-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="88bab-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="88bab-124">Affected APIs</span></span>

<span data-ttu-id="88bab-125">None</span><span class="sxs-lookup"><span data-stu-id="88bab-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
