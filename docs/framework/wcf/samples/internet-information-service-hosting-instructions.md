---
title: Instructions relatives à l'hébergement dans les Services Internet (IIS)
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 151c5ba8dd79e8554e7d79fb5b8182740b0be18e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237688"
---
# <a name="internet-information-service-hosting-instructions"></a><span data-ttu-id="c2947-102">Instructions relatives à l'hébergement dans les Services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="c2947-102">Internet Information Service Hosting Instructions</span></span>

<span data-ttu-id="c2947-103">Pour exécuter les exemples hébergés par les services IIS (Internet Information Services), vous devez vous assurer que les services IIS sont correctement installés et en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="c2947-103">To run the samples that are hosted by Internet Information Services (IIS), you must make sure that IIS is properly installed and is running.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a><span data-ttu-id="c2947-104">Pour installer IIS version 7.5 sur Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c2947-104">To install IIS version 7.5 on Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="c2947-105">Dans **Gestionnaire de serveur**, sélectionnez **rôles.**</span><span class="sxs-lookup"><span data-stu-id="c2947-105">From **Server Manager**, select **Roles.**</span></span> <span data-ttu-id="c2947-106">Sous **Résumé des rôles**, cliquez sur **Ajouter des rôles**.</span><span class="sxs-lookup"><span data-stu-id="c2947-106">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="c2947-107">Cliquez sur **suivant** pour afficher la boîte de dialogue **Sélectionner des rôles de serveurs** .</span><span class="sxs-lookup"><span data-stu-id="c2947-107">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="c2947-108">Sélectionnez **serveur d’applications** dans la liste **rôles** , puis cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue Sélectionner des **services de rôle** pour le rôle de serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="c2947-108">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="c2947-109">Activez la case à cocher **serveur Web (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="c2947-109">Select the **Web Server (IIS)** check box.</span></span> <span data-ttu-id="c2947-110">Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les fonctionnalités requises**.</span><span class="sxs-lookup"><span data-stu-id="c2947-110">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="c2947-111">Cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner des services de rôle** pour le rôle serveur Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="c2947-111">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="c2947-112">Développez **outils de gestion**, puis développez **compatibilité avec la gestion IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c2947-112">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="c2947-113">Sélectionnez **outils de script IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c2947-113">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="c2947-114">Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les services de rôle requis**.</span><span class="sxs-lookup"><span data-stu-id="c2947-114">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="c2947-115">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2947-115">Click **Next**.</span></span>  
  
6. <span data-ttu-id="c2947-116">Si le résumé des sélections est correct, cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="c2947-116">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="c2947-117">Une fois l’installation terminée, cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="c2947-117">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-75-on-windows-7"></a><span data-ttu-id="c2947-118">Pour installer IIS version 7.5 sur Windows 7</span><span class="sxs-lookup"><span data-stu-id="c2947-118">To install IIS version 7.5 on Windows 7</span></span>  
  
1. <span data-ttu-id="c2947-119">Cliquez sur **Démarrer**, puis sur **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="c2947-119">Click **Start**, and then click **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c2947-120">Ouvrez le groupe **programmes** .</span><span class="sxs-lookup"><span data-stu-id="c2947-120">Open the **Programs** group.</span></span>  
  
3. <span data-ttu-id="c2947-121">Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="c2947-121">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="c2947-122">La boîte de dialogue **contrôle de compte d’utilisateur** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c2947-122">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="c2947-123">Cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="c2947-123">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="c2947-124">La boîte de dialogue **fonctionnalités de Windows** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c2947-124">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="c2947-125">Développez l’élément intitulé **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="c2947-125">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="c2947-126">Développez l’élément intitulé **Services World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="c2947-126">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="c2947-127">Développez l’élément **fonctionnalités de développement d’applications**.</span><span class="sxs-lookup"><span data-stu-id="c2947-127">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="c2947-128">Assurez-vous que les éléments suivants sont sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="c2947-128">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="c2947-129">**Extensibilité .NET**</span><span class="sxs-lookup"><span data-stu-id="c2947-129">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="c2947-130">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="c2947-130">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="c2947-131">**Extensions ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c2947-131">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="c2947-132">**Filtres ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c2947-132">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="c2947-133">Sous l’élément intitulé **Services World Wide Web**, développez **fonctionnalités http communes**.</span><span class="sxs-lookup"><span data-stu-id="c2947-133">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
10. <span data-ttu-id="c2947-134">Assurez-vous que **contenu statique** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c2947-134">Make sure **Static Content** is selected.</span></span>  
  
