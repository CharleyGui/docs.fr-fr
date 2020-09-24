---
title: <system.serviceModel.activation>
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: cbb12ce84f53f55f7d5b2dabd449a116969dc9b8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157133"
---
# \<system.serviceModel.activation>

<span data-ttu-id="c77e6-102">Cette section de configuration représente les paramètres de configuration définis pour l'outil SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="c77e6-102">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="c77e6-103">Les éléments de configuration peuvent être configurés dans le fichier SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="c77e6-103">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="c77e6-104">Spécifiquement, cela inclut tous les paramètres à l'échelle de ordinateur qui doivent être configurés.</span><span class="sxs-lookup"><span data-stu-id="c77e6-104">Specifically, it includes all machine-wide settings that must be configured.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel.activation>**  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="c77e6-105">Exemple de fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c77e6-105">Sample Configuration File</span></span>  

 <span data-ttu-id="c77e6-106">Les éléments suivants constituent un exemple de fichier de configuration (SMSvcHost.exe.config), utilisé par le processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="c77e6-106">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>
  <runtime>
    <gcConcurrent enabled="false" />
  </runtime>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="10"
             maxPendingAccepts="2"
             maxPendingConnections="100"
             receiveTimeout="00:00:10"
             teredoEnabled="false">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
    <net.pipe maxConnectionsPendingDispatch="100"
              maxPendingAccepts="2"
              receiveTimeout="00:00:10">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
    <diagnostics performanceCountersEnabled="true" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="c77e6-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c77e6-107">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration>
