---
title: Filtres de message
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: b8de58b6935ee59fc8c787dfcf7445afcd0774b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912697"
---
# <a name="message-filters"></a>Filtres de message
Pour implémenter le routage basé sur le contenu, le service de routage utilise des implémentations <xref:System.ServiceModel.Dispatcher.MessageFilter> qui inspectent des sections particulières d'un message, telles que l'adresse, le nom du point de terminaison ou une instruction XPath spécifique. Si aucun des filtres de message fournis avec [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ne répond à vos besoins, vous pouvez créer un filtre personnalisé en créant une nouvelle implémentation de la classe <xref:System.ServiceModel.Dispatcher.MessageFilter> de base.  
  
 Lorsque vous configurez le service de routage, vous devez définir<xref:System.ServiceModel.Routing.Configuration.FilterElement> des éléments de filtre (objets) qui décrivent le type de **MessageFilter** et les données de prise en charge requises pour créer le filtre, telles que des valeurs de chaîne spécifiques à rechercher dans le message. . Notez que la création des éléments de filtre définit uniquement le filtre de message individuel ; pour que les filtres permettent d'évaluer et de router des messages, vous devez également définir une table de filtres (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).  
  
 Chaque entrée dans la table de filtres référence un élément de filtre et spécifie le point de terminaison client vers lequel un message sera routé si celui-ci correspond au filtre. Les entrées de table de filtres vous permettent également de spécifier une collection de points de terminaison de sauvegarde (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Cette collection définit une liste des points de terminaison auxquels le message est transmis en cas d’échec de transmission lors de l’envoi au point de terminaison primaire. Ces points de terminaison sont testés dans l'ordre spécifié jusqu'à la réussite de l'un d'eux.  
  
## <a name="message-filters"></a>Filtres de message  
 Les filtres de message utilisés par le service de routage fournissent des fonctionnalités communes de sélection de message, par exemple, évaluer le nom du point de terminaison auquel un message a été envoyé, l'action SOAP, l'adresse ou le préfixe d'adresse auquel le message a été envoyé. Il est également possible de joindre deux filtres par une condition `AND`, de manière à router les messages vers un seul point de terminaison si le message correspond aux deux filtres. Vous pouvez aussi créer des filtres personnalisés en créant votre propre implémentation de <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 Le tableau suivant répertorie le <xref:System.ServiceModel.Routing.Configuration.FilterType> utilisé par le service de routage, la classe qui implémente le filtre de message spécifique, et les paramètres <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> requis.  
  
|Type de filtre|Description|Signification des données de filtre|Exemple de filtre|  
|------------------|-----------------|-------------------------|--------------------|  
|Action|Utilise la classe <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> pour filtrer les messages qui contiennent une action spécifique.|Action à laquelle appliquer un filtre.|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|EndpointAddress|Utilise la <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> classe, avec <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  == pourfairecorrespondre lesmessagescontenantuneadressespécifique`true` .|Adresse à laquelle appliquer un filtre (dans l'en-tête À).|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|Utilise la <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> classe, avec <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  == pourfairecorrespondre lesmessagescontenantunpréfixed’adressespécifique.`true`|Adresse à laquelle appliquer un filtre utilisant le plus long préfixe correspondant.|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|and|Utilise la classe <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> qui évalue toujours les deux conditions avant de retourner.|filterData n’est pas utilisé; à la place, filter1 et filter2 ont le même nom que les filtres de messages correspondants (également dans le tableau), qui doivent être **et**Ed ensemble.|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|Personnalisé|Type défini par l'utilisateur qui étend la classe <xref:System.ServiceModel.Dispatcher.MessageFilter> et possède un constructeur qui prend une chaîne.|L'attribut customType est le nom de type qualifié complet de la classe à créer ; filterData est la chaîne à passer au constructeur lors de la création du filtre.|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|Utilise la classe <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> pour filtrer les messages en fonction du nom du point de terminaison de service sur lequel ils sont arrivés.|Nom du point de terminaison de service, par exemple: «serviceEndpoint1».  Ce doit être l'un des points de terminaison exposés sur le service de routage.|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|Utilise la classe <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>. Ce filtre correspond à tous les messages entrants.|filterData n'est pas utilisé. Ce filtre correspondra toujours à tous les messages.|\<filter name="matchAll1" filterType="MatchAll" />|  
|XPath|Utilise la classe <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> pour filtrer des requêtes XPath spécifiques dans le message.|Requête XPath à utiliser lors de la mise en correspondance des messages.|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 L’exemple suivant définit des entrées de filtre qui utilisent les filtres de message XPath, EndpointName et PrefixEndpointAddress. Cet exemple montre également l'utilisation d'un filtre personnalisé pour les entrées RoundRobinFilter1 et RoundRobinFilter2.  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"   
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"   
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"   
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
> La simple définition d'un filtre n'entraîne pas l'évaluation des messages par rapport au filtre. Le filtre doit être ajouté à une table de filtres, associée ensuite au point de terminaison de service exposé par le service de routage.  
  
### <a name="namespace-table"></a>Table d'espace de noms  
 Lors de l'utilisation d'un Filtre XPath, les données de filtre qui contiennent la requête XPath peuvent devenir extrêmement volumineuses en raison de l'utilisation d'espaces de noms. Pour pallier ce problème, le service de routage offre la possibilité de définir vos propres préfixes d'espace de noms à l'aide de la table d'espace de noms.  
  
 La table d’espace de noms est une collection d’objets <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> qui définit les préfixes d’espaces de noms communs qui peuvent être utilisés dans un XPath. Voici les espaces de noms et les préfixes d'espace de noms par défaut contenus dans la table d'espace de noms.  
  
|Préfixe|Espace de noms|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 Si vous prévoyez d’utiliser un espace de noms spécifique dans vos requêtes XPath, vous pouvez l’ajouter à la table d’espace de noms avec un préfixe d’espace de noms unique, et utiliser ce préfixe à la place de l’espace de noms complet dans toutes les requêtes XPath. L’exemple suivant définit un préfixe «custom» pour l’espace `"http://my.custom.namespace"`de noms, qui est ensuite utilisé dans la requête XPath contenue dans FilterData.  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>Tables de filtres  
 Tandis que chaque élément de filtre définit une comparaison logique qui peut s'appliquer à un message, la table de filtres fournit l'association entre l'élément de filtre et le point de terminaison de client de destination. Une table de filtres est une collection nommée d'objets <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> qui définissent l'association entre un filtre, un point de terminaison de destination primaire et une liste d'autres points de terminaison de sauvegarde. Les entrées de la table de filtres vous permettent également de spécifier une priorité facultative pour chaque condition de filtre. L'exemple suivant définit deux filtres, puis une table de filtres qui associe chaque filtre à un point de terminaison de destination.  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>      
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a>Priorité d'évaluation du filtre  
 Par défaut, toutes les entrées de la table de filtres sont évaluées simultanément, et le message qui est évalué est routé vers le ou les points de terminaison associés à chaque entrée de filtre correspondante. Si plusieurs filtres doivent avoir la valeur `true`, et si le message est en mode monodirectionnel ou duplex, le message est envoyé en mode multidiffusion aux points de terminaison de tous les filtres correspondants. Les messages demande-réponse ne peuvent pas être envoyés en mode multidiffusion parce que seule une réponse peut être retournée au client.  
  
 Une logique de routage plus complexe peut être implémentée en spécifiant des niveaux de priorité pour chaque filtre ; le service de routage évalue en premier tous les filtres au niveau de priorité le plus élevé. Si un message correspond à un filtre de ce niveau, aucun filtre de priorité plus faible n'est traité. Par exemple, un message entrant monodirectionnel est évalué par rapport à tous les filtres avec une priorité de niveau 2. Le message ne correspond à aucun filtre à ce niveau de priorité, donc le message est ensuite comparé aux filtres avec une priorité de niveau 1. Deux filtres de priorité 1 correspondent au message, et parce qu'il s'agit d'un message monodirectionnel, il est routé vers les deux points de terminaison de destination.  Étant donné qu'une correspondance a été trouvée parmi les filtres de priorité 1, aucun filtre de priorité 0 n'est évalué.  
  
> [!NOTE]
> Si aucune priorité n'est spécifiée, la valeur de priorité 0 est utilisée par défaut.  
  
 L'exemple suivant définit une table de filtres qui spécifie des priorités de 2, 1 et 0 pour les filtres référencés dans la table.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"   
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"   
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"   
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"   
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 Dans l’exemple précédent, si un message correspond au XPathFilter, il est routé vers le roundingCalcEndpoint et aucun filtre supplémentaire dans la table n’est évalué car tous les autres filtres sont de priorité plus faible. Toutefois, si le message ne correspond pas au XPathFilter, il est alors évalué par rapport à tous les filtres suivants de priorité plus faible, EndpointNameFilter et PrefixAddressFilter.  
  
> [!NOTE]
> Si possible, utilisez des filtres exclusifs au lieu de spécifier une priorité. En effet, l'évaluation des priorités risque d'entraîner une dégradation des performances.  
  
### <a name="backup-lists"></a>Listes de sauvegarde  
 Chaque filtre de la table de filtres peut éventuellement spécifier une liste de sauvegarde, qui est une collection nommée de points de terminaison (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>). Cette collection contient une liste ordonnée des points de terminaison auxquels le message sera transmis en cas de <xref:System.ServiceModel.CommunicationException> lors de l’envoi au point de terminaison primaire spécifié dans la propriété <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>. L’exemple suivant définit une liste de sauvegarde nommée «backupServiceEndpoints» qui contient deux points de terminaison.  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 Dans l’exemple précédent, si un envoi vers le point de terminaison principal «destination» échoue, le service de routage essaiera d’envoyer à chaque point de terminaison dans l’ordre dans lequel ils sont répertoriés, en commençant par envoyer à backupServiceQueue et en l’envoyant par la suite à alternateServiceQueue si le l’envoi à backupServiceQueue échoue. Si tous les points de terminaison de sauvegarde échouent, une erreur est retournée.
