---
title: Changements d’exécution et de retargeting - Cadre .NET
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196698"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="7fa44-102">Compatibilité des applications dans le cadre .NET</span><span class="sxs-lookup"><span data-stu-id="7fa44-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="7fa44-103">La compatibilité est un objectif important de chaque version .NET.</span><span class="sxs-lookup"><span data-stu-id="7fa44-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="7fa44-104">La compatibilité garantit que chaque version est additive, de sorte que les versions précédentes continueront à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="7fa44-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="7fa44-105">D’autre part, les modifications apportées aux fonctionnalités précédentes (par exemple, pour améliorer les performances, résoudre les problèmes de sécurité ou corriger les bogues) peuvent causer des problèmes de compatibilité dans le code existant ou les applications existantes qui s’exécutent sous une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="7fa44-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="7fa44-106">Chaque application cible une version spécifique du cadre .NET en :</span><span class="sxs-lookup"><span data-stu-id="7fa44-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="7fa44-107">La définition d’une version cible de .NET Framework dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7fa44-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="7fa44-108">La spécification de la version cible de .NET Framework dans un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="7fa44-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="7fa44-109">L’application d’un <xref:System.Runtime.Versioning.TargetFrameworkAttribute> au code source.</span><span class="sxs-lookup"><span data-stu-id="7fa44-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="7fa44-110">Lors de la migration d’une version du cadre .NET à une autre, il existe deux types de changements à considérer:</span><span class="sxs-lookup"><span data-stu-id="7fa44-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="7fa44-111">Changements d’exécution</span><span class="sxs-lookup"><span data-stu-id="7fa44-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="7fa44-112">Changements de retargeting</span><span class="sxs-lookup"><span data-stu-id="7fa44-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="7fa44-113">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="7fa44-113">Runtime changes</span></span>

<span data-ttu-id="7fa44-114">Les problèmes d’exécution sont ceux qui se posent lorsqu’un nouveau temps d’exécution est placé sur une machine et que le comportement d’une application change.</span><span class="sxs-lookup"><span data-stu-id="7fa44-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="7fa44-115">Lors de l’exécution sur une version plus récente que ce qui a été ciblé, le cadre .NET utilise un comportement *bizarre* pour imiter l’ancienne version ciblée.</span><span class="sxs-lookup"><span data-stu-id="7fa44-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="7fa44-116">L’application s’exécute sur la version la plus récente, mais agit comme si elle est en cours d’exécution sur l’ancienne version.</span><span class="sxs-lookup"><span data-stu-id="7fa44-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="7fa44-117">La plupart des problèmes de compatibilité entre les versions du .NET Framework sont atténués via ce modèle de subterfuge.</span><span class="sxs-lookup"><span data-stu-id="7fa44-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="7fa44-118">Par exemple, si un binaire a été compilé pour .NET Framework 4.0 mais fonctionne sur une machine avec .NET Framework 4.5 ou plus tard, il fonctionne en mode de compatibilité .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="7fa44-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="7fa44-119">Cela signifie que beaucoup de changements dans la version ultérieure n’affectent pas le binaire.</span><span class="sxs-lookup"><span data-stu-id="7fa44-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="7fa44-120">La version du cadre .NET qu’une application cible est déterminée par la version cible de l’assemblage d’entrée pour le domaine d’application dans lequel le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="7fa44-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="7fa44-121">Tous les assemblages supplémentaires chargés dans ce domaine d’application ciblent cette version.</span><span class="sxs-lookup"><span data-stu-id="7fa44-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="7fa44-122">Par exemple, dans le cas d’un exécutable, la version que les cibles exécutables est le mode de compatibilité de tous les assemblages dans ce domaine d’application s’exécutent sous.</span><span class="sxs-lookup"><span data-stu-id="7fa44-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="7fa44-123">Pour voir une liste des modifications d’exécution qui s’appliquent à votre environnement, sélectionnez la version cadre .NET que vous ciblez actuellement, puis la version que vous souhaitez migrer vers :</span><span class="sxs-lookup"><span data-stu-id="7fa44-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="7fa44-124">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="7fa44-124">Retargeting changes</span></span>

<span data-ttu-id="7fa44-125">Les modifications de retargeting sont celles qui surviennent lorsqu’une assemblée est recompilée pour cibler une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="7fa44-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="7fa44-126">Cibler une version plus récente signifie que l’assemblage opte pour les nouvelles fonctionnalités ainsi que les problèmes de compatibilité potentiels pour les anciennes fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="7fa44-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="7fa44-127">Pour voir une liste de modifications de retargeting qui s’appliquent à votre environnement, sélectionnez la version cadre .NET que vous ciblez actuellement, puis la version que vous souhaitez migrer vers :</span><span class="sxs-lookup"><span data-stu-id="7fa44-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="7fa44-128">Classification de l’impact</span><span class="sxs-lookup"><span data-stu-id="7fa44-128">Impact classification</span></span>

<span data-ttu-id="7fa44-129">Dans les sujets qui décrivent les changements de temps d’exécution et de retargeting, par exemple, [les changements de retargeting pour la migration de 4.7.2 à 4.8](retargeting/4.7.2-4.8.md), les éléments individuels sont classés par leur impact prévu comme suit :</span><span class="sxs-lookup"><span data-stu-id="7fa44-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="7fa44-130">**Majeur**</span><span class="sxs-lookup"><span data-stu-id="7fa44-130">**Major**</span></span>\
<span data-ttu-id="7fa44-131">Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code.</span><span class="sxs-lookup"><span data-stu-id="7fa44-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="7fa44-132">**Mineur**</span><span class="sxs-lookup"><span data-stu-id="7fa44-132">**Minor**</span></span>\
<span data-ttu-id="7fa44-133">Modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications du code.</span><span class="sxs-lookup"><span data-stu-id="7fa44-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="7fa44-134">**Cas Edge**</span><span class="sxs-lookup"><span data-stu-id="7fa44-134">**Edge case**</span></span>\
<span data-ttu-id="7fa44-135">Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.</span><span class="sxs-lookup"><span data-stu-id="7fa44-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="7fa44-136">**Transparent**</span><span class="sxs-lookup"><span data-stu-id="7fa44-136">**Transparent**</span></span>\
<span data-ttu-id="7fa44-137">Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application.</span><span class="sxs-lookup"><span data-stu-id="7fa44-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="7fa44-138">L'application n'a pas besoin d'être modifiée en raison de cette modification.</span><span class="sxs-lookup"><span data-stu-id="7fa44-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fa44-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fa44-139">See also</span></span>

- [<span data-ttu-id="7fa44-140">Versions et dépendances</span><span class="sxs-lookup"><span data-stu-id="7fa44-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="7fa44-141">Nouveautés</span><span class="sxs-lookup"><span data-stu-id="7fa44-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="7fa44-142">Ce qui est obsolète</span><span class="sxs-lookup"><span data-stu-id="7fa44-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
