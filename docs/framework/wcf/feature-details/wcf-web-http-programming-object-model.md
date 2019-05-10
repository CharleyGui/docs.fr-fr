---
title: Modèle objet de programmation Web HTTP WCF
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: f8bda6292506b64057dee006fa59b7723fa406b2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648412"
---
# <a name="wcf-web-http-programming-object-model"></a>Modèle objet de programmation Web HTTP WCF
Le modèle de programmation WCF WEB HTTP permet aux développeurs d’exposer des services Web de Windows Communication Foundation (WCF) via les demandes HTTP de base sans avoir recours à SOAP. Le modèle de programmation WCF WEB HTTP repose sur le modèle d’extensibilité WCF existant. Il définit les classes suivantes :  
  
 **Modèle de programmation :**  
  
- <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
- <xref:System.ServiceModel.Web.WebGetAttribute>  
  
- <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
- <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **Canaux et l’Infrastructure de répartiteur :**  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **Points d’extensibilité et les Classes d’utilitaire :**  
  
- <xref:System.UriTemplate>  
  
- <xref:System.UriTemplateTable>  
  
- <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 En cas d'application à une opération de service, <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> indique le profil de cache de sortie ASP.NET dans le fichier de configuration qui doit être utilisé pour mettre des réponses de l'opération dans le cache de sortie ASP .NET. Cette propriété accepte un seul paramètre, le nom de profil de cache qui spécifie les paramètres de cache dans le fichier de configuration.  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 L'attribut <xref:System.ServiceModel.Web.WebGetAttribute> est utilisé pour marquer une opération de service en tant qu'opération répondant aux requêtes HTTP GET. Il s'agit d'un comportement d'opération passif (les méthodes <xref:System.ServiceModel.Description.IOperationBehavior> n'ont aucune action) qui ajoute des métadonnées à la description de l'opération. L’attribut <xref:System.ServiceModel.Web.WebGetAttribute> n’a aucun effet à moins qu’un comportement recherchant ces métadonnées dans la description de l’opération (en particulier <xref:System.ServiceModel.Description.WebHttpBehavior>) soit ajouté à la collection de comportements du service. L'attribut <xref:System.ServiceModel.Web.WebGetAttribute> accepte les paramètres optionnels indiqués dans le tableau suivant :  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`BodyStyle`|Contrôle si les demandes envoyées à l'opération de service à laquelle l'attribut est appliqué et les réponses reçues en retour doivent être encapsulées.|  
|`RequestFormat`|Contrôle la mise en forme des messages de demande.|  
|`ResponseFormat`|Contrôle la mise en forme des messages de réponse.|  
|`UriTemplate`|Spécifie le modèle URI qui contrôle quelles requêtes HTTP sont mappées à l'opération de service à laquelle l'attribut est appliqué.|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 La classe <xref:System.ServiceModel.WebHttpBinding> intègre une prise en charge des données XML, JSON et des données binaires brutes à l'aide de <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>. Elle se compose d'un <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, d'un <xref:System.ServiceModel.Channels.HttpTransportBindingElement> et d'un objet <xref:System.ServiceModel.WebHttpSecurity>. <xref:System.ServiceModel.WebHttpBinding> est conçu pour être utilisé en conjonction avec <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 L'attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> est semblable au <xref:System.ServiceModel.Web.WebGetAttribute>, mais il est utilisé pour marquer une opération de service en tant qu'opération qui répond aux requêtes HTTP autres que GET. Il s'agit d'un comportement d'opération passif (les méthodes <xref:System.ServiceModel.Description.IOperationBehavior> n'ont aucune action) qui ajoute des métadonnées à la description de l'opération. L’attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> n’a aucun effet à moins qu’un comportement recherchant ces métadonnées dans la description de l’opération (en particulier <xref:System.ServiceModel.Description.WebHttpBehavior>) soit ajouté à la collection de comportements du service.  
  
 L'attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> accepte les paramètres optionnels indiqués dans le tableau suivant :  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`BodyStyle`|Contrôle si les demandes envoyées à l'opération de service à laquelle l'attribut est appliqué et les réponses reçues en retour doivent être encapsulées.|  
|`Method`|Spécifie la méthode HTTP à laquelle l'opération de service est mappée.|  
|`RequestFormat`|Contrôle la mise en forme des messages de demande.|  
|`ResponseFormat`|Contrôle la mise en forme des messages de réponse.|  
|`UriTemplate`|Spécifie le modèle URI qui contrôle quelles demandes GET sont mappées à l'opération de service à laquelle l'attribut est appliqué.|  
  
