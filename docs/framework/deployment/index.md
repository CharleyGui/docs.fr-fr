---
title: Déploiement d'applications et du .NET Framework
description: Commencez à déployer .NET avec votre application. .NET fournit des applications sans impact, des composants privés par défaut, le partage de code contrôlé, et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: 9948d5313c5168965f3ff991b26a4bc913f7d7ee
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817027"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="9852e-104">Déploiement d'applications et du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9852e-104">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="9852e-105">Cet article est conçu pour vous aider à prendre en main le processus de déploiement du .NET Framework avec votre application.</span><span class="sxs-lookup"><span data-stu-id="9852e-105">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="9852e-106">Les informations fournies sont principalement destinées aux développeurs, aux OEM et aux administrateurs d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9852e-106">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="9852e-107">Les utilisateurs qui souhaitent installer le .NET Framework sur leurs ordinateurs sont invités à lire la page [Installer le .NET Framework](../install/index.md).</span><span class="sxs-lookup"><span data-stu-id="9852e-107">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="9852e-108">Ressources principales de déploiement</span><span class="sxs-lookup"><span data-stu-id="9852e-108">Key Deployment Resources</span></span>

<span data-ttu-id="9852e-109">Utilisez les liens suivants vers d'autres articles MSDN pour obtenir des informations spécifiques sur le déploiement et la maintenance du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9852e-109">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="9852e-110">**Installation et déploiement**</span><span class="sxs-lookup"><span data-stu-id="9852e-110">**Setup and deployment**</span></span>

