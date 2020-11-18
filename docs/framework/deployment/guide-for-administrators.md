---
title: Guide de déploiement du .NET Framework pour les administrateurs
description: Lisez le Guide de déploiement de .NET pour les administrateurs. Utilisez ces informations pour déployer .NET version 4,5 et ses dépendances système sur un réseau.
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: 12076334d3ede0c8ab9b618ba2018f23c9fc6ae4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817092"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="54147-104">Guide de déploiement du .NET Framework pour les administrateurs</span><span class="sxs-lookup"><span data-stu-id="54147-104">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="54147-105">Cet article décrit étape par étape comment un administrateur système peut déployer .NET Framework 4,5 et ses dépendances système sur un réseau à l’aide de Configuration Manager de point de terminaison Microsoft.</span><span class="sxs-lookup"><span data-stu-id="54147-105">This step-by-step article describes how a system administrator can deploy .NET Framework 4.5 and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="54147-106">Cet article suppose que tous les ordinateurs clients cibles respectent la configuration minimale requise pour .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54147-106">This article assumes that all target client computers meet the minimum requirements for .NET Framework.</span></span> <span data-ttu-id="54147-107">Pour obtenir la liste des configurations logicielle et matérielle requises pour l’installation de .NET Framework 4,5, consultez [Configuration système requise](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54147-107">For a list of the software and hardware requirements for installing .NET Framework 4.5, see [System Requirements](../get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="54147-108">Les logiciels référencés dans ce document, y compris, sans limitation, .NET Framework 4,5, Configuration Manager et Active Directory, sont soumis aux termes et conditions du contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="54147-108">The software referenced in this document, including, without limitation, .NET Framework 4.5, Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="54147-109">Les présentes instructions supposent que lesdits termes et conditions du contrat de licence ont été passés en revue et acceptés par les propriétaires de licences des logiciels concernés.</span><span class="sxs-lookup"><span data-stu-id="54147-109">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="54147-110">Ces instructions ne remplacent pas les termes et conditions desdits contrats de licence.</span><span class="sxs-lookup"><span data-stu-id="54147-110">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="54147-111">Pour plus d’informations sur la prise en charge de .NET Framework, consultez [.NET Framework stratégie de support officielle](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) sur le site Web Support Microsoft.</span><span class="sxs-lookup"><span data-stu-id="54147-111">For information about support for .NET Framework, see [.NET Framework official support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) on the Microsoft Support website.</span></span>

<span data-ttu-id="54147-112">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="54147-112">This topic contains the following sections:</span></span>

- [<span data-ttu-id="54147-113">Processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="54147-113">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="54147-114">Déploiement de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54147-114">Deploying .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="54147-115">Création d'une collection</span><span class="sxs-lookup"><span data-stu-id="54147-115">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="54147-116">Créer un package et un programme</span><span class="sxs-lookup"><span data-stu-id="54147-116">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="54147-117">Sélectionner un point de distribution</span><span class="sxs-lookup"><span data-stu-id="54147-117">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="54147-118">Déploiement du package</span><span class="sxs-lookup"><span data-stu-id="54147-118">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="54147-119">Ressources</span><span class="sxs-lookup"><span data-stu-id="54147-119">Resources</span></span>](#resources)
- [<span data-ttu-id="54147-120">Dépannage</span><span class="sxs-lookup"><span data-stu-id="54147-120">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="54147-121">Processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="54147-121">The deployment process</span></span>

<span data-ttu-id="54147-122">Lorsque l’infrastructure de prise en charge est en place, vous utilisez Configuration Manager pour déployer le .NET Framework package redistribuable sur les ordinateurs du réseau.</span><span class="sxs-lookup"><span data-stu-id="54147-122">When you have the supporting infrastructure in place, you use Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="54147-123">Générer l’infrastructure implique la création et la définition de cinq éléments principaux : les regroupements, un package et un programme pour les logiciels, des points de distribution et des déploiements.</span><span class="sxs-lookup"><span data-stu-id="54147-123">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="54147-124">Les **regroupements** sont des groupes de ressources de Configuration Manager, tels que des utilisateurs, des groupes d’utilisateurs ou des ordinateurs, sur lesquels .NET Framework est déployé.</span><span class="sxs-lookup"><span data-stu-id="54147-124">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which .NET Framework is deployed.</span></span> <span data-ttu-id="54147-125">Pour plus d’informations, consultez [Présentation des regroupements dans Configuration Manager](/configmgr/core/clients/manage/collections/introduction-to-collections) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="54147-125">For more information, see [Introduction to collections in Configuration Manager](/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="54147-126">Les **packages et programmes** sont généralement les applications logicielles à installer sur un ordinateur client, mais ils peuvent également contenir des fichiers individuels, des mises à jour, ou même des commandes individuelles.</span><span class="sxs-lookup"><span data-stu-id="54147-126">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="54147-127">Pour plus d’informations, consultez [packages et programmes dans Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="54147-127">For more information, see [Packages and programs in Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="54147-128">Les **points de distribution** sont des rôles de système de site Configuration Manager qui stockent les fichiers requis pour l’exécution des logiciels sur les ordinateurs clients.</span><span class="sxs-lookup"><span data-stu-id="54147-128">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="54147-129">Lorsque le client Configuration Manager reçoit et traite un déploiement de logiciel, il contacte un point de distribution pour télécharger le contenu associé au logiciel et démarrer le processus d'installation.</span><span class="sxs-lookup"><span data-stu-id="54147-129">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="54147-130">Pour plus d’informations, consultez [Concepts fondamentaux de la gestion de contenu dans Configuration Manager](/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) dans la bibliothèque de la documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="54147-130">For more information, see [Fundamental concepts for content management in Configuration Manager](/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="54147-131">Les **déploiements** font en sorte que les membres applicables du regroupement cible spécifié installent le package logiciel.</span><span class="sxs-lookup"><span data-stu-id="54147-131">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="54147-132">Les procédures de cette rubrique contiennent les paramètres classiques pour créer et déployer un package et un programme, et ne couvrent pas tous les paramètres possibles.</span><span class="sxs-lookup"><span data-stu-id="54147-132">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="54147-133">Pour d’autres options de déploiement de Configuration Manager, consultez la [Bibliothèque de documentation Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682041(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="54147-133">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](/previous-versions/system-center/system-center-2012-R2/gg682041(v=technet.10)).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-net-framework"></a><span data-ttu-id="54147-134">Déploiement de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="54147-134">Deploying .NET Framework</span></span>

<span data-ttu-id="54147-135">Vous pouvez utiliser Configuration Manager pour déployer une installation sans assistance de .NET Framework 4,5, où les utilisateurs n’interagissent pas avec le processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="54147-135">You can use Configuration Manager to deploy a silent installation of .NET Framework 4.5, where the users do not interact with the installation process.</span></span> <span data-ttu-id="54147-136">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="54147-136">Follow these steps:</span></span>

1. <span data-ttu-id="54147-137">[Créer une collection](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="54147-137">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="54147-138">[Créez un package et un programme pour le package redistribuable .Net Framework](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="54147-138">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="54147-139">[Sélectionnez un point de distribution](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="54147-139">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="54147-140">[Déployez le package](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="54147-140">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="54147-141">Création d'une collection</span><span class="sxs-lookup"><span data-stu-id="54147-141">Create a collection</span></span>

<span data-ttu-id="54147-142">Dans cette étape, sélectionnez les ordinateurs sur lesquels seront déployés le package et le programme, et regroupez-les dans un regroupement de périphériques.</span><span class="sxs-lookup"><span data-stu-id="54147-142">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="54147-143">Pour créer un regroupement dans Configuration Manager, utilisez des règles d’adhésion directes (où les membres du regroupement sont spécifiés manuellement) ou des règles de requête (où Configuration Manager détermine les membres du regroupement selon des critères que vous avez spécifiés).</span><span class="sxs-lookup"><span data-stu-id="54147-143">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="54147-144">Pour plus d’informations sur les règles d’adhésion, notamment les requêtes et les règles directes, consultez [Présentation des regroupements dans Configuration Manager](/configmgr/core/clients/manage/collections/introduction-to-collections) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="54147-144">For more information about membership rules, including queries and direct rules, see [Introduction to collections in Configuration Manager](/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="54147-145">Pour créer une collection :</span><span class="sxs-lookup"><span data-stu-id="54147-145">To create a collection:</span></span>

1. <span data-ttu-id="54147-146">Dans la console Configuration Manager, choisissez **Ressources et Conformité**.</span><span class="sxs-lookup"><span data-stu-id="54147-146">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="54147-147">Dans l’espace de travail **Ressources et Conformité**, choisissez **Regroupements de périphériques**.</span><span class="sxs-lookup"><span data-stu-id="54147-147">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="54147-148">Sous l’onglet **Accueil** dans le groupe **Créer**, choisissez **Créer un regroupement de périphériques**.</span><span class="sxs-lookup"><span data-stu-id="54147-148">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="54147-149">Dans la page **Général** de l’**Assistant Création d’un regroupement de périphériques**, entrez un nom pour le regroupement.</span><span class="sxs-lookup"><span data-stu-id="54147-149">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="54147-150">Choisissez **Parcourir** pour spécifier un regroupement limité.</span><span class="sxs-lookup"><span data-stu-id="54147-150">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="54147-151">Dans la page **Règles d’adhésion**, choisissez **Ajouter une règle**, puis **Règle directe** pour ouvrir l’**Assistant Création d’une règle d’adhésion directe**.</span><span class="sxs-lookup"><span data-stu-id="54147-151">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="54147-152">Choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-152">Choose **Next**.</span></span>

7. <span data-ttu-id="54147-153">Dans la page **Rechercher des ressources**, dans la liste **Classe de ressource**, choisissez **Ressource système**.</span><span class="sxs-lookup"><span data-stu-id="54147-153">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="54147-154">Dans la liste **Nom de l’attribut**, choisissez **Nom**.</span><span class="sxs-lookup"><span data-stu-id="54147-154">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="54147-155">Dans le champ **Valeur**, entrez `%` et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-155">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="54147-156">Dans la page **Sélectionner les ressources**, cochez la case de chaque ordinateur sur lequel vous souhaitez déployer le .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="54147-156">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="54147-157">Choisissez **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="54147-157">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="54147-158">Dans la page **Règles d’adhésion** de l’**Assistant Création d’un regroupement de périphériques**, choisissez **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="54147-158">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="54147-159">Créer un package et un programme pour le package redistribuable .Net Framework</span><span class="sxs-lookup"><span data-stu-id="54147-159">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="54147-160">Les étapes suivantes permettent de créer manuellement un package pour le package redistribuable .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54147-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="54147-161">Le package contient les paramètres spécifiés pour l’installation de .NET Framework et l’emplacement à partir duquel le package sera distribué aux ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="54147-161">The package contains the specified parameters for installing .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="54147-162">Pour créer un package :</span><span class="sxs-lookup"><span data-stu-id="54147-162">To create a package:</span></span>

1. <span data-ttu-id="54147-163">Dans la console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="54147-163">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="54147-164">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="54147-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="54147-165">Sous l’onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer un package**.</span><span class="sxs-lookup"><span data-stu-id="54147-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="54147-166">Dans la page **Package** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="54147-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="54147-167">Nom : `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="54147-167">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="54147-168">Fabricant : `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="54147-168">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="54147-169">Langue :</span><span class="sxs-lookup"><span data-stu-id="54147-169">Language.</span></span> `English (US)`

5. <span data-ttu-id="54147-170">Choisissez **Ce package contient des fichiers sources**, puis **Parcourir** pour sélectionner le dossier local ou réseau qui contient les fichiers d’installation du .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="54147-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="54147-171">Quand vous avez sélectionné le dossier, choisissez **OK**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="54147-172">Dans la page **Type de programme** de l’Assistant, choisissez **Programme standard**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="54147-173">Dans la page **Programme** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="54147-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="54147-174">**Nom :**`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="54147-174">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="54147-175">**Ligne de commande :** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (les options de ligne de commande sont décrites dans le tableau après ces étapes)</span><span class="sxs-lookup"><span data-stu-id="54147-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="54147-176">**Exécuter :** choisissez **Masqué**.</span><span class="sxs-lookup"><span data-stu-id="54147-176">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="54147-177">**Le programme peut s’exécuter :** sélectionnez l’option qui spécifie que le programme peut s’exécuter que l’utilisateur soit connecté ou non.</span><span class="sxs-lookup"><span data-stu-id="54147-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="54147-178">Dans la page **Exigences**, acceptez les valeurs par défaut en choisissant **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="54147-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="54147-179">Le tableau suivant décrit les options de ligne de commande spécifiées dans l'étape 7.</span><span class="sxs-lookup"><span data-stu-id="54147-179">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="54147-180">Option</span><span class="sxs-lookup"><span data-stu-id="54147-180">Option</span></span>|<span data-ttu-id="54147-181">Description</span><span class="sxs-lookup"><span data-stu-id="54147-181">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="54147-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="54147-182">**/q**</span></span>|<span data-ttu-id="54147-183">Active le mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="54147-183">Sets quiet mode.</span></span> <span data-ttu-id="54147-184">Aucune entrée d'utilisateur n'est requise, et aucun résultat n'est affiché.</span><span class="sxs-lookup"><span data-stu-id="54147-184">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="54147-185">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="54147-185">**/norestart**</span></span>|<span data-ttu-id="54147-186">Empêche le programme d'installation de redémarrer automatiquement.</span><span class="sxs-lookup"><span data-stu-id="54147-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="54147-187">Si vous utilisez cette option, Configuration Manager doit gérer le redémarrage de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="54147-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="54147-188">**/chainingpackage** *nom_package*</span><span class="sxs-lookup"><span data-stu-id="54147-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="54147-189">Spécifie le nom du package qui effectue le chaînage.</span><span class="sxs-lookup"><span data-stu-id="54147-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="54147-190">Ces informations sont stockées avec d'autres informations de session d'installation pour les personnes inscrites au Programme d'amélioration du produit Microsoft (CEIP).</span><span class="sxs-lookup"><span data-stu-id="54147-190">This information is reported with other installation session information for those who have signed up for the Microsoft Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="54147-191">Si le nom du package inclut des espaces, utilisez des guillemets doubles comme délimiteurs. Par exemple : **/chainingpackage "Chaining Product"**.</span><span class="sxs-lookup"><span data-stu-id="54147-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="54147-192">Les étapes suivantes créent un package nommé .Net Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="54147-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="54147-193">Le programme déploie une installation sans assistance de .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="54147-193">The program deploys a silent installation of .NET Framework 4.5.</span></span> <span data-ttu-id="54147-194">Dans une installation sans assistance, les utilisateurs n’interagissent pas avec le processus d’installation et l’application de chaînage doit capturer le code de retour et gérer le redémarrage. Pour plus d’informations, consultez [Getting Progress Information from an Installation Package](/previous-versions/cc825975(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="54147-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](/previous-versions/cc825975(v=vs.100)).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="54147-195">Sélectionner un point de distribution</span><span class="sxs-lookup"><span data-stu-id="54147-195">Select a distribution point</span></span>

<span data-ttu-id="54147-196">Pour distribuer le package et le programme aux ordinateurs clients à partir d'un serveur, vous devez d'abord désigner un système de site comme un point de distribution, puis distribuer le package au point de distribution.</span><span class="sxs-lookup"><span data-stu-id="54147-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="54147-197">Utilisez les étapes suivantes pour sélectionner un point de distribution pour le package de .Net Framework 4.5 créé au cours la section précédente :</span><span class="sxs-lookup"><span data-stu-id="54147-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="54147-198">Dans la console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="54147-198">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="54147-199">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="54147-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="54147-200">Dans la liste de packages, sélectionnez le package **.Net Framework 4.5** créé dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="54147-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="54147-201">Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Distribuer du contenu**.</span><span class="sxs-lookup"><span data-stu-id="54147-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="54147-202">Sous l’onglet **Général** de l’**Assistant Distribuer du contenu**, choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="54147-203">Dans la page **Destination du contenu** de l’Assistant, choisissez **Ajouter**, puis **Point de distribution**.</span><span class="sxs-lookup"><span data-stu-id="54147-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="54147-204">Dans la boîte de dialogue **Ajouter des points de distribution**, sélectionnez les points de distribution qui hébergeront le package et le programme, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="54147-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="54147-205">Effectuez toutes les étapes de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="54147-205">Complete the wizard.</span></span>

<span data-ttu-id="54147-206">Le package contient désormais toutes les informations dont vous avez besoin pour déployer sans assistance .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="54147-206">The package now contains all the information you need to silently deploy .NET Framework 4.5.</span></span> <span data-ttu-id="54147-207">Avant de déployer le package et le programme, vérifiez qu’il a été installé sur le point de distribution. consultez la section « surveillance de l’état du contenu » de la page [surveiller le contenu que vous distribuez avec Configuration Manager](/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="54147-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Content status monitoring" section of [Monitor content you distribute with Configuration Manager](/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="54147-208">Déploiement du package</span><span class="sxs-lookup"><span data-stu-id="54147-208">Deploy the package</span></span>

<span data-ttu-id="54147-209">Pour déployer le package et le programme .Net Framework 4.5 :</span><span class="sxs-lookup"><span data-stu-id="54147-209">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="54147-210">Dans la console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="54147-210">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="54147-211">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="54147-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="54147-212">Dans la liste des packages, sélectionnez le package que vous avez créé, appelé **.Net Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="54147-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="54147-213">Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="54147-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="54147-214">Dans la page **Général** de l’**Assistant Déploiement logiciel**, choisissez **Parcourir**, puis sélectionnez le regroupement créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="54147-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="54147-215">Choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-215">Choose **Next**.</span></span>

6. <span data-ttu-id="54147-216">Dans la page **Contenu** de l’Assistant, vérifiez que le point à partir duquel vous souhaitez distribuer le logiciel s’affiche, puis choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="54147-217">Dans la page **Paramètres de déploiement** de l’Assistant, vérifiez que **Action** est défini sur **Installer**, et **Objectif** sur **Requis**.</span><span class="sxs-lookup"><span data-stu-id="54147-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="54147-218">Cela garantit que le package logiciel est une installation obligatoire sur les ordinateurs ciblés.</span><span class="sxs-lookup"><span data-stu-id="54147-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="54147-219">Choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-219">Choose **Next**.</span></span>

8. <span data-ttu-id="54147-220">Sur la page **planification** de l’Assistant, spécifiez quand vous souhaitez installer .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54147-220">On the **Scheduling** page of the wizard, specify when you want .NET Framework to be installed.</span></span> <span data-ttu-id="54147-221">Choisissez **Nouveau** pour déterminer le moment de l’installation, ou demandez au logiciel d’effectuer l’installation quand l’utilisateur se connecte ou se déconnecte, ou dès que possible.</span><span class="sxs-lookup"><span data-stu-id="54147-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="54147-222">Choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-222">Choose **Next**.</span></span>

9. <span data-ttu-id="54147-223">Dans la page **Expérience utilisateur** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="54147-224">Il est possible que votre environnement de production ait des stratégies qui requièrent des sélections différentes pour la planification de déploiement.</span><span class="sxs-lookup"><span data-stu-id="54147-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span>

10. <span data-ttu-id="54147-225">Dans la page **Points de distribution** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="54147-225">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="54147-226">Effectuez toutes les étapes de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="54147-226">Complete the wizard.</span></span> <span data-ttu-id="54147-227">Vous pouvez surveiller la progression du déploiement dans le nœud **Déploiements** de l’espace de travail **Surveillance**.</span><span class="sxs-lookup"><span data-stu-id="54147-227">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="54147-228">Le package est déployé dans le regroupement ciblé et l’installation sans assistance du .Net Framework 4.5 peut commencer.</span><span class="sxs-lookup"><span data-stu-id="54147-228">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="54147-229">Pour plus d’informations sur les codes d’erreur liés à l’installation du .NET Framework 4.5, consultez la section [Codes de retour](#return_codes) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="54147-229">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="54147-230">Ressources</span><span class="sxs-lookup"><span data-stu-id="54147-230">Resources</span></span>

<span data-ttu-id="54147-231">Pour plus d’informations sur l’infrastructure pour tester le déploiement du package redistribuable de .NET Framework 4.5, consultez les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="54147-231">For more information about the infrastructure for testing the deployment of the .NET Framework 4.5 redistributable package, see the following resources.</span></span>

<span data-ttu-id="54147-232">**Active Directory, DNS, DHCP :**</span><span class="sxs-lookup"><span data-stu-id="54147-232">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="54147-233">Services de domaine Active Directory</span><span class="sxs-lookup"><span data-stu-id="54147-233">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="54147-234">DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="54147-234">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="54147-235">Protocole DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="54147-235">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="54147-236">**SQL Server 2008 :**</span><span class="sxs-lookup"><span data-stu-id="54147-236">**SQL Server 2008:**</span></span>

- <span data-ttu-id="54147-237">[Installer SQL Server 2008 (vidéo SQL Server)](/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="54147-237">[Installing SQL Server 2008 (SQL Server Video)](/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="54147-238">Vue d’ensemble de la sécurité SQL Server 2008 pour les administrateurs de base de données</span><span class="sxs-lookup"><span data-stu-id="54147-238">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="54147-239">**System Center 2012 Configuration Manager (point de gestion, point de distribution) :**</span><span class="sxs-lookup"><span data-stu-id="54147-239">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- <span data-ttu-id="54147-240">[Administration de site pour System Center 2012 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg681983(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="54147-240">[Site Administration for System Center 2012 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg681983(v=technet.10))</span></span>

<span data-ttu-id="54147-241">**Client System Center 2012 Configuration Manager pour ordinateurs Windows :**</span><span class="sxs-lookup"><span data-stu-id="54147-241">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- <span data-ttu-id="54147-242">[Déployer des clients pour System Center 2012 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699391(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="54147-242">[Deploying Clients for System Center 2012 Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg699391(v=technet.10))</span></span>

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="54147-243">Dépannage</span><span class="sxs-lookup"><span data-stu-id="54147-243">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="54147-244">Emplacements des fichiers journaux</span><span class="sxs-lookup"><span data-stu-id="54147-244">Log file locations</span></span>

<span data-ttu-id="54147-245">Les fichiers journaux suivants sont générés lors de l’installation du .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="54147-245">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="54147-246">%temp%\Microsoft .NET Framework *version* \* . txt</span><span class="sxs-lookup"><span data-stu-id="54147-246">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="54147-247">%temp%\Microsoft .NET Framework *version* \* . html</span><span class="sxs-lookup"><span data-stu-id="54147-247">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="54147-248">où *version* est la version de .NET Framework que vous installez, par exemple 4,5 ou 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="54147-248">where *version* is the version of .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="54147-249">Vous pouvez également spécifier le répertoire où les fichiers journaux sont écrits avec l’option de ligne de commande `/log` dans la commande d’installation du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54147-249">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="54147-250">Pour plus d’informations, consultez [Guide de déploiement du .NET Framework pour les développeurs](deployment-guide-for-developers.md#command-line-options).</span><span class="sxs-lookup"><span data-stu-id="54147-250">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="54147-251">Vous pouvez utiliser [l’outil de collecte des journaux](https://www.microsoft.com/download/details.aspx?id=12493) pour collecter les fichiers journaux du .NET Framework et créer un fichier CAB compressé (.cab) afin de réduire la taille des fichiers.</span><span class="sxs-lookup"><span data-stu-id="54147-251">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="54147-252">Codes de retour</span><span class="sxs-lookup"><span data-stu-id="54147-252">Return codes</span></span>

<span data-ttu-id="54147-253">Le tableau suivant liste les codes de retour les plus courants du programme d’installation du package redistribuable de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="54147-253">The following table lists the most common return codes from the .NET Framework 4.5 redistributable installation program.</span></span> <span data-ttu-id="54147-254">Les codes de retour sont identiques pour toutes les versions du programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="54147-254">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="54147-255">Pour plus d’informations, consultez la section suivante : [Codes d’erreur de téléchargement](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="54147-255">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="54147-256">Code de retour</span><span class="sxs-lookup"><span data-stu-id="54147-256">Return code</span></span>|<span data-ttu-id="54147-257">Description</span><span class="sxs-lookup"><span data-stu-id="54147-257">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="54147-258">0</span><span class="sxs-lookup"><span data-stu-id="54147-258">0</span></span>|<span data-ttu-id="54147-259">Installation terminée.</span><span class="sxs-lookup"><span data-stu-id="54147-259">Installation completed successfully.</span></span>|
|<span data-ttu-id="54147-260">1602</span><span class="sxs-lookup"><span data-stu-id="54147-260">1602</span></span>|<span data-ttu-id="54147-261">L'utilisateur a annulé l'installation.</span><span class="sxs-lookup"><span data-stu-id="54147-261">The user canceled installation.</span></span>|
|<span data-ttu-id="54147-262">1603</span><span class="sxs-lookup"><span data-stu-id="54147-262">1603</span></span>|<span data-ttu-id="54147-263">Une erreur irrécupérable s’est produite pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="54147-263">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="54147-264">1641</span><span class="sxs-lookup"><span data-stu-id="54147-264">1641</span></span>|<span data-ttu-id="54147-265">Un redémarrage est nécessaire pour terminer l'installation.</span><span class="sxs-lookup"><span data-stu-id="54147-265">A restart is required to complete the installation.</span></span> <span data-ttu-id="54147-266">Ce message indique que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="54147-266">This message indicates success.</span></span>|
|<span data-ttu-id="54147-267">3010</span><span class="sxs-lookup"><span data-stu-id="54147-267">3010</span></span>|<span data-ttu-id="54147-268">Un redémarrage est nécessaire pour terminer l'installation.</span><span class="sxs-lookup"><span data-stu-id="54147-268">A restart is required to complete the installation.</span></span> <span data-ttu-id="54147-269">Ce message indique que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="54147-269">This message indicates success.</span></span>|
|<span data-ttu-id="54147-270">5100</span><span class="sxs-lookup"><span data-stu-id="54147-270">5100</span></span>|<span data-ttu-id="54147-271">L'ordinateur de l'utilisateur n'a pas la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="54147-271">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="54147-272">Codes d'erreur de téléchargement</span><span class="sxs-lookup"><span data-stu-id="54147-272">Download error codes</span></span>

- [<span data-ttu-id="54147-273">Codes d’erreur du service de transfert intelligent en arrière-plan (BITS)</span><span class="sxs-lookup"><span data-stu-id="54147-273">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- <span data-ttu-id="54147-274">[Codes d’erreur du moniker d’URL](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="54147-274">[URL moniker error codes](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145(v=vs.85))</span></span>

- [<span data-ttu-id="54147-275">Codes d’erreur WinHttp</span><span class="sxs-lookup"><span data-stu-id="54147-275">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="54147-276">Autres codes d'erreur :</span><span class="sxs-lookup"><span data-stu-id="54147-276">Other error codes:</span></span>

- [<span data-ttu-id="54147-277">Codes d’erreur Windows Installer</span><span class="sxs-lookup"><span data-stu-id="54147-277">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="54147-278">[Codes de résultat de l’agent de mise à jour automatique Windows Update](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="54147-278">[Windows Update Agent result codes](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="54147-279">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54147-279">See also</span></span>

- [<span data-ttu-id="54147-280">Guide de déploiement pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="54147-280">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="54147-281">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="54147-281">System Requirements</span></span>](../get-started/system-requirements.md)