11. <span data-ttu-id="c2947-135">Sous l’élément nommé **World Wide Web services**, développez **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="c2947-135">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
12. <span data-ttu-id="c2947-136">Assurez-vous que **l’option authentification Windows** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="c2947-136">Make sure that **Windows Authentication** is selected.</span></span>  
  
13. <span data-ttu-id="c2947-137">Sous le répertoire **Internet Information Services** , développez l’élément **Outils d’administration Web**, puis sélectionnez **console de gestion IIS**.</span><span class="sxs-lookup"><span data-stu-id="c2947-137">Under the **Internet Information Services** directory, expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
14. <span data-ttu-id="c2947-138">Développez l’élément **compatibilité avec la gestion IIS 6**, puis sélectionnez **outils de script IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c2947-138">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="c2947-139">Sous le répertoire **Internet Information Services** , développez l’élément intitulé **Microsoft .NET Framework 3.5.1**, puis sélectionnez **Windows Communication Foundation activation http**.</span><span class="sxs-lookup"><span data-stu-id="c2947-139">Under the **Internet Information Services** directory, expand the item labeled **Microsoft .NET Framework 3.5.1**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="c2947-140">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2947-140">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a><span data-ttu-id="c2947-141">Pour installer IIS version 7.0 sur Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="c2947-141">To install IIS version 7.0 on Windows Server 2008</span></span>  
  
1. <span data-ttu-id="c2947-142">Dans **Gestionnaire de serveur**, sélectionnez **rôles**.</span><span class="sxs-lookup"><span data-stu-id="c2947-142">From **Server Manager**, select **Roles**.</span></span> <span data-ttu-id="c2947-143">Sous **Résumé des rôles**, cliquez sur **Ajouter des rôles**.</span><span class="sxs-lookup"><span data-stu-id="c2947-143">Under **Roles Summary**, click **Add Roles**.</span></span>  
  
2. <span data-ttu-id="c2947-144">Cliquez sur **suivant** pour afficher la boîte de dialogue **Sélectionner des rôles de serveurs** .</span><span class="sxs-lookup"><span data-stu-id="c2947-144">Click **Next** to display the **Select Server Roles** dialog.</span></span>  
  
3. <span data-ttu-id="c2947-145">Sélectionnez **serveur d’applications** dans la liste **rôles** , puis cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue Sélectionner des **services de rôle** pour le rôle de serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="c2947-145">Select **Application Server** from the **Roles** list, and then click **Next** twice to display the **Select Role Services** dialog for the Application Server role.</span></span>  
  
