---
title: <serviceDebug>
ms.date: 03/30/2017
ms.assetid: 6d7ea986-f232-49fe-842c-f934d9966889
ms.openlocfilehash: 4eb79cc91ef489501c4c8bb6311f240d855ed053
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399640"
---
# \<serviceDebug>
Spécifie les fonctionnalités de débogage et d’informations d’aide pour un service Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDebug>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceDebug httpHelpPageBinding="String"
              httpHelpPageBindingConfiguration="String"
              httpHelpPageEnabled="Boolean"
              httpHelpPageUrl="Uri"
              httpsHelpPageBinding="String"
              httpsHelpPageBindingConfiguration="String"
              httpsHelpPageEnabled="Boolean"
              httpsHelpPageUrl="Uri"
              includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|httpHelpPageBinding|Valeur de chaîne qui spécifie le type de liaison à utiliser lorsque le protocole HTTP permet d’accéder à la page d’aide du service.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType>. En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpHelpPageBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpHelpPageBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison. Le même nom doit être défini dans la section `<bindings>`.|  
|httpHelpPageEnabled|Valeur booléenne qui contrôle si WCF publie une page d’aide HTML à l’adresse spécifiée par l' `httpHelpPageUrl` attribut. Par défaut, il s’agit de `true`.<br /><br /> Vous pouvez affecter la valeur `false` à cette propriété pour désactiver la publication d'une page d'aide HTML visible par les navigateurs HTML.<br /><br /> Pour vous assurer que la page d'aide HTML est publiée à l'emplacement contrôlé par l'attribut `httpHelpPageUrl`, vous devez affecter la valeur `true` à cet attribut. L'une des conditions suivantes doit également être remplie :<br /><br /> -L' `httpHelpPageUrl` attribut est une adresse absolue qui prend en charge le schéma de protocole http.<br />: Il existe une adresse de base pour le service qui prend en charge le schéma de protocole HTTP.<br /><br /> Bien qu'une exception soit levée si une adresse absolue qui ne prend pas en charge le schéma de protocole HTTP est assignée à l'attribut `httpHelpPageUrl`, tout autre scénario dans lequel aucun des critères précédents n'est rempli ne lève pas d'exception et ne génère aucune page d'aide HTML.|  
|httpHelpPageUrl|URI qui spécifie l'URL basée sur HTTP relative ou absolue du fichier d'aide HTML personnalisé que l'utilisateur consulte lorsque le point de terminaison est affiché à l'aide d'un navigateur HTML.<br /><br /> Vous pouvez utiliser cet attribut pour activer l'utilisation d'un fichier d'aide HTML personnalisé retourné par une requête HTTP/Get, à partir d'un navigateur HTML par exemple. L'emplacement du fichier d'aide HTML est résolu comme suit.<br /><br /> 1. Si la valeur de cet attribut est une adresse relative, l’emplacement du fichier d’aide HTML est la valeur de l’adresse de base du service qui prend en charge les requêtes HTTP, plus cette valeur de propriété.<br />2. Si la valeur de cet attribut est une adresse absolue et prend en charge les requêtes HTTP, l’emplacement du fichier d’aide HTML est la valeur de cette propriété.<br />3. Si la valeur de cet attribut est absolue mais ne prend pas en charge les requêtes HTTP, une exception est levée.<br /><br /> Cet attribut est valide uniquement lorsque l' `httpHelpPageEnabled` attribut est `true` .|  
|httpsHelpPageBinding|Valeur de chaîne qui spécifie le type de liaison à utiliser lorsque le protocole HTTPS permet d’accéder à la page d’aide du service.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>. En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.|  
|httpsHelpPageBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpsHelpPageBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison. Le même nom doit être défini dans la section `<bindings>`.|  
|httpsHelpPageEnabled|Valeur booléenne qui contrôle si WCF publie une page d’aide HTML à l’adresse spécifiée par l' `httpsHelpPageUrl` attribut. Par défaut, il s’agit de `true`.<br /><br /> Vous pouvez affecter la valeur `false` à cette propriété pour désactiver la publication d'une page d'aide HTML visible par les navigateurs HTML.<br /><br /> Pour vous assurer que la page d'aide HTML est publiée à l'emplacement contrôlé par l'attribut `httpsHelpPageUrl`, vous devez affecter la valeur `true` à cet attribut. L'une des conditions suivantes doit également être remplie :<br /><br /> -L' `httpsHelpPageUrl` attribut est une adresse absolue qui prend en charge le schéma de protocole HTTPS.<br />: Il existe une adresse de base pour le service qui prend en charge le schéma de protocole HTTPs.<br /><br /> Bien qu'une exception soit levée si une adresse absolue qui ne prend pas en charge le schéma de protocole HTTPS est assignée à l'attribut `httpsHelpPageUrl`, tout autre scénario dans lequel aucun des critères précédents n'est rempli ne lève pas d'exception et ne génère aucune page d'aide HTML.|  
|httpsHelpPageUrl|URI qui spécifie l'URL basée sur HTTPS relative ou absolue du fichier d'aide HTML personnalisé que l'utilisateur consulte lorsque le point de terminaison est affiché à l'aide d'un navigateur HTML.<br /><br /> Vous pouvez utiliser cet attribut pour activer l'utilisation d'un fichier d'aide HTML personnalisé retourné par une requête HTTPS/Get, à partir d'un navigateur HTML par exemple. L'emplacement du fichier d'aide HTML est résolu comme suit :<br /><br /> -Si la valeur de cette propriété est une adresse relative, l’emplacement du fichier d’aide HTML est la valeur de l’adresse de base du service qui prend en charge les requêtes HTTPs, plus cette valeur de propriété.<br />-Si la valeur de cette propriété est une adresse absolue et prend en charge les requêtes HTTPs, l’emplacement du fichier d’aide HTML est la valeur de cette propriété.<br />-Si la valeur de cette propriété est absolue mais ne prend pas en charge les requêtes HTTPs, une exception est levée.<br /><br /> Cet attribut est valide uniquement lorsque l' `httpHelpPageEnabled` attribut est `true` .|  
|includeExceptionDetailInFaults|Valeur qui spécifie si des informations sur les exceptions managées doivent être incluses dans les informations sur les erreurs SOAP retournées au client à des fins de débogage. Par défaut, il s’agit de `false`.<br /><br /> Si vous affectez par programme la valeur `true` à l'attribut, vous pouvez activer le flux d'informations sur les exceptions managées pour le client à des fins de débogage, ainsi que la publication de fichiers d'informations HTML pour les utilisateurs qui parcourent le service avec un navigateur Web. **Attention :**  Le retour d’informations sur les exceptions managées aux clients peut être un risque pour la sécurité. En effet, les détails de l'exception exposent des informations relatives à l'implémentation d'un service interne qui peuvent être utilisées par des clients non autorisés.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Remarques  
 L’affectation de la valeur `includeExceptionDetailInFaults` à `true` permet au service de retourner toute exception levée par le code d’application même si l’exception n’est pas déclarée à l’aide de <xref:System.ServiceModel.FaultContractAttribute> . Ce paramètre est utile lors du débogage de cas où le serveur lève une exception inattendue. Avec cet attribut, un formulaire sérialisé de l'exception inconnue est retourné et vous pouvez consulter plus de détails de l'exception.  
  
