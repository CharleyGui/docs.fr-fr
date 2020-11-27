---
title: Consultation des journaux de messages
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c8313b14a45051b7828a1ab223a3da63b2e7a153
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291152"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="67d74-102">Consultation des journaux de messages</span><span class="sxs-lookup"><span data-stu-id="67d74-102">Viewing Message Logs</span></span>

<span data-ttu-id="67d74-103">Cette rubrique contient des instructions permettant d'afficher les journaux des messages.</span><span class="sxs-lookup"><span data-stu-id="67d74-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="67d74-104">Consultation des journaux de messages dans Service Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="67d74-104">Viewing Message Logs in the Service Trace Viewer</span></span>  

 <span data-ttu-id="67d74-105">Un message est transformé au fur et à mesure qu’il est traité par WCF.</span><span class="sxs-lookup"><span data-stu-id="67d74-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="67d74-106">Par conséquent, un message consigné reflète uniquement le contenu du message au moment où il a été consigné, et non pas le contenu sur le câble.</span><span class="sxs-lookup"><span data-stu-id="67d74-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="67d74-107">Comme la sortie de l'enregistrement des messages n'est pas liée au format de transfert du message, l'enregistrement des messages génère le message décodé.</span><span class="sxs-lookup"><span data-stu-id="67d74-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="67d74-108">Si vous avez configuré l'enregistrement des messages correctement, tout message enregistré doit être au format de texte brut.</span><span class="sxs-lookup"><span data-stu-id="67d74-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="67d74-109">Par exemple, le format (texte brut) des messages enregistrés n'est pas affecté par l'utilisation d'un encodeur de message binaire.</span><span class="sxs-lookup"><span data-stu-id="67d74-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="67d74-110">La sortie de XmlWriterTraceListener est un fichier qui contient une séquence de fragments XML.</span><span class="sxs-lookup"><span data-stu-id="67d74-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="67d74-111">Sachez qu'il ne s'agit pas d'un fichier XML valide.</span><span class="sxs-lookup"><span data-stu-id="67d74-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="67d74-112">Il est recommandé d’utiliser l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pour afficher les fichiers journaux des messages.</span><span class="sxs-lookup"><span data-stu-id="67d74-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="67d74-113">Pour plus d’informations sur l’utilisation de cet outil, consultez [utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="67d74-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="67d74-114">Dans Service Trace Viewer, les messages sont répertoriés sous l’onglet **message** . Les messages qui ont provoqué, ou sont liés à, une erreur de traitement sont mis en surbrillance en jaune (niveau d’avertissement) ou rouge (niveau d’erreur), en fonction de la gravité de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="67d74-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="67d74-115">Si vous double-cliquez sur le message, le suivi du message s'affiche dans le contexte de la demande.</span><span class="sxs-lookup"><span data-stu-id="67d74-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67d74-116">Si un message n'a pas d'en-tête, aucune balise `<header/>` n'est enregistrée.</span><span class="sxs-lookup"><span data-stu-id="67d74-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="67d74-117">Consultation des messages consignés par un client, un relais et un service</span><span class="sxs-lookup"><span data-stu-id="67d74-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  

 <span data-ttu-id="67d74-118">Votre environnement peut contenir un client, qui envoie un message à un relais, qui par la suite envoie le message au service.</span><span class="sxs-lookup"><span data-stu-id="67d74-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="67d74-119">Lorsque la journalisation des messages est activée sur les trois emplacements, et que les trois journaux des messages sont affichés simultanément dans l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) , les échanges de journaux de messages ne sont pas restitués correctement.</span><span class="sxs-lookup"><span data-stu-id="67d74-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="67d74-120">Cela est dû au fait que `CorrelationId` et `ActivityId` dans l'en-tête de message ne sont pas uniques pour chaque paire émetteur-récepteur.</span><span class="sxs-lookup"><span data-stu-id="67d74-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="67d74-121">Pour résoudre ce problème, utilisez l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="67d74-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
- <span data-ttu-id="67d74-122">Affichez uniquement deux des trois journaux de messages dans l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="67d74-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
- <span data-ttu-id="67d74-123">Si vous devez afficher les trois journaux dans l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) en même temps, vous pouvez modifier le service de relais en créant une nouvelle <xref:System.ServiceModel.Channels.Message> instance.</span><span class="sxs-lookup"><span data-stu-id="67d74-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="67d74-124">Cette instance doit être une copie du corps du message entrant et de tous les en-têtes à l'exception de `ActivityId` et `Action`.</span><span class="sxs-lookup"><span data-stu-id="67d74-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="67d74-125">L'exemple de code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="67d74-125">The following example code demonstrates how to do this.</span></span>  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="67d74-126">Cas exceptionnels de contenu de journalisation de message inexact</span><span class="sxs-lookup"><span data-stu-id="67d74-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  

 <span data-ttu-id="67d74-127">Dans les conditions suivantes, les messages consignés peuvent ne pas être la représentation exacte du flux d'octets présent sur le câble.</span><span class="sxs-lookup"><span data-stu-id="67d74-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
- <span data-ttu-id="67d74-128">Concernant BasicHttpBinding, les en-têtes d'enveloppe sont enregistrés pour les messages entrants de l'espace de noms /addressing/none.</span><span class="sxs-lookup"><span data-stu-id="67d74-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
- <span data-ttu-id="67d74-129">Les espaces blancs peuvent être incompatibles.</span><span class="sxs-lookup"><span data-stu-id="67d74-129">White spaces can be mismatched.</span></span>  
  
- <span data-ttu-id="67d74-130">Concernant les messages entrants, les éléments vides peuvent être représentés différemment.</span><span class="sxs-lookup"><span data-stu-id="67d74-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="67d74-131">Par exemple, \<tag> \</tag> au lieu de\<tag/></span><span class="sxs-lookup"><span data-stu-id="67d74-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
- <span data-ttu-id="67d74-132">Lorsque la journalisation PII connue est désactivée soit par défaut, soit par le paramètre explicite enableLoggingKnownPii= "true".</span><span class="sxs-lookup"><span data-stu-id="67d74-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
- <span data-ttu-id="67d74-133">L'encodage est activé pour la conversion au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="67d74-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d74-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67d74-134">See also</span></span>

- [<span data-ttu-id="67d74-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="67d74-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="67d74-136">Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="67d74-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="67d74-137">Journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="67d74-137">Message Logging</span></span>](message-logging.md)
