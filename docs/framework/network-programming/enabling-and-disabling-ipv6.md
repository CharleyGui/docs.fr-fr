---
title: Activation et désactivation d’IPv6
description: Suivez ces étapes de configuration pour activer l’utilisation du protocole IPv6, y compris la modification du fichier de configuration de l’ordinateur ou de l’application.
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 7729647b09df20a98d5d639a641cb0a31f557330
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502611"
---
# <a name="enabling-and-disabling-ipv6"></a>Activation et désactivation d’IPv6
Pour utiliser le protocole IPv6, vérifiez que vous exécutez une version du système d’exploitation qui prend en charge IPv6 et que le système d’exploitation et les classes de mise en réseau sont configurés correctement.  
  
## <a name="configuration-steps"></a>Étapes de configuration  
 Le tableau suivant répertorie les différentes configurations  
  
|Système d’exploitation compatible avec IPv6 ?|Classes de mise en réseau compatibles avec IPv6 ?|Description|  
|-------------------------------------|---------------------------------------|-----------------|  
|Non|Non|Peut analyser les adresses IPv6.|  
|Non|Oui|Peut analyser les adresses IPv6.|  
|Oui|Non|Peut analyser les adresses IPv6 et résoudre les adresses IPv6 à l’aide des méthodes de résolution de noms qui ne sont pas marquées comme obsolètes.|  
|Oui|Oui|Peut analyser et résoudre les adresses IPv6 à l’aide de toutes les méthodes, notamment celles marquées comme obsolètes.|  
  
 Notez que pour activer la prise en charge du protocole IPv6 pour toutes les classes dans l’espace de noms System.Net, vous devez modifier le fichier de configuration d’ordinateur ou le fichier de configuration de l’application. Le fichier de configuration pour une application est prioritaire par rapport au fichier de configuration d’ordinateur.  
  
 Pour obtenir un exemple illustrant comment modifier le fichier de configuration d’ordinateur, *machine.config*, pour activer la prise en charge du protocole Ipv6, consultez [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md) (Guide pratique pour modifier le fichier de configuration d’ordinateur pour activer la prise en charge du protocole IPv6). Vérifiez également que la prise en charge du protocole IPv6 est activée pour le système d’exploitation.  
  
 Le .NET Framework a un commutateur de configuration défini dans un fichier de configuration comme suit :  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 Pour le .NET Framework version 1.1 et antérieures, la valeur du commutateur de configuration **ipv6 enabled** spécifie si les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> retournent des adresses IPv6.  
  
 Pour le .NET Framework version 2.0 et ultérieures, si Windows prend en charge le protocole IPv6, les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType>, (par exemple la méthode <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>), retournent des adresses IPv6 avec une limitation. Les membres obsolètes du <xref:System.Net.Dns?displayProperty=nameWithType> DNS (par exemple la méthode <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lisent et reconnaissent la valeur dans le fichier de configuration pour le paramètre ipv6 enabled.  
  
## <a name="see-also"></a>Voir aussi

- [Protocole Internet version 6](internet-protocol-version-6.md)
- [Sockets](sockets.md)
- [Schéma des paramètres réseau](../configure-apps/file-schema/network/index.md)
- [\<ipv6>, Élément (paramètres réseau)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
