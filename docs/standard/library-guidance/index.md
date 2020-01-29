---
title: Conseils sur la bibliothèque .NET open source
description: Recommandations de bonne pratique à l’attention des développeurs qui créent des bibliothèques .NET de qualité.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731423"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="5bc9f-103">Conseils sur la bibliothèque open source</span><span class="sxs-lookup"><span data-stu-id="5bc9f-103">Open-source library guidance</span></span>

<span data-ttu-id="5bc9f-104">Cette aide fournit des recommandations à l’attention des développeurs qui créent des bibliothèques .NET de qualité.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="5bc9f-105">Cette documentation se concentre sur le *quoi* et le *pourquoi* de la création d’une bibliothèque .NET, mais pas sur le *comment*.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="5bc9f-106">Aspects des bibliothèques .NET open source de qualité :</span><span class="sxs-lookup"><span data-stu-id="5bc9f-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="5bc9f-107">**Inclusives** - Les bonnes bibliothèques .NET s’efforcent de prendre en charge plusieurs plateformes, langages de programmation et applications.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="5bc9f-108">**Stables** - Les bonnes bibliothèques .NET coexistent dans l’écosystème .NET en s’exécutant dans les applications créées avec de nombreuses bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="5bc9f-109">**Conçues pour évoluer** - Les bibliothèques .NET doivent s’améliorer et évoluer au fil du temps tout en prenant en charge les utilisateurs existants.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="5bc9f-110">**Débogables** - Les bibliothèques .NET doivent utiliser les derniers outils afin de créer une excellente expérience de débogage pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="5bc9f-111">**Approuvées** - Les bibliothèques .NET ont la confiance des développeurs en publiant sur NuGet à l’aide des bonnes pratiques de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5bc9f-112">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="5bc9f-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="5bc9f-113">Types de suggestions</span><span class="sxs-lookup"><span data-stu-id="5bc9f-113">Types of recommendations</span></span>

<span data-ttu-id="5bc9f-114">Chaque article présente quatre types de suggestions : **À faire**, **Envisager**, **Éviter** et **À ne pas faire**.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="5bc9f-115">Le type de suggestion indique si celle-ci doit être suivie ou pas.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="5bc9f-116">Vous devez presque toujours suivre une suggestion **À faire**.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="5bc9f-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5bc9f-117">For example:</span></span>

<span data-ttu-id="5bc9f-118">✔️ distribuer votre bibliothèque à l’aide d’un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-118">✔️ DO distribute your library using a NuGet package.</span></span>

<span data-ttu-id="5bc9f-119">En revanche, les recommandations **Envisager** doivent généralement être appliquées, mais il existe des exceptions à la règle qui sont fondées, c’est pourquoi vous ne devez pas vous inquiéter si vous ne les suivez pas :</span><span class="sxs-lookup"><span data-stu-id="5bc9f-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="5bc9f-120">✔️ envisagez d’utiliser [SemVer 2.0.0](https://semver.org/) pour la version de votre package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-120">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="5bc9f-121">Les suggestions **Éviter** indiquent quelque chose qui n’est généralement pas une bonne idée, mais enfreindre les règles peut parfois avoir du sens :</span><span class="sxs-lookup"><span data-stu-id="5bc9f-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="5bc9f-122">❌ éviter les références de package NuGet qui demandent une version exacte.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-122">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="5bc9f-123">Et enfin, les suggestions **À ne pas faire** désignent quelque chose que vous ne devez presque jamais faire :</span><span class="sxs-lookup"><span data-stu-id="5bc9f-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="5bc9f-124">❌ ne publiez pas de versions avec nom fort et non avec nom fort de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-124">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="5bc9f-125">Par exemple : `Contoso.Api` et `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="5bc9f-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="5bc9f-126">Suivant</span><span class="sxs-lookup"><span data-stu-id="5bc9f-126">Next</span></span>](get-started.md)
