---
title: 'Modification avec rupture : éblouissant : modifications apportées à la logique de routage dans les applications éblouissantes'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé éblouissant : modifications apportées à la logique de routage dans les applications éblouissantes'
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513522"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a><span data-ttu-id="0857f-103">Éblouissante : la logique de priorité des itinéraires a changé dans les applications éblouissantes</span><span class="sxs-lookup"><span data-stu-id="0857f-103">Blazor: Route precedence logic changed in Blazor apps</span></span>

<span data-ttu-id="0857f-104">Un bogue dans l’implémentation du routage éblouissant a affecté le mode de détermination de la priorité des itinéraires.</span><span class="sxs-lookup"><span data-stu-id="0857f-104">A bug in the Blazor routing implementation affected how the precedence of routes was determined.</span></span> <span data-ttu-id="0857f-105">Ce bogue affecte les itinéraires ou itinéraires Catch-All avec des paramètres facultatifs dans votre application éblouissante.</span><span class="sxs-lookup"><span data-stu-id="0857f-105">This bug affects catch-all routes or routes with optional parameters within your Blazor app.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0857f-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0857f-106">Version introduced</span></span>

<span data-ttu-id="0857f-107">5.0.1</span><span class="sxs-lookup"><span data-stu-id="0857f-107">5.0.1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="0857f-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="0857f-108">Old behavior</span></span>

<span data-ttu-id="0857f-109">Avec le comportement erroné, les itinéraires avec une priorité plus faible sont considérés et mis en correspondance avec les itinéraires avec une priorité plus élevée.</span><span class="sxs-lookup"><span data-stu-id="0857f-109">With the erroneous behavior, routes with lower precedence are considered and matched over routes with higher precedence.</span></span> <span data-ttu-id="0857f-110">Par exemple, l' `{*slug}` itinéraire est mis en correspondance avant `/customer/{id}` .</span><span class="sxs-lookup"><span data-stu-id="0857f-110">For example, the `{*slug}` route is matched before `/customer/{id}`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="0857f-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="0857f-111">New behavior</span></span>

<span data-ttu-id="0857f-112">Le comportement actuel correspond plus étroitement au comportement de routage défini dans les applications ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0857f-112">The current behavior more closely matches the routing behavior defined in ASP.NET Core apps.</span></span> <span data-ttu-id="0857f-113">L’infrastructure détermine d’abord la priorité de l’itinéraire pour chaque segment.</span><span class="sxs-lookup"><span data-stu-id="0857f-113">The framework determines the route precedence for each segment first.</span></span> <span data-ttu-id="0857f-114">La longueur de l’itinéraire est utilisée uniquement en tant que deuxième critère pour rompre les liens.</span><span class="sxs-lookup"><span data-stu-id="0857f-114">The route's length is used only as a second criteria to break ties.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0857f-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="0857f-115">Reason for change</span></span>

<span data-ttu-id="0857f-116">Le comportement d’origine est considéré comme un bogue dans l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="0857f-116">The original behavior is considered a bug in the implementation.</span></span> <span data-ttu-id="0857f-117">En guise d’objectif, le système de routage dans les applications éblouissantes doit se comporter de la même façon que le système de routage dans le reste de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0857f-117">As a goal, the routing system in Blazor apps should behave the same way as the routing system in the rest of ASP.NET Core.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0857f-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0857f-118">Recommended action</span></span>

<span data-ttu-id="0857f-119">Si vous effectuez une mise à niveau à partir de versions précédentes de éblouissant vers 5. x, utilisez l' `PreferExactMatches` attribut sur le `Router` composant.</span><span class="sxs-lookup"><span data-stu-id="0857f-119">If upgrading from previous versions of Blazor to 5.x, use the `PreferExactMatches` attribute on the `Router` component.</span></span> <span data-ttu-id="0857f-120">Cet attribut peut être utilisé pour choisir le comportement correct.</span><span class="sxs-lookup"><span data-stu-id="0857f-120">This attribute can be used to opt into the correct behavior.</span></span> <span data-ttu-id="0857f-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0857f-121">For example:</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

<span data-ttu-id="0857f-122">Lorsque `PreferExactMatches` a la valeur `true` , la correspondance des itinéraires préfère les correspondances exactes par rapport aux caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="0857f-122">When `PreferExactMatches` is set to `true`, route matching prefers exact matches over wildcards.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0857f-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="0857f-123">Affected APIs</span></span>

<span data-ttu-id="0857f-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="0857f-124">None</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
