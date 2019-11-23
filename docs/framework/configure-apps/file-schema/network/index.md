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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698152"
---
# <a name="network-settings-schema"></a>Schéma des paramètres réseau
Les paramètres réseau spécifient la façon dont le .NET Framework se connecte à Internet.

Les paramètres \<System. net > spécifient la façon dont le .NET Framework se connecte au réseau. Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous [\<system.Net>, élément (paramètres réseau)](system-net-element-network-settings.md).  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<authenticationModules, élément (paramètres réseau)](authenticationmodules-element-network-settings.md)|Spécifie les modules utilisés pour authentifier les requêtes Internet.|  
|[\<connectionManagement>, élément (paramètres réseau)](connectionmanagement-element-network-settings.md)|Spécifie le nombre maximal de connexions à destination des hôtes Internet.|  
|[\<defaultProxy>, élément(paramètres réseau)](defaultproxy-element-network-settings.md)|Spécifie le serveur proxy utilisé pour les requêtes HTTP à destination d’Internet.|  
|[\<mailSettings>, élément (paramètres réseau)](mailsettings-element-network-settings.md)|Contient les paramètres des options d’envoi de courrier.|  
|[\<requestCaching>, élément (paramètres réseau)](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
|[\<webRequestModules>, élément (paramètres réseau)](webrequestmodules-element-network-settings.md)|Spécifie les modules utilisés pour demander des informations à partir des hôtes Internet.|  
  
Les paramètres de > URI \<spécifient la façon dont le .NET Framework gère les adresses Web exprimées à l’aide d’URI (Uniform Resource Identifier). Le tableau suivant décrit la fonction de chaque élément de configuration enfant sous le [\<uri > élément (paramètres d’URI)](uri-element-uri-settings.md).  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<idn>, élément (paramètres d’Uri)](idn-element-uri-settings.md)|Spécifie si l’analyse de nom de domaine international (IDN) s’applique aux noms de domaine.|  
|[\<iriParsing>, élément (paramètres d’Uri)](iriparsing-element-uri-settings.md)|Spécifie si l’analyse d’identificateur de ressource internationale (IRI) s’applique à un <xref:System.Uri> et si les règles d’analyse IRI doivent s’appliquer.|  
|[\<schemeSettings, élément (paramètres d’Uri)](schemesettings-element-uri-settings.md)|Spécifie la façon dont un <xref:System.Uri> est analysé pour les schémas spécifiques.|  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des applications Internet](../../../network-programming/configuring-internet-applications.md)
- [Schéma des fichiers de configuration](../index.md)
