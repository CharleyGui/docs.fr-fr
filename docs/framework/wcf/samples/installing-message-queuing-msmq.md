---
title: Installation de Message Queuing (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 8ecbd07adfb6bfb4e9898f9b8508809480d17e16
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921102"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="07f74-102">Installation de Message Queuing (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="07f74-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="07f74-103">Les procédures suivantes indiquent comment installer Message Queuing 4.0 et Message Queuing 3.0.</span><span class="sxs-lookup"><span data-stu-id="07f74-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07f74-104">Message Queuing 4,0 n’est pas disponible dans Windows XP et Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="07f74-104">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="07f74-105">Pour installer Message Queuing 4.0 sur Windows Server 2008 ou Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="07f74-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="07f74-106">Dans Gestionnaire de serveur, cliquez sur **fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="07f74-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="07f74-107">Dans le volet de droite, sous **Résumé des fonctionnalités**, cliquez sur **Ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="07f74-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="07f74-108">Dans la fenêtre qui s’affiche, développez **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="07f74-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="07f74-109">Développez **Services Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="07f74-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="07f74-110">Cliquez sur **intégration des services d’annuaire** (pour les ordinateurs joints à un domaine), puis cliquez sur **prise en charge http**.</span><span class="sxs-lookup"><span data-stu-id="07f74-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="07f74-111">Cliquez sur **suivant**, puis sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="07f74-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="07f74-112">Pour installer Message Queuing 4.0 sur Windows 7 ou Windows Vista</span><span class="sxs-lookup"><span data-stu-id="07f74-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="07f74-113">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="07f74-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="07f74-114">Cliquez sur **programmes** puis, sous **programmes et fonctionnalités**, cliquez sur **activer et désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="07f74-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="07f74-115">Développez Microsoft Message Queue Server (MSMQ), développez Noyau du serveur MSMQ (Microsoft Message Queue), puis cochez les cases des fonctionnalités Message Queuing à installer :</span><span class="sxs-lookup"><span data-stu-id="07f74-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="07f74-116">Intégration des services de domaine Active Directory MSMQ (pour les ordinateurs liés à un domaine).</span><span class="sxs-lookup"><span data-stu-id="07f74-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="07f74-117">Prise en charge HTTP MSMQ.</span><span class="sxs-lookup"><span data-stu-id="07f74-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="07f74-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07f74-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="07f74-119">Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="07f74-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="07f74-120">Pour installer Message Queuing 3.0 sur Windows XP et Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="07f74-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="07f74-121">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="07f74-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="07f74-122">Cliquez sur **Ajout/suppression de programmes** , puis sur Ajouter des **composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="07f74-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="07f74-123">Sélectionnez Message Queuing, puis cliquez sur **Détails**.</span><span class="sxs-lookup"><span data-stu-id="07f74-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="07f74-124">Si vous exécutez Windows Server 2003, sélectionnez serveur d’applications pour accéder à Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="07f74-124">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="07f74-125">Vérifiez que l'option Prise en charge HTTP MSMQ est activée dans la page de détails.</span><span class="sxs-lookup"><span data-stu-id="07f74-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="07f74-126">Cliquez sur **OK** pour quitter la page de détails, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="07f74-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="07f74-127">Terminez l'installation.</span><span class="sxs-lookup"><span data-stu-id="07f74-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="07f74-128">Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="07f74-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f74-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07f74-129">See also</span></span>

- [<span data-ttu-id="07f74-130">Instructions d’installation</span><span class="sxs-lookup"><span data-stu-id="07f74-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
