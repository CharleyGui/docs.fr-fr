---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855125"
---
# \<messageLogging>
<span data-ttu-id="3f7ac-101">Cet élément définit les paramètres pour les fonctions d'enregistrement des messages de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3f7ac-101">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a><span data-ttu-id="3f7ac-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f7ac-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f7ac-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3f7ac-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3f7ac-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f7ac-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="3f7ac-105">Attributes</span></span>  
  
|<span data-ttu-id="3f7ac-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="3f7ac-106">Attribute</span></span>|<span data-ttu-id="3f7ac-107">Description</span><span class="sxs-lookup"><span data-stu-id="3f7ac-107">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="3f7ac-108">Valeur booléenne qui spécifie si le message entier (en-tête et corps du message) est enregistré.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-108">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="3f7ac-109">La valeur par défaut est `false` ce qui signifie que seul l'en-tête de message est enregistré.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-109">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="3f7ac-110">Ce paramètre affecte tous les niveaux d'enregistrement de message (messages de service, de transport et malformés).</span><span class="sxs-lookup"><span data-stu-id="3f7ac-110">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="3f7ac-111">Valeur booléenne qui spécifie si les messages incorrects sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-111">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="3f7ac-112">Les messages incorrects ne comptent pas pour le `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-112">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="3f7ac-113">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-113">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="3f7ac-114">Valeur booléenne qui spécifie si les messages sont suivis au niveau du service (avant les transformations associées au chiffrement et au transport).</span><span class="sxs-lookup"><span data-stu-id="3f7ac-114">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="3f7ac-115">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-115">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="3f7ac-116">Valeur booléenne qui spécifie si les messages sont suivis au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-116">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="3f7ac-117">Tous les filtres spécifiés dans le fichier de configuration sont appliqués et seuls les messages qui correspondent aux filtres sont suivis.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-117">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="3f7ac-118">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-118">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="3f7ac-119">Entier positif qui spécifie le nombre maximal de messages à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-119">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="3f7ac-120">La valeur par défaut est 1000.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-120">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="3f7ac-121">Entier positif qui spécifie la taille maximale, en octets, d'un message à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-121">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="3f7ac-122">Les messages plus grands que la limite ne seront pas enregistrés.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-122">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="3f7ac-123">Ce paramètre affecte tous les niveaux de suivi.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-123">This setting affects all trace levels.</span></span> <span data-ttu-id="3f7ac-124">La valeur par défaut est 262144(0x4000).</span><span class="sxs-lookup"><span data-stu-id="3f7ac-124">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f7ac-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3f7ac-125">Child Elements</span></span>  
  
|<span data-ttu-id="3f7ac-126">Élément</span><span class="sxs-lookup"><span data-stu-id="3f7ac-126">Element</span></span>|<span data-ttu-id="3f7ac-127">Description</span><span class="sxs-lookup"><span data-stu-id="3f7ac-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f7ac-128">filtres</span><span class="sxs-lookup"><span data-stu-id="3f7ac-128">filters</span></span>|<span data-ttu-id="3f7ac-129">L'élément `filters` maintient une collection de filtres XPath.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-129">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="3f7ac-130">Lorsque l'enregistrement des messages de transport est activé (`logMessagesAtTransportLevel` a la valeur `true`), seuls les messages correspondant aux filtres sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-130">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="3f7ac-131">Les filtres sont appliqués uniquement à la couche transport.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-131">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="3f7ac-132">Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-132">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="3f7ac-133">Le seul attribut pour cet élément, `filter`, est un XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-133">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f7ac-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3f7ac-134">Parent Elements</span></span>  
  
|<span data-ttu-id="3f7ac-135">Élément</span><span class="sxs-lookup"><span data-stu-id="3f7ac-135">Element</span></span>|<span data-ttu-id="3f7ac-136">Description</span><span class="sxs-lookup"><span data-stu-id="3f7ac-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f7ac-137">diagnostics</span><span class="sxs-lookup"><span data-stu-id="3f7ac-137">diagnostics</span></span>|<span data-ttu-id="3f7ac-138">Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-138">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f7ac-139">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f7ac-139">Remarks</span></span>  
 <span data-ttu-id="3f7ac-140">Les messages sont entrés à trois niveaux différents dans la pile : les messages de service, de transport et incorrects.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-140">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="3f7ac-141">Chaque niveau peut être activé séparément.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-141">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="3f7ac-142">Les filtres XPath peuvent être ajoutés afin d’enregistrer des messages spécifiques aux niveaux de transport et de service.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-142">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="3f7ac-143">Si aucun filtre n'est défini, tous les messages sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-143">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="3f7ac-144">Les filtres sont appliqués uniquement aux en-têtes du message.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-144">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="3f7ac-145">Le corps est ignoré.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-145">The body is ignored.</span></span> <span data-ttu-id="3f7ac-146">WCF ignore le corps du message pour améliorer la performance.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-146">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="3f7ac-147">Si vous souhaitez filtrer le contenu du corps, vous pouvez créer un écouteur personnalisé avec un filtre approprié.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-147">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="3f7ac-148">Vous devez créer un écouteur de trace pour activer le suivi de message.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-148">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="3f7ac-149">L'écouteur lui-même peut être tout écouteur qui fonctionne avec le <xref:System.Diagnostics> qui effectue le suivi de l'architecture.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-149">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="3f7ac-150">L'exemple suivant montre comment créer un écouteur de ce type.</span><span class="sxs-lookup"><span data-stu-id="3f7ac-150">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="3f7ac-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f7ac-151">Example</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="3f7ac-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f7ac-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="3f7ac-153">Configuration de la journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="3f7ac-153">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
