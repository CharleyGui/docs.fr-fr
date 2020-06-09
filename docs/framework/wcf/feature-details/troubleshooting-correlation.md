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
# <a name="troubleshooting-correlation"></a>Dépannage de la corrélation
La corrélation est utilisée pour établir une relation entre des messages de service de workflow et avec l'instance de workflow appropriée, mais si elle n'est pas proprement configurée, les messages ne seront pas reçus et les applications ne fonctionneront pas correctement. Cette rubrique fournit une vue d'ensemble de plusieurs méthodes de résolution des problèmes de corrélation et présente certains problèmes courants qui peuvent se produire lorsque vous utilisez la corrélation.

## <a name="handle-the-unknownmessagereceived-event"></a>Gérer l'événement UnknownMessageReceived
 L'événement <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> se produit lorsqu'un message inconnu est reçu par un service, notamment les messages qui ne peuvent pas être mis en corrélation avec une instance existante. Pour les services auto-hébergés, cet événement peut être géré dans l'application hôte.

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 Pour les services hébergés sur le Web, cet événement peut être géré en dérivant une classe de <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> et en substituant <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.

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

 Ce <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> personnalisé peut ensuite être spécifié dans le fichier `svc` du service.

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 Lorsque ce gestionnaire est appelé, le message peut être récupéré à l'aide de la propriété <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> du <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> et ressemblera au message suivant.

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

 L'inspection des messages distribués au gestionnaire <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> peut fournir des indices permettant de comprendre pourquoi le message n'a pas été mis en corrélation avec une instance du service de workflow.

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>Utiliser le suivi pour surveiller la progression du workflow
 Le suivi offre un moyen de surveiller la progression d'un workflow. Par défaut, des enregistrements de suivi sont émis pour les événements de cycle de vie du workflow, les événements de cycle de vie de l'activité, la propagation d'erreur et la reprise de signet. En outre, des enregistrements de suivi personnalisés peuvent être émis par des activités personnalisées. Lorsqu'il s'agit de résoudre les problèmes de corrélation, les enregistrements de suivi d'activité, de reprise de signet et de propagation d'erreur sont les plus utiles. Les enregistrements de suivi d'activité peuvent être utilisés pour déterminer la progression actuelle du workflow et contribuent à identifier l'activité de messagerie qui attend actuellement des messages. Les enregistrements de reprise de signet sont utiles parce qu'ils indiquent qu'un message a été reçu par le workflow, et les enregistrements de propagation d'erreur fournissent un enregistrement de toutes les erreurs présentes dans le workflow. Pour activer le suivi, spécifiez le <xref:System.Activities.Tracking.TrackingParticipant> voulu dans le <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> du <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Dans l’exemple suivant, le `ConsoleTrackingParticipant` (de l’exemple de [suivi personnalisé](../../windows-workflow-foundation/samples/custom-tracking.md) ) est configuré à l’aide du profil de suivi par défaut.

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 Un participant de suivi tel que ConsoleTrackingParticipant est utile pour les services de workflow auto-hébergés qui ont une fenêtre de console. Pour un service hébergé sur le Web, un participant de suivi qui enregistre les informations de suivi dans un magasin fiable doit être utilisé, tel que le <xref:System.Activities.Tracking.EtwTrackingParticipant> participant intégré ou un participant de suivi personnalisé qui enregistre les informations dans un fichier.

 Pour plus d’informations sur le suivi et la configuration du suivi pour un service de flux de travail hébergé sur le Web, consultez [suivi et traçage de workflow](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [configuration du suivi d’un workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)et [exemples de suivi &#91;WF&#93;](../../windows-workflow-foundation/samples/tracking.md) exemples.

## <a name="use-wcf-tracing"></a>Utiliser le suivi WCF
 Le suivi WCF fournit un suivi du flux de messages à destination et en provenance d'un service de workflow. Ces informations de suivi sont utiles dans la résolution des problèmes de corrélation, en particulier lorsqu'il s'agit de corrélation basée sur le contenu. Pour activer le suivi, spécifiez les écouteurs de suivi voulus dans la section `system.diagnostics` du fichier `web.config` si le service de workflow est hébergé sur le Web ou du fichier `app.config` si le service de workflow est auto-hébergé. Pour inclure le contenu des messages dans le fichier de trace, spécifiez `true` pour `logEntireMessage` dans l'élément `messageLogging` de la section `diagnostics` de `system.serviceModel`. Dans l'exemple suivant, les informations de suivi, notamment le contenu des messages, sont configurées pour être écrites dans un fichier nommé `service.svclog`.

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

 Pour afficher les informations de suivi contenues dans `service.svclog` , l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) est utilisé. Celui-ci est particulièrement utile pour résoudre les problèmes de corrélation basée sur le contenu, car vous pouvez consulter le contenu des messages, voir exactement ce qui est passé, et si cela correspond au <xref:System.ServiceModel.CorrelationQuery> de la corrélation basée sur le contenu. Pour plus d’informations sur le suivi WCF, consultez [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [configuration du suivi](../diagnostics/tracing/configuring-tracing.md)et [utilisation du suivi pour résoudre les problèmes de votre application](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="common-context-exchange-correlation-issues"></a>Problèmes courants rencontrés avec la corrélation basée sur l'échange de contextes
 Certains types de corrélation requièrent pour fonctionner correctement l’utilisation d’un type spécifique de liaison. C'est par exemple le cas de la corrélation demande-réponse, qui requiert une liaison bidirectionnelle telle que <xref:System.ServiceModel.BasicHttpBinding> et de la corrélation basée sur l'échange de contextes, qui requiert une liaison basée sur le contexte, telle que <xref:System.ServiceModel.BasicHttpContextBinding>. La plupart des liaisons prennent en charge des opérations bidirectionnelles, aussi cela ne constitue-t-il pas un problème courant pour la corrélation demande-réponse, mais il n’existe qu’une poignée de liaisons basées sur le contexte, notamment <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> et <xref:System.ServiceModel.NetTcpContextBinding>. Si l’une de ces liaisons n’est pas utilisée, l’appel initial à un service de workflow réussira, mais les appels suivants échoueront avec le <xref:System.ServiceModel.FaultException> suivant :

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 Les informations de contexte utilisées pour la corrélation de contexte peuvent être retournées par le <xref:System.ServiceModel.Activities.SendReply> à l'activité <xref:System.ServiceModel.Activities.Receive> qui initialise la corrélation de contexte lors de l'utilisation d'une opération bidirectionnelle, ou elles peuvent être spécifiées par l'appelant si l'opération est unidirectionnelle. Si le contexte n'est pas envoyé par l'appelant ou retourné par le service de workflow, le <xref:System.ServiceModel.FaultException> décrit précédemment sera retourné lorsqu'une opération suivante sera appelée.

## <a name="common-request-reply-correlation-issues"></a>Problèmes courants rencontrés avec la corrélation demande-réponse
 La corrélation demande-réponse est utilisée avec une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire pour implémenter une opération bidirectionnelle dans un service de workflow et avec une <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire qui appelle une opération bidirectionnelle dans un autre service Web. Lors de l’appel d’une opération bidirectionnelle dans un service WCF, le service peut être soit un service WCF basé sur du code impératif traditionnel, soit un service de flux de travail. Pour utiliser la corrélation demande-réponse, une liaison bidirectionnelle doit être utilisée, telle que <xref:System.ServiceModel.BasicHttpBinding>, et les opérations doivent être bidirectionnelles.

 Si le service de workflow a des opérations bidirectionnelles en parallèle, ou se chevauchent <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> , la gestion de handle de corrélation implicite fournie par <xref:System.ServiceModel.Activities.WorkflowServiceHost> peut ne pas suffire, en particulier dans les scénarios à forte contrainte, et les messages peuvent ne pas être correctement routés. Pour éviter la survenue de ce problème, nous vous recommandons de toujours spécifier explicitement un <xref:System.ServiceModel.Activities.CorrelationHandle> lors de l'utilisation de la corrélation demande-réponse. Lorsque vous utilisez les modèles **SendAndReceiveReply** et **ReceiveAndSendReply** à partir de la section messagerie de la **boîte à outils** du concepteur de flux de travail, un <xref:System.ServiceModel.Activities.CorrelationHandle> est explicitement configuré par défaut. Lors de la génération d'un workflow à l'aide de code, le <xref:System.ServiceModel.Activities.CorrelationHandle> est spécifié dans le <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> de la première activité de la paire. Dans l'exemple suivant, une activité <xref:System.ServiceModel.Activities.Receive> est configurée avec un <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> explicite spécifié dans le <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.

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

 La persistance n’est pas autorisée entre une <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> paire ou une <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> paire. Une zone de non-persistance valide tant que les deux activités ne sont pas terminées, est créée. Si une activité, telle qu'une activité de délai, se trouve dans cette zone de non-persistance et cause une inactivité du workflow, ce dernier ne sera pas rendu persistant même si l'hôte est configuré pour rendre persistants les workflows lorsqu'ils deviennent inactifs. Si une activité, telle qu'une activité persistante, tente de persister de façon explicite dans la zone de non-persistance, une exception irrécupérable est levée, le workflow est abandonné et un <xref:System.ServiceModel.FaultException> est retourné à l'appelant. Le message d'exception irrécupérable est « System.InvalidOperationException : Les activités Persist ne peuvent pas être contenues au sein de blocs sans persistance ». Cette exception n'est pas retournée à l'appelant mais peut-être observée si le suivi est activé. Le message du <xref:System.ServiceModel.FaultException> retourné à l'appelant est « Impossible d'effectuer l'opération car WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' a terminé ».

 Pour plus d’informations sur la corrélation demande-réponse, consultez [demande-réponse](request-reply-correlation.md).

## <a name="common-content-correlation-issues"></a>Problèmes courants rencontrés avec la corrélation basée sur le contenu
 La corrélation basée sur le contenu est utilisée lorsqu'un service de workflow reçoit plusieurs messages et dispose de quelques données dans les messages échangés qui identifient l'instance souhaitée. La corrélation basée sur le contenu utilise ces données dans les messages, par exemple un numéro de client ou un ID de commande, pour router les messages vers l'instance de workflow appropriée. Cette section décrit plusieurs problèmes courants qui peuvent se produire lors de l'utilisation de la corrélation basée sur le contenu.

### <a name="ensure-the-identifying-data-is-unique"></a>Unicité des données d'identification
 Les données utilisées pour identifier l'instance sont hachées en une clé de corrélation. Il est important de s'assurer que les données utilisées pour la corrélation sont uniques, pour éviter que des conflits se produisent dans la clé hachée, entraînant des confusions dans le routage des messages. Par exemple, une corrélation basée uniquement sur un nom de client risque de provoquer un conflit, au cas où d'autres clients aient un nom identique. Les deux-points (:) ne doivent pas être utilisés à l'intérieur des données qui servent à mettre les messages en corrélation. En effet, ils servent déjà à délimiter la clé et la valeur de la requête de message pour former la chaîne qui est ensuite hachée. Si la persistance est utilisée, assurez-vous que les données d'identification actuelles n'ont pas été utilisées par une instance rendue persistante précédemment. Désactiver temporairement la persistance peut aider à identifier ce problème. Le suivi WCF peut être utilisé pour afficher la clé de corrélation calculée et est utile pour déboguer ce genre de problème.

### <a name="race-conditions"></a>Conditions de concurrence
 Il existe un petit intervalle entre le moment où le service reçoit un message et où la corrélation est réellement initialisée, pendant lequel les messages de suivi sont ignorés. Si un service de workflow initialise la corrélation basée sur le contenu à l'aide des données transmises par le client lors d'une opération unidirectionnelle et que l'appelant envoie des messages de suivi immédiats, ces messages sont ignorés pendant cet intervalle. Cela peut être évité en utilisant une opération bidirectionnelle pour initialiser la corrélation, ou en utilisant un <xref:System.ServiceModel.Activities.TransactedReceiveScope>.

### <a name="correlation-query-issues"></a>Problèmes de requête de corrélation
 Les requêtes de corrélation permettent de spécifier les données d'un message qui servent à mettre le message en corrélation. Ces données sont spécifiées à l'aide d'une requête XPath. Si des messages adressés à un service ne sont pas distribués alors que tout semble correct, une stratégie de résolution des problèmes consiste à spécifier une valeur littérale qui correspond à la valeur des données de message au lieu d'une requête XPath. Pour spécifier une valeur littérale, utilisez la fonction `string`. Dans l'exemple suivant, un <xref:System.ServiceModel.MessageQuerySet> est configuré de façon à utiliser la valeur littérale `11445` pour l'`OrderId` et des marques de commentaire sont ajoutées à la requête XPath pour la supprimer.

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

 Si une requête XPath est configurée incorrectement et aucune donnée de corrélation n’est récupérée, une erreur est retournée avec le message suivant : «  Une requête de corrélation a donné un jeu de résultats vide. Vérifiez que les requêtes de corrélation pour le point de terminaison sont correctement configurées. ». Une solution pour résoudre rapidement ce problème consiste à remplacer la requête XPath avec une valeur littérale comme décrit dans la section précédente. Ce problème peut se produire si vous utilisez le générateur de requêtes XPath dans les boîtes de dialogue **Ajouter des initialiseurs de corrélation** ou **définition de CorrelatesOn** et que votre service de flux de travail utilise des contrats de message. Dans l'exemple suivant, une classe de contrat de message est définie.

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

 Ce contrat de message est utilisé par une activité <xref:System.ServiceModel.Activities.Receive> dans un workflow. Le `CartId` dans l'en-tête du message est utilisé pour corréler le message à l'instance correcte. Si la requête XPath qui récupère le `CartId` est créée à l’aide de boîtes de dialogue de corrélation dans le concepteur de workflow, la requête XPath incorrecte suivante est générée.

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 Cette requête XPath serait correcte si l’activité <xref:System.ServiceModel.Activities.Receive> utilisait des paramètres pour les données, mais puisqu’elle utilise un contrat de message, elle est incorrecte. La requête XPath suivante est celle qu’il faut utiliser pour récupérer le `CartId` de l’en-tête.

```
sm:header()/tempuri:CartId
```

Ceci peut être vérifié en examinant le corps du message.

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

L'exemple suivant illustre une activité <xref:System.ServiceModel.Activities.Receive> configurée pour une opération `AddItem` qui utilise le contrat de message précédent pour recevoir les données. La requête XPath est configurée correctement.

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
