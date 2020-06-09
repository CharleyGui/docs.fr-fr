---
title: Unwrapped Messages
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: ea90a6355f63d5fffd0cc3c5d350f83e395c31c5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591083"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="daac1-102">Unwrapped Messages</span><span class="sxs-lookup"><span data-stu-id="daac1-102">Unwrapped Messages</span></span>
<span data-ttu-id="daac1-103">Cet exemple montre des messages non encapsulés.</span><span class="sxs-lookup"><span data-stu-id="daac1-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="daac1-104">Par défaut, le corps du message est mis en forme de manière à ce que les paramètres d'une opération de service soient encapsulés.</span><span class="sxs-lookup"><span data-stu-id="daac1-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="daac1-105">L'exemple suivant montre un message de demande `Add` au service `ICalculator` en mode encapsulé.</span><span class="sxs-lookup"><span data-stu-id="daac1-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="daac1-106">L'élément `<Add>` dans le corps du message encapsule les paramètres `n1` et `n2`.</span><span class="sxs-lookup"><span data-stu-id="daac1-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="daac1-107">Par opposition, l'exemple suivant montre le message équivalent en mode non encapsulé.</span><span class="sxs-lookup"><span data-stu-id="daac1-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
```  
  
 <span data-ttu-id="daac1-108">Le message non encapsulé n'encapsule pas les paramètres `n1` et `n2` dans un élément contenant, ils sont des enfants directs de l'élément de corps SOAP.</span><span class="sxs-lookup"><span data-stu-id="daac1-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daac1-109">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="daac1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="daac1-110">Dans cet exemple, un message non encapsulé est créé en appliquant l'<xref:System.ServiceModel.MessageContractAttribute> au type de paramètre de l'opération de service et au type de valeur de retour comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="daac1-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="daac1-111">Pour vous permettre de voir les messages qui sont envoyés et reçus, cet exemple utilise le suivi.</span><span class="sxs-lookup"><span data-stu-id="daac1-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="daac1-112">De plus, la <xref:System.ServiceModel.WSHttpBinding> a été configurée sans sécurité, pour réduire le nombre de messages qu'elle enregistre.</span><span class="sxs-lookup"><span data-stu-id="daac1-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="daac1-113">Le journal des traces obtenu (c:\logs\Message.log) peut être affiché à l’aide de l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="daac1-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="daac1-114">Pour afficher le contenu d’un message, sélectionnez **messages** dans les volets de gauche et de droite de l’outil Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="daac1-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="daac1-115">Les journaux de suivi dans cet exemple sont configurés pour être générés dans le dossier C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="daac1-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="daac1-116">Créez ce dossier avant d'exécuter l'exemple et accordez à l'utilisateur l'accès en écriture au service réseau pour ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="daac1-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="daac1-117">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="daac1-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="daac1-118">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="daac1-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="daac1-119">Créez un répertoire C:\LOGS pour l'enregistrement des messages.</span><span class="sxs-lookup"><span data-stu-id="daac1-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="daac1-120">Accordez à l'utilisateur des droits d'accès en écriture au service réseau pour ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="daac1-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="daac1-121">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="daac1-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="daac1-122">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="daac1-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="daac1-123">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="daac1-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="daac1-124">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="daac1-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="daac1-125">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="daac1-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="daac1-126">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="daac1-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
