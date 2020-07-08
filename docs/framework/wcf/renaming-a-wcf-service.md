---
title: Attribution d'un nouveau nom à un service WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052050"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="728c3-102">Attribution d'un nouveau nom à un service WCF</span><span class="sxs-lookup"><span data-stu-id="728c3-102">Renaming a WCF Service</span></span>
<span data-ttu-id="728c3-103">Cette rubrique décrit comment vous pouvez renommer un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="728c3-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="728c3-104">Attribution d'un nouveau nom à un service WCF</span><span class="sxs-lookup"><span data-stu-id="728c3-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="728c3-105">Pour renommer un service dans un modèle Windows Communication Foundation (WCF), procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="728c3-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="728c3-106">Modifiez le nom de la classe qui implémente le service.</span><span class="sxs-lookup"><span data-stu-id="728c3-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="728c3-107">Dans le fichier de configuration du service, remplacez le nom du service par celui que vous avez choisi, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="728c3-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="728c3-108">Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.</span><span class="sxs-lookup"><span data-stu-id="728c3-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="728c3-109">Si votre service est hébergé sur un serveur, il utilise un fichier \* \* . svc\* .</span><span class="sxs-lookup"><span data-stu-id="728c3-109">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="728c3-110">Ouvrez le fichier svc et modifiez le nom de votre service comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="728c3-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="728c3-111">Cette étape n'est pas nécessaire pour les applications auto-hébergées, puisqu'il n'y a pas de fichier svc.</span><span class="sxs-lookup"><span data-stu-id="728c3-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="728c3-112">Attribution d'un nouveau nom à un contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="728c3-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="728c3-113">Effectuez les étapes suivantes pour renommer le contrat de service</span><span class="sxs-lookup"><span data-stu-id="728c3-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="728c3-114">Modifiez le nom du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="728c3-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="728c3-115">Dans le fichier de configuration du service, remplacez le nom du contrat de service par le celui que vous avez choisi, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="728c3-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="728c3-116">Selon votre modèle d'hébergement, le fichier de configuration sera app.config ou web.config.</span><span class="sxs-lookup"><span data-stu-id="728c3-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
