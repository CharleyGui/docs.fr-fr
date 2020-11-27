---
title: Différences entre la validation de certificat de service effectuée par Internet Explorer et celle effectuée par WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 574a6fa5411bcb662514982923e5c51200f98ae2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272200"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Différences entre la validation de certificat de service effectuée par Internet Explorer et celle effectuée par WCF

En raison de la différence entre la manière dont Internet Explorer et Windows Communication Foundation (WCF) valident les certificats de service lorsque le protocole HTTPs est utilisé, il est possible qu’Internet Explorer ne soit pas en mesure d’accéder à la page d’aide ou à Web Services Description Language (WSDL) d’un service même si un client WCF est en mesure d’envoyer des messages aux points de terminaison de service. Cela est dû au fait qu’Internet Explorer vérifie si le certificat de service a les `ServerAuthentication` identificateurs d’objet (OID) dans les indicateurs d’utilisation améliorés, alors que WCF n’applique pas une telle contrainte. Si Internet Explorer ne peut pas accéder à la page d’aide du service ou au WSDL pour le service, utilisez l' [outil ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour accéder aux métadonnées du service.  
  
## <a name="see-also"></a>Voir aussi

- [Différences de validation des certificats entre HTTPS, SSL sur TCP et la sécurité SOAP](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Procédure : récupérer des métadonnées et implémenter un service conforme](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
