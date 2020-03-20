---
title: 'Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184752"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET

Windows Communication Foundation (WCF) vous permet de créer un service qui expose un ASP.NET point de terminaison COMPATIBLE AJAX qui peut être appelé à partir de JavaScript sur un site Web client. Les procédures de base pour la construction de ces services sont discutées dans [Comment: Utiliser la configuration pour ajouter un ASP.NET POINT d’end AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) et [comment: Ajouter un ASP.NET point de terminaison AJAX sans utiliser la configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX prend en charge des opérations utilisant les verbes HTTP POST et HTTP GET, avec HTTP POST comme valeur par défaut. Lors de la création d'une opération qui n'a pas d'effets secondaires et qui retourne des données qui changent rarement, voire jamais, utilisez HTTP GET à la place. Les résultats des opérations GET peuvent être mis en cache, ce qui signifie que les conversations multiples vers la même opération peuvent aboutir à une seule demande à votre service. La mise en cache n’est pas effectuée par WCF, mais peut avoir lieu à n’importe quel niveau (dans le navigateur d’un utilisateur, sur un serveur proxy, et d’autres niveaux.) Le cachage est avantageux si vous voulez augmenter les performances du service, mais peut ne pas être acceptable si les données changent fréquemment ou si l’opération effectue une certaine action.  
  
 Par exemple, si vous destinez le service à la gestion de la médiathèque d’un utilisateur, une opération qui recherche les artistes par titre d’album peut utiliser avantageusement GET, mais une opération qui ajoute un album à la collection personnelle de l’utilisateur doit utiliser POST.  
  
 Pour contrôler la durée de vie du cache, utilisez le type <xref:System.ServiceModel.Web.OutgoingWebResponseContext>. Par exemple, lorsque vous concevez un service qui retourne des prévisions météorologiques mises à jour toutes les heures, vous pouvez utiliser GET mais il convient de limiter la durée de mise en cache à une heure ou moins pour éviter que les utilisateurs du service accèdent à des données périmées.  
  
 Lors de l'utilisation de services à partir d'une page ASP.NET AJAX utilisant le contrôle Script Manager ASP.Net AJAX, c'est égal si les opérations utilisent GET ou POST, le mécanisme du gestionnaire de script garantit que le type de demande correct est publié.  
  
 Les opérations HTTP GET utilisent tous les paramètres d'entrée pris en charge par les opérations POST, y compris les types de contrat de données complexes. Toutefois, il est recommandé dans la plupart des cas d'éviter un trop grand nombre de paramètres ou des paramètres trop complexes dans les opérations GET parce que cela réduit l'efficacité de la mise en cache.  
  
 Cette rubrique explique comment sélectionner GET et POST en ajoutant les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> aux opérations pertinentes dans le contrat de service. Les autres étapes (pour implémenter, configurer et héberger le service) qui sont nécessaires pour obtenir le service en cours d’exécution sont similaires à celles utilisées par tout service ASP.NET AJAX dans WCF.  
  
 Une opération marquée avec <xref:System.ServiceModel.Web.WebGetAttribute> utilise toujours une demande GET. Une opération marquée avec <xref:System.ServiceModel.Web.WebInvokeAttribute> ou une opération qu n'est marquée avec aucun des deux attributs, utilise une demande POST. <xref:System.ServiceModel.Web.WebInvokeAttribute> autorise l'utilisation de verbes HTTP autres que GET et POST (tels que PUT et DELETE) à travers la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>. Toutefois, ces verbes ne sont pas pris en charge par ASP.NET AJAX. Si vous projetez d'utiliser le service à partir des pages ASP.NET à l'aide du contrôle Script Manager ASP.Net AJAX, n'utilisez pas la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>.  
  
 Pour un exemple de travail de passage à GET, consultez l’échantillon [de base du service AJAX.](../../../../docs/framework/wcf/samples/basic-ajax-service.md)  
  
 Pour un échantillon qui utilise POST, consultez l’échantillon [AJAX Service à l’aide de l’échantillon HTTP POST.](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Pour créer un service WCF qui répond aux demandes HTTP GET ou HTTP POST
  
1. Définissez un contrat de service WCF <xref:System.ServiceModel.ServiceContractAttribute> de base avec une interface marquée avec l’attribut. Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>. Ajoutez l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> pour stipuler qu'une opération doit répondre aux demandes HTTP GET. Vous pouvez également ajouter l'attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> pour spécifier explicitement HTTP POST ou ne pas spécifier d'attribut, dans ce cas la valeur par défaut est HTTP POST.
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. Implémentez le contrat de service `IMusicService` avec un `MusicService`.
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. Créez un nouveau fichier pour le service avec une extension .svc dans l'application. Modifier ce fichier en ajoutant les informations de directive [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service. Spécifiez que la <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> directive [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) doit être utilisée pour configurer automatiquement un ASP.NET point de terminaison AJAX.  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Pour appeler le service  
  
1. Vous pouvez tester les opérations GET de votre service sans aucun code client, en utilisant le navigateur. Par exemple, si votre service `http://example.com/service.svc` est configuré `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` à l’adresse, puis taper dans la barre d’adresse du navigateur invoque le service et provoque le téléchargement ou l’affichage de la réponse.
  
2. Vous pouvez utiliser les services avec les opérations GET de la même façon que tous les autres services ASP.NET AJAX, en tapant l’URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX. Par exemple, voir le [service AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Voir aussi

- [Création de services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
