---
title: 'Modification avec rupture : éblouissant : logique de validation mise à jour pour les ressources Web statiques'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé « éblouissant » : logique de validation mise à jour pour les ressources Web statiques'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f201818c0130739e8da4f42e7b1f3a1987f70d1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760964"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a><span data-ttu-id="05ce7-103">Éblouissant : logique de validation mise à jour pour les ressources Web statiques</span><span class="sxs-lookup"><span data-stu-id="05ce7-103">Blazor: Updated validation logic for static web assets</span></span>

<span data-ttu-id="05ce7-104">Un problème est survenu lors de la validation des ressources Web statiques dans ASP.NET Core 3,1 et éblouissant webassembly 3,2.</span><span class="sxs-lookup"><span data-stu-id="05ce7-104">There was an issue in conflict validation for static web assets in ASP.NET Core 3.1 and Blazor WebAssembly 3.2.</span></span> <span data-ttu-id="05ce7-105">Le problème :</span><span class="sxs-lookup"><span data-stu-id="05ce7-105">The issue:</span></span>

* <span data-ttu-id="05ce7-106">A empêché la détection de conflit appropriée entre les ressources et les ressources de l’ordinateur hôte à partir des bibliothèques de classes Razor (RCLs) et des applications webassembly éblouissantes.</span><span class="sxs-lookup"><span data-stu-id="05ce7-106">Prevented proper conflict detection between the host assets and assets from Razor Class Libraries (RCLs) and Blazor WebAssembly apps.</span></span>
* <span data-ttu-id="05ce7-107">Affecte principalement les applications de webassembly éblouissantes, car par défaut, les ressources Web statiques dans RCLs sont traitées sous le `_content/$(PackageId)` préfixe.</span><span class="sxs-lookup"><span data-stu-id="05ce7-107">Mostly affects Blazor WebAssembly apps, since by default, static web assets in RCLs are served under the `_content/$(PackageId)` prefix.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="05ce7-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="05ce7-108">Version introduced</span></span>

<span data-ttu-id="05ce7-109">5.0</span><span class="sxs-lookup"><span data-stu-id="05ce7-109">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="05ce7-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="05ce7-110">Old behavior</span></span>

<span data-ttu-id="05ce7-111">Pendant le développement, les ressources Web statiques d’un RCL peuvent être remplacées en mode silencieux par des ressources de projet hôte sur le même chemin d’accès d’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="05ce7-111">During development, an RCL's static web assets could be silently overridden with host project assets on the same host path.</span></span> <span data-ttu-id="05ce7-112">Prenons l’exemple d’un RCL qui a défini une ressource Web statique à prendre en charge à */folder/file.txt*.</span><span class="sxs-lookup"><span data-stu-id="05ce7-112">Consider an RCL that has defined a static web asset to be served at */folder/file.txt*.</span></span> <span data-ttu-id="05ce7-113">Si l’hôte a placé un fichier sur *wwwroot/dossier/file.txt*, le fichier sur le serveur a remplacé silencieusement le fichier sur l’application RCL ou éblouissant webassembly.</span><span class="sxs-lookup"><span data-stu-id="05ce7-113">If the host placed a file at *wwwroot/folder/file.txt*, the file on the server silently overrode the file on the RCL or Blazor WebAssembly app.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="05ce7-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="05ce7-114">New behavior</span></span>

<span data-ttu-id="05ce7-115">ASP.NET Core détecte correctement quand ce problème se produit.</span><span class="sxs-lookup"><span data-stu-id="05ce7-115">ASP.NET Core correctly detects when this issue happens.</span></span> <span data-ttu-id="05ce7-116">Il vous informe de l’utilisateur, du conflit, afin que vous puissiez prendre les mesures appropriées.</span><span class="sxs-lookup"><span data-stu-id="05ce7-116">It informs you, the user, of the conflict so that you can take the appropriate action.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="05ce7-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="05ce7-117">Reason for change</span></span>

