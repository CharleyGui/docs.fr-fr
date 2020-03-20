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
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Comment : Afficher les certificats avec le snap-in MMC
Lorsque vous créez un client ou un service sécurisé, vous pouvez utiliser un [certificat](working-with-certificates.md) comme titre d’identification. Par exemple, un type commun d’identification est le certificat X.509, que vous créez avec la <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> méthode.

Il existe trois types différents de magasins de certificats que vous pouvez examiner avec la console de gestion Microsoft (MMC) sur les systèmes Windows:

- Ordinateur local: Le magasin est local à l’appareil et mondial pour tous les utilisateurs sur l’appareil.

- Utilisateur actuel : Le magasin est local au compte utilisateur actuel sur l’appareil.

- Compte de service : Le magasin est local à un service particulier sur l’appareil.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Afficher les certificats dans le snap-in MMC

La procédure suivante montre comment examiner les magasins de votre appareil local pour trouver un certificat approprié :
  
1. Sélectionnez **Exécuter** dans le menu **Démarrer,** puis entrez *mmc*.

    Le MMC apparaît.
  
2. Dans le menu **Fichier,** sélectionnez **Ajouter/Supprimer Snap In**.

    La fenêtre **Add or Remove Snap-ins** apparaît.
  
3. De la liste **snap-ins disponible,** choisissez **des certificats,** puis sélectionnez **Ajouter**.  

    ![Ajouter le snap-in de certificat](./media/mmc-add-certificate-snap-in.png)
  
4. Dans la fenêtre **Snap-in Certificates,** sélectionnez **compte informatique,** puis sélectionnez **Next**.
  
    Optionnellement, vous pouvez sélectionner **Mon compte utilisateur** pour l’utilisateur actuel ou le compte **Service** pour un service particulier.

    > [!NOTE]
    > Si vous n’êtes pas administrateur de votre appareil, vous ne pouvez gérer les certificats que pour votre compte utilisateur.
  
5. Dans la fenêtre **Select Computer,** laissez **l’ordinateur local** sélectionné, puis sélectionnez **Finition**.  
  
6. Dans la fenêtre **Ajouter ou supprimer Snap-in,** sélectionnez **OK**.  
  
    ![Ajouter le snap-in de certificat](./media/mmc-certificate-snap-in-selected.png)

7. Option : À partir du menu **Fichier,** sélectionnez **Enregistrer** ou **enregistrer** le fichier de console MMC pour une utilisation ultérieure.  

8. Pour afficher vos certificats dans le snap-in MMC, sélectionnez **Console Root** dans le volet gauche, puis élargissez **les certificats (ordinateur local).**

    Une liste d’annuaires pour chaque type de certificat apparaît. De chaque répertoire de certificat, vous pouvez afficher, exporter, importer et supprimer ses certificats.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Afficher les certificats avec l’outil Certificate Manager

Vous pouvez également afficher, exporter, importer et supprimer des certificats en utilisant l’outil Certificate Manager.

### <a name="to-view-certificates-for-the-local-device"></a>Pour afficher les certificats pour l’appareil local

1. Sélectionnez **Exécuter** dans le menu **Démarrer,** puis entrez *certlm.msc*.

    L’outil Certificate Manager pour l’appareil local apparaît.
  
2. Pour consulter vos certificats, en vertu **de Certificats - Ordinateur local** dans le volet gauche, élargissez l’annuaire pour le type de certificat que vous souhaitez consulter.

### <a name="to-view-certificates-for-the-current-user"></a>Pour afficher les certificats pour l’utilisateur actuel

1. Sélectionnez **Exécuter** dans le menu **Démarrer,** puis entrez *certmgr.msc*.

    L’outil Certificate Manager pour l’utilisateur actuel apparaît.
  
2. Pour consulter vos certificats, en vertu **de Certificats - Utilisateur actuel** dans le volet gauche, élargissez l’annuaire pour le type de certificat que vous souhaitez consulter.

## <a name="see-also"></a>Voir aussi

- [Travailler avec des certificats](working-with-certificates.md)
- [Comment : Créer des certificats temporaires pour une utilisation pendant le développement](how-to-create-temporary-certificates-for-use-during-development.md)
- [Comment: Récupérer l’empreinte du pouce d’un certificat](how-to-retrieve-the-thumbprint-of-a-certificate.md)
