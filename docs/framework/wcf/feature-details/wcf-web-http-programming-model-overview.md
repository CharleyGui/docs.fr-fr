---
title: Vue d'ensemble du modèle de programmation Web HTTP WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: d4908eb75324d4316ea615d1a0acc286750752e7
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487721"
---
# <a name="wcf-web-http-programming-model-overview"></a>Vue d'ensemble du modèle de programmation Web HTTP WCF
Le modèle de programmation HTTP WEB de Windows Communication Foundation (WCF) fournit les éléments de base requis pour générer des services WEB HTTP avec WCF. Les services HTTP WEB WCF sont conçus pour être accessibles par la majorité des clients possibles, y compris les navigateurs Web et ont les spécifications uniques suivantes :  
  
- **URI et traitement des URI** URI jouent un rôle central dans la conception de services WEB HTTP. La programmation WEB HTTP WCF modèle utilise le <xref:System.UriTemplate> et <xref:System.UriTemplateTable> classes pour fournir des capacités de traitement des URI.  
  
- **Prise en charge pour les opérations GET et POST** rendre les services WEB HTTP utilisent le verbe GET pour la récupération de données, en plus de divers verbes de commande pour la modification des données et l’appel distant. La programmation WEB HTTP WCF modèle utilise le <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> pour associer des opérations de service GET et autres verbes HTTP tels que PUT, POST et DELETE.  
  
