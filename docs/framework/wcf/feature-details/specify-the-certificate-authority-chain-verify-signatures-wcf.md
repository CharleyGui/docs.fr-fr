---
title: "Comment : spécifier la chaîne de certificats d'autorité de certification utilisée pour vérifier des signatures (WCF)"
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 0a03902c9a0d36ebd6e2c38f4a827737cacec447
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245030"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Comment : spécifier la chaîne de certificats d'autorité de certification utilisée pour vérifier des signatures (WCF)

Lorsque Windows Communication Foundation (WCF) reçoit un message SOAP signé à l’aide d’un certificat X. 509, par défaut, il vérifie que le certificat X. 509 a été émis par une autorité de certification approuvée. Il consulte pour cela un magasin de certificats et détermine si le certificat de cette autorité de certification a été désigné comme approuvé. Pour que WCF puisse effectuer cette détermination, la chaîne de certificats de l’autorité de certification doit être installée dans le magasin de certificats approprié.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Pour installer une chaîne de certificats d'autorité de certification  
  
- Pour chaque autorité de certification qu’un destinataire de message SOAP envisage d’approuver les certificats X. 509 émis par, installez la chaîne de certificats de l’autorité de certification dans le magasin de certificats dans lequel WCF est configuré pour récupérer les certificats X. 509.  
  
     Par exemple, si un destinataire de message SOAP envisage de faire confiance à des certificats X. 509 émis par Microsoft, la chaîne de certificats de l’autorité de certification pour Microsoft doit être installée dans le magasin de certificats que WCF est configuré pour rechercher les certificats X. 509 à partir de. Le magasin de certificats dans lequel WCF recherche les certificats X. 509 peut être spécifié dans le code ou la configuration. Par exemple, cela peut être spécifié dans le code à l’aide de la <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> méthode ou dans la configuration de plusieurs façons, y compris [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Windows étant fourni avec un ensemble de chaînes de certificats par défaut pour les autorités de certification approuvées, il ne sera peut-être pas nécessaire d'installer la chaîne de certificats pour toutes les autorités de certification.  
  
    1. Exportez la chaîne de certificats d'autorité de certification.  
  
         La procédure exacte dépend de l'autorité de certification. Si l’autorité de certification exécute les services de certificats Microsoft, sélectionnez **Télécharger un certificat d’autorité de certification, une chaîne de certificats ou une liste de révocation** de certificats, puis choisissez **Télécharger le certificat d’autorité** de certification.  
  
    2. Importez la chaîne de certificats d'autorité de certification.  
  
         Dans la console MMC (Microsoft Management Console), ouvrez le composant logiciel enfichable Certificats. Pour le magasin de certificats que WCF est configuré pour récupérer les certificats X. 509, sélectionnez le dossier **autorités de certification** **racines de confiance** . Sous le dossier **autorités de certification racines de confiance** , cliquez avec le bouton droit sur le dossier **certificats** , pointez sur **toutes les tâches**, puis cliquez sur **Importer**. Fournissez le fichier exporté à l'étape a.  
  
         Pour plus d’informations sur l’utilisation du composant logiciel enfichable Certificats avec MMC, consultez [Comment : afficher des certificats avec le composant logiciel enfichable MMC](how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des certificats](working-with-certificates.md)
