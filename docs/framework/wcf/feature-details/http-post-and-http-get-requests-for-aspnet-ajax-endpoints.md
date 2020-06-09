---
title: 'Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 15d7ad43ce9120e97aba9119aff6a6c1a19f301f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596914"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET

Windows Communication Foundation (WCF) vous permet de créer un service qui expose un point de terminaison compatible AJAX ASP.NET qui peut être appelé à partir de JavaScript sur un site Web client. Les procédures de base pour la création de ces services sont décrites dans [Comment : utiliser la configuration pour ajouter un point de terminaison ajax ASP.net](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) et [Comment : ajouter un point de terminaison ASP.NET AJAX sans utiliser la configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX prend en charge des opérations utilisant les verbes HTTP POST et HTTP GET, avec HTTP POST comme valeur par défaut. Lors de la création d'une opération qui n'a pas d'effets secondaires et qui retourne des données qui changent rarement, voire jamais, utilisez HTTP GET à la place. Les résultats des opérations GET peuvent être mis en cache, ce qui signifie que les conversations multiples vers la même opération peuvent aboutir à une seule demande à votre service. La mise en cache n’est pas effectuée par WCF, mais peut avoir lieu à n’importe quel niveau (dans le navigateur d’un utilisateur, sur un serveur proxy et d’autres niveaux). La mise en cache est avantageuse si vous souhaitez augmenter les performances du service, mais peut ne pas être acceptable si les données changent fréquemment ou si l’opération effectue une action.  
  
 Par exemple, si vous destinez le service à la gestion de la médiathèque d’un utilisateur, une opération qui recherche les artistes par titre d’album peut utiliser avantageusement GET, mais une opération qui ajoute un album à la collection personnelle de l’utilisateur doit utiliser POST.  
  
 Pour contrôler la durée de vie du cache, utilisez le type <xref:System.ServiceModel.Web.OutgoingWebResponseContext>. Par exemple, lorsque vous concevez un service qui retourne des prévisions météorologiques mises à jour toutes les heures, vous pouvez utiliser GET mais il convient de limiter la durée de mise en cache à une heure ou moins pour éviter que les utilisateurs du service accèdent à des données périmées.  
  
 Lors de l'utilisation de services à partir d'une page ASP.NET AJAX utilisant le contrôle Script Manager ASP.Net AJAX, c'est égal si les opérations utilisent GET ou POST, le mécanisme du gestionnaire de script garantit que le type de demande correct est publié.  
  
 Les opérations HTTP GET utilisent tous les paramètres d'entrée pris en charge par les opérations POST, y compris les types de contrat de données complexes. Toutefois, il est recommandé dans la plupart des cas d'éviter un trop grand nombre de paramètres ou des paramètres trop complexes dans les opérations GET parce que cela réduit l'efficacité de la mise en cache.  
  
 Cette rubrique explique comment sélectionner GET et POST en ajoutant les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> aux opérations pertinentes dans le contrat de service. Les autres étapes (pour implémenter, configurer et héberger le service) requises pour l’exécution du service sont similaires à celles utilisées par tout service ASP.NET AJAX dans WCF.  
  
 Une opération marquée avec <xref:System.ServiceModel.Web.WebGetAttribute> utilise toujours une demande GET. Une opération marquée avec <xref:System.ServiceModel.Web.WebInvokeAttribute> ou une opération qu n'est marquée avec aucun des deux attributs, utilise une demande POST. <xref:System.ServiceModel.Web.WebInvokeAttribute> autorise l'utilisation de verbes HTTP autres que GET et POST (tels que PUT et DELETE) à travers la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>. Toutefois, ces verbes ne sont pas pris en charge par ASP.NET AJAX. Si vous projetez d'utiliser le service à partir des pages ASP.NET à l'aide du contrôle Script Manager ASP.Net AJAX, n'utilisez pas la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A>.  
  
 Pour obtenir un exemple fonctionnel de basculement vers, consultez l’exemple [Basic AJAX Service](../samples/basic-ajax-service.md) .  
  
 Pour obtenir un exemple qui utilise la publication, consultez l’exemple [service Ajax à l’aide du protocole http](../samples/ajax-service-using-http-post.md) .  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Pour créer un service WCF qui répond aux demandes HTTP GET ou HTTP POST
  
1. Définissez un contrat de service WCF de base avec une interface marquée avec l' <xref:System.ServiceModel.ServiceContractAttribute> attribut. Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>. Ajoutez l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> pour stipuler qu'une opération doit répondre aux demandes HTTP GET. Vous pouvez également ajouter l'attribut <xref:System.ServiceModel.Web.WebInvokeAttribute> pour spécifier explicitement HTTP POST ou ne pas spécifier d'attribut, dans ce cas la valeur par défaut est HTTP POST.
  
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
  
3. Créez un nouveau fichier pour le service avec une extension .svc dans l'application. Modifiez ce fichier en ajoutant les informations de directive [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service. Spécifiez que <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> doit être utilisé dans la directive [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) pour configurer automatiquement un point de terminaison ASP.NET AJAX.  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Pour appeler le service  
  
1. Vous pouvez tester les opérations GET de votre service sans aucun code client, en utilisant le navigateur. Par exemple, si votre service est configuré à l' `http://example.com/service.svc` adresse, la saisie `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` dans la barre d’adresse du navigateur appelle le service et provoque le téléchargement ou l’affichage de la réponse.
  
2. Vous pouvez utiliser les services avec les opérations GET de la même façon que tous les autres services ASP.NET AJAX, en tapant l’URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX. Pour obtenir un exemple, consultez le [service Ajax de base](../samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Voir aussi

- [Création de services WCF pour ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md)
- [Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
