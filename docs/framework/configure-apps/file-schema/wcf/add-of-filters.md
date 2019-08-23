---
title: <add> de <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926696"
---
# <a name="add-of-filters"></a>\<Ajouter > de \<filtres >
Filtre XPath qui spécifie le type de message à enregistrer.  
  
 \<system.ServiceModel>  
\<> de diagnostic  
\<messageLogging>  
\<filters>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|filter|Chaîne qui spécifie une requête sur un document XML défini par une expression XPath 1.0. Pour plus d'informations, consultez <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filtres>](filters.md)|Contient une collection de filtres XPath utilisés pour contrôler le type de message enregistré.|  
  
## <a name="remarks"></a>Notes  
 Les filtres sont appliqués uniquement à la couche de transport, spécifiée par `logMessagesAtTransportLevel` (valeur `true`). Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.  
  
 Pour ajouter un filtre à la collection, utilisez le mot clé `add`. Lorsqu'un ou plusieurs filtres sont définis, seuls les messages qui correspondent au moins à l'un des filtres sont enregistrés. Si aucun filtre n'est défini, tous les messages passent.  
  
 Les filtres prennent en charge la syntaxe XPath complète et s’appliquent dans l’ordre dans lequel ils apparaissent dans le fichier de configuration. Un filtre syntaxiquement incorrect provoque la levée d'une exception de configuration.  
  
 L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Configuration de la journalisation des messages](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
