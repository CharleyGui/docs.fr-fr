---
title: Instructions sur les pare-feu
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: e2c4dd8e784599a5e110e7454d9d0e709cbc5776
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544780"
---
# <a name="firewall-instructions"></a><span data-ttu-id="867c2-102">Instructions sur les pare-feu</span><span class="sxs-lookup"><span data-stu-id="867c2-102">Firewall Instructions</span></span>
<span data-ttu-id="867c2-103">Vous devez activer plusieurs ports ou programmes dans le pare-feu pour que les exemples Windows Communication Foundation (WCF) puissent fonctionner.</span><span class="sxs-lookup"><span data-stu-id="867c2-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="867c2-104">Un grand nombre d'exemples communique en utilisant des ports contenus dans la plage 8000-8003, ainsi que le port 9000.</span><span class="sxs-lookup"><span data-stu-id="867c2-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="867c2-105">Le pare-feu est activé par défaut et empêche l'accès à ces ports.</span><span class="sxs-lookup"><span data-stu-id="867c2-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="867c2-106">Pour activer le pare-feu pour les exemples, exécutez l’une des procédures suivantes, selon vos besoins et votre environnement de sécurité :</span><span class="sxs-lookup"><span data-stu-id="867c2-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
- <span data-ttu-id="867c2-107">Option 1: Activation interactive des exemples en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="867c2-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="867c2-108">N'apportez aucune modification à l'avance à votre configuration de pare-feu et lancez la création et l'exécution des exemples.</span><span class="sxs-lookup"><span data-stu-id="867c2-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="867c2-109">Quand un exemple est exécuté, une boîte de dialogue **alerte de sécurité Windows** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="867c2-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="867c2-110">L'exemple de programme en question peut ensuite être ajouté interactivement à une liste non bloquée.</span><span class="sxs-lookup"><span data-stu-id="867c2-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="867c2-111">Dans le cadre de cette procédure, vous devrez peut-être redémarrer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="867c2-111">With this procedure, you may have to then restart the sample.</span></span>  
  
- <span data-ttu-id="867c2-112">Option 2: Activation des exemples de programmes à l'avance.</span><span class="sxs-lookup"><span data-stu-id="867c2-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="867c2-113">Démarrez l’applet du **panneau de configuration du pare-feu Windows** et activez les exemples de programmes que vous prévoyez d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="867c2-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="867c2-114">Vous devez générer en premier les programmes afin que les fichiers exécutables existent.</span><span class="sxs-lookup"><span data-stu-id="867c2-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="867c2-115">Vous trouverez des instructions plus détaillées dans la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="867c2-115">You can find more detailed instructions in the following procedure.</span></span>  
  
