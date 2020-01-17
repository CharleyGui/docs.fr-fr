---
title: Formats de métadonnées
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: e7208a8d5fd6d100ac2a2c4fb1369a571c63e7fc
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212170"
---
# <a name="metadata-formats"></a>Formats de métadonnées
Windows Communication Foundation (WCF) prend en charge les formats de métadonnées dans le tableau suivant.  
  
## <a name="metadata-specifications-and-usage"></a>Spécification et utilisation des métadonnées  
  
|Protocole|Spécification et utilisation|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF utilise Web Services Description Language (WSDL) pour décrire les services.|  
|Schéma XML|[XML Schema Part 2 : Datatypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) et [XML Schema Part 1 : structures Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF utilise le schéma XML pour décrire les types de données utilisés dans les messages.|  
|WS-Policy|[Stratégie de services Web 1,2-Framework (WS-Policy)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Stratégie de services Web 1,5-Framework](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF utilise les spécifications WS-Policy 1,2 ou 1,5 avec des assertions spécifiques au domaine pour décrire les exigences et les fonctionnalités du service.|  
|Pièces jointes WS-Policy|[Stratégie de services Web 1,2-Attachment (WS-PolicyAttachment)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF implémente les pièces jointes WS-Policy pour joindre des expressions de stratégie à différentes étendues dans WSDL.|  
|Échange de métadonnées WS|[Web services Metadata Exchange (WS-MetadataExchange) version 1,1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
|WS-Addressing Binding pour WSDL|[Adressage de services Web 1,0-liaison WSDL](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF implémente la liaison WS-Addressing pour WSDL pour joindre les informations d’adressage dans WSDL.|  
  
## <a name="see-also"></a>Voir aussi

- [Protocoles de services web pris en charge par des liaisons d’interopérabilité fournies par le système](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL et stratégie](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
