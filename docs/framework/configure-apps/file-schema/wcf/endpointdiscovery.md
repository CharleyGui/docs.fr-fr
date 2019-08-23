---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919049"
---
# <a name="endpointdiscovery"></a>\<endpointDiscovery>
Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.  
  
\<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<> de comportement  
\<endpointDiscovery>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Valeur booléenne qui spécifie si la détectabilité est activée sur ce point de terminaison. Par défaut, il s’agit de `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|Collection d'URI de portée pour le point de terminaison. Plusieurs URI de portée peuvent être associés au même point de terminaison.|  
|[\<extensions>](extensions.md) [of \<endpointDiscovery>]|Collection d'éléments XML qui vous permet de spécifier des métadonnées personnalisées à publier pour un point de terminaison.|  
|\<types>|Collection d'interfaces à rechercher.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
|||  
  
## <a name="remarks"></a>Notes  
 Lorsqu'il est ajouté à la configuration de comportement du point de terminaison et si le jeu d'attributs `enabled` a la valeur `true`, cet élément de configuration devient détectable. En outre, vous pouvez utiliser les [ \<étendues >](scopes.md)élément enfant pour spécifier des URI de portée personnalisée qui peuvent être utilisés pour filtrer les points de terminaison de service pendant la requête, ainsi que les [ \<extensions >](extensions.md) élément enfant pour spécifier personnalisé les métadonnées qui doivent être publiées avec les métadonnées détectables standard (EPR, ContractTypeName, BindingName, Scope et ListenURI).  
  
 Cet élément de configuration dépend de l' [ \<élément serviceDiscovery >](servicediscovery.md) qui fournit le contrôle du niveau de service de la détectabilité. Cela signifie que les paramètres de cet élément sont ignorés si [ \<serviceDiscovery >](servicediscovery.md) n’est pas présent dans la configuration.  
  
## <a name="example"></a>Exemple  
 L'exemple de configuration suivant spécifie des portées de filtrage et des métadonnées d'extension à publier pour un point de terminaison.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
