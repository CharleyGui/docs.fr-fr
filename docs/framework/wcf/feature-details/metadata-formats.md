---
title: Formats de métadonnées
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a74a57843beaba09b969678a34cad3ad8bed7050
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598838"
---
# <a name="metadata-formats"></a>Formats de métadonnées
Windows Communication Foundation (WCF) prend en charge les formats de métadonnées dans le tableau suivant.  
  
## <a name="metadata-specifications-and-usage"></a>Spécification et utilisation des métadonnées  
  
|Protocol|Spécification et utilisation|  
|--------------|-----------------------------|  
|WSDL 1.1|[WSDL (Web Services Description Language) 1.1 (page pouvant être en anglais)](https://www.w3.org/TR/wsdl/)<br /><br /> WCF utilise Web Services Description Language (WSDL) pour décrire les services.|  
|Schéma XML|[XML Schema Part 2 : Datatypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) et [XML Schema Part 1 : structures Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF utilise le schéma XML pour décrire les types de données utilisés dans les messages.|  
|WS-Policy|[Services Web-Policy 1.2 - Infrastructure (WS-Policy)  (page pouvant être en anglais)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Services Web-Policy 1.5 - Infrastructure  (page pouvant être en anglais)](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF utilise les spécifications WS-Policy 1,2 ou 1,5 avec des assertions spécifiques au domaine pour décrire les exigences et les fonctionnalités du service.|  
|Pièces jointes WS-Policy|[Services Web-Policy 1.2 – Pièces jointes (WS-PolicyAttachment)  (page pouvant être en anglais)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF implémente les pièces jointes WS-Policy pour joindre des expressions de stratégie à différentes étendues dans WSDL.|  
|Échange de métadonnées WS|[WS-MetadataExchange (Web Services Metadata Exchange) version 1.1  (page pouvant être en anglais)](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implémente WS-MetadataExchange pour récupérer le schéma XML, WSDL et WS-Policy.|  
|WS-Addressing Binding pour WSDL|[Web Services Addressing 1.0 – Liaison WSDL (page pouvant être en anglais)](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF implémente la liaison WS-Addressing pour WSDL pour joindre les informations d’adressage dans WSDL.|  
  
## <a name="see-also"></a>Voir aussi

- [Protocoles de services Web pris en charge par des liaisons d’interopérabilité fournies par le système](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL et stratégie](wsdl-and-policy.md)
