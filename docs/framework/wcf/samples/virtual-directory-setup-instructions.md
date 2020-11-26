---
title: Instructions d'installation du répertoire virtuel
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: dba6547888935ccf36ec0924fd3c95e8fbda5688
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243649"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="cf66c-102">Instructions d'installation du répertoire virtuel</span><span class="sxs-lookup"><span data-stu-id="cf66c-102">Virtual Directory Setup Instructions</span></span>

<span data-ttu-id="cf66c-103">Les exemples de Windows Communication Foundation (WCF) sont destinés à partager un répertoire virtuel commun nommé servicemodelsamples mappé au dossier%SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cf66c-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf66c-104">%SystemDrive% correspond généralement à C: ou D:, en fonction de l'emplacement de lecteur où Internet Information Services (IIS) est installé.</span><span class="sxs-lookup"><span data-stu-id="cf66c-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="cf66c-105">Vous pouvez exécuter les fichiers Setupvroot.bat et Cleanupvroot.bat à partir de la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md) afin de créer le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="cf66c-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="cf66c-106">Si vous préférez créer le répertoire virtuel manuellement, exécutez les procédures suivantes.</span><span class="sxs-lookup"><span data-stu-id="cf66c-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="cf66c-107">Procédures</span><span class="sxs-lookup"><span data-stu-id="cf66c-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="cf66c-108">Pour créer un répertoire virtuel dans IIS 7,0 ou 7,5</span><span class="sxs-lookup"><span data-stu-id="cf66c-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cf66c-109">Dans le menu **Démarrer** , cliquez sur **exécuter**, puis tapez **inetmgr** pour ouvrir le composant logiciel enfichable MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="cf66c-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="cf66c-110">Dans le volet gauche, développez le nœud portant le nom de l’ordinateur, puis développez le nœud **sites** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="cf66c-111">Cliquez avec le bouton droit sur **site Web par défaut**, puis sélectionnez **Ajouter une application** pour ouvrir la **fenêtre Ajouter une application**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="cf66c-112">Dans la fenêtre, tapez `servicemodelsamples` comme alias pour le répertoire virtuel que vous créez.</span><span class="sxs-lookup"><span data-stu-id="cf66c-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="cf66c-113">Créez le répertoire suivant : %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="cf66c-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="cf66c-114">Affectez la valeur %SystemDrive%\inetpub\wwwroot\servicemodelsamples au chemin d’accès physique.</span><span class="sxs-lookup"><span data-stu-id="cf66c-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="cf66c-115">La plupart des exemples WCF copient les fichiers exécutables de service dans cet emplacement une fois générés.</span><span class="sxs-lookup"><span data-stu-id="cf66c-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="cf66c-116">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-116">Click **OK**.</span></span> <span data-ttu-id="cf66c-117">L'application Web est créée pour les exemples WCF.</span><span class="sxs-lookup"><span data-stu-id="cf66c-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cf66c-118">Cette tâche ne doit être effectuée qu’une seule fois, car tous les exemples WCF utilisent la même application Web servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cf66c-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cf66c-119">Dans cette documentation, le terme `virtual directory` est synonyme du terme `Web application`.</span><span class="sxs-lookup"><span data-stu-id="cf66c-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="cf66c-120">En plus de créer le répertoire virtuel, vous devez également définir ses propriétés pour permettre l’exécution des services WCF.</span><span class="sxs-lookup"><span data-stu-id="cf66c-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="cf66c-121">Voir les détails ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="cf66c-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="cf66c-122">Pour créer un répertoire virtuel dans IIS 5.1 ou 6.0 :</span><span class="sxs-lookup"><span data-stu-id="cf66c-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cf66c-123">Ouvrez une fenêtre d’invite de commandes et tapez `start inetmgr` pour ouvrir le composant logiciel enfichable MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="cf66c-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="cf66c-124">Dans le volet gauche, développez le nœud portant le nom de l’ordinateur, puis développez le nœud **sites Web** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="cf66c-125">Cliquez avec le bouton droit sur **site Web par défaut** et sélectionnez **nouveau, répertoire virtuel** pour ouvrir l’Assistant Création de répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="cf66c-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="cf66c-126">Dans l’Assistant, tapez `servicemodelsamples` comme alias pour le répertoire virtuel que vous créez.</span><span class="sxs-lookup"><span data-stu-id="cf66c-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="cf66c-127">Affectez la valeur %SystemDrive%\inetpub\wwwroot\servicemodelsamples au chemin.</span><span class="sxs-lookup"><span data-stu-id="cf66c-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="cf66c-128">La plupart des exemples WCF copient les fichiers exécutables de service dans cet emplacement une fois générés.</span><span class="sxs-lookup"><span data-stu-id="cf66c-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="cf66c-129">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-129">Click **Next**.</span></span>  
  
