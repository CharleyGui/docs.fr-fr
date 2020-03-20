---
title: Guide de déploiement du .NET Framework pour les administrateurs
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: be15ce0b0bed37da6fe400e98bfdd118c48f7ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716535"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="21213-102">Guide de déploiement du .NET Framework pour les administrateurs</span><span class="sxs-lookup"><span data-stu-id="21213-102">.NET Framework Deployment Guide for Administrators</span></span>

<span data-ttu-id="21213-103">Cet article étape par étape décrit comment un administrateur système peut déployer le cadre .NET 4.5 et ses dépendances système sur un réseau en utilisant Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="21213-103">This step-by-step article describes how a system administrator can deploy the .NET Framework 4.5 and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="21213-104">Cet article suppose que tous les ordinateurs clients cibles ont la configuration minimale requise pour le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21213-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="21213-105">Pour obtenir la liste des configurations logicielle et matérielle requises pour installer .NET Framework 4.5, consultez [Configuration système requise](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21213-105">For a list of the software and hardware requirements for installing the .NET Framework 4.5, see [System Requirements](../get-started/system-requirements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="21213-106">Le logiciel référencé dans ce document, y compris, sans limitation, le cadre .NET 4.5, Le gestionnaire de configuration et l’annuaire actif, sont chacun soumis aux conditions de licence.</span><span class="sxs-lookup"><span data-stu-id="21213-106">The software referenced in this document, including, without limitation, the .NET Framework 4.5, Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="21213-107">Les présentes instructions supposent que lesdits termes et conditions du contrat de licence ont été passés en revue et acceptés par les propriétaires de licences des logiciels concernés.</span><span class="sxs-lookup"><span data-stu-id="21213-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="21213-108">Ces instructions ne remplacent pas les termes et conditions desdits contrats de licence.</span><span class="sxs-lookup"><span data-stu-id="21213-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>
>
> <span data-ttu-id="21213-109">Pour plus d’informations sur le support pour le cadre .NET, voir [.NET Framework politique de soutien officiel](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) sur le site Web microsoft Support.</span><span class="sxs-lookup"><span data-stu-id="21213-109">For information about support for the .NET Framework, see [.NET Framework official support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) on the Microsoft Support website.</span></span>

<span data-ttu-id="21213-110">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="21213-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="21213-111">Le processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="21213-111">The deployment process</span></span>](#the_deployment_process)
- [<span data-ttu-id="21213-112">Déployer le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="21213-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)
- [<span data-ttu-id="21213-113">Créer une collection</span><span class="sxs-lookup"><span data-stu-id="21213-113">Create a collection</span></span>](#creating_a_collection)
- [<span data-ttu-id="21213-114">Créer un package et un programme</span><span class="sxs-lookup"><span data-stu-id="21213-114">Create a package and program</span></span>](#creating_a_package)
- [<span data-ttu-id="21213-115">Sélectionner un point de distribution</span><span class="sxs-lookup"><span data-stu-id="21213-115">Select a distribution point</span></span>](#select_dist_point)
- [<span data-ttu-id="21213-116">Déployer le paquet</span><span class="sxs-lookup"><span data-stu-id="21213-116">Deploy the package</span></span>](#deploying_package)
- [<span data-ttu-id="21213-117">Ressources</span><span class="sxs-lookup"><span data-stu-id="21213-117">Resources</span></span>](#resources)
- [<span data-ttu-id="21213-118">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="21213-118">Troubleshooting</span></span>](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a><span data-ttu-id="21213-119">Processus de déploiement</span><span class="sxs-lookup"><span data-stu-id="21213-119">The deployment process</span></span>

<span data-ttu-id="21213-120">Lorsque vous avez l’infrastructure de support en place, vous utilisez Configuration Manager pour déployer le paquet redistributable .NET Framework sur les ordinateurs du réseau.</span><span class="sxs-lookup"><span data-stu-id="21213-120">When you have the supporting infrastructure in place, you use Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="21213-121">Générer l’infrastructure implique la création et la définition de cinq éléments principaux : les regroupements, un package et un programme pour les logiciels, des points de distribution et des déploiements.</span><span class="sxs-lookup"><span data-stu-id="21213-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>

- <span data-ttu-id="21213-122">Les **regroupements** sont des ensembles de ressources de Configuration Manager, tels que des utilisateurs, des groupes d’utilisateurs ou des ordinateurs, sur lesquels le .Net Framework est déployé.</span><span class="sxs-lookup"><span data-stu-id="21213-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="21213-123">Pour plus d’informations, voir [Introduction aux collections dans Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="21213-123">For more information, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="21213-124">Les **packages et programmes** sont généralement les applications logicielles à installer sur un ordinateur client, mais ils peuvent également contenir des fichiers individuels, des mises à jour, ou même des commandes individuelles.</span><span class="sxs-lookup"><span data-stu-id="21213-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="21213-125">Pour plus d’informations, consultez [les forfaits et les programmes dans Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) dans la bibliothèque de documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="21213-125">For more information, see [Packages and programs in Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="21213-126">Les **points de distribution** sont des rôles de système de site Configuration Manager qui stockent les fichiers requis pour l’exécution des logiciels sur les ordinateurs clients.</span><span class="sxs-lookup"><span data-stu-id="21213-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="21213-127">Lorsque le client Configuration Manager reçoit et traite un déploiement de logiciel, il contacte un point de distribution pour télécharger le contenu associé au logiciel et démarrer le processus d'installation.</span><span class="sxs-lookup"><span data-stu-id="21213-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="21213-128">Pour plus d’informations, consultez [Concepts fondamentaux de la gestion de contenu dans Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) dans la bibliothèque de la documentation Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="21213-128">For more information, see [Fundamental concepts for content management in Configuration Manager](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>

- <span data-ttu-id="21213-129">Les **déploiements** font en sorte que les membres applicables du regroupement cible spécifié installent le package logiciel.</span><span class="sxs-lookup"><span data-stu-id="21213-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21213-130">Les procédures de cette rubrique contiennent les paramètres classiques pour créer et déployer un package et un programme, et ne couvrent pas tous les paramètres possibles.</span><span class="sxs-lookup"><span data-stu-id="21213-130">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="21213-131">Pour d’autres options de déploiement de Configuration Manager, consultez la [Bibliothèque de documentation Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="21213-131">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span></span>

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a><span data-ttu-id="21213-132">Déployer le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="21213-132">Deploying the .NET Framework</span></span>

<span data-ttu-id="21213-133">Vous pouvez utiliser Configuration Manager pour déployer une installation silencieuse du cadre .NET 4.5, où les utilisateurs n’interagissent pas avec le processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="21213-133">You can use Configuration Manager to deploy a silent installation of the .NET Framework 4.5, where the users do not interact with the installation process.</span></span> <span data-ttu-id="21213-134">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="21213-134">Follow these steps:</span></span>

1. <span data-ttu-id="21213-135">[Créer une collection](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="21213-135">[Create a collection](#creating_a_collection).</span></span>

2. <span data-ttu-id="21213-136">[Créez un package et un programme pour le package redistribuable .Net Framework](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="21213-136">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>

3. <span data-ttu-id="21213-137">[Sélectionnez un point de distribution](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="21213-137">[Select a distribution point](#select_dist_point).</span></span>

4. <span data-ttu-id="21213-138">[Déployez le paquet](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="21213-138">[Deploy the package](#deploying_package).</span></span>

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a><span data-ttu-id="21213-139">Création d'une collection</span><span class="sxs-lookup"><span data-stu-id="21213-139">Create a collection</span></span>

<span data-ttu-id="21213-140">Dans cette étape, sélectionnez les ordinateurs sur lesquels seront déployés le package et le programme, et regroupez-les dans un regroupement de périphériques.</span><span class="sxs-lookup"><span data-stu-id="21213-140">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="21213-141">Pour créer un regroupement dans Configuration Manager, utilisez des règles d’adhésion directes (où les membres du regroupement sont spécifiés manuellement) ou des règles de requête (où Configuration Manager détermine les membres du regroupement selon des critères que vous avez spécifiés).</span><span class="sxs-lookup"><span data-stu-id="21213-141">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="21213-142">Pour plus d’informations sur les règles d’adhésion, y compris les requêtes et les règles directes, voir [Introduction aux collections dans Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) dans la Bibliothèque de documentation Du gestionnaire de configuration.</span><span class="sxs-lookup"><span data-stu-id="21213-142">For more information about membership rules, including queries and direct rules, see [Introduction to collections in Configuration Manager](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>

<span data-ttu-id="21213-143">Pour créer un regroupement</span><span class="sxs-lookup"><span data-stu-id="21213-143">To create a collection:</span></span>

1. <span data-ttu-id="21213-144">Dans la Console Configuration Manager, choisissez **Ressources et Conformité**.</span><span class="sxs-lookup"><span data-stu-id="21213-144">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>

2. <span data-ttu-id="21213-145">Dans l’espace de travail **Ressources et Conformité**, choisissez **Regroupements de périphériques**.</span><span class="sxs-lookup"><span data-stu-id="21213-145">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>

3. <span data-ttu-id="21213-146">Sous l’onglet **Accueil** dans le groupe **Créer**, choisissez **Créer un regroupement de périphériques**.</span><span class="sxs-lookup"><span data-stu-id="21213-146">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>

4. <span data-ttu-id="21213-147">Dans la page **Général** de l’**Assistant Création d’un regroupement de périphériques**, entrez un nom pour le regroupement.</span><span class="sxs-lookup"><span data-stu-id="21213-147">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>

5. <span data-ttu-id="21213-148">Choisissez **Parcourir** pour spécifier un regroupement limité.</span><span class="sxs-lookup"><span data-stu-id="21213-148">Choose **Browse** to specify a limiting collection.</span></span>

6. <span data-ttu-id="21213-149">Dans la page **Règles d’adhésion**, choisissez **Ajouter une règle**, puis **Règle directe** pour ouvrir l’**Assistant Création d’une règle d’adhésion directe**.</span><span class="sxs-lookup"><span data-stu-id="21213-149">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="21213-150">Choisissez **La prochaine**.</span><span class="sxs-lookup"><span data-stu-id="21213-150">Choose **Next**.</span></span>

7. <span data-ttu-id="21213-151">Dans la page **Rechercher des ressources**, dans la liste **Classe de ressource**, choisissez **Ressource système**.</span><span class="sxs-lookup"><span data-stu-id="21213-151">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="21213-152">Dans la liste **Nom de l’attribut**, choisissez **Nom**.</span><span class="sxs-lookup"><span data-stu-id="21213-152">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="21213-153">Dans le champ **Valeur**, entrez `%` et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="21213-153">In the **Value** field, enter `%`, and then choose **Next**.</span></span>

8. <span data-ttu-id="21213-154">Dans la page **Sélectionner les ressources**, cochez la case de chaque ordinateur sur lequel vous souhaitez déployer le .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="21213-154">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="21213-155">Choisissez **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="21213-155">Choose **Next**, and then complete the wizard.</span></span>

9. <span data-ttu-id="21213-156">Dans la page **Règles d’adhésion** de l’**Assistant Création d’un regroupement de périphériques**, choisissez **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="21213-156">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="21213-157">Créer un package et un programme pour le package redistribuable .Net Framework</span><span class="sxs-lookup"><span data-stu-id="21213-157">Create a package and program for the .NET Framework redistributable package</span></span>

<span data-ttu-id="21213-158">Les étapes suivantes permettent de créer manuellement un package pour le package redistribuable .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21213-158">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="21213-159">Le package contient les paramètres spécifiés pour l'installation du .Net Framework et l'emplacement à partir duquel le package sera distribué aux ordinateurs cibles.</span><span class="sxs-lookup"><span data-stu-id="21213-159">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>

<span data-ttu-id="21213-160">Pour créer un package :</span><span class="sxs-lookup"><span data-stu-id="21213-160">To create a package:</span></span>

1. <span data-ttu-id="21213-161">Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="21213-161">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="21213-162">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="21213-162">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="21213-163">Sous l’onglet **Accueil**, dans le groupe **Créer**, choisissez **Créer un package**.</span><span class="sxs-lookup"><span data-stu-id="21213-163">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>

4. <span data-ttu-id="21213-164">Dans la page **Package** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="21213-164">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    - <span data-ttu-id="21213-165">Nom : `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="21213-165">Name: `.NET Framework 4.5`</span></span>

    - <span data-ttu-id="21213-166">Fabricant : `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="21213-166">Manufacturer: `Microsoft`</span></span>

    - <span data-ttu-id="21213-167">Langue :</span><span class="sxs-lookup"><span data-stu-id="21213-167">Language.</span></span> `English (US)`

5. <span data-ttu-id="21213-168">Choisissez **Ce package contient des fichiers sources**, puis **Parcourir** pour sélectionner le dossier local ou réseau qui contient les fichiers d’installation du .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="21213-168">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="21213-169">Quand vous avez sélectionné le dossier, choisissez **OK**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="21213-169">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>

6. <span data-ttu-id="21213-170">Dans la page **Type de programme** de l’Assistant, choisissez **Programme standard**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="21213-170">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>

7. <span data-ttu-id="21213-171">Dans la page **Programme** de l’**Assistant Création d’un package et d’un programme**, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="21213-171">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>

    1. <span data-ttu-id="21213-172">**Nom:**`.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="21213-172">**Name:** `.NET Framework 4.5`</span></span>

    2. <span data-ttu-id="21213-173">**Ligne de commande :** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (les options de ligne de commande sont décrites dans le tableau après ces étapes)</span><span class="sxs-lookup"><span data-stu-id="21213-173">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>

    3. <span data-ttu-id="21213-174">**Exécuter :** choisissez **Masqué**.</span><span class="sxs-lookup"><span data-stu-id="21213-174">**Run:** Choose **Hidden**.</span></span>

    4. <span data-ttu-id="21213-175">**Le programme peut s’exécuter :** sélectionnez l’option qui spécifie que le programme peut s’exécuter que l’utilisateur soit connecté ou non.</span><span class="sxs-lookup"><span data-stu-id="21213-175">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>

8. <span data-ttu-id="21213-176">Dans la page **Exigences**, acceptez les valeurs par défaut en choisissant **Suivant**, puis terminez l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="21213-176">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>

<span data-ttu-id="21213-177">Le tableau suivant décrit les options de ligne de commande spécifiées dans l'étape 7.</span><span class="sxs-lookup"><span data-stu-id="21213-177">The following table describes the command-line options specified in step 7.</span></span>

|<span data-ttu-id="21213-178">Option</span><span class="sxs-lookup"><span data-stu-id="21213-178">Option</span></span>|<span data-ttu-id="21213-179">Description</span><span class="sxs-lookup"><span data-stu-id="21213-179">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="21213-180">**/q**</span><span class="sxs-lookup"><span data-stu-id="21213-180">**/q**</span></span>|<span data-ttu-id="21213-181">Active le mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="21213-181">Sets quiet mode.</span></span> <span data-ttu-id="21213-182">Aucune entrée d'utilisateur n'est requise, et aucun résultat n'est affiché.</span><span class="sxs-lookup"><span data-stu-id="21213-182">No user input is required, and no output is shown.</span></span>|
|<span data-ttu-id="21213-183">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="21213-183">**/norestart**</span></span>|<span data-ttu-id="21213-184">Empêche le programme d'installation de redémarrer automatiquement.</span><span class="sxs-lookup"><span data-stu-id="21213-184">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="21213-185">Si vous utilisez cette option, Configuration Manager doit gérer le redémarrage de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="21213-185">If you use this option, Configuration Manager must handle the computer restart.</span></span>|
|<span data-ttu-id="21213-186">**/chainingpackage** *nom_package*</span><span class="sxs-lookup"><span data-stu-id="21213-186">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="21213-187">Spécifie le nom du package qui effectue le chaînage.</span><span class="sxs-lookup"><span data-stu-id="21213-187">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="21213-188">Ces informations sont stockées avec d'autres informations de session d'installation pour les personnes inscrites au Programme d'amélioration du produit Microsoft (CEIP).</span><span class="sxs-lookup"><span data-stu-id="21213-188">This information is reported with other installation session information for those who have signed up for the Microsoft Customer Experience Improvement Program (CEIP).</span></span> <span data-ttu-id="21213-189">Si le nom du package inclut des espaces, utilisez des guillemets doubles comme délimiteurs. Par exemple : **/chainingpackage "Chaining Product"**.</span><span class="sxs-lookup"><span data-stu-id="21213-189">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|

<span data-ttu-id="21213-190">Les étapes suivantes créent un package nommé .Net Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="21213-190">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="21213-191">Le programme déploie une installation sans assistance de .Net Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="21213-191">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="21213-192">Dans une installation sans assistance, les utilisateurs n’interagissent pas avec le processus d’installation et l’application de chaînage doit capturer le code de retour et gérer le redémarrage. Pour plus d’informations, consultez [Getting Progress Information from an Installation Package](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="21213-192">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100)).</span></span>

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a><span data-ttu-id="21213-193">Sélectionner un point de distribution</span><span class="sxs-lookup"><span data-stu-id="21213-193">Select a distribution point</span></span>

<span data-ttu-id="21213-194">Pour distribuer le package et le programme aux ordinateurs clients à partir d'un serveur, vous devez d'abord désigner un système de site comme un point de distribution, puis distribuer le package au point de distribution.</span><span class="sxs-lookup"><span data-stu-id="21213-194">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>

<span data-ttu-id="21213-195">Utilisez les étapes suivantes pour sélectionner un point de distribution pour le package de .Net Framework 4.5 créé au cours la section précédente :</span><span class="sxs-lookup"><span data-stu-id="21213-195">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>

1. <span data-ttu-id="21213-196">Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="21213-196">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="21213-197">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="21213-197">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="21213-198">Dans la liste de packages, sélectionnez le package **.Net Framework 4.5** créé dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="21213-198">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>

4. <span data-ttu-id="21213-199">Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Distribuer du contenu**.</span><span class="sxs-lookup"><span data-stu-id="21213-199">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>

5. <span data-ttu-id="21213-200">Sous l’onglet **Général** de l’**Assistant Distribuer du contenu**, choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="21213-200">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>

6. <span data-ttu-id="21213-201">Dans la page **Destination du contenu** de l’Assistant, choisissez **Ajouter**, puis **Point de distribution**.</span><span class="sxs-lookup"><span data-stu-id="21213-201">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>

7. <span data-ttu-id="21213-202">Dans la boîte de dialogue **Ajouter des points de distribution**, sélectionnez les points de distribution qui hébergeront le package et le programme, puis choisissez **OK**.</span><span class="sxs-lookup"><span data-stu-id="21213-202">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>

8. <span data-ttu-id="21213-203">Terminez l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="21213-203">Complete the wizard.</span></span>

<span data-ttu-id="21213-204">Le package contient désormais toutes les informations nécessaires au déploiement sans assistance de .Net Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="21213-204">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="21213-205">Avant de déployer le paquet et le programme, vérifiez qu’il a été installé sur le point de distribution; consultez la section « Surveillance de l’état du contenu » du [contenu Monitor que vous distribuez avec Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) dans la bibliothèque de documentation du gestionnaire de configuration.</span><span class="sxs-lookup"><span data-stu-id="21213-205">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Content status monitoring" section of [Monitor content you distribute with Configuration Manager](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a><span data-ttu-id="21213-206">Déploiement du package</span><span class="sxs-lookup"><span data-stu-id="21213-206">Deploy the package</span></span>

<span data-ttu-id="21213-207">Pour déployer le package et le programme .Net Framework 4.5 :</span><span class="sxs-lookup"><span data-stu-id="21213-207">To deploy the .NET Framework 4.5 package and program:</span></span>

1. <span data-ttu-id="21213-208">Dans la Console Configuration Manager, choisissez **Bibliothèque de logiciels**.</span><span class="sxs-lookup"><span data-stu-id="21213-208">In the Configuration Manager console, choose **Software Library**.</span></span>

2. <span data-ttu-id="21213-209">Dans l’espace de travail **Bibliothèque de logiciels**, développez **Gestion des applications**, puis choisissez **Packages**.</span><span class="sxs-lookup"><span data-stu-id="21213-209">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>

3. <span data-ttu-id="21213-210">Dans la liste des packages, sélectionnez le package que vous avez créé, appelé **.Net Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="21213-210">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>

4. <span data-ttu-id="21213-211">Sous l’onglet **Accueil**, dans le groupe **Déploiement**, choisissez **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="21213-211">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>

5. <span data-ttu-id="21213-212">Dans la page **Général** de l’**Assistant Déploiement logiciel**, choisissez **Parcourir**, puis sélectionnez le regroupement créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="21213-212">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="21213-213">Choisissez **La prochaine**.</span><span class="sxs-lookup"><span data-stu-id="21213-213">Choose **Next**.</span></span>

6. <span data-ttu-id="21213-214">Dans la page **Contenu** de l’Assistant, vérifiez que le point à partir duquel vous souhaitez distribuer le logiciel s’affiche, puis choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="21213-214">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>

7. <span data-ttu-id="21213-215">Dans la page **Paramètres de déploiement** de l’Assistant, vérifiez que **Action** est défini sur **Installer**, et **Objectif** sur **Requis**.</span><span class="sxs-lookup"><span data-stu-id="21213-215">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="21213-216">Cela garantit que le package logiciel est une installation obligatoire sur les ordinateurs ciblés.</span><span class="sxs-lookup"><span data-stu-id="21213-216">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="21213-217">Choisissez **La prochaine**.</span><span class="sxs-lookup"><span data-stu-id="21213-217">Choose **Next**.</span></span>

8. <span data-ttu-id="21213-218">Dans la page **Planification** de l’Assistant, spécifiez à quel moment vous souhaitez que le .Net Framework soit installé.</span><span class="sxs-lookup"><span data-stu-id="21213-218">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="21213-219">Choisissez **Nouveau** pour déterminer le moment de l’installation, ou demandez au logiciel d’effectuer l’installation quand l’utilisateur se connecte ou se déconnecte, ou dès que possible.</span><span class="sxs-lookup"><span data-stu-id="21213-219">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="21213-220">Choisissez **La prochaine**.</span><span class="sxs-lookup"><span data-stu-id="21213-220">Choose **Next**.</span></span>

9. <span data-ttu-id="21213-221">Dans la page **Expérience utilisateur** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="21213-221">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="21213-222">Il est possible que votre environnement de production ait des stratégies qui requièrent des sélections différentes pour la planification de déploiement.</span><span class="sxs-lookup"><span data-stu-id="21213-222">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="21213-223">Pour plus d’informations sur ces options, consultez [Propriétés du nom de la publication : Onglet Calendrier](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span><span class="sxs-lookup"><span data-stu-id="21213-223">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span></span>

10. <span data-ttu-id="21213-224">Dans la page **Points de distribution** de l’Assistant, utilisez les valeurs par défaut et choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="21213-224">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>

11. <span data-ttu-id="21213-225">Terminez l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="21213-225">Complete the wizard.</span></span> <span data-ttu-id="21213-226">Vous pouvez surveiller la progression du déploiement dans le nœud **Déploiements** de l’espace de travail **Surveillance**.</span><span class="sxs-lookup"><span data-stu-id="21213-226">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>

<span data-ttu-id="21213-227">Le package est déployé dans le regroupement ciblé et l’installation sans assistance du .Net Framework 4.5 peut commencer.</span><span class="sxs-lookup"><span data-stu-id="21213-227">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="21213-228">Pour plus d’informations sur les codes d’erreur liés à l’installation du .NET Framework 4.5, consultez la section [Codes de retour](#return_codes) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="21213-228">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>

<a name="resources"></a>

## <a name="resources"></a><span data-ttu-id="21213-229">Ressources</span><span class="sxs-lookup"><span data-stu-id="21213-229">Resources</span></span>

<span data-ttu-id="21213-230">Pour plus d’informations sur l’infrastructure pour tester le déploiement du package redistribuable de .NET Framework 4.5, consultez les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="21213-230">For more information about the infrastructure for testing the deployment of the .NET Framework 4.5 redistributable package, see the following resources.</span></span>

<span data-ttu-id="21213-231">**Active Directory, DNS, DHCP :**</span><span class="sxs-lookup"><span data-stu-id="21213-231">**Active Directory, DNS, DHCP:**</span></span>

- [<span data-ttu-id="21213-232">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="21213-232">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)

- [<span data-ttu-id="21213-233">DNS (Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="21213-233">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)

- [<span data-ttu-id="21213-234">Protocole DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="21213-234">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)

<span data-ttu-id="21213-235">**Serveur SQL 2008:**</span><span class="sxs-lookup"><span data-stu-id="21213-235">**SQL Server 2008:**</span></span>

- <span data-ttu-id="21213-236">[Installer SQL Server 2008 (vidéo SQL Server)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="21213-236">[Installing SQL Server 2008 (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))</span></span>

- [<span data-ttu-id="21213-237">Vue d’ensemble de la sécurité SQL Server 2008 pour les administrateurs de base de données</span><span class="sxs-lookup"><span data-stu-id="21213-237">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

<span data-ttu-id="21213-238">**System Center 2012 Configuration Manager (point de gestion, point de distribution) :**</span><span class="sxs-lookup"><span data-stu-id="21213-238">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>

- [<span data-ttu-id="21213-239">Administration de site pour System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="21213-239">Site Administration for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [<span data-ttu-id="21213-240">Planification et déploiement d’un site unique Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="21213-240">Configuration Manager Single Site Planning and Deployment</span></span>](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

<span data-ttu-id="21213-241">**Client System Center 2012 Configuration Manager pour ordinateurs Windows :**</span><span class="sxs-lookup"><span data-stu-id="21213-241">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>

- [<span data-ttu-id="21213-242">Déployer des clients pour System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="21213-242">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="21213-243">Dépannage</span><span class="sxs-lookup"><span data-stu-id="21213-243">Troubleshooting</span></span>

### <a name="log-file-locations"></a><span data-ttu-id="21213-244">Emplacements des fichiers journaux</span><span class="sxs-lookup"><span data-stu-id="21213-244">Log file locations</span></span>

<span data-ttu-id="21213-245">Les fichiers journaux suivants sont générés lors de l’installation du .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="21213-245">The following log files are generated during .NET Framework setup:</span></span>

- <span data-ttu-id="21213-246">%temp%-Microsoft .NET *Framework version*\*.txt</span><span class="sxs-lookup"><span data-stu-id="21213-246">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>
- <span data-ttu-id="21213-247">%temp%-Microsoft .NET *Framework version*\*.html</span><span class="sxs-lookup"><span data-stu-id="21213-247">%temp%\Microsoft .NET Framework *version*\*.html</span></span>

<span data-ttu-id="21213-248">où *version* est la version du .NET Framework que vous installez, comme 4.5 ou 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="21213-248">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>

<span data-ttu-id="21213-249">Vous pouvez également spécifier le répertoire où les fichiers journaux sont écrits avec l’option de ligne de commande `/log` dans la commande d’installation du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21213-249">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="21213-250">Pour plus d’informations, consultez [Guide de déploiement du .NET Framework pour les développeurs](deployment-guide-for-developers.md#command-line-options).</span><span class="sxs-lookup"><span data-stu-id="21213-250">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span>

<span data-ttu-id="21213-251">Vous pouvez utiliser [l’outil de collecte des journaux](https://www.microsoft.com/download/details.aspx?id=12493) pour collecter les fichiers journaux du .NET Framework et créer un fichier CAB compressé (.cab) afin de réduire la taille des fichiers.</span><span class="sxs-lookup"><span data-stu-id="21213-251">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>

<a name="return_codes"></a>

### <a name="return-codes"></a><span data-ttu-id="21213-252">Codes de retour</span><span class="sxs-lookup"><span data-stu-id="21213-252">Return codes</span></span>

<span data-ttu-id="21213-253">Le tableau suivant liste les codes de retour les plus courants du programme d’installation du package redistribuable de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="21213-253">The following table lists the most common return codes from the .NET Framework 4.5 redistributable installation program.</span></span> <span data-ttu-id="21213-254">Les codes de retour sont identiques pour toutes les versions du programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="21213-254">The return codes are the same for all versions of the installer.</span></span>

<span data-ttu-id="21213-255">Pour plus d’informations, consultez la section suivante : [Codes d’erreur de téléchargement](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="21213-255">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>

|<span data-ttu-id="21213-256">Code de retour</span><span class="sxs-lookup"><span data-stu-id="21213-256">Return code</span></span>|<span data-ttu-id="21213-257">Description</span><span class="sxs-lookup"><span data-stu-id="21213-257">Description</span></span>|
|-----------------|-----------------|
|<span data-ttu-id="21213-258">0</span><span class="sxs-lookup"><span data-stu-id="21213-258">0</span></span>|<span data-ttu-id="21213-259">Installation terminée.</span><span class="sxs-lookup"><span data-stu-id="21213-259">Installation completed successfully.</span></span>|
|<span data-ttu-id="21213-260">1602</span><span class="sxs-lookup"><span data-stu-id="21213-260">1602</span></span>|<span data-ttu-id="21213-261">L'utilisateur a annulé l'installation.</span><span class="sxs-lookup"><span data-stu-id="21213-261">The user canceled installation.</span></span>|
|<span data-ttu-id="21213-262">1603</span><span class="sxs-lookup"><span data-stu-id="21213-262">1603</span></span>|<span data-ttu-id="21213-263">Une erreur irrécupérable s’est produite pendant l’installation.</span><span class="sxs-lookup"><span data-stu-id="21213-263">A fatal error occurred during installation.</span></span>|
|<span data-ttu-id="21213-264">1641</span><span class="sxs-lookup"><span data-stu-id="21213-264">1641</span></span>|<span data-ttu-id="21213-265">Un redémarrage est nécessaire pour terminer l'installation.</span><span class="sxs-lookup"><span data-stu-id="21213-265">A restart is required to complete the installation.</span></span> <span data-ttu-id="21213-266">Ce message indique que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="21213-266">This message indicates success.</span></span>|
|<span data-ttu-id="21213-267">3010</span><span class="sxs-lookup"><span data-stu-id="21213-267">3010</span></span>|<span data-ttu-id="21213-268">Un redémarrage est nécessaire pour terminer l'installation.</span><span class="sxs-lookup"><span data-stu-id="21213-268">A restart is required to complete the installation.</span></span> <span data-ttu-id="21213-269">Ce message indique que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="21213-269">This message indicates success.</span></span>|
|<span data-ttu-id="21213-270">5100</span><span class="sxs-lookup"><span data-stu-id="21213-270">5100</span></span>|<span data-ttu-id="21213-271">L'ordinateur de l'utilisateur n'a pas la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="21213-271">The user's computer does not meet system requirements.</span></span>|

<a name="additional_error_codes"></a>

### <a name="download-error-codes"></a><span data-ttu-id="21213-272">Codes d'erreur de téléchargement</span><span class="sxs-lookup"><span data-stu-id="21213-272">Download error codes</span></span>

- [<span data-ttu-id="21213-273">Codes d’erreur du service de transfert intelligent en arrière-plan (BITS)</span><span class="sxs-lookup"><span data-stu-id="21213-273">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)

- [<span data-ttu-id="21213-274">Codes d’erreur du moniker d’URL</span><span class="sxs-lookup"><span data-stu-id="21213-274">URL moniker error codes</span></span>](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [<span data-ttu-id="21213-275">Codes d’erreur WinHttp</span><span class="sxs-lookup"><span data-stu-id="21213-275">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)

<span data-ttu-id="21213-276">Autres codes d'erreur :</span><span class="sxs-lookup"><span data-stu-id="21213-276">Other error codes:</span></span>

- [<span data-ttu-id="21213-277">Codes d’erreur Windows Installer</span><span class="sxs-lookup"><span data-stu-id="21213-277">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

- <span data-ttu-id="21213-278">[Codes de résultat de l’agent de mise à jour automatique Windows Update](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="21213-278">[Windows Update Agent result codes](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="21213-279">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21213-279">See also</span></span>

- [<span data-ttu-id="21213-280">Guide de déploiement pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="21213-280">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="21213-281">Exigences du système</span><span class="sxs-lookup"><span data-stu-id="21213-281">System Requirements</span></span>](../get-started/system-requirements.md)
