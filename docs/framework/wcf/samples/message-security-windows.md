---
title: Message Security Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 7b5b9ba0cc9a6d867b0478720b6151c7a561da16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584712"
---
# <a name="message-security-windows"></a>Message Security Windows
Cet exemple illustre comment configurer une liaison <xref:System.ServiceModel.WSHttpBinding> pour permettre l'utilisation de la sécurité de niveau message avec authentification Windows. Cet exemple est basé sur le [prise en main](getting-started-sample.md). Dans cet exemple, le service est hébergé dans les services IIS (Internet Information Services) et le client est une application console (.exe).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La sécurité par défaut pour le [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) est la sécurité de message utilisant l’authentification Windows. Les fichiers de configuration de cet exemple attribuent explicitement à l' `mode` attribut de la valeur [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Message` et à l’attribut la valeur `clientCredentialType` `Windows` . Ces valeurs correspondent aux valeurs par défaut de cette liaison. Cependant, elles ont été configurées de manière explicite, ainsi qu'en témoigne l'exemple de configuration suivant, afin d'illustrer leur utilisation.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 La configuration du point de terminaison du client se compose d’une adresse absolue pour le point de terminaison du service, de la liaison et du contrat. La liaison du client est configurée avec le `securityMode` et le `authenticationMode` appropriés.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"
            binding="wsHttpBinding"
            bindingConfiguration="Binding1"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Le code source du service a été modifié afin d'illustrer comment le <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> peut être utilisé afin d'accéder à l'identité de l'appelant.  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. La première méthode appelée, `GetCallerIdentity`, retourne le nom de l'identité de l'appelant au client. Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
