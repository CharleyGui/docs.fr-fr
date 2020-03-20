---
title: 'Comment : Afficher les certificats avec le snap-in MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184782"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="c2f2c-102">Comment : Afficher les certificats avec le snap-in MMC</span><span class="sxs-lookup"><span data-stu-id="c2f2c-102">How to: View certificates with the MMC snap-in</span></span>
<span data-ttu-id="c2f2c-103">Lorsque vous créez un client ou un service sécurisé, vous pouvez utiliser un [certificat](working-with-certificates.md) comme titre d’identification.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-103">When you create a secure client or service, you can use a [certificate](working-with-certificates.md) as the credential.</span></span> <span data-ttu-id="c2f2c-104">Par exemple, un type commun d’identification est le certificat X.509, que vous créez avec la <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-104">For example, a common type of credential is the X.509 certificate, which you create with the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c2f2c-105">Il existe trois types différents de magasins de certificats que vous pouvez examiner avec la console de gestion Microsoft (MMC) sur les systèmes Windows:</span><span class="sxs-lookup"><span data-stu-id="c2f2c-105">There are three different types of certificate stores that you can examine with the Microsoft Management Console (MMC) on Windows systems:</span></span>

- <span data-ttu-id="c2f2c-106">Ordinateur local: Le magasin est local à l’appareil et mondial pour tous les utilisateurs sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-106">Local computer: The store is local to the device and global to all users on the device.</span></span>

- <span data-ttu-id="c2f2c-107">Utilisateur actuel : Le magasin est local au compte utilisateur actuel sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-107">Current user: The store is local to the current user account on the device.</span></span>

- <span data-ttu-id="c2f2c-108">Compte de service : Le magasin est local à un service particulier sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-108">Service account: The store is local to a particular service on the device.</span></span>

## <a name="view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="c2f2c-109">Afficher les certificats dans le snap-in MMC</span><span class="sxs-lookup"><span data-stu-id="c2f2c-109">View certificates in the MMC snap-in</span></span>

<span data-ttu-id="c2f2c-110">La procédure suivante montre comment examiner les magasins de votre appareil local pour trouver un certificat approprié :</span><span class="sxs-lookup"><span data-stu-id="c2f2c-110">The following procedure demonstrates how to examine the stores on your local device to find an appropriate certificate:</span></span>
  
1. <span data-ttu-id="c2f2c-111">Sélectionnez **Exécuter** dans le menu **Démarrer,** puis entrez *mmc*.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-111">Select **Run** from the **Start** menu, and then enter *mmc*.</span></span>

    <span data-ttu-id="c2f2c-112">Le MMC apparaît.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-112">The MMC appears.</span></span>
  
2. <span data-ttu-id="c2f2c-113">Dans le menu **Fichier,** sélectionnez **Ajouter/Supprimer Snap In**.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-113">From the **File** menu, select **Add/Remove Snap In**.</span></span>

    <span data-ttu-id="c2f2c-114">La fenêtre **Add or Remove Snap-ins** apparaît.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-114">The **Add or Remove Snap-ins** window appears.</span></span>
  
3. <span data-ttu-id="c2f2c-115">De la liste **snap-ins disponible,** choisissez **des certificats,** puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-115">From the **Available snap-ins** list, choose **Certificates**, then select **Add**.</span></span>  

    ![Ajouter le snap-in de certificat](./media/mmc-add-certificate-snap-in.png)
  
4. <span data-ttu-id="c2f2c-117">Dans la fenêtre **Snap-in Certificates,** sélectionnez **compte informatique,** puis sélectionnez **Next**.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-117">In the **Certificates snap-in** window, select **Computer account**, and then select **Next**.</span></span>
  
    <span data-ttu-id="c2f2c-118">Optionnellement, vous pouvez sélectionner **Mon compte utilisateur** pour l’utilisateur actuel ou le compte **Service** pour un service particulier.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-118">Optionally, you can select **My user account** for the current user or **Service account** for a particular service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c2f2c-119">Si vous n’êtes pas administrateur de votre appareil, vous ne pouvez gérer les certificats que pour votre compte utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-119">If you're not an administrator for your device, you can manage certificates only for your user account.</span></span>
  
5. <span data-ttu-id="c2f2c-120">Dans la fenêtre **Select Computer,** laissez **l’ordinateur local** sélectionné, puis sélectionnez **Finition**.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-120">In the **Select Computer** window, leave **Local computer** selected, and then select **Finish**.</span></span>  
  
