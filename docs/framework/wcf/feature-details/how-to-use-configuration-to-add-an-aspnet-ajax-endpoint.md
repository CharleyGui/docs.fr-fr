---
title: 'Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184834"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET
Windows Communication Foundation (WCF) vous permet de créer un service qui rend disponible un ASP.NET point de terminaison COMPATIBLE AJAX qui peut être appelé à partir de JavaScript sur un site Web client. Pour créer un tel point de terminaison, vous pouvez soit utiliser un fichier de configuration, comme avec tous les autres paramètres de la Windows Communication Foundation (WCF), soit utiliser une méthode qui ne nécessite aucun élément de configuration. Cette rubrique décrit l'approche utilisant le fichier de configuration.  
  
 La partie de la procédure qui permet au point de terminaison de service de <xref:System.ServiceModel.WebHttpBinding> devenir ASP.NET COMPATIBLE AJAX consiste à configurer le point de terminaison pour utiliser le et à ajouter le [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportement de point de terminaison enableWebScript>. Après avoir configuré le point de terminaison, les étapes pour implémenter et héberger le service sont similaires à celles utilisées par n’importe quel service WCF. Pour un exemple de travail, voir le [service AJAX à l’aide de HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Pour plus d’informations sur la façon de configurer un ASP.NET point de terminaison AJAX sans utiliser la configuration, voir [Comment : Ajouter un point de terminaison AJAX ASP.NET sans utiliser la configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Pour créer un service WCF de base  
  
1. Définissez un contrat de service WCF <xref:System.ServiceModel.ServiceContractAttribute> de base avec une interface marquée avec l’attribut. Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>. Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. Implémentez le contrat de service `ICalculator` avec un `CalculatorService`.  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Pour créer un point de terminaison ASP.NET AJAX pour le service  
  
1. Créez une configuration de [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportement et spécifiez le comportement de>de l’activation de l’activation pour ASP.NET des paramètres compatibles AJAX du service.  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. Créez un point de terminaison pour le service qui utilise <xref:System.ServiceModel.WebHttpBinding> et le comportement ASP.NET AJAX défini dans l'étape précédente.  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a>Pour héberger le service dans IIS  
  
1. Pour héberger le service dans IIS, créez un nouveau fichier nommé "Service" avec une extension .svc dans l’application. Modifier ce fichier en ajoutant les informations de directive [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service. Le contenu du fichier Service pour l'exemple `CalculatorService` contient les informations suivantes :  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Pour plus d’informations sur l’hébergement dans l’IIS, voir [Comment: Organiser un service WCF dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Pour appeler le service  
  
1. Le point de terminaison est configuré à une adresse vide par rapport au fichier .svc, de\<sorte que le service est maintenant disponible et `Add` peut être invoqué en envoyant des demandes à service.svc/ opération> - par exemple, service.svc/Add pour l’opération. Vous pouvez l’utiliser en entrant le point l’URL du point de terminaison dans la collection Scripts du contrôle Script Manager ASP.NET AJAX . Par exemple, voir le [service AJAX à l’aide de HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Voir aussi

- [Création de services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