> [!CAUTION]
> Le retour d'informations sur les exceptions managées aux clients peut constituer un problème de sécurité, car les détails d'exception exposent des informations relatives à l'implémentation de service interne que des clients non autorisés pourraient utiliser. En raison des risques de sécurité encourus, il est fortement recommandé de n'utiliser cette méthode que dans le cadre de scénarios de débogage contrôlés. Vous devez affecter la valeur `includeExceptionDetailInFaults` à `false` lors du déploiement de l'application.  
  
 Pour plus d’informations sur les problèmes de sécurité liés à l’exception managée, consultez [spécification et gestion des erreurs dans les contrats et les services](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md). Pour obtenir un exemple de code, consultez [comportement de débogage de service](../../../wcf/samples/service-debug-behavior.md).  
  
 Vous pouvez également définir `httpsHelpPageEnabled` et `httpsHelpPageUrl` pour activer ou désactiver la page d'aide. Chaque service peut éventuellement exposer une page d'aide qui contient des informations sur le service, et notamment le point de terminaison permettant d'obtenir le WSDL pour le service. Pour ce faire, affectez `httpHelpPageEnabled` à `true`. Cela permet de retourner la page d'aide dans une demande GET à l'adresse de base du service. Pour modifier cette adresse, définissez l'attribut `httpHelpPageUrl`. En outre, vous pouvez faire sécuriser cette procédure en utilisant HTTPS au lieu de HTTP.  
  
 Les attributs facultatifs `httpHelpPageBinding` et `httpHelpPageBinding` vous permettent de configurer les liaisons utilisées pour accéder à la page Web du service. S’ils ne sont pas spécifiés, les liaisons par défaut (`HttpTransportBindingElement` dans le cas de HTTP et `HttpsTransportBindingElement` dans le cas de HTTPS) sont utilisées pour accéder à la page d’aide du service. Notez que vous ne pouvez pas utiliser ces attributs avec les liaisons WCF intégrées. Seules les liaisons avec des éléments de liaison internes qui prennent en charge XREF : System. ServiceModel. Channels. IReplyChannel> sont prises en charge. En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceDebugElement>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
- [Spécification et gestion des erreurs dans les contrats et les services](../../../wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Gestion des exceptions et des erreurs](../../../wcf/extending/handling-exceptions-and-faults.md)
- [Service Debug Behavior](../../../wcf/samples/service-debug-behavior.md)