<span data-ttu-id="05ce7-118">Les ressources Web statiques n’étaient pas destinées à être substituables par des fichiers sur l’hôte *wwwroot* du projet.</span><span class="sxs-lookup"><span data-stu-id="05ce7-118">Static web assets weren't intended to be overridable by files on the *wwwroot* host of the project.</span></span> <span data-ttu-id="05ce7-119">Le fait d’autoriser le remplacement de ces fichiers peut entraîner des erreurs difficiles à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="05ce7-119">Allowing for the overriding of those files could lead to errors that are difficult to diagnose.</span></span> <span data-ttu-id="05ce7-120">Le résultat peut être des modifications de comportement non définies dans les applications publiées.</span><span class="sxs-lookup"><span data-stu-id="05ce7-120">The result could be undefined behavior changes in published apps.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="05ce7-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="05ce7-121">Recommended action</span></span>

<span data-ttu-id="05ce7-122">Par défaut, il n’y a aucune raison pour qu’un fichier RCL soit en conflit avec un fichier sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="05ce7-122">By default, there's no reason for an RCL file to conflict with a file on the host.</span></span> <span data-ttu-id="05ce7-123">Les fichiers RCL sont précédés du préfixe `_content/${PackageId}` .</span><span class="sxs-lookup"><span data-stu-id="05ce7-123">RCL files are prefixed with `_content/${PackageId}`.</span></span> <span data-ttu-id="05ce7-124">Les fichiers webassembly éblouissant sont placés à la racine de l’espace d’URL de l’hôte, ce qui facilite les conflits.</span><span class="sxs-lookup"><span data-stu-id="05ce7-124">Blazor WebAssembly files are placed at the root of the host URL space, which makes conflicts easier.</span></span> <span data-ttu-id="05ce7-125">Par exemple, les applications de webassembly éblouissantes contiennent un fichier *favicon. ico* que l’hôte peut également inclure dans son dossier *wwwroot* .</span><span class="sxs-lookup"><span data-stu-id="05ce7-125">For example, Blazor WebAssembly apps contain a *favicon.ico* file that the host might also include in its *wwwroot* folder.</span></span>

<span data-ttu-id="05ce7-126">Si la source du conflit est un fichier RCL, cela signifie souvent que le code copie les ressources de la bibliothèque dans le dossier *wwwroot* du projet.</span><span class="sxs-lookup"><span data-stu-id="05ce7-126">If the conflict's source is an RCL file, it often means code is copying assets from the library into the project's *wwwroot* folder.</span></span> <span data-ttu-id="05ce7-127">L’écriture de code pour copier des fichiers est à l’encontre d’un objectif principal des ressources Web statiques.</span><span class="sxs-lookup"><span data-stu-id="05ce7-127">Writing code to copy files defeats a primary goal of static web assets.</span></span> <span data-ttu-id="05ce7-128">Cet objectif est fondamental pour obtenir des mises à jour sur le navigateur lorsque le contenu est mis à jour sans avoir à déclencher une nouvelle compilation.</span><span class="sxs-lookup"><span data-stu-id="05ce7-128">This goal is fundamental to get updates on the browser when the contents are updated without having to trigger a new compilation.</span></span>

<span data-ttu-id="05ce7-129">Vous pouvez choisir de conserver ce comportement et de conserver le fichier sur l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="05ce7-129">You may choose to preserve this behavior and maintain the file on the host.</span></span> <span data-ttu-id="05ce7-130">Pour ce faire, supprimez le fichier de la liste des ressources Web statiques avec une cible MSBuild personnalisée.</span><span class="sxs-lookup"><span data-stu-id="05ce7-130">To do so, remove the file from the list of static web assets with a custom MSBuild target.</span></span>

<span data-ttu-id="05ce7-131">Pour utiliser le fichier de RCL ou le fichier de l’application éblouissante webassembly au lieu du fichier du projet hôte, supprimez le fichier du projet hôte.</span><span class="sxs-lookup"><span data-stu-id="05ce7-131">To use the RCL's file or the Blazor WebAssembly app's file instead of the host project's file, remove the file from the host project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="05ce7-132">API affectées</span><span class="sxs-lookup"><span data-stu-id="05ce7-132">Affected APIs</span></span>

<span data-ttu-id="05ce7-133">None</span><span class="sxs-lookup"><span data-stu-id="05ce7-133">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