- **Plusieurs formats de données** services de style Web traitent de nombreux types de données en plus des messages SOAP. La programmation WEB HTTP WCF modèle utilise le <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> pour prendre en charge de nombreux formats de données différents y compris des documents XML, JSON objet de données et des flux de contenu binaire tels que des images, des fichiers vidéo ou texte brut.  
  
 Le modèle de programmation HTTP WEB WCF étend la portée de WCF pour couvrir des scénarios de style Web qui incluent des services HTTP WEB, les services AJAX et JSON et les flux de syndication (ATOM/RSS). Pour plus d’informations sur les services AJAX et JSON, consultez [intégration d’AJAX et prise en charge JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Pour plus d’informations sur la Syndication, consultez [vue d’ensemble de la Syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Il n'existe aucune restriction supplémentaire sur les types de données qui peuvent être retournées à partir d'un service Web HTTP. Tout type sérialisable peut être retourné à partir d'une opération de service WEB HTTP. Parce que les opérations de service WEB HTTP peuvent être appelées par un navigateur Web, il existe une restriction sur les types de données pouvant être spécifiées dans une URL. Pour plus d’informations sur les types sont pris en charge par défaut, consultez le **paramètres de chaîne de requête UriTemplate et URL** section ci-dessous. Le comportement par défaut peut être modifié en fournissant votre propre implémentation T:System.ServiceModel.Dispatcher.QueryStringConverter, qui indique comment convertir les paramètres spécifiés dans une URL en type de paramètre réel. Pour plus d'informations, consultez <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Services écrits avec le modèle de programmation HTTP WEB WCF n’utilisent pas de messages SOAP. SOAP n’étant pas utilisée, les fonctionnalités de sécurité fournies par WCF ne peut pas être utilisées. Toutefois, vous pouvez utiliser la sécurité basée sur le transport en hébergeant votre service avec HTTPS. Pour plus d’informations sur la sécurité WCF, consultez [vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  L’installation d’une extension WebDAV pour IIS peut entraîner les services HTTP Web à retourner une erreur HTTP 405 lorsque l’extension WebDav essaie de gérer toutes les demandes PUT. Pour contourner ce problème, vous pouvez désinstaller l’extension WebDav ou désactiver l’extension WebDav pour votre site web. Pour plus d’informations, consultez [IIS et WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Traitement des URI avec UriTemplate et UriTemplateTable  
 Les modèles URI fournissent une syntaxe efficace pour exprimer des larges jeux d'URI dont la structure est semblable. Par exemple, le modèle suivant exprime le jeu de tous les URI à trois segments qui commencent par "a" et se terminent par "c" sans tenir compte de la valeur du segment intermédiaire : a/{segment}/c  
  
 Ce modèle décrit des URI comme suit :  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- et ainsi de suite.  
  
 Dans ce modèle, la notation avec accolade ("{segment}") indique un segment variable au lieu d'une valeur littérale.  
  
 Le .NET Framework fournit une API sur l'utilisation des modèles d'URI appelée <xref:System.UriTemplate>. `UriTemplates` vous permet d'effectuer les opérations suivantes :  
  
- Vous pouvez appeler une de la `Bind` méthodes avec un ensemble de paramètres pour produire un *URI complètement fermé* qui correspond au modèle. Cela signifie que toutes les variables dans le modèle URI sont remplacées par des valeurs réelles.  
  
- Vous pouvez appeler `Match`() avec un URI candidat qui utilise un modèle pour décomposer les parties qui constituent un URI candidat et qui retourne un dictionnaire qui contient les différentes parties de l'URI libellé selon les variables du modèle.  
  
- `Bind`() et `Match`() sont des inverses qui vous permettent d'appeler `Match`( `Bind`(x)) et de revenir dans le même environnement de démarrage.  
  
 Il arrive souvent (surtout sur le serveur où la distribution d'une demande vers une opération de service basée sur l'URI est nécessaire) de vouloir effectuer le suivi d'un jeu d'objets <xref:System.UriTemplate> dans une structure de données qui peut adresser indépendamment chacun des modèles contenus. <xref:System.UriTemplateTable> représente un ensemble de modèles d'URI et sélectionne la meilleure correspondance en fonction d'un ensemble de modèles et d'un URI candidat. Cela n’est pas affilié à une pile de mise en réseau particulière (WCF inclus) afin que vous puissiez l’utiliser chaque fois que nécessaire.  
  
 Le modèle de service WCF utilise <xref:System.UriTemplate> et <xref:System.UriTemplateTable> pour associer des opérations de service à un jeu d'URI décrit par un <xref:System.UriTemplate>. Une opération de service est associée à un <xref:System.UriTemplate> à l'aide de <xref:System.ServiceModel.Web.WebGetAttribute> ou de <xref:System.ServiceModel.Web.WebInvokeAttribute>. Pour plus d’informations sur <xref:System.UriTemplate> et <xref:System.UriTemplateTable>, consultez [UriTemplate et UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Attributs WebGet et WebInvoke  
 Rendre des services HTTP WEB WCF utilisent des verbes de récupération (par exemple HTTP GET) en plus de divers verbes (par exemple HTTP POST, PUT et DELETE). Le modèle de programmation HTTP WEB WCF permet aux développeurs de service de contrôle le modèle URI et le verbe associé à leurs opérations de service avec le <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> vous permettent de contrôler comment les opérations individuelles sont attachées aux URI et les méthodes HTTP associées à ces URI. Par exemple, ajouter <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> dans le code suivant.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,   
                               string newName );  
}  
```  
  
 Le code précédent vous permet d'effectuer les demandes HTTP suivantes.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> prend la valeur POST par défaut mais vous pouvez l'utiliser aussi pour d'autres verbes.  
  
```  
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Pour voir un exemple complet d’un service WCF qui utilise le modèle de programmation HTTP WEB WCF, consultez [Comment : Créer un Service Web HTTP de WCF de base](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Paramètres de chaîne de requête UriTemplate et URL  
 Les services de style Web peuvent être appelés depuis un navigateur Web en tapant une URL associée à une opération de service. Ces opérations de service peuvent accepter des paramètres de chaîne de requête qui doivent être spécifiés sous forme de chaîne dans l'URL. Le tableau suivant affiche les types qui peuvent être passés dans une URL et le format utilisé.  
  
|Type|Format|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (la notation d'exposant n'est pas requise)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (la notation d'exposant n'est pas requise)|  
|<xref:System.Char>|Tout caractère unique|  
|<xref:System.Decimal>|Tout décimal en notation standard (aucun exposant)|  
|<xref:System.Boolean>|True ou False (ne respecte pas la casse)|  
|<xref:System.String>|Toute chaîne (la chaîne Null n'est pas prise en charge et aucun échappement n'est fait)|  
|<xref:System.DateTime>|MM/DD/YYYY<br /><br /> MM/JJ/AAAA HH : MM : [AM&AMP;#124;PM]<br /><br /> Mois Jour Année<br /><br /> Mois jour année hh : mm : [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Où DD = jours, HH = heures, MM = minutes, SS = secondes|  
|<xref:System.Guid>|Un GUID, par exemple :<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> Où DD = jours, HH = heures, MM = minutes, SS = secondes|  
|Énumérations|La valeur d'énumération, par exemple, qui définit l'énumération comme indiqué dans le code suivant.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Chacune des valeurs d'énumération individuelles (ou leurs valeurs entières correspondantes) peut être spécifiée dans la chaîne de requête.|  
|Types qui ont un `TypeConverterAttribute` pouvant convertir le type vers et depuis une représentation sous forme de chaîne.|Dépend du convertisseur de type.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formats et le modèle de programmation Web HTTP WCF  
 Le modèle de programmation HTTP WEB WCF dispose de nouvelles fonctionnalités pour travailler avec nombreux formats de données différents. Au niveau de la couche de liaison, <xref:System.ServiceModel.WebHttpBinding> peut lire et écrire les différents types suivants de données :  
  
- XML  
  
- JSON  
  
- Flux binaires opaques  
  
 Cela signifie que le modèle de programmation HTTP WEB WCF peut gérer n’importe quel type de données, mais vous risquez de programmer par rapport à <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] assure la prise en charge des données JSON (AJAX) ainsi que des flux de syndication (notamment ATOM et RSS). Pour plus d’informations sur ces fonctionnalités, consultez [mise en forme de WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[vue d’ensemble de la Syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) et [intégration d’AJAX et prise en charge JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Modèle de programmation Web HTTP WCF et sécurité  
 Étant donné que le modèle de programmation HTTP WEB WCF ne prend pas en charge WS-* protocoles, la seule façon de sécuriser un service HTTP WEB WCF doit exposer le service via HTTPS à l’aide de SSL. Pour plus d’informations sur la configuration de SSL avec IIS 7.0, consultez [comment implémenter SSL dans IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Dépannage du modèle de programmation HTTP Web WCF  
 Lors de l'appel de services Web HTTP WCF à l'aide d'un <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> afin de créer un canal, le <xref:System.ServiceModel.Description.WebHttpBehavior> utilise le <xref:System.ServiceModel.EndpointAddress> défini dans le fichier de configuration même si un <xref:System.ServiceModel.EndpointAddress> différent est passé au <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Voir aussi

- [Syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Modèle objet de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Modèle de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
