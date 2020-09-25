---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: d0587ae942d1b0c7eb72bee830ca3ced76e4270c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190031"
---
# \<endpointExtensions>

Cette section inscrit un nouveau point de terminaison standard dans la section des extensions du fichier de configuration machine ou d'application. Vous pouvez ajouter un point de terminaison standard à cette collection à l’aide du mot clé `add` et affecter à l’attribut `type` de l’élément le type du point de terminaison et à l’attribut `name` le nom du point de terminaison standard.  
  
 L'exemple suivant utilise l'élément `add`, ainsi que l'attribut `name`, pour ajouter un point de terminaison standard à la section `<endpointExtensions>` du fichier de configuration.  
  
```xml  
<system.serviceModel>
  <extensions>
    <endpointExtensions>
      <add name="udpDiscoveryEndpoint"
           type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Après avoir inscrit le point de terminaison standard, vous pouvez l'utiliser comme indiqué dans l'exemple suivant. Dans l' [\<endpoint>](endpoint-element.md) élément, l' `kind` attribut spécifie le type de point de terminaison standard qui a été enregistré dans la `<endpointExtensions>` section. L' `endpointConfiguration` attribut sera identique à l' `name` attribut de l’élément de configuration du point de terminaison standard dans la `<standardEndpoints>` section.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Service1">
      <endpoint kind="udpDiscoveryEndpoint"
                endpointConfiguration="udpConfig" />
    </service>
  </services>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
