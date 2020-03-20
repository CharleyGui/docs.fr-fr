---
title: 'Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185137"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration
Windows Communication Foundation (WCF) vous permet de créer un service qui expose un ASP.NET point de terminaison COMPATIBLE AJAX qui peut être appelé à partir de JavaScript sur un site Web client. Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison WCF, ou utiliser une méthode qui ne requiert aucun élément de configuration. Cette rubrique décrit la deuxième approche.  
  
 Pour créer des services avec les points de terminaison ASP.NET AJAX sans configuration, les services doivent être hébergés par les services IIS (Internet Information Services). Pour activer un ASP.NET point de terminaison <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> AJAX à l’aide de cette approche, spécifiez le paramètre Factory dans la [ \@directive ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dans le fichier .svc. Cette fabrication personnalisée est le composant qui configure automatiquement un point de terminaison ASP.NET AJAX afin qu’il puisse être appelé à partir de JavaScript sur un site web client.  
  
 Pour un exemple de travail, voir le [service AJAX Sans configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Pour un aperçu de la façon de configurer un point de terminaison AJAX ASP.NET à l’aide d’éléments de configuration, voir [Comment : Utilisez configuration pour ajouter un point de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Pour créer un service WCF de base  
  
1. Définissez un contrat de service WCF <xref:System.ServiceModel.ServiceContractAttribute> de base avec une interface marquée avec l’attribut. Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>. Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
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
  
    //Other operations omitted…  
    ```  
  
3. Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Pour héberger le service dans les services IIS sans configuration  
  
1. Créez un nouveau fichier pour le service avec une extension .svc dans l'application. Modifier ce fichier en ajoutant les informations de directive [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service. Spécifiez que la <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> directive [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) doit être utilisée pour configurer automatiquement un ASP.NET point de terminaison AJAX.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Générez le service et appelez-le à partir du client. Les services IIS (Internet Information Services) activent le service lorsqu'il est appelé. Pour plus d’informations sur l’hébergement dans l’IIS, voir [Comment: Organiser un service WCF dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Pour appeler le service  
  
1. Le point de terminaison est configuré à une adresse vide par rapport au fichier .svc, de\<sorte que le service est maintenant disponible et `Add` peut être invoqué en envoyant des demandes à service.svc/ opération> - par exemple, service.svc/Add pour l’opération. Vous pouvez l'utiliser en entrant l'URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX. Par exemple, voir le [service AJAX Sans configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a> Exemple  
  
 Le point de terminaison configuré automatiquement est créé au niveau d'une adresse vide qui est fonction de l'URL de base. Un fichier de configuration peut également être ajouté et utilisé avec cette approche. Si le fichier de configuration contient des définitions de point de terminaison, ces points de terminaison sont ajoutés au point de terminaison configuré automatiquement.  
  
 Par exemple, service.svc utilise <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> et le répertoire du service contient un fichier Web.config qui définit un point de terminaison pour le même service en utilisant <xref:System.ServiceModel.BasicHttpBinding> au niveau de l'adresse relative « soap ». Dans ce cas, le service contient deux points de terminaison : un au niveau de service.svc (qui répond aux demandes ASP.NET AJAX) et un autre au niveau de service.svc/soap (qui répond aux demandes SOAP).  
  
 Si le fichier de configuration définit un point de terminaison au niveau d'une adresse relative vide et <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé, une exception est levée et le service ne peut pas démarrer.  
  
 Vous ne pouvez pas utiliser de configuration pour modifier des paramètres sur le point de terminaison configuré automatiquement. Si un paramètre (tel qu'un quota de lecteur) doit être modifié, vous ne devez pas utiliser l'approche sans configuration en supprimant <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dans le fichier .svc et en créant une entrée de configuration pour le point de terminaison.  
  
 Si votre service requiert le mode de compatibilité ASP.NET, par exemple, s'il utilise la classe <xref:System.Web.HttpContext> ou les mécanismes d'autorisation ASP.NET, un fichier de configuration est néanmoins requis pour activer ce mode. L’élément de configuration requis est le [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) élément, qui doit être ajouté comme suit.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Pour plus d’informations, consultez le sujet des services et ASP.NET de [la WCF.](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
  
 La classe <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est dérivée de la classe <xref:System.ServiceModel.Activation.ServiceHostFactory>. Pour une explication détaillée du mécanisme de l’usine d’accueil de service, voir le thème [d’hébergement d’extension utilisant ServiceHostFactory.](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
  
## <a name="see-also"></a>Voir aussi

- [Création de services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