6. <span data-ttu-id="c2f2c-121">Dans la fenêtre **Ajouter ou supprimer Snap-in,** sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-121">In the **Add or Remove Snap-in** window, select **OK**.</span></span>  
  
    ![Ajouter le snap-in de certificat](./media/mmc-certificate-snap-in-selected.png)

7. <span data-ttu-id="c2f2c-123">Option : À partir du menu **Fichier,** sélectionnez **Enregistrer** ou **enregistrer** le fichier de console MMC pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-123">Optional: From the **File** menu, select **Save** or **Save As** to save the MMC console file for later use.</span></span>  

8. <span data-ttu-id="c2f2c-124">Pour afficher vos certificats dans le snap-in MMC, sélectionnez **Console Root** dans le volet gauche, puis élargissez **les certificats (ordinateur local).**</span><span class="sxs-lookup"><span data-stu-id="c2f2c-124">To view your certificates in the MMC snap-in, select **Console Root** in the left pane, then expand **Certificates (Local Computer)**.</span></span>

    <span data-ttu-id="c2f2c-125">Une liste d’annuaires pour chaque type de certificat apparaît.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-125">A list of directories for each type of certificate appears.</span></span> <span data-ttu-id="c2f2c-126">De chaque répertoire de certificat, vous pouvez afficher, exporter, importer et supprimer ses certificats.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-126">From each certificate directory, you can view, export, import, and delete its certificates.</span></span>

## <a name="view-certificates-with-the-certificate-manager-tool"></a><span data-ttu-id="c2f2c-127">Afficher les certificats avec l’outil Certificate Manager</span><span class="sxs-lookup"><span data-stu-id="c2f2c-127">View certificates with the Certificate Manager tool</span></span>

<span data-ttu-id="c2f2c-128">Vous pouvez également afficher, exporter, importer et supprimer des certificats en utilisant l’outil Certificate Manager.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-128">You can also view, export, import, and delete certificates by using the Certificate Manager tool.</span></span>

### <a name="to-view-certificates-for-the-local-device"></a><span data-ttu-id="c2f2c-129">Pour afficher les certificats pour l’appareil local</span><span class="sxs-lookup"><span data-stu-id="c2f2c-129">To view certificates for the local device</span></span>

1. <span data-ttu-id="c2f2c-130">Sélectionnez **Exécuter** dans le menu **Démarrer,** puis entrez *certlm.msc*.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-130">Select **Run** from the **Start** menu, and then enter *certlm.msc*.</span></span>

    <span data-ttu-id="c2f2c-131">L’outil Certificate Manager pour l’appareil local apparaît.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-131">The Certificate Manager tool for the local device appears.</span></span>
  
2. <span data-ttu-id="c2f2c-132">Pour consulter vos certificats, en vertu **de Certificats - Ordinateur local** dans le volet gauche, élargissez l’annuaire pour le type de certificat que vous souhaitez consulter.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-132">To view your certificates, under **Certificates - Local Computer** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

### <a name="to-view-certificates-for-the-current-user"></a><span data-ttu-id="c2f2c-133">Pour afficher les certificats pour l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="c2f2c-133">To view certificates for the current user</span></span>

1. <span data-ttu-id="c2f2c-134">Sélectionnez **Exécuter** dans le menu **Démarrer,** puis entrez *certmgr.msc*.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-134">Select **Run** from the **Start** menu, and then enter *certmgr.msc*.</span></span>

    <span data-ttu-id="c2f2c-135">L’outil Certificate Manager pour l’utilisateur actuel apparaît.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-135">The Certificate Manager tool for the current user appears.</span></span>
  
2. <span data-ttu-id="c2f2c-136">Pour consulter vos certificats, en vertu **de Certificats - Utilisateur actuel** dans le volet gauche, élargissez l’annuaire pour le type de certificat que vous souhaitez consulter.</span><span class="sxs-lookup"><span data-stu-id="c2f2c-136">To view your certificates, under **Certificates - Current User** in the left pane, expand the directory for the type of certificate you want to view.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2f2c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2f2c-137">See also</span></span>

- [<span data-ttu-id="c2f2c-138">Travailler avec des certificats</span><span class="sxs-lookup"><span data-stu-id="c2f2c-138">Working with certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="c2f2c-139">Comment : Créer des certificats temporaires pour une utilisation pendant le développement</span><span class="sxs-lookup"><span data-stu-id="c2f2c-139">How to: Create temporary certificates for use during development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
- [<span data-ttu-id="c2f2c-140">Comment: Récupérer l’empreinte du pouce d’un certificat</span><span class="sxs-lookup"><span data-stu-id="c2f2c-140">How to: Retrieve the thumbprint of a certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
