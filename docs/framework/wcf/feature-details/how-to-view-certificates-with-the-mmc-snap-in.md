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
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Procédure : afficher les certificats avec le composant logiciel enfichable MMC

Lorsque vous créez un client ou un service sécurisé, vous pouvez utiliser un [certificat](working-with-certificates.md) comme informations d’identification. Par exemple, un type commun d’informations d’identification est le certificat X. 509, que vous créez à l’aide de la <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> méthode.

Il existe trois types différents de magasins de certificats que vous pouvez examiner avec la console MMC (Microsoft Management Console) sur les systèmes Windows :

- Ordinateur local : le magasin est local sur l’appareil et global pour tous les utilisateurs sur l’appareil.

- Utilisateur actuel : le magasin est local sur le compte d’utilisateur actuel sur l’appareil.

- Compte de service : le magasin est local pour un service particulier sur l’appareil.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Afficher les certificats dans le composant logiciel enfichable MMC

La procédure suivante montre comment examiner les magasins sur votre appareil local pour trouver un certificat approprié :
  
1. Sélectionnez **exécuter** dans le menu **Démarrer** , puis entrez *MMC*.

    La console MMC s’affiche.
  
2. Dans le menu **fichier** , sélectionnez **Ajouter/supprimer un composant logiciel enfichable**.

    La fenêtre **Ajouter ou supprimer des composants logiciels enfichables** s’affiche.
  
3. Dans la liste **composants logiciels enfichables disponibles** , cliquez sur **certificats**, puis sélectionnez **Ajouter**.  

    ![Ajouter un composant logiciel enfichable certificat](./media/mmc-add-certificate-snap-in.png)
  
4. Dans la fenêtre du **composant logiciel enfichable Certificats** , sélectionnez **compte d’ordinateur**, puis cliquez sur **suivant**.
  
    Si vous le souhaitez, vous pouvez sélectionner **mon compte d’utilisateur** pour l’utilisateur actuel ou le **compte de service** pour un service particulier.

    > [!NOTE]
    > Si vous n’êtes pas administrateur de votre appareil, vous pouvez gérer les certificats uniquement pour votre compte d’utilisateur.
  
5. Dans la fenêtre **Sélectionner un ordinateur** , laissez l’option **ordinateur local** sélectionné, puis sélectionnez **Terminer**.  
  
6. Dans la fenêtre **Ajouter ou supprimer un composant logiciel enfichable** , sélectionnez **OK**.  
  
    ![Ajouter un composant logiciel enfichable certificat](./media/mmc-certificate-snap-in-selected.png)

7. Facultatif : dans le menu **fichier** , sélectionnez **Enregistrer** ou **Enregistrer sous** pour enregistrer le fichier de console MMC en vue d’une utilisation ultérieure.  

8. Pour afficher vos certificats dans le composant logiciel enfichable MMC, sélectionnez racine de la **console** dans le volet gauche, puis développez **certificats (ordinateur local)**.

    Une liste de répertoires pour chaque type de certificat s’affiche. À partir de chaque répertoire de certificat, vous pouvez afficher, exporter, importer et supprimer ses certificats.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Afficher les certificats à l’aide de l’outil Gestionnaire de certificats

Vous pouvez également afficher, exporter, importer et supprimer des certificats à l’aide de l’outil Gestionnaire de certificats.

### <a name="to-view-certificates-for-the-local-device"></a>Pour afficher les certificats pour l’appareil local

1. Sélectionnez **exécuter** dans le menu **Démarrer** , puis entrez *certlm. msc*.

    L’outil Gestionnaire de certificats pour l’appareil local s’affiche.
  
2. Pour afficher vos certificats, sous **certificats-ordinateur local** dans le volet gauche, développez le répertoire correspondant au type de certificat que vous souhaitez afficher.

### <a name="to-view-certificates-for-the-current-user"></a>Pour afficher les certificats de l’utilisateur actuel

1. Sélectionnez **Exécuter** dans le menu **Démarrer**, puis entrez *certmgr.msc*.

    L’outil Gestionnaire de certificats pour l’utilisateur actuel s’affiche.
  
2. Pour afficher vos certificats, sous **certificats-utilisateur actuel** dans le volet gauche, développez le répertoire correspondant au type de certificat que vous souhaitez afficher.

## <a name="see-also"></a>Voir aussi

- [Utilisation des certificats](working-with-certificates.md)
- [Comment : créer des certificats temporaires à utiliser pendant le développement](how-to-create-temporary-certificates-for-use-during-development.md)
- [Comment : récupérer l’empreinte numérique d’un certificat](how-to-retrieve-the-thumbprint-of-a-certificate.md)
