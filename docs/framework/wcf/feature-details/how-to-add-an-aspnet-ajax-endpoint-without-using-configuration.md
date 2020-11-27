---
title: 'Procédure : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: e33f1fed7dd7bf45966815949ac544250f4d1de8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257624"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Procédure : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration

Windows Communication Foundation (WCF) vous permet de créer un service qui expose un point de terminaison compatible AJAX ASP.NET qui peut être appelé à partir de JavaScript sur un site Web client. Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison WCF, ou utiliser une méthode qui ne requiert aucun élément de configuration. Cette rubrique décrit la deuxième approche.  
  
 Pour créer des services avec les points de terminaison ASP.NET AJAX sans configuration, les services doivent être hébergés par les services IIS (Internet Information Services). Pour activer un point de terminaison AJAX ASP.NET à l’aide de cette approche, spécifiez <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> comme paramètre de fabrique dans la directive [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) du fichier. svc. Cette fabrication personnalisée est le composant qui configure automatiquement un point de terminaison ASP.NET AJAX afin qu’il puisse être appelé à partir de JavaScript sur un site web client.  
  
 Pour obtenir un exemple fonctionnel, consultez le [service Ajax sans configuration](../samples/ajax-service-without-configuration.md).  
  
 Pour obtenir un aperçu de la configuration d’un point de terminaison AJAX ASP.NET à l’aide d’éléments de configuration, consultez [Comment : utiliser la configuration pour ajouter un point de terminaison ASP.NET AJAX](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Pour créer un service WCF de base  
  
1. Définissez un contrat de service WCF de base avec une interface marquée avec l' <xref:System.ServiceModel.ServiceContractAttribute> attribut. Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>. Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
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
  
1. Créez un nouveau fichier pour le service avec une extension .svc dans l'application. Modifiez ce fichier en ajoutant les informations de directive [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service. Spécifiez que <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> doit être utilisé dans la directive [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) pour configurer automatiquement un point de terminaison ASP.NET AJAX.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Générez le service et appelez-le à partir du client. Les services IIS (Internet Information Services) activent le service lorsqu'il est appelé. Pour plus d’informations sur l’hébergement dans IIS, consultez [Comment : héberger un service WCF dans IIS](how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Pour appeler le service  
  
1. Le point de terminaison est configuré à une adresse vide relative au fichier. svc. par conséquent, le service est maintenant disponible et peut être appelé en envoyant des demandes à service. svc/ \<operation> -par exemple, service. svc/Add pour l' `Add` opération. Vous pouvez l'utiliser en entrant l'URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX. Pour obtenir un exemple, consultez le [service Ajax sans configuration](../samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a> Exemple  
  
 Le point de terminaison configuré automatiquement est créé au niveau d'une adresse vide qui est fonction de l'URL de base. Un fichier de configuration peut également être ajouté et utilisé avec cette approche. Si le fichier de configuration contient des définitions de point de terminaison, ces points de terminaison sont ajoutés au point de terminaison configuré automatiquement.  
  
 Par exemple, service.svc utilise <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> et le répertoire du service contient un fichier Web.config qui définit un point de terminaison pour le même service en utilisant <xref:System.ServiceModel.BasicHttpBinding> au niveau de l'adresse relative « soap ». Dans ce cas, le service contient deux points de terminaison : un au niveau de service.svc (qui répond aux demandes ASP.NET AJAX) et un autre au niveau de service.svc/soap (qui répond aux demandes SOAP).  
  
 Si le fichier de configuration définit un point de terminaison au niveau d'une adresse relative vide et <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé, une exception est levée et le service ne peut pas démarrer.  
  
 Vous ne pouvez pas utiliser de configuration pour modifier des paramètres sur le point de terminaison configuré automatiquement. Si un paramètre (tel qu'un quota de lecteur) doit être modifié, vous ne devez pas utiliser l'approche sans configuration en supprimant <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dans le fichier .svc et en créant une entrée de configuration pour le point de terminaison.  
  
 Si votre service requiert le mode de compatibilité ASP.NET, par exemple, s'il utilise la classe <xref:System.Web.HttpContext> ou les mécanismes d'autorisation ASP.NET, un fichier de configuration est néanmoins requis pour activer ce mode. L’élément de configuration requis est l' [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) élément, qui doit être ajouté comme suit.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Pour plus d’informations, consultez la rubrique [services WCF et ASP.net](wcf-services-and-aspnet.md) .  
  
 La classe <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est dérivée de la classe <xref:System.ServiceModel.Activation.ServiceHostFactory>. Pour obtenir une explication détaillée du mécanisme de fabrique d’hôte de service, consultez la rubrique extension de l' [Hébergement à l’aide de ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md) .  
  
## <a name="see-also"></a>Voir aussi

- [Création de services WCF pour ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md)
- [Procédure : migrer des services web ASP.NET compatibles AJAX vers WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
