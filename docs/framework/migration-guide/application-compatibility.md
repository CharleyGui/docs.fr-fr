---
title: Modifications du runtime et du reciblage-.NET Framework
description: En savoir plus sur la compatibilité des applications dans .NET Framework et sur la manière dont elle est affectée par le runtime et les modifications de reciblage lors de la migration vers une autre version.
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: 26f36dd34c6c5ecae8fc5ab373ff60d9e56f8245
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475487"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="1bc32-103">Compatibilité des applications dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1bc32-103">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="1bc32-104">La compatibilité est un objectif important de chaque version de .NET.</span><span class="sxs-lookup"><span data-stu-id="1bc32-104">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="1bc32-105">La compatibilité garantit que chaque version est additive, de sorte que les versions précédentes continuent de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="1bc32-105">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="1bc32-106">En revanche, les modifications apportées à la fonctionnalité précédente (par exemple, pour améliorer les performances, résoudre les problèmes de sécurité ou corriger les bogues) peuvent entraîner des problèmes de compatibilité dans le code existant ou dans des applications existantes qui s’exécutent sous une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="1bc32-106">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="1bc32-107">Chaque application cible une version spécifique du .NET Framework par :</span><span class="sxs-lookup"><span data-stu-id="1bc32-107">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="1bc32-108">La définition d’une version cible de .NET Framework dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1bc32-108">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="1bc32-109">La spécification de la version cible de .NET Framework dans un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="1bc32-109">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="1bc32-110">L’application d’un <xref:System.Runtime.Versioning.TargetFrameworkAttribute> au code source.</span><span class="sxs-lookup"><span data-stu-id="1bc32-110">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="1bc32-111">Lors de la migration d’une version de la .NET Framework vers une autre, il existe deux types de modifications à prendre en compte :</span><span class="sxs-lookup"><span data-stu-id="1bc32-111">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="1bc32-112">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="1bc32-112">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="1bc32-113">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="1bc32-113">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="1bc32-114">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="1bc32-114">Runtime changes</span></span>

<span data-ttu-id="1bc32-115">Les problèmes d’exécution sont ceux qui surviennent lorsqu’un nouveau Runtime est placé sur un ordinateur et que le comportement d’une application change.</span><span class="sxs-lookup"><span data-stu-id="1bc32-115">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="1bc32-116">En cas d’exécution sur une version plus récente que celle ciblée, le .NET Framework utilise un comportement *excentrique* pour imiter l’ancienne version ciblée.</span><span class="sxs-lookup"><span data-stu-id="1bc32-116">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="1bc32-117">L’application s’exécute sur la version plus récente, mais agit comme si elle s’exécutait sur l’ancienne version.</span><span class="sxs-lookup"><span data-stu-id="1bc32-117">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="1bc32-118">La plupart des problèmes de compatibilité entre les versions du .NET Framework sont atténués via ce modèle de subterfuge.</span><span class="sxs-lookup"><span data-stu-id="1bc32-118">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="1bc32-119">Par exemple, si un fichier binaire a été compilé pour .NET Framework 4,0, mais qu’il s’exécute sur un ordinateur avec .NET Framework 4,5 ou version ultérieure, il s’exécute en mode de compatibilité .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="1bc32-119">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="1bc32-120">Cela signifie que la plupart des modifications apportées à la version ultérieure n’affectent pas le binaire.</span><span class="sxs-lookup"><span data-stu-id="1bc32-120">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="1bc32-121">La version de la .NET Framework qu’une application cible est déterminée par la version cible de l’assembly d’entrée pour le domaine d’application dans lequel le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="1bc32-121">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="1bc32-122">Tous les assemblys supplémentaires chargés dans ce domaine d’application ciblent cette version.</span><span class="sxs-lookup"><span data-stu-id="1bc32-122">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="1bc32-123">Par exemple, dans le cas d’un exécutable, la version ciblée par l’exécutable est le mode de compatibilité dans lequel tous les assemblys de ce domaine d’application s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="1bc32-123">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="1bc32-124">Pour afficher la liste des modifications à l’exécution qui s’appliquent à votre environnement, sélectionnez la version de .NET Framework que vous ciblez actuellement, puis la version vers laquelle vous souhaitez effectuer la migration :</span><span class="sxs-lookup"><span data-stu-id="1bc32-124">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="1bc32-125">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="1bc32-125">Retargeting changes</span></span>

<span data-ttu-id="1bc32-126">Les modifications de reciblage sont celles qui surviennent lorsqu’un assembly est recompilé pour cibler une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="1bc32-126">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="1bc32-127">Le ciblage d’une version plus récente signifie que l’assembly choisit les nouvelles fonctionnalités, ainsi que les problèmes de compatibilité potentiels pour les anciennes fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="1bc32-127">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="1bc32-128">Pour afficher la liste des modifications de reciblage qui s’appliquent à votre environnement, sélectionnez la version de .NET Framework que vous ciblez actuellement, puis la version vers laquelle vous souhaitez effectuer la migration :</span><span class="sxs-lookup"><span data-stu-id="1bc32-128">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="1bc32-129">Classification d’impact</span><span class="sxs-lookup"><span data-stu-id="1bc32-129">Impact classification</span></span>

<span data-ttu-id="1bc32-130">Dans les rubriques qui décrivent les modifications du runtime et du reciblage, par exemple, les [modifications de reciblage pour la migration de 4.7.2 vers 4,8](retargeting/4.7.2-4.8.md), les éléments individuels sont classés en fonction de leur impact attendu comme suit :</span><span class="sxs-lookup"><span data-stu-id="1bc32-130">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="1bc32-131">**Envergure**</span><span class="sxs-lookup"><span data-stu-id="1bc32-131">**Major**</span></span>\
<span data-ttu-id="1bc32-132">Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code.</span><span class="sxs-lookup"><span data-stu-id="1bc32-132">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="1bc32-133">**Mineure**</span><span class="sxs-lookup"><span data-stu-id="1bc32-133">**Minor**</span></span>\
<span data-ttu-id="1bc32-134">Modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications du code.</span><span class="sxs-lookup"><span data-stu-id="1bc32-134">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="1bc32-135">**Cas limite**</span><span class="sxs-lookup"><span data-stu-id="1bc32-135">**Edge case**</span></span>\
<span data-ttu-id="1bc32-136">Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.</span><span class="sxs-lookup"><span data-stu-id="1bc32-136">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="1bc32-137">**Transparente**</span><span class="sxs-lookup"><span data-stu-id="1bc32-137">**Transparent**</span></span>\
<span data-ttu-id="1bc32-138">Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application.</span><span class="sxs-lookup"><span data-stu-id="1bc32-138">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="1bc32-139">L'application n'a pas besoin d'être modifiée en raison de cette modification.</span><span class="sxs-lookup"><span data-stu-id="1bc32-139">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bc32-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bc32-140">See also</span></span>

- [<span data-ttu-id="1bc32-141">Versions et dépendances</span><span class="sxs-lookup"><span data-stu-id="1bc32-141">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="1bc32-142">Nouveautés</span><span class="sxs-lookup"><span data-stu-id="1bc32-142">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="1bc32-143">Éléments obsolètes</span><span class="sxs-lookup"><span data-stu-id="1bc32-143">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
