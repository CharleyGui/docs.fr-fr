---
title: Utilisation d'un service de données dans une application cliente (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: b921e78c1b3d3d90d9ac8b4a459df496cf6d14dd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180580"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Utilisation d'un service de données dans une application cliente (services de données WCF)

Vous pouvez accéder à un service qui expose un flux OData (Open Data Protocol) en fournissant un URI à un navigateur Web. L'URI fournit l'adresse d'une ressource, et les messages de demande sont envoyés à ces adresses pour accéder ou modifier les données sous-jacentes que représente la ressource. Le navigateur émet une commande HTTP obten et retourne la ressource demandée sous forme de flux OData. Pour plus d’informations, consultez [accès au service à partir d’un navigateur Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Même si un navigateur Web peut être utile pour vérifier qu’un service OData retourne les données attendues, les services OData de production qui vous permettent également de créer, mettre à jour et supprimer des données sont généralement accessibles par le code d’application ou les langages de script d’une page Web. Cette rubrique fournit une vue d’ensemble de l’accès aux flux OData à partir d’une application cliente.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Accès et modification des données à l'aide de la sémantique REST  

 OData permet de garantir l’interopérabilité entre les services qui exposent les flux OData et les applications qui consomment des flux OData. Les applications accèdent aux données et les modifient dans un service OData en envoyant des messages de demande d’une action HTTP spécifique et avec un URI qui adresse une ressource d’entité par rapport à laquelle l’action doit être effectuée. Lorsque les données d'entité doivent être fournies, elles le sont comme une charge utile spécifiquement encodée dans le corps du message.  
  
### <a name="http-actions"></a>Actions HTTP  

 OData prend en charge les actions HTTP suivantes pour effectuer des opérations de création, lecture, mise à jour et suppression sur les données d’entité que la ressource adressée représente :  
  
- **Http obtient** : il s’agit de l’action par défaut lorsqu’un utilisateur accède à une ressource à partir d’un navigateur. Aucune charge utile n'est fournie dans le message de demande, et une méthode de réponse avec une charge utile qui contient les données demandées est retournée.  
  
- **Http postérieur** -insère les nouvelles données d’entité dans la ressource fournie. Les données à insérer sont fournies dans la charge utile du message de demande. La charge utile du message de réponse contient les données de l'entité créée récemment. Cela inclut les valeurs de clés créées automatiquement. L'en-tête contient également l'URI qui adresse la nouvelle ressource d'entité.  
  
- **Http Delete** -supprime les données d’entité que la ressource spécifiée représente. Une charge utile n'est pas présente dans les messages de demande ou de réponse.  
  
- **Http put** -remplace les données d’entité existantes au niveau de la ressource demandée par les nouvelles données fournies dans la charge utile du message de demande.  
  
- **Http Merge** -en raison de l’efficacité de l’exécution d’une suppression suivie d’une insertion dans la source de données uniquement pour modifier les données d’entité, OData introduit une nouvelle action de fusion http. La charge utile du message de demande contient les propriétés qui doivent être changées sur la ressource d'entité adressée. Étant donné que la fusion HTTP n’est pas définie dans la spécification HTTP, elle peut nécessiter un traitement supplémentaire pour acheminer une demande de fusion HTTP via des serveurs non compatibles OData.  
  
 Pour plus d’informations, consultez [OData : Operations](https://www.odata.org/documentation/odata-version-2-0/operations/).
  
### <a name="payload-formats"></a>Formats de charge utile  

 Pour une demande HTTP PUT, HTTP POST ou HTTP MERGE, la charge utile d’un message de demande contient les données d’entité que vous envoyez au service de données. Le contenu de la charge utile dépend du format de données du message. Les réponses HTTP à toutes les actions sauf DELETE contiennent également une charge utile. OData prend en charge les formats de charge utile suivants pour l’accès et la modification des données avec le service :  
  
- **Atom** : encodage de message XML défini par OData en tant qu’extension du protocole de publication Atom (AtomPub) pour permettre l’échange de données sur http pour les flux Web, les podcasts, les wikis et les fonctionnalités Internet basées sur XML. Pour plus d’informations, consultez [OData : format Atom](https://www.odata.org/documentation/odata-version-2-0/atom-format/).
  
- **JSON-JavaScript Object Notation** (JSON) est un format d’échange de données léger basé sur un sous-ensemble du langage de programmation JavaScript. Pour plus d’informations, consultez [OData : format JSON](https://www.odata.org/documentation/odata-version-2-0/json-format/).
  
 Le format du message de la charge utile est demandé dans l'en-tête du message de requête HTTP. Pour plus d’informations, consultez [OData : Operations](https://www.odata.org/documentation/odata-version-2-0/operations/).
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Accès et modification des données à l'aide des bibliothèques clientes  

 WCF Data Services comprend des bibliothèques clientes qui vous permettent de consommer plus facilement un flux OData à partir d' .NET Framework et d’applications clientes basées sur Silverlight. Ces bibliothèques simplifient l'envoi et la réception des messages HTTP. Elles traduisent également la charge utile de message dans les objets CLR qui représentent des données d'entité. Les bibliothèques clientes comprennent les deux classes principales <xref:System.Data.Services.Client.DataServiceContext> et <xref:System.Data.Services.Client.DataServiceQuery%601>. Ces classes vous permettent d'interroger un service de données, puis d'utiliser les données d'entité retournées sous forme d'objets CLR. Pour plus d’informations, consultez [WCF Data Services bibliothèque cliente](wcf-data-services-client-library.md) et [WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à un service de données. Cet outil demande les métadonnées de service à un service de données référencé et génère le <xref:System.Data.Services.Client.DataServiceContext> qui représente un service de données, ainsi que les classes de service de données client qui représentent des entités. Pour plus d’informations, consultez [génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md).  
  
 Des bibliothèques de programmation peuvent être utilisées pour consommer un flux OData dans d’autres types d’applications clientes. Pour plus d’informations sur le kit de développement logiciel (SDK) OData, consultez [exemple de code ODATA SDK](https://www.odata.org/ecosystem/#sdk).
  
## <a name="see-also"></a>Voir aussi

- [Accès aux ressources d’un service de données](accessing-data-service-resources-wcf-data-services.md)
- [Démarrage rapide](quickstart-wcf-data-services.md)
