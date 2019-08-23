---
title: 'Procédure : Obtenir un certificat (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: e720a6742506f6270fda65de12f510c2a6224873
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929193"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Procédure : Obtenir un certificat (WCF)
Pour utiliser l’une des fonctionnalités de Windows Communication Foundation (WCF) de qui utilisent des certificats X. 509, vous devez tout d’abord obtenir des certificats.  
  
### <a name="to-obtain-an-x509-certificate"></a>Pour obtenir un certificat X.509  
  
1. Choisissez l'une des valeurs suivantes :  
  
    - Achetez un certificat auprès d'une autorité de certification, telle que VeriSign, Inc.  
  
    - Installez votre propre service de certificats et faites en sorte qu'une autorité de certification signe les certificats. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter et Windows 2000 Datacenter Server incluent tous des services de certificat qui prennent en charge l'infrastructure à clé publique. Dans Windows Server 2008, utilisez le rôle [services de certificats Active Directory](https://go.microsoft.com/fwlink/?LinkID=153483) pour gérer une autorité de certification.  
  
    - Installez votre propre service de certificats et ne faites pas signer les certificats.  
  
    > [!NOTE]
    > Quelle que soit la méthode adoptée, le destinataire de la demande SOAP contenant le certificat X.509 doit approuver ce dernier. Cela signifie que le certificat X.509 ou un émetteur dans la chaîne de certificats se trouve dans le magasin de certificats Personnes de confiance et que le certificat X.509 ne se trouve pas dans le magasin de certificats non fiables.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Guide pratique pour Créer des certificats temporaires à utiliser pendant le développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
