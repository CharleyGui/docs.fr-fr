---
title: Documentation de .NET Framework
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5a86b3abf821a37944a0e478d0bc8f1bea31ccb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699053"
---
# <a name="net-framework-guide"></a><span data-ttu-id="47e0b-102">Guide du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47e0b-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="47e0b-103">Dans cette documentation du .NET Framework, vous trouverez des informations relatives aux versions 4.5 à 4.8.</span><span class="sxs-lookup"><span data-stu-id="47e0b-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="47e0b-104">Pour télécharger le .NET Framework, consultez [Installation du .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="47e0b-105">Pour obtenir la liste des nouvelles fonctionnalités et des modifications apportées au .NET Framework, consultez [Nouveautés du .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="47e0b-106">Pour obtenir la liste des plateformes prises en charge, consultez la [Configuration requise pour .NET Framework](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="47e0b-107">Pour obtenir une documentation sur les versions antérieures du .NET Framework, consultez la [documentation des versions précédentes de .NET](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="47e0b-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="47e0b-108">Le .NET Framework est une plateforme de développement permettant de générer des applications pour le web, Windows, Windows Phone, Windows Server et Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="47e0b-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="47e0b-109">Il se compose du common language runtime (CLR) et de la bibliothèque de classes .NET Framework, qui offre une vaste gamme de fonctionnalités et prend en charge de nombreux standards.</span><span class="sxs-lookup"><span data-stu-id="47e0b-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="47e0b-110">Le .NET Framework propose plusieurs services, notamment la gestion de la mémoire, la cohérence des types, la sûreté de la mémoire, la sécurité, la mise en réseau et le déploiement d’applications.</span><span class="sxs-lookup"><span data-stu-id="47e0b-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="47e0b-111">Il fournit des structures de données et des API faciles à utiliser qui permettent d’abstraire le système d’exploitation Windows de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="47e0b-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="47e0b-112">Vous pouvez utiliser différents langages de programmation avec le .NET Framework, notamment C#, F# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="47e0b-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="47e0b-113">Pour une présentation générale du .NET Framework à destination des utilisateurs et des développeurs, consultez [Bien démarrer](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="47e0b-114">Pour une présentation de l’architecture et des fonctionnalités clés du .NET Framework, consultez la [vue d’ensemble](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="47e0b-115">Vous pouvez utiliser le .NET Framework avec Docker et des [conteneurs Windows](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="47e0b-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="47e0b-116">Installation</span><span class="sxs-lookup"><span data-stu-id="47e0b-116">Installation</span></span>

<span data-ttu-id="47e0b-117">Le .NET Framework étant fourni avec Windows, vous pouvez exécuter des applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47e0b-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="47e0b-118">Toutefois, vous aurez peut-être besoin d’une version du .NET Framework plus récente que celle fournie avec votre version de Windows.</span><span class="sxs-lookup"><span data-stu-id="47e0b-118">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="47e0b-119">Pour plus d'informations, voir [Installer le .NET Framework sur Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="47e0b-120">Pour savoir comment réparer votre installation du .NET Framework si vous rencontrez des erreurs pendant l’installation, consultez [Réparer le .NET Framework](./install/repair.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="47e0b-121">Pour plus d’informations détaillées sur le téléchargement du .NET Framework, consultez [Installer le .NET Framework pour les développeurs](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="47e0b-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="47e0b-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="47e0b-122">In this section</span></span>

* [<span data-ttu-id="47e0b-123">Nouveautés</span><span class="sxs-lookup"><span data-stu-id="47e0b-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="47e0b-124">Décrit les nouvelles fonctionnalités et modifications clés des dernières versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47e0b-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="47e0b-125">Inclut les listes des types et membres obsolètes et fournit un guide pour la migration de vos applications à partir de la version antérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47e0b-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="47e0b-126">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="47e0b-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="47e0b-127">Fournit une vue d'ensemble complète du .NET Framework et des liens vers des ressources supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="47e0b-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="47e0b-128">Guide d’installation</span><span class="sxs-lookup"><span data-stu-id="47e0b-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="47e0b-129">Fournit les ressources et les conseils sur l’installation et la résolution des problèmes de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47e0b-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="47e0b-130">Guide de migration</span><span class="sxs-lookup"><span data-stu-id="47e0b-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="47e0b-131">Fournit les ressources et la liste des modifications dont vous devez tenir compte si vous migrez votre application vers une nouvelle version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47e0b-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="47e0b-132">Guide de développement</span><span class="sxs-lookup"><span data-stu-id="47e0b-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="47e0b-133">Fournit un guide sur tous les domaines technologiques clés et les tâches relatives au développement d’applications, notamment la création, la configuration, le débogage, la sécurisation et le déploiement de votre application, ainsi que des informations sur la programmation dynamique, l’interopérabilité, l’extensibilité, la gestion de mémoire et les threads.</span><span class="sxs-lookup"><span data-stu-id="47e0b-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="47e0b-134">Outils</span><span class="sxs-lookup"><span data-stu-id="47e0b-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="47e0b-135">Décrit les outils qui permettent de développer, de configurer et de déployer des applications à l'aide des technologies .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47e0b-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="47e0b-136">API et bibliothèques de classes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="47e0b-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="47e0b-137">Fournit la documentation des API .NET Framework privées utilisées par les outils Microsoft.</span><span class="sxs-lookup"><span data-stu-id="47e0b-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="47e0b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47e0b-138">See also</span></span>

- [<span data-ttu-id="47e0b-139">Bibliothèque de classes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47e0b-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
