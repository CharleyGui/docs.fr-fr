---
title: 'Procédure : afficher les certificats avec le composant logiciel enfichable MMC'
description: Un client ou un service WCF sécurisé peut utiliser un certificat comme informations d’identification. En savoir plus sur les types de magasins de certificats que vous pouvez examiner à l’aide du plug-in MMC.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 1f20384f16b3b5b898f926258d76a6a2773eaaa1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280622"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="a758a-104">Procédure : afficher les certificats avec le composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="a758a-104">How to: View certificates with the MMC snap-in</span></span>

<span data-ttu-id="a758a-105">Lorsque vous créez un client ou un service sécurisé, vous pouvez utiliser un [certificat](working-with-certificates.md) comme informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a758a-105">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="a758a-106">Par exemple, un type commun d’informations d’identification est le certificat X. 509, que vous créez à l’aide de la <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="a758a-106">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="a758a-107">Il existe trois types différents de magasins de certificats que vous pouvez examiner avec la console MMC (Microsoft Management Console) sur les systèmes Windows :</span><span class="sxs-lookup"><span data-stu-id="a758a-107">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="a758a-108">Ordinateur local : le magasin est local sur l’appareil et global pour tous les utilisateurs sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="a758a-108">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="a758a-109">Utilisateur actuel : le magasin est local sur le compte d’utilisateur actuel sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="a758a-109">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="a758a-110">Compte de service : le magasin est local pour un service particulier sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="a758a-110">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="a758a-111">Afficher les certificats dans le composant logiciel enfichable MMC</span><span class="sxs-lookup"><span data-stu-id="a758a-111">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="a758a-112">La procédure suivante montre comment examiner les magasins sur votre appareil local pour trouver un certificat approprié :</span><span class="sxs-lookup"><span data-stu-id="a758a-112">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="a758a-113">Sélectionnez **exécuter** dans le menu **Démarrer** , puis entrez *MMC*.</span><span class="sxs-lookup"><span data-stu-id="a758a-113">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="a758a-114">La console MMC s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a758a-114">The MMC appears.</span></span>
  
2. <span data-ttu-id="a758a-115">Dans le menu **fichier** , sélectionnez **Ajouter/supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="a758a-115">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="a758a-116">La fenêtre **Ajouter ou supprimer des composants logiciels enfichables** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a758a-116">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="a758a-117">Dans la liste **composants logiciels enfichables disponibles** , cliquez sur **certificats**, puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="a758a-117">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Ajouter un composant logiciel enfichable certificat](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="a758a-119">Dans la fenêtre du **composant logiciel enfichable Certificats** , sélectionnez **compte d’ordinateur**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a758a-119">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="a758a-120">Si vous le souhaitez, vous pouvez sélectionner **mon compte d’utilisateur** pour l’utilisateur actuel ou le **compte de service** pour un service particulier.</span><span class="sxs-lookup"><span data-stu-id="a758a-120">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a758a-121">Si vous n’êtes pas administrateur de votre appareil, vous pouvez gérer les certificats uniquement pour votre compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a758a-121">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="a758a-122">Dans la fenêtre **Sélectionner un ordinateur** , laissez l’option **ordinateur local** sélectionné, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="a758a-122">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="a758a-123">Dans la fenêtre **Ajouter ou supprimer un composant logiciel enfichable** , sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="a758a-123">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Ajouter un composant logiciel enfichable certificat](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="a758a-125">Facultatif : dans le menu **fichier** , sélectionnez **Enregistrer** ou **Enregistrer sous** pour enregistrer le fichier de console MMC en vue d’une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a758a-125">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="a758a-126">Pour afficher vos certificats dans le composant logiciel enfichable MMC, sélectionnez racine de la **console** dans le volet gauche, puis développez **certificats (ordinateur local)**.</span><span class="sxs-lookup"><span data-stu-id="a758a-126">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="a758a-127">Une liste de répertoires pour chaque type de certificat s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a758a-127">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="a758a-128">À partir de chaque répertoire de certificat, vous pouvez afficher, exporter, importer et supprimer ses certificats.</span><span class="sxs-lookup"><span data-stu-id="a758a-128">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="a758a-129">Afficher les certificats à l’aide de l’outil Gestionnaire de certificats</span><span class="sxs-lookup"><span data-stu-id="a758a-129">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="a758a-130">Vous pouvez également afficher, exporter, importer et supprimer des certificats à l’aide de l’outil Gestionnaire de certificats.</span><span class="sxs-lookup"><span data-stu-id="a758a-130">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="a758a-131">Pour afficher les certificats pour l’appareil local</span><span class="sxs-lookup"><span data-stu-id="a758a-131">To view certificates for the local device</span></span>

1. <span data-ttu-id="a758a-132">Sélectionnez **exécuter** dans le menu **Démarrer** , puis entrez *certlm. msc*.</span><span class="sxs-lookup"><span data-stu-id="a758a-132">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="a758a-133">L’outil Gestionnaire de certificats pour l’appareil local s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a758a-133">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="a758a-134">Pour afficher vos certificats, sous **certificats-ordinateur local** dans le volet gauche, développez le répertoire correspondant au type de certificat que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="a758a-134">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="a758a-135">Pour afficher les certificats de l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="a758a-135">To view certificates for the current user</span></span>

1. <span data-ttu-id="a758a-136">Sélectionnez **Exécuter** dans le menu **Démarrer**, puis entrez *certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="a758a-136">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="a758a-137">L’outil Gestionnaire de certificats pour l’utilisateur actuel s’affiche.</span><span class="sxs-lookup"><span data-stu-id="a758a-137">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="a758a-138">Pour afficher vos certificats, sous **certificats-utilisateur actuel** dans le volet gauche, développez le répertoire correspondant au type de certificat que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="a758a-138">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="a758a-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a758a-139">See also</span></span>

- [<span data-ttu-id="a758a-140">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="a758a-140">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="a758a-141">Comment : créer des certificats temporaires à utiliser pendant le développement</span><span class="sxs-lookup"><span data-stu-id="a758a-141">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="a758a-142">Comment : récupérer l’empreinte numérique d’un certificat</span><span class="sxs-lookup"><span data-stu-id="a758a-142">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
