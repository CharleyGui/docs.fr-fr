---
title: 'Procédure : modifier le fichier config de l’ordinateur en vue d’activer la prise en charge IPv6'
description: Découvrez comment modifier le fichier de configuration de l’ordinateur, machine.config, pour activer la prise en charge D’ipv6 dans le .NET Framework.
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 2c5e3e094eca480a7cab4f7c25cc0fedba196338
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269598"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Procédure : modifier le fichier config de l’ordinateur en vue d’activer la prise en charge IPv6

L’exemple de code suivant montre comment modifier le fichier de configuration (*machine.config*) d’un ordinateur pour activer la prise en charge d’IPv6. Le fichier *machine.config* est stocké dans le dossier *%Windir%\Microsoft.NET\Framework*, situé dans le répertoire d’installation de Windows. Il y a un fichier *machine.config* distinct dans les dossiers sous *%Windir%\Microsoft.NET\Framework* pour chaque version de .NET Framework installée sur l’ordinateur (par exemple, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.  
  
 Pour le .NET Framework version 1.1 et antérieures, la valeur du commutateur de configuration **ipv6 enabled** spécifie si les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> retournent des adresses IPv6.  
  
 Pour .NET Framework version 2.0 ou ultérieure, si Windows prend en charge le protocole IPv6, tous les membres de la classe <xref:System.Net.Dns?displayProperty=nameWithType> (par exemple, la méthode <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>) retournent des adresses IPv6 avec une limitation. Les membres obsolètes de la classe <xref:System.Net.Dns?displayProperty=nameWithType> (par exemple, la méthode <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) lisent et reconnaissent la valeur dans le fichier de configuration.  
  
> [!NOTE]
> Pour .NET Framework version 2.0 ou ultérieure, IPv6 est activé par défaut. Pour .NET Framework version 1.1 ou antérieure, IPv6 est désactivé par défaut.  
  
## <a name="example"></a>Exemple  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>
    ……………  
    </settings>  
    ………………  
</system.net>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Adressage IPv6](ipv6-addressing.md)
- [Schéma des paramètres réseau](../configure-apps/file-schema/network/index.md)
- [\<ipv6> , Élément (paramètres réseau)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
