---
title: Vue d’ensemble des bibliothèques Runtime
description: Découvrez ce qui est inclus dans la section bibliothèques Runtime de la table des matières.
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507610"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="ab954-103">Vue d’ensemble des bibliothèques Runtime</span><span class="sxs-lookup"><span data-stu-id="ab954-103">Runtime libraries overview</span></span>

<span data-ttu-id="ab954-104">Le [Runtime .net](../core/introduction.md#sdk-and-runtimes), qui est installé sur un ordinateur pour une utilisation par les [applications dépendantes du Framework](../core/introduction.md#deployment-models), possède un ensemble standard de bibliothèques de classes :</span><span class="sxs-lookup"><span data-stu-id="ab954-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries:</span></span>

* <span data-ttu-id="ab954-105">Ensemble principal, inclus dans le runtime et connu sous le nom de [bibliothèques de classes de base (BCL)](glossary.md#bcl).</span><span class="sxs-lookup"><span data-stu-id="ab954-105">The core set, included in the runtime and known as the [base class libraries (BCL)](glossary.md#bcl).</span></span>
* <span data-ttu-id="ab954-106">Ensemble complet, inclus dans le runtime et connu sous le nom de [bibliothèques d’exécution](glossary.md#runtime) ou de bibliothèques d' [infrastructure](glossary.md#framework).</span><span class="sxs-lookup"><span data-stu-id="ab954-106">The complete set, included in the runtime and known as the [runtime libraries](glossary.md#runtime) or [framework libraries](glossary.md#framework).</span></span>
* <span data-ttu-id="ab954-107">Extensions des bibliothèques Runtime, fournies dans les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="ab954-107">Extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="ab954-108">Ces bibliothèques fournissent des implémentations pour de nombreux types généraux et spécifiques à l’application, des algorithmes et des fonctionnalités d’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="ab954-108">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="base-class-libraries"></a><span data-ttu-id="ab954-109">Bibliothèques de classes de base</span><span class="sxs-lookup"><span data-stu-id="ab954-109">Base class libraries</span></span>

<span data-ttu-id="ab954-110">La bibliothèque de classes de base fournit les types de base et les fonctionnalités de l’utilitaire et constitue la base de toutes les autres bibliothèques de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="ab954-110">The BCL provides the foundational types and utility functionality and is the base of all other .NET class libraries.</span></span> <span data-ttu-id="ab954-111">La <xref:System.String?displayProperty=nameWithType> classe, qui fournit des API pour l’utilisation de chaînes, en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="ab954-111">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="ab954-112">Bibliothèques Runtime</span><span class="sxs-lookup"><span data-stu-id="ab954-112">Runtime libraries</span></span>

<span data-ttu-id="ab954-113">Également appelés bibliothèques d’infrastructure, les bibliothèques Runtime s’appuient sur la BCL pour fournir des API utilitaire pour les tâches courantes.</span><span class="sxs-lookup"><span data-stu-id="ab954-113">Also known as the framework libraries, the runtime libraries build on the BCL to provide utility APIs for common tasks.</span></span> <span data-ttu-id="ab954-114">Les [bibliothèques de sérialisation](serialization/index.md)en sont un exemple.</span><span class="sxs-lookup"><span data-stu-id="ab954-114">An example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="ab954-115">Extensions des bibliothèques Runtime</span><span class="sxs-lookup"><span data-stu-id="ab954-115">Extensions to the runtime libraries</span></span>

<span data-ttu-id="ab954-116">Certaines des bibliothèques Runtime sont fournies dans les packages NuGet au lieu d’être intégrées au runtime qui est installé pour les applications dépendantes du Framework.</span><span class="sxs-lookup"><span data-stu-id="ab954-116">Some of the runtime libraries are provided in NuGet packages rather than built-in to the runtime that is installed for framework-dependent apps.</span></span> <span data-ttu-id="ab954-117">L' [API de journalisation .net](../core/extensions/logging.md)en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="ab954-117">An example is the [.NET Logging API](../core/extensions/logging.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab954-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab954-118">See also</span></span>

* [<span data-ttu-id="ab954-119">Introduction à .NET</span><span class="sxs-lookup"><span data-stu-id="ab954-119">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="ab954-120">Installer le kit de développement logiciel (SDK) .NET ou Runtime</span><span class="sxs-lookup"><span data-stu-id="ab954-120">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="ab954-121">Sélectionnez le kit de développement logiciel (SDK) .NET installé ou la version du runtime à utiliser</span><span class="sxs-lookup"><span data-stu-id="ab954-121">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="ab954-122">Publier des applications dépendantes du Framework</span><span class="sxs-lookup"><span data-stu-id="ab954-122">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