- <span data-ttu-id="9852e-111">Informations générales relatives au programme d'installation et au déploiement :</span><span class="sxs-lookup"><span data-stu-id="9852e-111">General installer and deployment information:</span></span>

  - <span data-ttu-id="9852e-112">Options du programme d'installation :</span><span class="sxs-lookup"><span data-stu-id="9852e-112">Installer options:</span></span>

    - [<span data-ttu-id="9852e-113">Programme d’installation web</span><span class="sxs-lookup"><span data-stu-id="9852e-113">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="9852e-114">Programme d’installation hors connexion</span><span class="sxs-lookup"><span data-stu-id="9852e-114">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="9852e-115">Modes d'installation :</span><span class="sxs-lookup"><span data-stu-id="9852e-115">Installation modes:</span></span>

    - [<span data-ttu-id="9852e-116">Installation sans assistance</span><span class="sxs-lookup"><span data-stu-id="9852e-116">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="9852e-117">Affichage d’une interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="9852e-117">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="9852e-118">Réduction des redémarrages du système lors des installations .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="9852e-118">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="9852e-119">Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9852e-119">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="9852e-120">Déploiement du .NET Framework avec une application cliente (pour les développeurs) :</span><span class="sxs-lookup"><span data-stu-id="9852e-120">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="9852e-121">[Utilisation d'InstallShield](deployment-guide-for-developers.md#installshield-deployment) dans un projet d'installation et de déploiement</span><span class="sxs-lookup"><span data-stu-id="9852e-121">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="9852e-122">Utilisation d’une application ClickOnce de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9852e-122">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="9852e-123">Création d’un package d’installation WiX</span><span class="sxs-lookup"><span data-stu-id="9852e-123">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="9852e-124">Utilisation d’un programme d’installation personnalisé</span><span class="sxs-lookup"><span data-stu-id="9852e-124">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="9852e-125">[Informations supplémentaires](deployment-guide-for-developers.md) pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="9852e-125">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="9852e-126">Déploiement du .NET Framework (pour les OEM et les administrateurs) :</span><span class="sxs-lookup"><span data-stu-id="9852e-126">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="9852e-127">Kit de déploiement et d’évaluation Windows (ADK)</span><span class="sxs-lookup"><span data-stu-id="9852e-127">Windows Assessment and Deployment Kit (ADK)</span></span>](/windows-hardware/get-started/adk-install)

  - [<span data-ttu-id="9852e-128">Guide de l’administrateur</span><span class="sxs-lookup"><span data-stu-id="9852e-128">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="9852e-129">**Maintenance**</span><span class="sxs-lookup"><span data-stu-id="9852e-129">**Servicing**</span></span>

- <span data-ttu-id="9852e-130">Pour obtenir des informations générales, consultez le [blog .NET Framework](https://devblogs.microsoft.com/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="9852e-130">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="9852e-131">Détection des versions</span><span class="sxs-lookup"><span data-stu-id="9852e-131">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="9852e-132">Détection des Service Packs et des mises à jour</span><span class="sxs-lookup"><span data-stu-id="9852e-132">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="9852e-133">Fonctionnalités d’aide au déploiement</span><span class="sxs-lookup"><span data-stu-id="9852e-133">Features That Simplify Deployment</span></span>

<span data-ttu-id="9852e-134">Le .NET Framework offre de nombreuses fonctionnalités de base qui facilitent le déploiement de vos applications :</span><span class="sxs-lookup"><span data-stu-id="9852e-134">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="9852e-135">Applications sans impact.</span><span class="sxs-lookup"><span data-stu-id="9852e-135">No-impact applications.</span></span>

     <span data-ttu-id="9852e-136">Cette fonctionnalité permet d'isoler les applications et élimine les conflits de DLL.</span><span class="sxs-lookup"><span data-stu-id="9852e-136">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="9852e-137">Par défaut, les composants n'ont pas d'incidence sur d'autres applications.</span><span class="sxs-lookup"><span data-stu-id="9852e-137">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="9852e-138">Composants privés par défaut.</span><span class="sxs-lookup"><span data-stu-id="9852e-138">Private components by default.</span></span>

     <span data-ttu-id="9852e-139">Par défaut, les composants sont déployés dans le répertoire de l'application et sont accessibles uniquement par l'application conteneur.</span><span class="sxs-lookup"><span data-stu-id="9852e-139">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="9852e-140">Partage de code contrôlé.</span><span class="sxs-lookup"><span data-stu-id="9852e-140">Controlled code sharing.</span></span>

     <span data-ttu-id="9852e-141">Avec cette fonctionnalité, vous devez explicitement rendre le code disponible pour le partager (ce n'est plus le comportement par défaut).</span><span class="sxs-lookup"><span data-stu-id="9852e-141">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="9852e-142">Contrôle de version côte à côte.</span><span class="sxs-lookup"><span data-stu-id="9852e-142">Side-by-side versioning.</span></span>

     <span data-ttu-id="9852e-143">Plusieurs versions d'un composant ou d'une application peuvent coexister. Vous pouvez choisir les versions à utiliser et le common language runtime applique la stratégie de contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="9852e-143">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="9852e-144">Déploiement et réplication XCOPY.</span><span class="sxs-lookup"><span data-stu-id="9852e-144">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="9852e-145">Les composants et les applications autodescriptifs et autonomes peuvent être déployés sans entrées de Registre ni dépendances.</span><span class="sxs-lookup"><span data-stu-id="9852e-145">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="9852e-146">Mises à jour instantanées.</span><span class="sxs-lookup"><span data-stu-id="9852e-146">On-the-fly updates.</span></span>

     <span data-ttu-id="9852e-147">Les administrateurs peuvent utiliser des hôtes, tels que ASP.NET, pour mettre à jour les DLL de programmes, y compris sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="9852e-147">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="9852e-148">Intégration avec Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9852e-148">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="9852e-149">Les fonctionnalités de publication, de réparation et d'installation à la demande sont toutes disponibles pendant le déploiement de votre application.</span><span class="sxs-lookup"><span data-stu-id="9852e-149">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="9852e-150">Déploiement d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="9852e-150">Enterprise deployment.</span></span>

     <span data-ttu-id="9852e-151">Cette fonctionnalité permet de distribuer facilement des logiciels, notamment avec Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9852e-151">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="9852e-152">Téléchargement et mise en cache.</span><span class="sxs-lookup"><span data-stu-id="9852e-152">Downloading and caching.</span></span>

     <span data-ttu-id="9852e-153">Les téléchargements incrémentiels permettent de réduire la taille des téléchargements. Les composants peuvent être isolés pour être utilisés uniquement par l'application et garantir ainsi un déploiement à faible impact.</span><span class="sxs-lookup"><span data-stu-id="9852e-153">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="9852e-154">Code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="9852e-154">Partially trusted code.</span></span>

     <span data-ttu-id="9852e-155">L'identité est basée sur le code au lieu de l'utilisateur. Aucune boîte de dialogue de certificat ne s'affiche.</span><span class="sxs-lookup"><span data-stu-id="9852e-155">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="9852e-156">Empaquetage et distribution d'applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9852e-156">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="9852e-157">Certains aspects de l'empaquetage et du déploiement pour le .NET Framework sont traités dans d'autres sections de la documentation.</span><span class="sxs-lookup"><span data-stu-id="9852e-157">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="9852e-158">Ces sections comportent des informations sur les unités autodescriptives appelées [assemblys](../../standard/assembly/index.md), qui ne nécessitent aucune entrée de Registre, les [assemblys portant un nom fort](../../standard/assembly/strong-named.md), qui garantissent l'unicité des noms et empêchent l'usurpation de noms, et le [contrôle de version des assemblys](../../standard/assembly/versioning.md), qui résout de nombreux problèmes liés aux conflits de DLL.</span><span class="sxs-lookup"><span data-stu-id="9852e-158">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="9852e-159">Les sections suivantes fournissent des informations sur l'empaquetage et la distribution d'applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9852e-159">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="9852e-160">Packaging</span><span class="sxs-lookup"><span data-stu-id="9852e-160">Packaging</span></span>

<span data-ttu-id="9852e-161">Le .NET Framework offre les options suivantes pour empaqueter des applications :</span><span class="sxs-lookup"><span data-stu-id="9852e-161">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="9852e-162">Sous forme d'un assembly unique ou d'une collection d'assemblys.</span><span class="sxs-lookup"><span data-stu-id="9852e-162">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="9852e-163">Avec cette option, vous utilisez simplement les fichiers .dll ou .exe tels qu'ils ont été générés.</span><span class="sxs-lookup"><span data-stu-id="9852e-163">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="9852e-164">Sous forme de fichiers CAB.</span><span class="sxs-lookup"><span data-stu-id="9852e-164">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="9852e-165">Avec cette option, vous compressez les fichiers en fichiers .cab pour accélérer la distribution ou le téléchargement.</span><span class="sxs-lookup"><span data-stu-id="9852e-165">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="9852e-166">Sous forme d'un package Windows Installer ou d'un autre format de programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="9852e-166">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="9852e-167">Avec cette option, vous créez des fichiers .msi utilisables avec Windows Installer ou vous empaquetez votre application pour l'utiliser avec un autre programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="9852e-167">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="9852e-168">Distribution</span><span class="sxs-lookup"><span data-stu-id="9852e-168">Distribution</span></span>

<span data-ttu-id="9852e-169">Le .NET Framework offre les options suivantes pour distribuer des applications :</span><span class="sxs-lookup"><span data-stu-id="9852e-169">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="9852e-170">Avec XCOPY ou FTP.</span><span class="sxs-lookup"><span data-stu-id="9852e-170">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="9852e-171">Les applications du common language runtime sont autodescriptives et ne nécessitent aucune entrée de Registre. Vous pouvez donc utiliser XCOPY ou FTP pour copier simplement l'application dans un répertoire approprié.</span><span class="sxs-lookup"><span data-stu-id="9852e-171">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="9852e-172">L'application peut ensuite être exécutée à partir de ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="9852e-172">The application can then be run from that directory.</span></span>

- <span data-ttu-id="9852e-173">Avec le téléchargement de code.</span><span class="sxs-lookup"><span data-stu-id="9852e-173">Use code download.</span></span>

     <span data-ttu-id="9852e-174">Si vous distribuez votre application sur Internet ou via un intranet d'entreprise, vous pouvez simplement télécharger le code sur un ordinateur et exécuter l'application à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9852e-174">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="9852e-175">Avec un programme d'installation (tel que Windows Installer 2.0).</span><span class="sxs-lookup"><span data-stu-id="9852e-175">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="9852e-176">Windows Installer 2.0 permet d'installer, de réparer ou de supprimer des assemblys .NET Framework dans le Global Assembly Cache et dans des répertoires privés.</span><span class="sxs-lookup"><span data-stu-id="9852e-176">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="9852e-177">Emplacement d'installation</span><span class="sxs-lookup"><span data-stu-id="9852e-177">Installation Location</span></span>

<span data-ttu-id="9852e-178">Pour déterminer où déployer les assemblys de votre application afin qu'ils puissent être localisés par le runtime, consultez la page [Méthode de localisation des assemblys par le runtime](how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9852e-178">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="9852e-179">Prenez également en compte les considérations de sécurité dans votre choix de la méthode de déploiement de votre application.</span><span class="sxs-lookup"><span data-stu-id="9852e-179">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="9852e-180">Des autorisations de sécurité sont accordées au code managé en fonction de l'emplacement du code.</span><span class="sxs-lookup"><span data-stu-id="9852e-180">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="9852e-181">Le déploiement d'une application ou d'un composant à un emplacement présentant un niveau de confiance faible (Internet, par exemple) limite les actions réalisables par cette application ou ce composant.</span><span class="sxs-lookup"><span data-stu-id="9852e-181">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="9852e-182">Pour plus d'informations sur le déploiement et la sécurité, consultez la page [Informations de base sur la sécurité d'accès du code](../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="9852e-182">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="9852e-183">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9852e-183">Related Topics</span></span>

|<span data-ttu-id="9852e-184">Intitulé</span><span class="sxs-lookup"><span data-stu-id="9852e-184">Title</span></span>|<span data-ttu-id="9852e-185">Description</span><span class="sxs-lookup"><span data-stu-id="9852e-185">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="9852e-186">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="9852e-186">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="9852e-187">Décrit comment le common language runtime détermine quel assembly utiliser pour répondre à une demande de liaison.</span><span class="sxs-lookup"><span data-stu-id="9852e-187">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="9852e-188">Meilleures pratiques pour le chargement d'assembly</span><span class="sxs-lookup"><span data-stu-id="9852e-188">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="9852e-189">Explique les moyens d'éviter les problèmes d'identités de type qui peuvent générer des exceptions <xref:System.InvalidCastException> et <xref:System.MissingMethodException>, et d'autres erreurs.</span><span class="sxs-lookup"><span data-stu-id="9852e-189">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="9852e-190">Réduction des redémarrages système lors des installations de .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9852e-190">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="9852e-191">Décrit le Gestionnaire de redémarrage qui empêche les redémarrages si possible, et explique les avantages de son utilisation pour les applications qui installent le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9852e-191">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="9852e-192">Guide de déploiement pour les administrateurs</span><span class="sxs-lookup"><span data-stu-id="9852e-192">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="9852e-193">Explique comment un administrateur système peut déployer le .NET Framework et ses dépendances système sur un réseau à l’aide de points de terminaison Microsoft Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9852e-193">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="9852e-194">Guide de déploiement pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="9852e-194">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="9852e-195">Explique comment les développeurs peuvent installer le .NET Framework sur les ordinateurs des utilisateurs avec leurs applications.</span><span class="sxs-lookup"><span data-stu-id="9852e-195">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="9852e-196">Déploiement d’applications, de services et de composants</span><span class="sxs-lookup"><span data-stu-id="9852e-196">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="9852e-197">Présente les différentes options de déploiement dans Visual Studio, y compris les instructions de publication d'une application à l'aide des fonctionnalités ClickOnce et Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9852e-197">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="9852e-198">Publication d'applications ClickOnce</span><span class="sxs-lookup"><span data-stu-id="9852e-198">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="9852e-199">Décrit comment empaqueter une application Windows Forms pour la déployer ensuite avec ClickOnce sur des ordinateurs clients d’un réseau.</span><span class="sxs-lookup"><span data-stu-id="9852e-199">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="9852e-200">Empaquetage et déploiement de ressources</span><span class="sxs-lookup"><span data-stu-id="9852e-200">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="9852e-201">Décrit le modèle « Hub and Spoke » utilisé par le .NET Framework pour empaqueter et déployer des ressources. Fournit des informations sur les conventions de dénomination des ressources, le processus de secours et les alternatives à l'empaquetage.</span><span class="sxs-lookup"><span data-stu-id="9852e-201">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="9852e-202">Déploiement d'une application d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="9852e-202">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="9852e-203">Explique comment livrer et installer des applications Interop, qui comportent généralement un assembly client .NET Framework, un ou plusieurs assemblys d'interopérabilité représentant des bibliothèques de types COM distinctes et un ou plusieurs composants COM inscrits.</span><span class="sxs-lookup"><span data-stu-id="9852e-203">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="9852e-204">Procédure : suivre la progression du programme d’installation de .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="9852e-204">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="9852e-205">Décrit comment lancer et suivre le processus d'installation sans assistance du .NET Framework tout en affichant votre propre vue de la progression de l'installation.</span><span class="sxs-lookup"><span data-stu-id="9852e-205">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9852e-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9852e-206">See also</span></span>

- [<span data-ttu-id="9852e-207">Guide de développement</span><span class="sxs-lookup"><span data-stu-id="9852e-207">Development Guide</span></span>](../development-guide.md)
