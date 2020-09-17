---
title: Formats de métadonnées
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 01f0d7a2212b2af7e2d3a959ed91624edec46ce8
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720463"
---
# <a name="metadata-formats"></a>Formats de métadonnées

Windows Communication Foundation (WCF) prend en charge les formats de métadonnées dans le tableau suivant.  
  
## <a name="metadata-specifications-and-usage"></a>Spécification et utilisation des métadonnées  
  
|Protocole|Spécification et utilisation|  
|--------------|-----------------------------|  
|WSDL 1.1|[WSDL (Web Services Description Language) 1.1 (page pouvant être en anglais)](https://www.w3.org/TR/wsdl/)<br /><br /> WCF utilise Web Services Description Language (WSDL) pour décrire les services.|  
|Schéma XML|[XML Schema Part 2 : Datatypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) et [XML Schema Part 1 : structures Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF utilise le schéma XML pour décrire les types de données utilisés dans les messages.|  
|WS-Policy|[Services Web-Policy 1.2 - Infrastructure (WS-Policy)  (page pouvant être en anglais)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Services Web-Policy 1.5 - Infrastructure  (page pouvant être en anglais)](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF utilise les spécifications WS-Policy 1,2 ou 1,5 avec des assertions spécifiques au domaine pour décrire les exigences et les fonctionnalités du service.|  
|Pièces jointes WS-Policy|[Services Web-Policy 1.2 – Pièces jointes (WS-PolicyAttachment)  (page pouvant être en anglais)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF implémente les pièces jointes WS-Policy pour joindre des expressions de stratégie à différentes étendues dans WSDL.|  
|Échange de métadonnées WS|[WS-MetadataExchange (Web Services Metadata Exchange) version 1.1  (page pouvant être en anglais)](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
|WS-Addressing Binding pour WSDL|[Web Services Addressing 1.0 – Liaison WSDL (page pouvant être en anglais)](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF implémente la liaison WS-Addressing pour WSDL pour joindre les informations d’adressage dans WSDL.|  
  
## <a name="see-also"></a>Voir aussi

- [Protocoles de services Web pris en charge par des liaisons d’interopérabilité fournies par le système](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL et stratégie](wsdl-and-policy.md)