7. <span data-ttu-id="cf66c-130">Les cases à cocher suivantes sont activées par défaut :</span><span class="sxs-lookup"><span data-stu-id="cf66c-130">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="cf66c-131">**Lire**</span><span class="sxs-lookup"><span data-stu-id="cf66c-131">**Read**</span></span>  
  
    - <span data-ttu-id="cf66c-132">**Exécuter les scripts (tels que ASP)**</span><span class="sxs-lookup"><span data-stu-id="cf66c-132">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="cf66c-133">Cliquez sur **suivant**, puis sur **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="cf66c-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cf66c-134">Cette tâche ne doit être effectuée qu’une seule fois, car tous les exemples WCF utilisent le même répertoire virtuel servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cf66c-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="cf66c-135">Pour définir des propriétés de répertoire virtuel supplémentaires dans IIS 7,0 ou 7,5</span><span class="sxs-lookup"><span data-stu-id="cf66c-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cf66c-136">Cliquez sur le nœud servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cf66c-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="cf66c-137">Deux vues figurent au bas de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="cf66c-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="cf66c-138">Sélectionnez **affichage des fonctionnalités** s’il n’est pas déjà sélectionné.</span><span class="sxs-lookup"><span data-stu-id="cf66c-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="cf66c-139">Double-cliquez sur l’entrée pour l' **exploration des répertoires**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="cf66c-140">Dans le volet Actions, sélectionnez l’option **activer** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="cf66c-141">Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.</span><span class="sxs-lookup"><span data-stu-id="cf66c-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="cf66c-142">Enfin, vous devez définir les propriétés de sécurité du dossier servicemodelsamples afin d’autoriser son accès.</span><span class="sxs-lookup"><span data-stu-id="cf66c-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="cf66c-143">Voir les détails ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="cf66c-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="cf66c-144">Pour définir des propriétés de répertoire virtuel supplémentaires dans IIS 5.1 ou 6.0</span><span class="sxs-lookup"><span data-stu-id="cf66c-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cf66c-145">Cliquez avec le bouton droit sur le nœud servicemodelsamples, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="cf66c-146">Les cases à cocher suivantes sont activées par défaut :</span><span class="sxs-lookup"><span data-stu-id="cf66c-146">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="cf66c-147">**Lire**</span><span class="sxs-lookup"><span data-stu-id="cf66c-147">**Read**</span></span>  
  
    - <span data-ttu-id="cf66c-148">**Visites des journaux**</span><span class="sxs-lookup"><span data-stu-id="cf66c-148">**Log visits**</span></span>  
  
    - <span data-ttu-id="cf66c-149">**Indexer cette ressource**</span><span class="sxs-lookup"><span data-stu-id="cf66c-149">**Index this resource**</span></span>  
  
