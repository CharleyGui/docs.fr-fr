---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69918884"
---
# \<filters>

<span data-ttu-id="e7a0f-101">L'élément `filters` détient une collection de filtres XPath utilisés pour contrôler le type de message enregistré.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-101">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="e7a0f-102">Les filtres sont appliqués uniquement à la couche de transport, spécifiée par `logMessagesAtTransportLevel` (valeur `true`).</span><span class="sxs-lookup"><span data-stu-id="e7a0f-102">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="e7a0f-103">Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-103">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="e7a0f-104">Pour ajouter un filtre à la collection, utilisez le mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-104">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="e7a0f-105">Lorsqu'un ou plusieurs filtres sont définis, seuls les messages qui correspondent au moins à l'un des filtres sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-105">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="e7a0f-106">Si aucun filtre n'est défini, tous les messages passent.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-106">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="e7a0f-107">Les filtres prennent en charge la syntaxe XPath complète et s’appliquent dans l’ordre dans lequel ils apparaissent dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-107">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="e7a0f-108">Un filtre syntaxiquement incorrect provoque la levée d'une exception de configuration.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-108">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="e7a0f-109">L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.</span><span class="sxs-lookup"><span data-stu-id="e7a0f-109">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="e7a0f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7a0f-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="e7a0f-111">Configuration de la journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="e7a0f-111">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
