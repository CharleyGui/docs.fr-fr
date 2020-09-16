---
title: Utilisation d'actions pour implémenter le comportement côté serveur
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 6595a2648730a25f5322f1bcb743795230ad27eb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555079"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Utilisation d'actions pour implémenter le comportement côté serveur

Les actions OData permettent d'implémenter un comportement qui agit sur une ressource extraite d'un service OData. Par exemple, prenez un film numérique comme ressource. Vous pouvez effectuer plusieurs opérations avec celui-ci : extraction, évaluation/commentaire ou archivage. Ce sont des exemples d'actions pouvant être implémentées par un service de données WCF qui gère les films numériques. Les actions sont écrites dans une réponse OData qui contient une ressource sur laquelle l'action peut être appelée. Lorsqu'un utilisateur demande une ressource qui représente un film numérique, la réponse retournée par le service de données WCF contient des informations sur les actions disponibles pour cette ressource. La disponibilité d'une action dépend de l'état du service de données ou de la ressource. Par exemple, une fois qu'un film numérique est extrait, il ne peut pas être extrait par un autre utilisateur. Les clients peuvent appeler une action en indiquant simplement une URL. Par exemple, `http://MyServer/MovieService.svc/Movies(6)` identifie un film numérique spécifique et `http://MyServer/MovieService.svc/Movies(6)/Checkout` appelle l’action sur le film spécifique. Les actions vous permettent d'exposer votre modèle de service sans exposer votre modèle de données. Poursuivons avec l'exemple de service de film, vous pouvez autoriser un utilisateur à évaluer un film, mais pas à exposer directement les données d'évaluation en tant que ressource. Vous pouvez implémenter une action d'évaluation pour autoriser l'utilisateur à évaluer un film, sans accéder directement aux données d'évaluation en tant que ressource.

## <a name="implementing-an-action"></a>Implémentation d'une action
 Pour implémenter une action de service, vous devez implémenter les <xref:System.IServiceProvider> interfaces, [IDataServiceActionProvider](/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))et [IDataServiceInvokable](/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) . <xref:System.IServiceProvider> permet à WCF Data Services d’accéder à votre implémentation de [IDataServiceActionProvider](/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)). [IDataServiceActionProvider](/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) permet à WCF Data Services de créer, Rechercher, décrire et appeler des actions de service. [IDataServiceInvokable](/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) vous permet d’appeler le code qui implémente le comportement des actions de service et d’obtenir les résultats, le cas échéant. N'oubliez pas que les services de données WCF sont des services WCF par appel ; une nouvelle instance du service est créée à chaque fois que le service est appelé.  Assurez-vous qu'aucun travail inutile n'est effectué lors de la création du service.

### <a name="iserviceprovider"></a>IServiceProvider
 <xref:System.IServiceProvider> contient une méthode appelée <xref:System.IServiceProvider.GetService%2A>. Cette méthode est appelée par les services de données WCF pour récupérer plusieurs fournisseurs de services, notamment des fournisseurs de services de métadonnées et des fournisseurs d'actions de service de données. Lorsque vous êtes invité à entrer un fournisseur d’action de service de données, retournez votre implémentation de [IDataServiceActionProvider](/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) .

### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider
 [IDataServiceActionProvider](/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) contient des méthodes qui vous permettent de récupérer des informations sur les actions disponibles. Lorsque vous implémentez [IDataServiceActionProvider](/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) , vous augmentez les métadonnées de votre service qui est défini par l’implémentation de [IDataServiceActionProvider](/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) par votre service avec des actions et en gérant la distribution à ces actions selon le cas.

#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction
 La [méthode AdvertiseServiceAction](/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103)) est appelée pour déterminer quelles actions sont disponibles pour la ressource spécifiée. Cette méthode est appelée uniquement pour les actions qui ne sont pas toujours disponibles. Elle s'utilise pour vérifier si l'action doit être incluse dans la réponse OData en fonction de l'état de la ressource demandée ou de l'état du service. Le mode de vérification dépend entièrement de vous. Si l'opération permettant de calculer la disponibilité et la ressource active dans un flux est coûteuse en ressources, la vérification peut être ignorée et l'action publiée. Le paramètre `inFeed` a la valeur `true` si la ressource active retournée fait partie d'un flux.

#### <a name="createinvokable"></a>CreateInvokable
 [CreateInvokable](/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103)) est appelé pour créer un [IDataServiceInvokable](/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) qui contient un délégué qui encapsule le code qui implémente le comportement de l’action. Cela crée l’instance [IDataServiceInvokable](/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) , mais n’appelle pas l’action. Les actions de service de données WCF ont des effets secondaires et doivent fonctionner conjointement avec le fournisseur de mise à jour pour enregistrer ces modifications sur le disque. La méthode [IDataServiceInvokable. Invoke](/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103)) est appelée à partir de la méthode SaveChanges () du fournisseur de mise à jour est appelée.

