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
# <a name="message-security-windows"></a><span data-ttu-id="f5e19-102">Message Security Windows</span><span class="sxs-lookup"><span data-stu-id="f5e19-102">Message Security Windows</span></span>
<span data-ttu-id="f5e19-103">Cet exemple illustre comment configurer une liaison <xref:System.ServiceModel.WSHttpBinding> pour permettre l'utilisation de la sécurité de niveau message avec authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f5e19-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="f5e19-104">Cet exemple est basé sur le [prise en main](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f5e19-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="f5e19-105">Dans cet exemple, le service est hébergé dans les services IIS (Internet Information Services) et le client est une application console (.exe).</span><span class="sxs-lookup"><span data-stu-id="f5e19-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5e19-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f5e19-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f5e19-107">La sécurité par défaut pour le [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) est la sécurité de message utilisant l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="f5e19-107">The default security for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="f5e19-108">Les fichiers de configuration de cet exemple attribuent explicitement à l' `mode` attribut de la valeur [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `Message` et à l’attribut la valeur `clientCredentialType` `Windows` .</span><span class="sxs-lookup"><span data-stu-id="f5e19-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="f5e19-109">Ces valeurs correspondent aux valeurs par défaut de cette liaison. Cependant, elles ont été configurées de manière explicite, ainsi qu'en témoigne l'exemple de configuration suivant, afin d'illustrer leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="f5e19-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="f5e19-110">La configuration du point de terminaison du client se compose d’une adresse absolue pour le point de terminaison du service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="f5e19-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="f5e19-111">La liaison du client est configurée avec le `securityMode` et le `authenticationMode` appropriés.</span><span class="sxs-lookup"><span data-stu-id="f5e19-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
  
 <span data-ttu-id="f5e19-112">Le code source du service a été modifié afin d'illustrer comment le <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> peut être utilisé afin d'accéder à l'identité de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="f5e19-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="f5e19-113">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="f5e19-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f5e19-114">La première méthode appelée, `GetCallerIdentity`, retourne le nom de l'identité de l'appelant au client.</span><span class="sxs-lookup"><span data-stu-id="f5e19-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="f5e19-115">Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="f5e19-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5e19-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f5e19-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f5e19-117">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5e19-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f5e19-118">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5e19-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f5e19-119">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5e19-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
