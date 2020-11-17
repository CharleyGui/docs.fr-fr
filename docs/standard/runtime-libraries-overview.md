---
title: Vue d’ensemble des bibliothèques Runtime
description: Découvrez ce qui est inclus dans la section bibliothèques Runtime de la table des matières.
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687893"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="03e2c-103">Vue d’ensemble des bibliothèques Runtime</span><span class="sxs-lookup"><span data-stu-id="03e2c-103">Runtime libraries overview</span></span>

<span data-ttu-id="03e2c-104">Le [Runtime .net](../core/introduction.md#sdk-and-runtimes), qui est installé sur un ordinateur pour une utilisation par les [applications dépendantes du Framework](../core/introduction.md#deployment-models), possède un ensemble standard de bibliothèques de classes, connu sous le nom de [bibliothèques Runtime](glossary.md#runtime), de [bibliothèques d’infrastructure](glossary.md#framework-libraries)ou de la bibliothèque de [classes de base (BCL)](glossary.md#bcl).</span><span class="sxs-lookup"><span data-stu-id="03e2c-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries, known as [runtime libraries](glossary.md#runtime), [framework libraries](glossary.md#framework-libraries), or the [base class library (BCL)](glossary.md#bcl).</span></span> <span data-ttu-id="03e2c-105">En outre, il existe des extensions pour les bibliothèques Runtime, fournies dans les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="03e2c-105">In addition, there are extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="03e2c-106">Ces bibliothèques fournissent des implémentations pour de nombreux types généraux et spécifiques à l’application, des algorithmes et des fonctionnalités d’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="03e2c-106">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="03e2c-107">Bibliothèques Runtime</span><span class="sxs-lookup"><span data-stu-id="03e2c-107">Runtime libraries</span></span>

<span data-ttu-id="03e2c-108">Ces bibliothèques fournissent les types fondamentaux et les fonctionnalités de l’utilitaire et constituent la base de toutes les autres bibliothèques de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="03e2c-108">These libraries provide the foundational types and utility functionality and are the base of all other .NET class libraries.</span></span> <span data-ttu-id="03e2c-109">La <xref:System.String?displayProperty=nameWithType> classe, qui fournit des API pour l’utilisation de chaînes, en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="03e2c-109">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span> <span data-ttu-id="03e2c-110">Les [bibliothèques de sérialisation](serialization/index.md)sont un autre exemple.</span><span class="sxs-lookup"><span data-stu-id="03e2c-110">Another example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="03e2c-111">Extensions des bibliothèques Runtime</span><span class="sxs-lookup"><span data-stu-id="03e2c-111">Extensions to the runtime libraries</span></span>

<span data-ttu-id="03e2c-112">Certaines bibliothèques sont fournies dans les packages NuGet au lieu d’être incluses dans le [Framework partagé](glossary.md#shared-framework)du Runtime.</span><span class="sxs-lookup"><span data-stu-id="03e2c-112">Some libraries are provided in NuGet packages rather than included in the runtime's [shared framework](glossary.md#shared-framework).</span></span> <span data-ttu-id="03e2c-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="03e2c-113">For example:</span></span>

* [<span data-ttu-id="03e2c-114">Logging</span><span class="sxs-lookup"><span data-stu-id="03e2c-114">Logging</span></span>](../core/extensions/logging.md)
* [<span data-ttu-id="03e2c-115">Injection de dépendances</span><span class="sxs-lookup"><span data-stu-id="03e2c-115">Dependency injection</span></span>](../core/extensions/dependency-injection.md)
* [<span data-ttu-id="03e2c-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="03e2c-116">Configuration</span></span>](../core/extensions/configuration.md)

## <a name="see-also"></a><span data-ttu-id="03e2c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03e2c-117">See also</span></span>

* [<span data-ttu-id="03e2c-118">Introduction à .NET</span><span class="sxs-lookup"><span data-stu-id="03e2c-118">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="03e2c-119">Installer le kit de développement logiciel (SDK) .NET ou Runtime</span><span class="sxs-lookup"><span data-stu-id="03e2c-119">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="03e2c-120">Sélectionnez le kit de développement logiciel (SDK) .NET installé ou la version du runtime à utiliser</span><span class="sxs-lookup"><span data-stu-id="03e2c-120">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="03e2c-121">Publier des applications dépendantes du Framework</span><span class="sxs-lookup"><span data-stu-id="03e2c-121">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