4. <span data-ttu-id="c2947-146">Activez la case à cocher **serveur Web (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="c2947-146">Select **Web Server (IIS)** check box.</span></span> <span data-ttu-id="c2947-147">Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les fonctionnalités requises**.</span><span class="sxs-lookup"><span data-stu-id="c2947-147">If you are prompted to install additional role services and features, click **Add Required Features**.</span></span> <span data-ttu-id="c2947-148">Cliquez sur **suivant** à deux reprises pour afficher la boîte de dialogue **Sélectionner des services de rôle** pour le rôle serveur Web (IIS).</span><span class="sxs-lookup"><span data-stu-id="c2947-148">Click **Next** twice to display the **Select Role Services** dialog for the Web Server (IIS) role.</span></span>  
  
5. <span data-ttu-id="c2947-149">Développez **outils de gestion**, puis développez **compatibilité avec la gestion IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c2947-149">Expand **Management Tools**, and then expand **IIS 6 Management Compatibility**.</span></span> <span data-ttu-id="c2947-150">Sélectionnez **outils de script IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c2947-150">Select **IIS 6 Scripting Tools**.</span></span> <span data-ttu-id="c2947-151">Si vous êtes invité à installer d’autres services de rôle et fonctionnalités, cliquez sur **Ajouter les services de rôle requis**.</span><span class="sxs-lookup"><span data-stu-id="c2947-151">If you are prompted to install additional role services and features, click **Add Required Role Services**.</span></span> <span data-ttu-id="c2947-152">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2947-152">Click **Next**.</span></span>  
  
6. <span data-ttu-id="c2947-153">Si le résumé des sélections est correct, cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="c2947-153">If the summary of selections is correct, click **Install**.</span></span>  
  
7. <span data-ttu-id="c2947-154">Une fois l’installation terminée, cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="c2947-154">When installation completes, click **Close**.</span></span>  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a><span data-ttu-id="c2947-155">Pour installer IIS version 7.0 sur Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c2947-155">To install IIS version 7.0 on Windows Vista</span></span>  
  
1. <span data-ttu-id="c2947-156">Cliquez sur Démarrer, puis sur Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="c2947-156">Click Start, and then click Control Panel.</span></span>  
  
2. <span data-ttu-id="c2947-157">Sélectionnez le groupe **programmes** .</span><span class="sxs-lookup"><span data-stu-id="c2947-157">Select the **Programs** group.</span></span>  
  
3. <span data-ttu-id="c2947-158">Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="c2947-158">Under **Programs and Features**, click **Turn Windows Features on or off**.</span></span>  
  
4. <span data-ttu-id="c2947-159">La boîte de dialogue **contrôle de compte d’utilisateur** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c2947-159">The **User Account Control** dialog is displayed.</span></span> <span data-ttu-id="c2947-160">Cliquez sur **Continuer**.</span><span class="sxs-lookup"><span data-stu-id="c2947-160">Click **Continue**.</span></span>  
  
5. <span data-ttu-id="c2947-161">La boîte de dialogue **fonctionnalités de Windows** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c2947-161">The **Windows Features** dialog is displayed.</span></span> <span data-ttu-id="c2947-162">Développez l’élément intitulé **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="c2947-162">Expand the item labeled **Internet Information Services**.</span></span>  
  
6. <span data-ttu-id="c2947-163">Développez l’élément intitulé **Services World Wide Web**.</span><span class="sxs-lookup"><span data-stu-id="c2947-163">Expand the item labeled **World Wide Web Services**.</span></span>  
  
7. <span data-ttu-id="c2947-164">Développez l’élément **fonctionnalités de développement d’applications**.</span><span class="sxs-lookup"><span data-stu-id="c2947-164">Expand the item labeled **Application Development Features**.</span></span>  
  
8. <span data-ttu-id="c2947-165">Assurez-vous que les éléments suivants sont sélectionnés :</span><span class="sxs-lookup"><span data-stu-id="c2947-165">Make sure the following items are selected:</span></span>  
  
    1. <span data-ttu-id="c2947-166">**Extensibilité .NET**</span><span class="sxs-lookup"><span data-stu-id="c2947-166">**.NET Extensibility**</span></span>  
  
    2. <span data-ttu-id="c2947-167">**ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="c2947-167">**ASP.NET**</span></span>  
  
    3. <span data-ttu-id="c2947-168">**Extensions ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c2947-168">**ISAPI Extensions**</span></span>  
  
    4. <span data-ttu-id="c2947-169">**Filtres ISAPI**</span><span class="sxs-lookup"><span data-stu-id="c2947-169">**ISAPI Filters**</span></span>  
  
9. <span data-ttu-id="c2947-170">Développez l’élément **Outils d’administration Web**, puis sélectionnez **console de gestion IIS**.</span><span class="sxs-lookup"><span data-stu-id="c2947-170">Expand the item labeled **Web Management Tools**, and then select **IIS Management Console**.</span></span>  
  
10. <span data-ttu-id="c2947-171">Sous l’élément intitulé **Services World Wide Web**, développez **fonctionnalités http communes**.</span><span class="sxs-lookup"><span data-stu-id="c2947-171">Under the item labeled **World Wide Web Services**, expand **Common Http Features**.</span></span>  
  
11. <span data-ttu-id="c2947-172">Assurez-vous que **contenu statique** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c2947-172">Make sure **Static Content** is selected.</span></span>  
  
12. <span data-ttu-id="c2947-173">Sous l’élément nommé **World Wide Web services**, développez **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="c2947-173">Under the item labeled **World Wide Web Services**, expand **Security**.</span></span>  
  
13. <span data-ttu-id="c2947-174">Vérifiez que **l’option authentification Windows** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="c2947-174">Make sure **Windows Authentication** is selected.</span></span>  
  
14. <span data-ttu-id="c2947-175">Développez l’élément **compatibilité avec la gestion IIS 6**, puis sélectionnez **outils de script IIS 6**.</span><span class="sxs-lookup"><span data-stu-id="c2947-175">Expand the item labeled **IIS 6 Management Compatibility**, and then select **IIS 6 Scripting Tools**.</span></span>  
  
15. <span data-ttu-id="c2947-176">Développez l’élément intitulé **Microsoft .NET Framework 3,0**, puis sélectionnez **Windows Communication Foundation activation http**.</span><span class="sxs-lookup"><span data-stu-id="c2947-176">Expand the item labeled **Microsoft .NET Framework 3.0**, and then select **Windows Communication Foundation Http Activation**.</span></span>  
  
16. <span data-ttu-id="c2947-177">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2947-177">Click **OK**.</span></span>  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a><span data-ttu-id="c2947-178">Pour installer IIS version 6.0 sur Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="c2947-178">To install IIS version 6.0 on Windows Server 2003</span></span>  
  
1. <span data-ttu-id="c2947-179">Dans **gérer votre serveur**, cliquez sur **Ajouter ou supprimer un rôle**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2947-179">From **Manage Your Server**, click **Add or remove a role**, and then click **Next**.</span></span>  
  
2. <span data-ttu-id="c2947-180">Sélectionnez **serveur d’applications (IIS, ASP.net)** dans la liste **rôle de serveur** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2947-180">Select **Application server (IIS, ASP.NET)** from the **Server Role** list, and then click **Next**.</span></span>  
  
3. <span data-ttu-id="c2947-181">Activez la case à cocher **activer ASP.net** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2947-181">Select **Enable ASP.NET** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="c2947-182">Si l'aperçu des sélections est correct, cliquez sur Suivant.</span><span class="sxs-lookup"><span data-stu-id="c2947-182">If the summary of selections is correct, click Next.</span></span>  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a><span data-ttu-id="c2947-183">Pour installer IIS version 5.1 sur Windows XP avec Service Pack 2 et Service Pack 3 installés</span><span class="sxs-lookup"><span data-stu-id="c2947-183">To install IIS version 5.1 on Windows XP with Service Pack 2 and Service Pack 3 installed</span></span>  
  
1. <span data-ttu-id="c2947-184">Dans le Panneau de configuration, cliquez sur **Ajout/Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="c2947-184">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2. <span data-ttu-id="c2947-185">Dans la boîte de dialogue **Ajouter ou supprimer des programmes**, cliquez sur **Ajouter ou supprimer des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="c2947-185">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3. <span data-ttu-id="c2947-186">Dans l **'Assistant composants de Windows**, activez la case à cocher **Internet Information Services (IIS)** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c2947-186">In the **Windows Components Wizard**, select the **Internet Information Services (IIS)** check box, and then click **Next**.</span></span>  
  
4. <span data-ttu-id="c2947-187">Si la boîte de dialogue **fichiers nécessaires** s’affiche, insérez le disque d’installation du système d’exploitation, accédez au dossier i386, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2947-187">If the **Files Needed** dialog box is displayed, insert your operating system installation disc, browse to the i386 folder, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="c2947-188">Une fois l’installation terminée, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="c2947-188">When installation completes, click **Finish**.</span></span>  
  
6. <span data-ttu-id="c2947-189">Fermez la boîte de dialogue **Ajout/suppression de programmes** , puis fermez le **panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="c2947-189">Close the **Add or Remove Programs** dialog box, and then close **Control Panel**.</span></span>  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a><span data-ttu-id="c2947-190">Pour vérifier l'installation d'IIS et d'ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2947-190">To verify the installation of IIS and ASP.NET</span></span>  
  
1. <span data-ttu-id="c2947-191">Enregistrez le fichier HTML indiqué à la fin de cette rubrique dans le répertoire \InetPub\wwwroot racine et nommez-le Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="c2947-191">Save the HTML file found at the end of this topic in the root \InetPub\wwwroot directory and name it Default.aspx.</span></span>  
  
2. <span data-ttu-id="c2947-192">Ouvrez une fenêtre de navigateur.</span><span class="sxs-lookup"><span data-stu-id="c2947-192">Open a browser window.</span></span>  
  
3. <span data-ttu-id="c2947-193">Tapez `http://localhost/Default.aspx` dans la zone adresse, puis appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="c2947-193">Type `http://localhost/Default.aspx` in the address box, and then press ENTER.</span></span>  
  
4. <span data-ttu-id="c2947-194">Une page web contenant le texte « Hello World » doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="c2947-194">A Web page with the text "Hello World" should appear.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2947-195">Chaque fois que vous installez une nouvelle version du .NET Framework, vous devez réinscrire aspnet_isapi en tant qu’extension de service Web pour IIS.</span><span class="sxs-lookup"><span data-stu-id="c2947-195">Each time you install a new version of the .NET Framework, you must re-register aspnet_isapi as a Web service extension for IIS.</span></span> <span data-ttu-id="c2947-196">Pour ce faire, émettez la commande `aspnet_regiis –I –enable`.</span><span class="sxs-lookup"><span data-stu-id="c2947-196">To do so, issue the `aspnet_regiis –I –enable` command.</span></span>  
  
## <a name="sample-code"></a><span data-ttu-id="c2947-197">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="c2947-197">Sample Code</span></span>  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
