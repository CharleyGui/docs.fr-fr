---
title: Dépannage de la corrélation
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: a5942c13bb4026cfeb8f664c60fb658373ffcca5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596706"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="39825-102">Dépannage de la corrélation</span><span class="sxs-lookup"><span data-stu-id="39825-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="39825-103">La corrélation est utilisée pour établir une relation entre des messages de service de workflow et avec l'instance de workflow appropriée, mais si elle n'est pas proprement configurée, les messages ne seront pas reçus et les applications ne fonctionneront pas correctement.</span><span class="sxs-lookup"><span data-stu-id="39825-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="39825-104">Cette rubrique fournit une vue d'ensemble de plusieurs méthodes de résolution des problèmes de corrélation et présente certains problèmes courants qui peuvent se produire lorsque vous utilisez la corrélation.</span><span class="sxs-lookup"><span data-stu-id="39825-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="39825-105">Gérer l'événement UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="39825-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="39825-106">L'événement <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> se produit lorsqu'un message inconnu est reçu par un service, notamment les messages qui ne peuvent pas être mis en corrélation avec une instance existante.</span><span class="sxs-lookup"><span data-stu-id="39825-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="39825-107">Pour les services auto-hébergés, cet événement peut être géré dans l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="39825-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="39825-108">Pour les services hébergés sur le Web, cet événement peut être géré en dérivant une classe de <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> et en substituant <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="39825-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 <span data-ttu-id="39825-109">Ce <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> personnalisé peut ensuite être spécifié dans le fichier `svc` du service.</span><span class="sxs-lookup"><span data-stu-id="39825-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 <span data-ttu-id="39825-110">Lorsque ce gestionnaire est appelé, le message peut être récupéré à l'aide de la propriété <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> du <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> et ressemblera au message suivant.</span><span class="sxs-lookup"><span data-stu-id="39825-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="39825-111">L'inspection des messages distribués au gestionnaire <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> peut fournir des indices permettant de comprendre pourquoi le message n'a pas été mis en corrélation avec une instance du service de workflow.</span><span class="sxs-lookup"><span data-stu-id="39825-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="39825-112">Utiliser le suivi pour surveiller la progression du workflow</span><span class="sxs-lookup"><span data-stu-id="39825-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="39825-113">Le suivi offre un moyen de surveiller la progression d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="39825-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="39825-114">Par défaut, des enregistrements de suivi sont émis pour les événements de cycle de vie du workflow, les événements de cycle de vie de l'activité, la propagation d'erreur et la reprise de signet.</span><span class="sxs-lookup"><span data-stu-id="39825-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="39825-115">En outre, des enregistrements de suivi personnalisés peuvent être émis par des activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="39825-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="39825-116">Lorsqu'il s'agit de résoudre les problèmes de corrélation, les enregistrements de suivi d'activité, de reprise de signet et de propagation d'erreur sont les plus utiles.</span><span class="sxs-lookup"><span data-stu-id="39825-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="39825-117">Les enregistrements de suivi d'activité peuvent être utilisés pour déterminer la progression actuelle du workflow et contribuent à identifier l'activité de messagerie qui attend actuellement des messages.</span><span class="sxs-lookup"><span data-stu-id="39825-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="39825-118">Les enregistrements de reprise de signet sont utiles parce qu'ils indiquent qu'un message a été reçu par le workflow, et les enregistrements de propagation d'erreur fournissent un enregistrement de toutes les erreurs présentes dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="39825-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="39825-119">Pour activer le suivi, spécifiez le <xref:System.Activities.Tracking.TrackingParticipant> voulu dans le <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> du <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="39825-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="39825-120">Dans l’exemple suivant, le `ConsoleTrackingParticipant` (de l’exemple de [suivi personnalisé](../../windows-workflow-foundation/samples/custom-tracking.md) ) est configuré à l’aide du profil de suivi par défaut.</span><span class="sxs-lookup"><span data-stu-id="39825-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="39825-121">Un participant de suivi tel que ConsoleTrackingParticipant est utile pour les services de workflow auto-hébergés qui ont une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="39825-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="39825-122">Pour un service hébergé sur le Web, un participant de suivi qui enregistre les informations de suivi dans un magasin fiable doit être utilisé, tel que le <xref:System.Activities.Tracking.EtwTrackingParticipant> participant intégré ou un participant de suivi personnalisé qui enregistre les informations dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="39825-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="39825-123">Pour plus d’informations sur le suivi et la configuration du suivi pour un service de flux de travail hébergé sur le Web, consultez [suivi et traçage de workflow](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [configuration du suivi d’un workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)et [exemples de suivi &#91;WF&#93;](../../windows-workflow-foundation/samples/tracking.md) exemples.</span><span class="sxs-lookup"><span data-stu-id="39825-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="39825-124">Utiliser le suivi WCF</span><span class="sxs-lookup"><span data-stu-id="39825-124">Use WCF Tracing</span></span>
 <span data-ttu-id="39825-125">Le suivi WCF fournit un suivi du flux de messages à destination et en provenance d'un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="39825-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="39825-126">Ces informations de suivi sont utiles dans la résolution des problèmes de corrélation, en particulier lorsqu'il s'agit de corrélation basée sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="39825-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="39825-127">Pour activer le suivi, spécifiez les écouteurs de suivi voulus dans la section `system.diagnostics` du fichier `web.config` si le service de workflow est hébergé sur le Web ou du fichier `app.config` si le service de workflow est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="39825-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="39825-128">Pour inclure le contenu des messages dans le fichier de trace, spécifiez `true` pour `logEntireMessage` dans l'élément `messageLogging` de la section `diagnostics` de `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="39825-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="39825-129">Dans l'exemple suivant, les informations de suivi, notamment le contenu des messages, sont configurées pour être écrites dans un fichier nommé `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="39825-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="39825-130">Pour afficher les informations de suivi contenues dans `service.svclog` , l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="39825-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="39825-131">Celui-ci est particulièrement utile pour résoudre les problèmes de corrélation basée sur le contenu, car vous pouvez consulter le contenu des messages, voir exactement ce qui est passé, et si cela correspond au <xref:System.ServiceModel.CorrelationQuery> de la corrélation basée sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="39825-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="39825-132">Pour plus d’informations sur le suivi WCF, consultez [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [configuration du suivi](../diagnostics/tracing/configuring-tracing.md)et [utilisation du suivi pour résoudre les problèmes de votre application](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="39825-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="39825-133">Problèmes courants rencontrés avec la corrélation basée sur l'échange de contextes</span><span class="sxs-lookup"><span data-stu-id="39825-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="39825-134">Certains types de corrélation requièrent pour fonctionner correctement l’utilisation d’un type spécifique de liaison.</span><span class="sxs-lookup"><span data-stu-id="39825-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="39825-135">C'est par exemple le cas de la corrélation demande-réponse, qui requiert une liaison bidirectionnelle telle que <xref:System.ServiceModel.BasicHttpBinding> et de la corrélation basée sur l'échange de contextes, qui requiert une liaison basée sur le contexte, telle que <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="39825-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="39825-136">La plupart des liaisons prennent en charge des opérations bidirectionnelles, aussi cela ne constitue-t-il pas un problème courant pour la corrélation demande-réponse, mais il n’existe qu’une poignée de liaisons basées sur le contexte, notamment <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> et <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="39825-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="39825-137">Si l’une de ces liaisons n’est pas utilisée, l’appel initial à un service de workflow réussira, mais les appels suivants échoueront avec le <xref:System.ServiceModel.FaultException> suivant :</span><span class="sxs-lookup"><span data-stu-id="39825-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="39825-138">Les informations de contexte utilisées pour la corrélation de contexte peuvent être retournées par le <xref:System.ServiceModel.Activities.SendReply> à l'activité <xref:System.ServiceModel.Activities.Receive> qui initialise la corrélation de contexte lors de l'utilisation d'une opération bidirectionnelle, ou elles peuvent être spécifiées par l'appelant si l'opération est unidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="39825-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="39825-139">Si le contexte n'est pas envoyé par l'appelant ou retourné par le service de workflow, le <xref:System.ServiceModel.FaultException> décrit précédemment sera retourné lorsqu'une opération suivante sera appelée.</span><span class="sxs-lookup"><span data-stu-id="39825-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="39825-140">Problèmes courants rencontrés avec la corrélation demande-réponse</span><span class="sxs-lookup"><span data-stu-id="39825-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="39825-141">La corrélation demande-réponse est utilisée avec une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire pour implémenter une opération bidirectionnelle dans un service de workflow et avec une <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire qui appelle une opération bidirectionnelle dans un autre service Web.</span><span class="sxs-lookup"><span data-stu-id="39825-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="39825-142">Lors de l’appel d’une opération bidirectionnelle dans un service WCF, le service peut être soit un service WCF basé sur du code impératif traditionnel, soit un service de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="39825-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="39825-143">Pour utiliser la corrélation demande-réponse, une liaison bidirectionnelle doit être utilisée, telle que <xref:System.ServiceModel.BasicHttpBinding>, et les opérations doivent être bidirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="39825-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="39825-144">Si le service de workflow a des opérations bidirectionnelles en parallèle, ou se chevauchent <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> , la gestion de handle de corrélation implicite fournie par <xref:System.ServiceModel.Activities.WorkflowServiceHost> peut ne pas suffire, en particulier dans les scénarios à forte contrainte, et les messages peuvent ne pas être correctement routés.</span><span class="sxs-lookup"><span data-stu-id="39825-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="39825-145">Pour éviter la survenue de ce problème, nous vous recommandons de toujours spécifier explicitement un <xref:System.ServiceModel.Activities.CorrelationHandle> lors de l'utilisation de la corrélation demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="39825-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="39825-146">Lorsque vous utilisez les modèles **SendAndReceiveReply** et **ReceiveAndSendReply** à partir de la section messagerie de la **boîte à outils** du concepteur de flux de travail, un <xref:System.ServiceModel.Activities.CorrelationHandle> est explicitement configuré par défaut.</span><span class="sxs-lookup"><span data-stu-id="39825-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="39825-147">Lors de la génération d'un workflow à l'aide de code, le <xref:System.ServiceModel.Activities.CorrelationHandle> est spécifié dans le <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> de la première activité de la paire.</span><span class="sxs-lookup"><span data-stu-id="39825-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="39825-148">Dans l'exemple suivant, une activité <xref:System.ServiceModel.Activities.Receive> est configurée avec un <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> explicite spécifié dans le <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="39825-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 <span data-ttu-id="39825-149">La persistance n’est pas autorisée entre une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire ou une <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire.</span><span class="sxs-lookup"><span data-stu-id="39825-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="39825-150">Une zone de non-persistance valide tant que les deux activités ne sont pas terminées, est créée.</span><span class="sxs-lookup"><span data-stu-id="39825-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="39825-151">Si une activité, telle qu'une activité de délai, se trouve dans cette zone de non-persistance et cause une inactivité du workflow, ce dernier ne sera pas rendu persistant même si l'hôte est configuré pour rendre persistants les workflows lorsqu'ils deviennent inactifs.</span><span class="sxs-lookup"><span data-stu-id="39825-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="39825-152">Si une activité, telle qu'une activité persistante, tente de persister de façon explicite dans la zone de non-persistance, une exception irrécupérable est levée, le workflow est abandonné et un <xref:System.ServiceModel.FaultException> est retourné à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="39825-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="39825-153">Le message d'exception irrécupérable est « System.InvalidOperationException : Les activités Persist ne peuvent pas être contenues au sein de blocs sans persistance ».</span><span class="sxs-lookup"><span data-stu-id="39825-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="39825-154">Cette exception n'est pas retournée à l'appelant mais peut-être observée si le suivi est activé.</span><span class="sxs-lookup"><span data-stu-id="39825-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="39825-155">Le message du <xref:System.ServiceModel.FaultException> retourné à l'appelant est « Impossible d'effectuer l'opération car WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' a terminé ».</span><span class="sxs-lookup"><span data-stu-id="39825-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="39825-156">Pour plus d’informations sur la corrélation demande-réponse, consultez [demande-réponse](request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="39825-156">For more information about request-reply correlation, see [Request-Reply](request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="39825-157">Problèmes courants rencontrés avec la corrélation basée sur le contenu</span><span class="sxs-lookup"><span data-stu-id="39825-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="39825-158">La corrélation basée sur le contenu est utilisée lorsqu'un service de workflow reçoit plusieurs messages et dispose de quelques données dans les messages échangés qui identifient l'instance souhaitée.</span><span class="sxs-lookup"><span data-stu-id="39825-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="39825-159">La corrélation basée sur le contenu utilise ces données dans les messages, par exemple un numéro de client ou un ID de commande, pour router les messages vers l'instance de workflow appropriée.</span><span class="sxs-lookup"><span data-stu-id="39825-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="39825-160">Cette section décrit plusieurs problèmes courants qui peuvent se produire lors de l'utilisation de la corrélation basée sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="39825-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="39825-161">Unicité des données d'identification</span><span class="sxs-lookup"><span data-stu-id="39825-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="39825-162">Les données utilisées pour identifier l'instance sont hachées en une clé de corrélation.</span><span class="sxs-lookup"><span data-stu-id="39825-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="39825-163">Il est important de s'assurer que les données utilisées pour la corrélation sont uniques, pour éviter que des conflits se produisent dans la clé hachée, entraînant des confusions dans le routage des messages.</span><span class="sxs-lookup"><span data-stu-id="39825-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="39825-164">Par exemple, une corrélation basée uniquement sur un nom de client risque de provoquer un conflit, au cas où d'autres clients aient un nom identique.</span><span class="sxs-lookup"><span data-stu-id="39825-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="39825-165">Les deux-points (:) ne doivent pas être utilisés à l'intérieur des données qui servent à mettre les messages en corrélation. En effet, ils servent déjà à délimiter la clé et la valeur de la requête de message pour former la chaîne qui est ensuite hachée.</span><span class="sxs-lookup"><span data-stu-id="39825-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="39825-166">Si la persistance est utilisée, assurez-vous que les données d'identification actuelles n'ont pas été utilisées par une instance rendue persistante précédemment.</span><span class="sxs-lookup"><span data-stu-id="39825-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="39825-167">Désactiver temporairement la persistance peut aider à identifier ce problème.</span><span class="sxs-lookup"><span data-stu-id="39825-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="39825-168">Le suivi WCF peut être utilisé pour afficher la clé de corrélation calculée et est utile pour déboguer ce genre de problème.</span><span class="sxs-lookup"><span data-stu-id="39825-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="39825-169">Conditions de concurrence</span><span class="sxs-lookup"><span data-stu-id="39825-169">Race Conditions</span></span>
 <span data-ttu-id="39825-170">Il existe un petit intervalle entre le moment où le service reçoit un message et où la corrélation est réellement initialisée, pendant lequel les messages de suivi sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="39825-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="39825-171">Si un service de workflow initialise la corrélation basée sur le contenu à l'aide des données transmises par le client lors d'une opération unidirectionnelle et que l'appelant envoie des messages de suivi immédiats, ces messages sont ignorés pendant cet intervalle.</span><span class="sxs-lookup"><span data-stu-id="39825-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="39825-172">Cela peut être évité en utilisant une opération bidirectionnelle pour initialiser la corrélation, ou en utilisant un <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="39825-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="39825-173">Problèmes de requête de corrélation</span><span class="sxs-lookup"><span data-stu-id="39825-173">Correlation Query Issues</span></span>
 <span data-ttu-id="39825-174">Les requêtes de corrélation permettent de spécifier les données d'un message qui servent à mettre le message en corrélation.</span><span class="sxs-lookup"><span data-stu-id="39825-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="39825-175">Ces données sont spécifiées à l'aide d'une requête XPath.</span><span class="sxs-lookup"><span data-stu-id="39825-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="39825-176">Si des messages adressés à un service ne sont pas distribués alors que tout semble correct, une stratégie de résolution des problèmes consiste à spécifier une valeur littérale qui correspond à la valeur des données de message au lieu d'une requête XPath.</span><span class="sxs-lookup"><span data-stu-id="39825-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="39825-177">Pour spécifier une valeur littérale, utilisez la fonction `string`.</span><span class="sxs-lookup"><span data-stu-id="39825-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="39825-178">Dans l'exemple suivant, un <xref:System.ServiceModel.MessageQuerySet> est configuré de façon à utiliser la valeur littérale `11445` pour l'`OrderId` et des marques de commentaire sont ajoutées à la requête XPath pour la supprimer.</span><span class="sxs-lookup"><span data-stu-id="39825-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 <span data-ttu-id="39825-179">Si une requête XPath est configurée incorrectement et aucune donnée de corrélation n’est récupérée, une erreur est retournée avec le message suivant : «  Une requête de corrélation a donné un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="39825-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="39825-180">Vérifiez que les requêtes de corrélation pour le point de terminaison sont correctement configurées. ».</span><span class="sxs-lookup"><span data-stu-id="39825-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="39825-181">Une solution pour résoudre rapidement ce problème consiste à remplacer la requête XPath avec une valeur littérale comme décrit dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="39825-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="39825-182">Ce problème peut se produire si vous utilisez le générateur de requêtes XPath dans les boîtes de dialogue **Ajouter des initialiseurs de corrélation** ou **définition de CorrelatesOn** et que votre service de flux de travail utilise des contrats de message.</span><span class="sxs-lookup"><span data-stu-id="39825-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="39825-183">Dans l'exemple suivant, une classe de contrat de message est définie.</span><span class="sxs-lookup"><span data-stu-id="39825-183">In the following example, a message contract class is defined.</span></span>

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 <span data-ttu-id="39825-184">Ce contrat de message est utilisé par une activité <xref:System.ServiceModel.Activities.Receive> dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="39825-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="39825-185">Le `CartId` dans l'en-tête du message est utilisé pour corréler le message à l'instance correcte.</span><span class="sxs-lookup"><span data-stu-id="39825-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="39825-186">Si la requête XPath qui récupère le `CartId` est créée à l’aide de boîtes de dialogue de corrélation dans le concepteur de workflow, la requête XPath incorrecte suivante est générée.</span><span class="sxs-lookup"><span data-stu-id="39825-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="39825-187">Cette requête XPath serait correcte si l’activité <xref:System.ServiceModel.Activities.Receive> utilisait des paramètres pour les données, mais puisqu’elle utilise un contrat de message, elle est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="39825-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="39825-188">La requête XPath suivante est celle qu’il faut utiliser pour récupérer le `CartId` de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="39825-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="39825-189">Ceci peut être vérifié en examinant le corps du message.</span><span class="sxs-lookup"><span data-stu-id="39825-189">This can be confirmed by examining the body of the message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="39825-190">L'exemple suivant illustre une activité <xref:System.ServiceModel.Activities.Receive> configurée pour une opération `AddItem` qui utilise le contrat de message précédent pour recevoir les données.</span><span class="sxs-lookup"><span data-stu-id="39825-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="39825-191">La requête XPath est configurée correctement.</span><span class="sxs-lookup"><span data-stu-id="39825-191">The XPath query is correctly configured.</span></span>

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
