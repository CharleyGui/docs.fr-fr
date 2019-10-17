---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393993"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="4a51c-101">Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="4a51c-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="4a51c-102">Dans le cadre de la création de ASP.NET Core plus de paiement pour la lecture, la `ObjectPoolProvider` a été supprimée de l’ensemble principal de dépendances.</span><span class="sxs-lookup"><span data-stu-id="4a51c-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="4a51c-103">Les composants spécifiques qui reposent sur `ObjectPoolProvider` l’ajoutent eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="4a51c-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="4a51c-104">Pour plus d’informations, consultez [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="4a51c-104">For discussion, see [aspnet/AspNetCore#5944](https://github.com/aspnet/AspNetCore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4a51c-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4a51c-105">Version introduced</span></span>

<span data-ttu-id="4a51c-106">3,0</span><span class="sxs-lookup"><span data-stu-id="4a51c-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4a51c-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="4a51c-107">Old behavior</span></span>

<span data-ttu-id="4a51c-108">`WebHostBuilder` fournit `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4a51c-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4a51c-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="4a51c-109">New behavior</span></span>

<span data-ttu-id="4a51c-110">`WebHostBuilder` ne fournit plus `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.</span><span class="sxs-lookup"><span data-stu-id="4a51c-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4a51c-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="4a51c-111">Reason for change</span></span>

<span data-ttu-id="4a51c-112">Cette modification a été apportée pour rendre ASP.NET Core plus payant.</span><span class="sxs-lookup"><span data-stu-id="4a51c-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a51c-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4a51c-113">Recommended action</span></span>

<span data-ttu-id="4a51c-114">Si votre composant requiert `ObjectPoolProvider`, il doit être ajouté à vos dépendances via le `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="4a51c-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="4a51c-115">Category</span><span class="sxs-lookup"><span data-stu-id="4a51c-115">Category</span></span>

<span data-ttu-id="4a51c-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a51c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a51c-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="4a51c-117">Affected APIs</span></span>

<span data-ttu-id="4a51c-118">aucune.</span><span class="sxs-lookup"><span data-stu-id="4a51c-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