3. <span data-ttu-id="cf66c-150">Activez la case à cocher **exploration de répertoire** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="cf66c-151">Cela permet d'accéder au répertoire du répertoire à l'aide d'Internet Explorer, ce qui est utile lors du débogage d'un service.</span><span class="sxs-lookup"><span data-stu-id="cf66c-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="cf66c-152">Pour définir les propriétés de sécurité du dossier dans IIS 7,0 ou 7,5</span><span class="sxs-lookup"><span data-stu-id="cf66c-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="cf66c-153">Ouvrez le répertoire %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cf66c-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="cf66c-154">Cliquez avec le bouton droit sur le dossier servicemodelsamples, puis cliquez sur **partager** ou **partager avec**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="cf66c-155">Cliquez sur la flèche vers le bas située à gauche du bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="cf66c-156">Sélectionnez l’entrée **Rechercher** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-156">Select the **Find** entry.</span></span> <span data-ttu-id="cf66c-157">La fenêtre **Sélectionner les utilisateurs ou les groupes** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="cf66c-157">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="cf66c-158">Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-158">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="cf66c-159">Cliquez sur **Emplacements**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-159">Click **Locations**.</span></span> <span data-ttu-id="cf66c-160">La fenêtre **emplacements** est maintenant ouverte.</span><span class="sxs-lookup"><span data-stu-id="cf66c-160">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="cf66c-161">Sélectionnez l'entrée correspondant à l'ordinateur en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="cf66c-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="cf66c-162">Il est important de sélectionner l'ordinateur local et non une entrée correspondant à tous les domaines ou réseaux répertoriés.</span><span class="sxs-lookup"><span data-stu-id="cf66c-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="cf66c-163">Une fois l’ordinateur sélectionné, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-163">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="cf66c-164">Cliquez sur **Rechercher**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-164">Click **Find Now**.</span></span> <span data-ttu-id="cf66c-165">Cela permet d'inclure dans les résultats de la recherche les objets associés à l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="cf66c-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="cf66c-166">Recherchez l’entrée **IIS_IUSRS** dans la colonne **nom (nom unique relatif)** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="cf66c-167">Sélectionnez cette entrée, puis cliquez sur **OK** pour fermer la fenêtre résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="cf66c-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="cf66c-168">Cliquez sur **OK** pour fermer la fenêtre **Sélectionner les utilisateurs ou les groupes** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="cf66c-169">Cliquez sur **partager** pour rendre les modifications persistantes.</span><span class="sxs-lookup"><span data-stu-id="cf66c-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="cf66c-170">Une fois que les modifications apportées à activer le partage sont terminées, cliquez sur **terminé** pour fermer la fenêtre de **partage de fichiers** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="cf66c-171">Pour définir les propriétés de sécurité de ce dossier dans IIS 5.1 ou 6.0 :</span><span class="sxs-lookup"><span data-stu-id="cf66c-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="cf66c-172">Ouvrez le répertoire %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="cf66c-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="cf66c-173">Cliquez avec le bouton droit sur le dossier **servicemodelsamples** , puis cliquez sur **partage et sécurité.**</span><span class="sxs-lookup"><span data-stu-id="cf66c-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="cf66c-174">Cliquez sur l’onglet **Security** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-174">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="cf66c-175">Si vous utilisez IIS 6,0, dans la zone **noms de groupes ou d’utilisateurs** , vérifiez si le **compte invité Internet** est répertorié.</span><span class="sxs-lookup"><span data-stu-id="cf66c-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="cf66c-176">Si elle ne s'y trouve pas :</span><span class="sxs-lookup"><span data-stu-id="cf66c-176">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="cf66c-177">Cliquez sur **Démarrer** , puis sur **panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="cf66c-178">Si vous ne voyez pas l’icône **comptes d’utilisateur** , cliquez sur **basculer vers l’affichage des catégories**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="cf66c-179">Cliquez sur l’icône **comptes d’utilisateurs** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-179">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="cf66c-180">Sous « ou choisissez une icône du panneau de configuration », cliquez sur **comptes d’utilisateurs**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="cf66c-181">Dans la boîte de dialogue **comptes d’utilisateur** , cliquez sur l’onglet **avancé** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="cf66c-182">Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-182">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="cf66c-183">Dans la boîte de dialogue **utilisateurs et groupes locaux** , cliquez pour développer le dossier **utilisateurs** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="cf66c-184">Dans le volet droit, double-cliquez sur **compte invité Internet**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="cf66c-185">Dans la boîte de dialogue **Propriétés** , copiez le nom utilisé en tant que compte invité Internet.</span><span class="sxs-lookup"><span data-stu-id="cf66c-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="cf66c-186">Par défaut, le nom commence par « USR_ » suivi du nom de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cf66c-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="cf66c-187">Fermez la boîte de dialogue **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="cf66c-188">Fermez la boîte de dialogue **utilisateurs et groupes locaux** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="cf66c-189">Fermez la boîte de dialogue **comptes d’utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="cf66c-190">Fermez la boîte de dialogue autres **comptes d’utilisateur** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="cf66c-191">Dans la boîte de dialogue **Propriétés de servicemodelsamples** , sous l’onglet **sécurité** , cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="cf66c-192">Tapez le nom de l’ordinateur suivi d’une barre oblique inverse, puis collez le nom du compte d’utilisateur Internet, par exemple myMachineName \\ % InternetGuestAccountName%.</span><span class="sxs-lookup"><span data-stu-id="cf66c-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="cf66c-193">Cliquez sur **vérifier les noms** pour vérifier l’ajout.</span><span class="sxs-lookup"><span data-stu-id="cf66c-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="cf66c-194">S'il est valide, ce nom figure en majuscules soulignées.</span><span class="sxs-lookup"><span data-stu-id="cf66c-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="cf66c-195">Pour IIS 6,0, vérifiez également que SERVICE réseau est indiqué dans la zone **noms de groupes ou d’utilisateurs** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="cf66c-196">Si SERVICE RÉSEAU n'est pas répertorié :</span><span class="sxs-lookup"><span data-stu-id="cf66c-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="cf66c-197">Cliquez sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-197">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="cf66c-198">Dans la boîte de dialogue **Sélectionner les utilisateurs ou les groupes** , tapez le nom de l’ordinateur suivi d’une barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="cf66c-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="cf66c-199">Tapez **service** après la barre oblique inverse (sans espace).</span><span class="sxs-lookup"><span data-stu-id="cf66c-199">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="cf66c-200">Cliquez sur **vérifier les noms**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-200">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="cf66c-201">Si plusieurs noms sont trouvés, sélectionnez **service réseau** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="cf66c-202">Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner des utilisateurs ou des groupes** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="cf66c-203">Si vous utilisez Windows XP SP2 avec IIS 5,1, vérifiez que compte invité Internet et ASPNET sont répertoriés dans la zone **noms de groupes ou d’utilisateurs** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="cf66c-204">Notez que l’utilisateur ASPNET peut être membre du groupe de sécurité **utilisateurs** intégré.</span><span class="sxs-lookup"><span data-stu-id="cf66c-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="cf66c-205">Si c’est le cas, si le groupe **utilisateurs** est répertorié dans la boîte de dialogue, vous n’avez pas besoin de l’ajouter en tant qu’élément distinct à la liste des utilisateurs autorisés.</span><span class="sxs-lookup"><span data-stu-id="cf66c-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="cf66c-206">Pour vérifier si ASPNET fait partie du groupe de sécurité **utilisateurs** :</span><span class="sxs-lookup"><span data-stu-id="cf66c-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="cf66c-207">Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="cf66c-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="cf66c-208">Cliquez sur l’icône **comptes d’utilisateurs** .</span><span class="sxs-lookup"><span data-stu-id="cf66c-208">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="cf66c-209">Dans la colonne **groupe** , vérifiez que la valeur de **ASPNET** est « utilisateurs ».</span><span class="sxs-lookup"><span data-stu-id="cf66c-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf66c-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf66c-210">See also</span></span>

- [<span data-ttu-id="cf66c-211">Instructions relatives à l'hébergement dans les Services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="cf66c-211">Internet Information Service Hosting Instructions</span></span>](internet-information-service-hosting-instructions.md)
