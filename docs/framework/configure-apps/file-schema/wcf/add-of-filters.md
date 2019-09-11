---
title: <add> de <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850564"
---
# <a name="add-of-filters"></a><span data-ttu-id="e97a5-102">\<Ajouter > de \<filtres ></span><span class="sxs-lookup"><span data-stu-id="e97a5-102">\<add> of \<filters></span></span>
<span data-ttu-id="e97a5-103">Filtre XPath qui spécifie le type de message à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="e97a5-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
<span data-ttu-id="e97a5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e97a5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e97a5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e97a5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e97a5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de diagnostic**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="e97a5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="e97a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<messageLogging >** ](messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="e97a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)</span></span>\
<span data-ttu-id="e97a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtres >** ](filters.md)</span><span class="sxs-lookup"><span data-stu-id="e97a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)</span></span>\
<span data-ttu-id="e97a5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="e97a5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97a5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e97a5-110">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e97a5-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e97a5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e97a5-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e97a5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e97a5-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e97a5-113">Attributes</span></span>  
  
|<span data-ttu-id="e97a5-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e97a5-114">Attribute</span></span>|<span data-ttu-id="e97a5-115">Description</span><span class="sxs-lookup"><span data-stu-id="e97a5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e97a5-116">filter</span><span class="sxs-lookup"><span data-stu-id="e97a5-116">filter</span></span>|<span data-ttu-id="e97a5-117">Chaîne qui spécifie une requête sur un document XML défini par une expression XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="e97a5-117">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="e97a5-118">Pour plus d'informations, consultez <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="e97a5-118">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e97a5-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e97a5-119">Child Elements</span></span>  
 <span data-ttu-id="e97a5-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e97a5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e97a5-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e97a5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e97a5-122">Élément</span><span class="sxs-lookup"><span data-stu-id="e97a5-122">Element</span></span>|<span data-ttu-id="e97a5-123">Description</span><span class="sxs-lookup"><span data-stu-id="e97a5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e97a5-124">\<filtres></span><span class="sxs-lookup"><span data-stu-id="e97a5-124">\<filters></span></span>](filters.md)|<span data-ttu-id="e97a5-125">Contient une collection de filtres XPath utilisés pour contrôler le type de message enregistré.</span><span class="sxs-lookup"><span data-stu-id="e97a5-125">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e97a5-126">Notes</span><span class="sxs-lookup"><span data-stu-id="e97a5-126">Remarks</span></span>  
 <span data-ttu-id="e97a5-127">Les filtres sont appliqués uniquement à la couche de transport, spécifiée par `logMessagesAtTransportLevel` (valeur `true`).</span><span class="sxs-lookup"><span data-stu-id="e97a5-127">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="e97a5-128">Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.</span><span class="sxs-lookup"><span data-stu-id="e97a5-128">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="e97a5-129">Pour ajouter un filtre à la collection, utilisez le mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="e97a5-129">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="e97a5-130">Lorsqu'un ou plusieurs filtres sont définis, seuls les messages qui correspondent au moins à l'un des filtres sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="e97a5-130">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="e97a5-131">Si aucun filtre n'est défini, tous les messages passent.</span><span class="sxs-lookup"><span data-stu-id="e97a5-131">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="e97a5-132">Les filtres prennent en charge la syntaxe XPath complète et s’appliquent dans l’ordre dans lequel ils apparaissent dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e97a5-132">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="e97a5-133">Un filtre syntaxiquement incorrect provoque la levée d'une exception de configuration.</span><span class="sxs-lookup"><span data-stu-id="e97a5-133">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="e97a5-134">L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.</span><span class="sxs-lookup"><span data-stu-id="e97a5-134">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e97a5-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="e97a5-135">Example</span></span>  
 <span data-ttu-id="e97a5-136">L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.</span><span class="sxs-lookup"><span data-stu-id="e97a5-136">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e97a5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e97a5-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="e97a5-138">Configuration de la journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="e97a5-138">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="e97a5-139">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="e97a5-139">\<messageLogging></span></span>](messagelogging.md)
