---
title: Schéma des paramètres réseau
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698152"
---
# <a name="network-settings-schema"></a>Schéma des paramètres réseau
Les paramètres réseau spécifient la façon dont le .NET Framework se connecte à Internet.

Les \<system.net> paramètres spécifient la façon dont le .NET Framework se connecte au réseau. Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous l' [ \<system.Net> élément (paramètres réseau)](system-net-element-network-settings.md).  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<authenticationModules>, Élément (paramètres réseau)](authenticationmodules-element-network-settings.md)|Spécifie les modules utilisés pour authentifier les requêtes Internet.|  
|[\<connectionManagement>, Élément (paramètres réseau)](connectionmanagement-element-network-settings.md)|Spécifie le nombre maximal de connexions à destination des hôtes Internet.|  
|[\<defaultProxy>, Élément (paramètres réseau)](defaultproxy-element-network-settings.md)|Spécifie le serveur proxy utilisé pour les requêtes HTTP à destination d’Internet.|  
|[\<mailSettings>, Élément (paramètres réseau)](mailsettings-element-network-settings.md)|Contient les paramètres des options d’envoi de courrier.|  
|[\<requestCaching>, Élément (paramètres réseau)](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
|[\<webRequestModules>, Élément (paramètres réseau)](webrequestmodules-element-network-settings.md)|Spécifie les modules utilisés pour demander des informations à partir des hôtes Internet.|  
  
Les \<uri> paramètres spécifient la façon dont le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier). Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous l' [ \<uri> élément (paramètres d’URI)](uri-element-uri-settings.md).  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<idn>, Élément (paramètres d’URI)](idn-element-uri-settings.md)|Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.|  
|[\<iriParsing>, Élément (paramètres d’URI)](iriparsing-element-uri-settings.md)|Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.|  
|[\<schemeSettings>, Élément (paramètres d’URI)](schemesettings-element-uri-settings.md)|Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.|  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des applications Internet](../../../network-programming/configuring-internet-applications.md)
- [Schéma du fichier de configuration](../index.md)
