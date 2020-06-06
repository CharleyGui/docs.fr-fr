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
Cet élément définit les paramètres pour les fonctions d'enregistrement des messages de Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`logEntireMessage`|Valeur booléenne qui spécifie si le message entier (en-tête et corps du message) est enregistré. La valeur par défaut est `false` ce qui signifie que seul l'en-tête de message est enregistré. Ce paramètre affecte tous les niveaux d'enregistrement de message (messages de service, de transport et malformés).|  
|`logMalformedMessages`|Valeur booléenne qui spécifie si les messages incorrects sont enregistrés. Les messages incorrects ne comptent pas pour le `maxMessagesToLog`. Par défaut, il s’agit de `false`.|  
|`logMessagesAtServiceLevel`|Valeur booléenne qui spécifie si les messages sont suivis au niveau du service (avant les transformations associées au chiffrement et au transport). Par défaut, il s’agit de `false`.|  
|`logMessagesAtTransportLevel`|Valeur booléenne qui spécifie si les messages sont suivis au niveau du transport. Tous les filtres spécifiés dans le fichier de configuration sont appliqués et seuls les messages qui correspondent aux filtres sont suivis. Par défaut, il s’agit de `false`.|  
|`maxMessagesToLog`|Entier positif qui spécifie le nombre maximal de messages à enregistrer. La valeur par défaut est 1000.|  
|`maxSizeOfMessageToLog`|Entier positif qui spécifie la taille maximale, en octets, d'un message à enregistrer. Les messages plus grands que la limite ne seront pas enregistrés. Ce paramètre affecte tous les niveaux de suivi. La valeur par défaut est 262144(0x4000).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|filtres|L'élément `filters` maintient une collection de filtres XPath. Lorsque l'enregistrement des messages de transport est activé (`logMessagesAtTransportLevel` a la valeur `true`), seuls les messages correspondant aux filtres sont enregistrés.<br /><br /> Les filtres sont appliqués uniquement à la couche transport. Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.<br /><br /> Le seul attribut pour cet élément, `filter`, est un XpathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|diagnostics|Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.|  
  
## <a name="remarks"></a>Remarques  
 Les messages sont entrés à trois niveaux différents dans la pile : les messages de service, de transport et incorrects. Chaque niveau peut être activé séparément.  
  
 Les filtres XPath peuvent être ajoutés afin d’enregistrer des messages spécifiques aux niveaux de transport et de service. Si aucun filtre n'est défini, tous les messages sont enregistrés. Les filtres sont appliqués uniquement aux en-têtes du message. Le corps est ignoré. WCF ignore le corps du message pour améliorer la performance. Si vous souhaitez filtrer le contenu du corps, vous pouvez créer un écouteur personnalisé avec un filtre approprié.  
  
 Vous devez créer un écouteur de trace pour activer le suivi de message. L'écouteur lui-même peut être tout écouteur qui fonctionne avec le <xref:System.Diagnostics> qui effectue le suivi de l'architecture. L'exemple suivant montre comment créer un écouteur de ce type.  
  
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
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [Configuration de la journalisation des messages](../../../wcf/diagnostics/configuring-message-logging.md)
