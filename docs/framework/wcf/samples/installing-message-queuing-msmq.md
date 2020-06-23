---
title: Installation de Message Queuing (MSMQ)
description: Découvrez comment installer Message Queuing 4,0 et Message Queuing 3,0 à utiliser avec les exemples WFC dans le cadre d’une procédure d’installation unique.
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 0d0cb87b40b1cb11eb7692c2fa1e890ec815b13d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244463"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="dc14c-103">Installation de Message Queuing (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="dc14c-103">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="dc14c-104">Les procédures suivantes indiquent comment installer Message Queuing 4.0 et Message Queuing 3.0.</span><span class="sxs-lookup"><span data-stu-id="dc14c-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc14c-105">Message Queuing 4,0 n’est pas disponible dans Windows XP et Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="dc14c-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="dc14c-106">Pour installer Message Queuing 4.0 sur Windows Server 2008 ou Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="dc14c-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="dc14c-107">Dans Gestionnaire de serveur, cliquez sur **fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="dc14c-108">Dans le volet de droite, sous **Résumé des fonctionnalités**, cliquez sur **Ajouter des fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="dc14c-109">Dans la fenêtre qui s’affiche, développez **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="dc14c-110">Développez **Services Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="dc14c-111">Cliquez sur **intégration des services d’annuaire** (pour les ordinateurs joints à un domaine), puis cliquez sur **prise en charge http**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="dc14c-112">Cliquez sur **suivant**, puis sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="dc14c-113">Pour installer Message Queuing 4.0 sur Windows 7 ou Windows Vista</span><span class="sxs-lookup"><span data-stu-id="dc14c-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="dc14c-114">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="dc14c-115">Cliquez sur **programmes** puis, sous **programmes et fonctionnalités**, cliquez sur **activer et désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="dc14c-116">Développez Microsoft Message Queue Server (MSMQ), développez le noyau du serveur MSMQ (Microsoft Message Queue), puis cochez les cases des fonctionnalités Message Queuing à installer :</span><span class="sxs-lookup"><span data-stu-id="dc14c-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="dc14c-117">Intégration des services de domaine Active Directory MSMQ (pour les ordinateurs liés à un domaine).</span><span class="sxs-lookup"><span data-stu-id="dc14c-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="dc14c-118">Prise en charge HTTP MSMQ.</span><span class="sxs-lookup"><span data-stu-id="dc14c-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="dc14c-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="dc14c-120">Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="dc14c-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="dc14c-121">Pour installer Message Queuing 3.0 sur Windows XP et Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="dc14c-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="dc14c-122">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="dc14c-123">Cliquez sur **Ajout/suppression de programmes** , puis sur Ajouter des **composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="dc14c-124">Sélectionnez Message Queuing, puis cliquez sur **Détails**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="dc14c-125">Si vous exécutez Windows Server 2003, sélectionnez serveur d’applications pour accéder à Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="dc14c-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="dc14c-126">Vérifiez que l'option Prise en charge HTTP MSMQ est activée dans la page de détails.</span><span class="sxs-lookup"><span data-stu-id="dc14c-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="dc14c-127">Cliquez sur **OK** pour quitter la page de détails, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="dc14c-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="dc14c-128">Terminez l'installation.</span><span class="sxs-lookup"><span data-stu-id="dc14c-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="dc14c-129">Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="dc14c-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc14c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc14c-130">See also</span></span>

- [<span data-ttu-id="dc14c-131">Instructions d'installation</span><span class="sxs-lookup"><span data-stu-id="dc14c-131">Set-Up Instructions</span></span>](set-up-instructions.md)