#### <a name="getserviceactions"></a>GetServiceActions
 Cette méthode retourne une collection d’instances [ServiceAction](/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) qui représentent toutes les actions exposées par un service de données WCF. [ServiceAction](/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) est la représentation de métadonnées d’une action et comprend des informations telles que le nom de l’action, ses paramètres et son type de retour.

#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType
 Cette méthode retourne une collection de toutes les instances [ServiceAction](/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) qui peuvent être liées au type de paramètre de liaison spécifié. En d’autres termes, tous les [ServiceAction](/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))qui peuvent agir sur le type de ressource spécifié (également appelé type de paramètre de liaison). Cela est utilisé lorsque le service retourne une ressource afin d’inclure des informations sur les actions qui peuvent être appelées par rapport à cette ressource. Cette méthode ne doit retourner que les actions qui lient au type exact de paramètre de liaison (aucun type dérivé). Cette méthode est appelée une fois par demande par type rencontré et le résultat est mis en cache par les services de données WCF.

#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction
 Cette méthode recherche un [ServiceAction](/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) spécifié et retourne `true` si le [ServiceAction](/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) est trouvé. S’il est trouvé, [ServiceAction](/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) est retourné dans le `serviceAction` `out` paramètre.

### <a name="idataserviceinvokable"></a>IDataServiceInvokable
 Cette interface offre un moyen d'exécuter une action de service de données WCF. Lorsque vous implémentez IDataServiceInvokable, vous êtes chargé de trois opérations :

1. capture et marshaling potentiel des paramètres ;

2. distribution des paramètres dans le code qui implémente réellement l'action lorsque la méthode Invoke() est appelée ;

3. stockage des résultats de la méthode Invoke() de façon à ce qu'ils puissent être récupérés en utilisant la méthode GetResult().

 Les paramètres peuvent être passés en tant que jetons. En effet, il est possible d’écrire un fournisseur de services de données qui fonctionne avec des jetons qui représentent des ressources ; le cas échéant, vous devrez peut-être convertir (marshaler) ces jetons en ressources réelles avant de les distribuer à l’action réelle. Une fois le paramètre marshalé, il doit être dans un état modifiable afin que toutes les modifications apportées à la ressource lorsque l’action est appelée soient enregistrées et écrites sur le disque.

 Cette interface nécessite deux méthodes : Invoke et GetResult. Invoke appelle le délégué qui implémente le comportement de l'action et GetResult retourne le résultat de l'action.

## <a name="invoking-a-wcf-data-service-action"></a>Appel d'une action de service de données WCF
 Les actions sont appelées en utilisant une requête POST HTTP. L'URL spécifie la ressource suivie par le nom de l'action. Les paramètres sont passés dans le corps de la requête. Par exemple, s'il existe un service appelé MovieService qui expose une action appelée Rate. Vous pouvez utiliser l'URL suivante pour appeler l'action Rate sur un film spécifique :

 `http://MovieServer/MovieService.svc/Movies(1)/Rate`

 Movies(1) indique le film que vous voulez évaluer et Rate indique l'action d'évaluation. La valeur réelle de l'évaluation sera dans la corps de la requête HTTP tel que l'illustre cet exemple :

```http
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1
Content-Type: application/json
Content-Length: 20
Host: localhost:15238
{
   "rating": 4
}
```

> [!WARNING]
> L'exemple de code ci-dessus ne fonctionnera qu'avec les services de données WCF version 5.2 et version ultérieure qui prennent en charge le format JSON léger. Si vous utilisez une version antérieure des services de données WCF, vous devez spécifier le type de contenu détaillé JSON comme suit : `application/json;odata=verbose`.

 Vous pouvez aussi appeler une action en utilisant le client des services de données WCF comme indiqué dans l'extrait de code suivant :

```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));
//...
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```

 Dans l'extrait de code ci-dessus, la classe `MoviesModel` a été générée en utilisant Visual Studio pour ajouter une référence de service à un service de données WCF.

## <a name="see-also"></a>Voir aussi

- [WCF Data Services 4.5](index.md)
- [Définition des services de données WCF](defining-wcf-data-services.md)
- [Développer et déployer WCF Data Services](developing-and-deploying-wcf-data-services.md)
- [Fournisseurs de services de données personnalisés](custom-data-service-providers-wcf-data-services.md)
