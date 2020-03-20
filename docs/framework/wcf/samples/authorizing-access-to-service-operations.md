---
title: Authorizing Access to Service Operations
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183922"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="651ea-102">Authorizing Access to Service Operations</span><span class="sxs-lookup"><span data-stu-id="651ea-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="651ea-103">Cet échantillon montre comment utiliser le <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) pour permettre l’utilisation de l’attribut pour autoriser l’accès aux opérations de service.</span><span class="sxs-lookup"><span data-stu-id="651ea-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="651ea-104">Cet échantillon est basé sur l’échantillon [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="651ea-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="651ea-105">Le service et le client sont configurés à l’aide de la [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="651ea-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="651ea-106">L’attribut `mode` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) de la>de sécurité `Message` a été fixé à et `clientCredentialType` a été fixé à `Windows`.</span><span class="sxs-lookup"><span data-stu-id="651ea-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="651ea-107">L'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliqué à chaque méthode de service et utilisé afin de restreindre l'accès à chaque opération.</span><span class="sxs-lookup"><span data-stu-id="651ea-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="651ea-108">L'appelant doit être un administrateur Windows pour pouvoir accéder à chaque opération.</span><span class="sxs-lookup"><span data-stu-id="651ea-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="651ea-109">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="651ea-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="651ea-110">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="651ea-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="651ea-111">Le fichier de configuration de service utilise le `principalPermissionMode` [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) pour définir l’attribut :</span><span class="sxs-lookup"><span data-stu-id="651ea-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="651ea-112">Affecter au `principalPermissionMode` la valeur `UseWindowsGroups` permet d'utiliser l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> en fonction des noms de groupe Windows.</span><span class="sxs-lookup"><span data-stu-id="651ea-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="651ea-113">L'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliqué à chaque opération, indiquant que l'appelant doit appartenir à un groupe Administrateurs Windows, tel qu'illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="651ea-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="651ea-114">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="651ea-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="651ea-115">Le client parvient à communiquer avec chaque opération s'il s'exécute sous un compte appartenant à un groupe Administrateurs. Dans le cas contraire, l'accès aux opérations lui sera refusé.</span><span class="sxs-lookup"><span data-stu-id="651ea-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="651ea-116">Faites l'expérience de ce genre d'échec en exécutant le client sous un compte n'appartenant pas à un groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="651ea-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="651ea-117">Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="651ea-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="651ea-118">Les services peuvent être informés des échecs d'autorisation en implémentant un <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="651ea-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="651ea-119">Voir [l’extension du contrôle sur le traitement des erreurs et les rapports](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) pour obtenir de l’information sur la mise `IErrorHandler`en œuvre .</span><span class="sxs-lookup"><span data-stu-id="651ea-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="651ea-120">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="651ea-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="651ea-121">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="651ea-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="651ea-122">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="651ea-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="651ea-123">Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="651ea-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
