---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901761"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="0af88-101">Hébergement : ObjectPoolProvider supprimé des dépendances WebHostBuilder</span><span class="sxs-lookup"><span data-stu-id="0af88-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="0af88-102">Dans le cadre de la création de ASP.NET Core plus de paiement `ObjectPoolProvider` pour la lecture, a été supprimé de l’ensemble principal de dépendances.</span><span class="sxs-lookup"><span data-stu-id="0af88-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="0af88-103">Les composants spécifiques qui dépendent `ObjectPoolProvider` de maintenant l’ajoutent eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="0af88-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="0af88-104">Pour plus d’informations, consultez [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="0af88-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0af88-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0af88-105">Version introduced</span></span>

<span data-ttu-id="0af88-106">3.0</span><span class="sxs-lookup"><span data-stu-id="0af88-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0af88-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="0af88-107">Old behavior</span></span>

<span data-ttu-id="0af88-108">`WebHostBuilder`fournit `ObjectPoolProvider` par défaut dans le conteneur d’injection de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0af88-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0af88-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="0af88-109">New behavior</span></span>

<span data-ttu-id="0af88-110">`WebHostBuilder`n’est plus `ObjectPoolProvider` fourni par défaut dans le conteneur d’injection de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0af88-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0af88-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="0af88-111">Reason for change</span></span>

<span data-ttu-id="0af88-112">Cette modification a été apportée pour rendre ASP.NET Core plus payant.</span><span class="sxs-lookup"><span data-stu-id="0af88-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0af88-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0af88-113">Recommended action</span></span>

<span data-ttu-id="0af88-114">Si votre composant requiert `ObjectPoolProvider`, il doit être ajouté à vos dépendances via le `IServiceCollection`.</span><span class="sxs-lookup"><span data-stu-id="0af88-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="0af88-115">Category</span><span class="sxs-lookup"><span data-stu-id="0af88-115">Category</span></span>

<span data-ttu-id="0af88-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0af88-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0af88-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="0af88-117">Affected APIs</span></span>

<span data-ttu-id="0af88-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="0af88-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