## <a name="uritemplate"></a>UriTemplate  
 La classe <xref:System.UriTemplate> vous permet de définir un jeu d'URI de structure similaire. Les modèles sont composés de deux parties : un chemin d’accès et une requête. Un chemin d’accès est constitué d’une série de segments délimités par une barre oblique (/). Chaque segment peut avoir une valeur littérale, une valeur de variable (écrite entre accolades [{}], contraint à adapter au contenu d’un seul segment) ou un caractère générique (écrit sous la forme d’un astérisque [\*], qui correspond à « le reste du chemin d’accès »), qui doit apparaître à la fin du chemin d’accès. L'expression de requête peut être entièrement omise. Si elle est présente, elle spécifie une série non triée de paires nom/valeur. Éléments de l’expression de requête peuvent être des paires littérales ( ? x = 2) ou des paires variables ( ? x = {*valeur*}). Les valeurs non couplées ne sont pas autorisées. <xref:System.UriTemplate> est utilisé en interne par le modèle de programmation WCF WEB HTTP pour mapper des URI spécifiques ou des groupes d’URI aux opérations de service.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 La classe <xref:System.UriTemplateTable> représente un jeu associatif d'objets <xref:System.UriTemplate> liés à un objet choisi par le développeur. Elle vous permet de faire correspondre les URI (Uniform Resource Identifiers) des candidats par rapport aux modèles du jeu et de récupérer les données associées aux modèles correspondants. <xref:System.UriTemplateTable> est utilisé en interne par le modèle de programmation WCF WEB HTTP pour mapper des URI spécifiques ou des groupes d’URI aux opérations de service.  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> étend le <xref:System.ServiceModel.ServiceHost> de manière à faciliter l'hébergement d'un service de style Web non-SOAP. Si <xref:System.ServiceModel.Web.WebServiceHost> ne trouve aucun point de terminaison dans la description du service, il crée automatiquement un point de terminaison par défaut au niveau de l'adresse de base du service. Lors de la création d'un point de terminaison HTTP par défaut, <xref:System.ServiceModel.Web.WebServiceHost> désactive également la page d'aide HTTP et la fonctionnalité WSDL (Web Services Description Language) GET afin que le point de terminaison des métadonnées n'interfère pas avec le point de terminaison HTTP par défaut.  <xref:System.ServiceModel.Web.WebServiceHost> garantit également que le <xref:System.ServiceModel.WebHttpBinding> requis soit attaché à tous les points de terminaison qui utilisent <xref:System.ServiceModel.Description.WebHttpBehavior>. Enfin, <xref:System.ServiceModel.Web.WebServiceHost> configure automatiquement la liaison du point de terminaison afin qu’il puisse profiter des paramètres de sécurité IIS (Internet Information Services) en cas d’utilisation dans un répertoire virtuel sécurisé.  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 La classe <xref:System.ServiceModel.Activation.WebServiceHostFactory> est utilisée pour créer dynamiquement un <xref:System.ServiceModel.Web.WebServiceHost> lorsqu'un service est hébergé dans les services IIS (Internet Information Services) ou WAS (Windows Process Activation Service). À la différence d'un service auto-hébergé où l'application d'hébergement instancie le <xref:System.ServiceModel.Web.WebServiceHost>, les services hébergés dans les services IIS ou WAS utilisent cette classe pour créer le <xref:System.ServiceModel.Web.WebServiceHost> pour ces services. La méthode <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> est appelée lorsqu'une demande entrante pour le service est reçue.  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 La classe <xref:System.ServiceModel.Description.WebHttpBehavior> fournit les formateurs, sélecteurs d'opération, etc. requis pour la prise en charge de service de style Web au niveau de la couche de modèle de service. Il est implémenté en tant que comportement de point de terminaison (utilisé en conjonction avec <xref:System.ServiceModel.WebHttpBinding>) et autorise la spécification de formateurs et de sélecteurs d'opération pour chaque point de terminaison, ce qui permet à une même implémentation de service d'exposer à la fois des points de terminaison SOAP et POX.  
  
### <a name="extending-webhttpbehavior"></a>Extension de WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> peut être étendu à l'aide de différentes méthodes virtuelles : <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>, <xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29> et <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>. Les développeurs peuvent dériver une classe de <xref:System.ServiceModel.Description.WebHttpBehavior> et substituer ces méthodes de manière à personnaliser le comportement par défaut.  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> est un exemple d'extension de <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> permet de recevoir des requêtes HTTP à partir d’un client ASP.NET AJAX basé sur navigateur des points de terminaison Windows Communication Foundation (WCF). Le [AJAX Service utilisant HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) est un exemple d’utilisation de ce point d’extensibilité.  
  
> [!WARNING]
>  Lors de l'utilisation de <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, <xref:System.UriTemplate> ne sont pas pris en charge dans les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 La classe <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> utilise les classes <xref:System.UriTemplate> et <xref:System.UriTemplateTable> pour distribuer les appels aux opérations de service.  
  
## <a name="compatibility"></a>Compatibilité  
 Le modèle de programmation WCF WEB HTTP n’utilise pas de messages basés sur SOAP et par conséquent ne prend pas en charge WS-* protocoles. Vous pouvez toutefois exposer le même contrat par deux points de terminaison différents, l'un utilisant SOAP et l'autre pas. Voir [Guide pratique pour Exposer un contrat à des Clients SOAP et Web](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) pour obtenir un exemple.  
  
## <a name="security"></a>Sécurité  
 Étant donné que le modèle de programmation WCF WEB HTTP ne prend pas en charge WS-* protocoles, la seule façon de sécuriser un service Web basé sur le modèle de programmation WCF WEB HTTP consiste à exposer votre service à l’aide de SSL. Pour plus d’informations sur la configuration de SSL avec [!INCLUDE[iisver](../../../../includes/iisver-md.md)] consultez [comment implémenter SSL dans IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [Vue d’ensemble du modèle de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