- <span data-ttu-id="867c2-116">Option 3: Activation d'une plage de ports à l'avance.</span><span class="sxs-lookup"><span data-stu-id="867c2-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="867c2-117">Démarrez l’applet du **panneau de configuration** du **pare-feu Windows** et activez les ports 80, 443, 8000-8003 et 9000, qui sont utilisés par les exemples.</span><span class="sxs-lookup"><span data-stu-id="867c2-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="867c2-118">Vous trouverez des instructions plus détaillées dans la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="867c2-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="867c2-119">Cette option est moins sécurisée que les autres, car elle permet à tout programme d'utiliser ces ports, et non aux exemples uniquement.</span><span class="sxs-lookup"><span data-stu-id="867c2-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="867c2-120">Si vous ne savez pas quelle procédure utiliser, choisissez la première option.</span><span class="sxs-lookup"><span data-stu-id="867c2-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="867c2-121">Si vous utilisez le pare-feu d'un autre fournisseur, vous devrez peut-être apporter des modifications semblables.</span><span class="sxs-lookup"><span data-stu-id="867c2-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="867c2-122">La modification de votre configuration de pare-feu affecte votre sécurité.</span><span class="sxs-lookup"><span data-stu-id="867c2-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="867c2-123">Il est recommandé d'enregistrer les modifications apportées et de les supprimer lorsque vous n'utilisez plus les exemples.</span><span class="sxs-lookup"><span data-stu-id="867c2-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="867c2-124">Pour activer à l'avance les programmes d'exemples</span><span class="sxs-lookup"><span data-stu-id="867c2-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="867c2-125">Générez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="867c2-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="867c2-126">Cliquez sur **Démarrer**, sur **exécuter**, puis tapez `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="867c2-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="867c2-127">L’applet du **panneau de configuration du pare-feu Windows** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="867c2-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="867c2-128">Pour exécuter des exemples qui requièrent la capacité de communiquer via le Pare-feu Windows, vous devez disposer des autorisations nécessaires pour modifier les paramètres du Pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="867c2-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="867c2-129">Si certains paramètres du pare-feu ne sont pas disponibles et que votre ordinateur est connecté à un domaine, il est possible que votre administrateur système contrôle ces paramètres au moyen d'une stratégie de groupe.</span><span class="sxs-lookup"><span data-stu-id="867c2-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="867c2-130">Effectuez l'une des étapes suivantes, selon votre système d'exploitation, pour autoriser un programme via le Pare-feu Windows :</span><span class="sxs-lookup"><span data-stu-id="867c2-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    - <span data-ttu-id="867c2-131">Sur Windows 7 ou Windows Server 2008 R2, cliquez sur **autoriser un programme ou une fonctionnalité via le pare-feu Windows**.</span><span class="sxs-lookup"><span data-stu-id="867c2-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="867c2-132">Cliquez sur **modifier les paramètres**, autoriser **un autre programme...** .</span><span class="sxs-lookup"><span data-stu-id="867c2-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    - <span data-ttu-id="867c2-133">Sur Windows Vista ou Windows Server 2008, cliquez sur **autoriser un programme via le pare-feu Windows**.</span><span class="sxs-lookup"><span data-stu-id="867c2-133">On Windows Vista or Windows Server 2008, click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="867c2-134">Sous l’onglet **exceptions** , cliquez sur **Ajouter un programme**.</span><span class="sxs-lookup"><span data-stu-id="867c2-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="867c2-135">Cliquez sur le bouton **Parcourir** et sélectionnez le fichier exécutable de l’exemple que vous prévoyez d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="867c2-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="867c2-136">Répétez les étapes 4 et 5 jusqu’à ce que vous ayez ajouté les fichiers exécutables de tous les exemples que vous prévoyez d’exécuter.</span><span class="sxs-lookup"><span data-stu-id="867c2-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="867c2-137">Cliquez sur **OK** pour fermer l’applet de pare-feu.</span><span class="sxs-lookup"><span data-stu-id="867c2-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="867c2-138">Pour activer une plage de ports à l'avance</span><span class="sxs-lookup"><span data-stu-id="867c2-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="867c2-139">Cliquez sur **Démarrer**, sur **exécuter**, puis tapez `firewall.cpl`.</span><span class="sxs-lookup"><span data-stu-id="867c2-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="867c2-140">L’applet du **panneau de configuration du pare-feu Windows** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="867c2-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="867c2-141">Sur Windows 7 ou Windows Server 2008 R2, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="867c2-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1. <span data-ttu-id="867c2-142">Cliquez sur **Paramètres avancés** dans la colonne de gauche de la fenêtre du pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="867c2-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2. <span data-ttu-id="867c2-143">Dans la colonne de gauche, cliquez sur **règles de trafic entrant** .</span><span class="sxs-lookup"><span data-stu-id="867c2-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3. <span data-ttu-id="867c2-144">Cliquez sur **nouvelles règles** dans la colonne de droite.</span><span class="sxs-lookup"><span data-stu-id="867c2-144">Click **New Rules** in the right column.</span></span>  
  
    4. <span data-ttu-id="867c2-145">Sélectionnez **port** et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="867c2-145">Select **Port** and click **next**.</span></span>  
  
    5. <span data-ttu-id="867c2-146">Sélectionnez **TCP** et entrez `8000, 8001, 8002, 8003, 9000, 80, 443` dans le champ **ports locaux spécifiques** .</span><span class="sxs-lookup"><span data-stu-id="867c2-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6. <span data-ttu-id="867c2-147">Cliquez sur **Next**.</span><span class="sxs-lookup"><span data-stu-id="867c2-147">Click **Next**.</span></span>  
  
    7. <span data-ttu-id="867c2-148">Sélectionnez **autoriser la connexion**, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="867c2-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8. <span data-ttu-id="867c2-149">Sélectionnez **domaine** et **privé**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="867c2-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="867c2-150">Nommez cette règle `WCF-WF 4.0 Samples`, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="867c2-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="867c2-151">Cliquez sur **règles de trafic sortant** et répétez les étapes c à h.</span><span class="sxs-lookup"><span data-stu-id="867c2-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="867c2-152">Sur Windows Vista ou Windows Server 2008, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="867c2-152">On Windows Vista or Windows Server 2008, follow these steps.</span></span>  
  
    1. <span data-ttu-id="867c2-153">Cliquez sur **Autoriser un programme via le Pare-feu Windows**.</span><span class="sxs-lookup"><span data-stu-id="867c2-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2. <span data-ttu-id="867c2-154">Sous l’onglet **exceptions** , cliquez sur **Ajouter un port**.</span><span class="sxs-lookup"><span data-stu-id="867c2-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3. <span data-ttu-id="867c2-155">Entrez un nom, entrez 8000 comme numéro de port, puis sélectionnez l’option **TCP** .</span><span class="sxs-lookup"><span data-stu-id="867c2-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4. <span data-ttu-id="867c2-156">Cliquez sur le bouton **modifier l’étendue** , sélectionnez l’option **mon réseau** (sous-réseau uniquement), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="867c2-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5. <span data-ttu-id="867c2-157">Répétez les étapes b à d pour les ports 8001, 8002, 8003, 9000, 80 et 443.</span><span class="sxs-lookup"><span data-stu-id="867c2-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="867c2-158">Cliquez sur **OK** pour fermer l’applet de pare-feu.</span><span class="sxs-lookup"><span data-stu-id="867c2-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="867c2-159">Supprimez toutes les exceptions de pare-feu une fois que vous n'utilisez plus les exemples.</span><span class="sxs-lookup"><span data-stu-id="867c2-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="867c2-160">Pour ce faire, ouvrez l’applet du **panneau de configuration du pare-feu Windows** et supprimez tous les programmes ou entrées de port ajoutés par les procédures précédentes.</span><span class="sxs-lookup"><span data-stu-id="867c2-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
