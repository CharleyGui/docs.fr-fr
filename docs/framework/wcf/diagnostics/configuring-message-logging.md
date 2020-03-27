---
title: Configuration de la journalisation des messages
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 283f43239d6cf5aea5ea668397a52313ff526e2a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345182"
---
# <a name="configuring-message-logging"></a>Configuration de la journalisation des messages

Cette rubrique contient des instructions permettant de configurer l'enregistrement des messages en fonction de différentes situations.

## <a name="enabling-message-logging"></a>Activation de la journalisation des messages

Windows Communication Foundation (WCF) ne enregistre pas de messages par défaut. Pour activer la journalisation des messages, vous devez ajouter un écouteur de suivi à la source de suivi `System.ServiceModel.MessageLogging` et définir les attributs de l'élément `<messagelogging>` dans le fichier de configuration.

L'exemple suivant indique comment activer la journalisation et spécifier des options supplémentaires.

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
         <add name="messages"
              type="System.Diagnostics.XmlWriterTraceListener"
              initializeData="c:\logs\messages.svclog" />
        </listeners>
    </source>
  </sources>
</system.diagnostics>

<system.serviceModel>
  <diagnostics>
    <messageLogging
         logEntireMessage="true"
         logMalformedMessages="false"
         logMessagesAtServiceLevel="true"
         logMessagesAtTransportLevel="false"
         maxMessagesToLog="3000"
         maxSizeOfMessageToLog="2000"/>
  </diagnostics>
</system.serviceModel>
```

Pour plus d’informations sur les paramètres de connexion de messages, voir [Paramètres recommandés pour le traçage et l’enregistrement des messages](./tracing/recommended-settings-for-tracing-and-message-logging.md).

Vous pouvez utiliser la méthode `add` afin d'indiquer le nom et type de l'écouteur de suivi à utiliser. Dans l'exemple de configuration, nous avons attribué le nom « messages » à l'écouteur et ajouté l'écouteur de suivi standard .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) comme type à utiliser. Si vous utilisez `System.Diagnostics.XmlWriterTraceListener`, vous devez spécifier l'emplacement et le nom du fichier de sortie dans le fichier de configuration. Pour ce faire, il suffit d'affecter le nom du fichier journal à `initializeData`. Si cette consigne n'est pas respectée, le système lèvera une exception. Vous pouvez également implémenter un écouteur personnalisé qui enregistrera les journaux dans un fichier par défaut.

> [!NOTE]
> Puisque la journalisation des messages accède à l'espace disque, vous devez limiter le nombre des messages à enregistrer pour chaque service. Cette limite atteinte, un message de suivi sera généré au niveau des informations et les messages cesseront d'être enregistrés.

Les niveaux d'enregistrement ainsi que d'autres options sont abordés dans la section Niveaux d'enregistrement et autres options.

L'attribut `switchValue` d'une `source` est uniquement valable dans le cadre du suivi. Si vous spécifiez un attribut `switchValue` pour la source de suivi `System.ServiceModel.MessageLogging` comme suit, cela sera sans effet.

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
</source>
```

Si vous souhaitez désactiver la source de suivi, vous devrez utiliser à la place les attributs `logMessagesAtServiceLevel`, `logMalformedMessages`et `logMessagesAtTransportLevel` de l'élément `messageLogging`. Vous devez affecter à tous ces attributs la valeur `false`. Pour ce faire, il suffit d'utiliser le fichier de configuration figurant dans l'exemple de code précédent avec l'Éditeur de configuration ou WMI. Pour plus d’informations sur l’outil Configuration Editor, voir [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md). Pour plus d’informations sur WMI, voir [Utiliser l’instrumentation de gestion Windows pour les diagnostics](./wmi/index.md).

## <a name="logging-levels-and-options"></a>Niveaux d'enregistrement et options supplémentaires

Pour les messages entrants, leur enregistrement intervient immédiatement après leur création, immédiatement avant leur arrivée dans le code utilisateur au niveau du service et lorsque des erreurs sont détectées les concernant.

Pour les messages sortants, leur enregistrement intervient immédiatement après leur départ du code utilisateur et immédiatement avant leur transmission.

WCF enregistre les messages à deux niveaux différents, le service et le transport. Les messages erronés sont également enregistrés. Ces trois niveaux sont indépendants les uns des autres et peuvent être activés séparément dans la configuration.

Vous pouvez contrôler le niveau d'enregistrement en définissant les attributs `logMessagesAtServiceLevel`, `logMalformedMessages` et `logMessagesAtTransportLevel` de l'élément `messageLogging`.

### <a name="service-level"></a>Niveau de service

Les messages enregistrés à ce niveau sont ceux qui sont sur le point d'arriver (côté destinataire) dans le code utilisateur ou de quitter ce dernier (côté expéditeur). Si des filtres ont été définis, seuls les messages respectant les critères définis par ces filtres seront enregistrés. Dans le cas contraire, tous les messages du niveau service seront enregistrés. Les messages d'infrastructure (transactions, canal homologue et sécurité) sont également enregistrés à ce niveau, à l'exception des messages de messagerie fiable. Pour les messages transmis en flux continu, seuls les en-têtes sont enregistrés. Les messages sécurisés sont également enregistrés et déchiffrés à ce niveau.

### <a name="transport-level"></a>Niveau transport

Les messages enregistrés à ce niveau sont prêts à être encodés ou décodés pour ou après transmission. Si des filtres ont été définis, seuls les messages respectant les critères définis par ces filtres seront enregistrés. Dans le cas contraire, tous les messages de niveau transport seront enregistrés. Tous les messages d'infrastructure sont enregistrés à ce niveau, notamment les messages de messagerie fiable. Pour les messages transmis en flux continu, seuls les en-têtes sont enregistrés. Les messages sécurisés sont également enregistrés à ce niveau sous leur forme chiffrée, sauf si un transport sécurisé tel qu'HTTPS est utilisé.

### <a name="malformed-level"></a>Niveau erreurs

Les messages malformés sont des messages qui sont rejetés par la pile WCF à n’importe quelle étape du traitement. Les messages mal formés sont enregistrés en l'état : sous leur forme chiffrée lorsqu'ils le sont, dans un langage XML incorrect et ainsi de suite. `maxSizeOfMessageToLog` définit la taille du message à enregistrer sous forme de CDATA. Par défaut, `maxSizeOfMessageToLog` est égal à 256K. Pour plus d’informations sur cet attribut, consultez la section Autres options.

### <a name="other-options"></a>Autres options

Outre les niveaux d'enregistrement, l'utilisateur peut spécifier les options suivantes :

- Enregistrer le message dans sa totalité (attribut `logEntireMessage`) : cette valeur spécifie si le message doit être enregistré dans son intégralité (corps et en-tête). La valeur par défaut est `false`, ce qui signifie que seul l'en-tête est enregistré. Ce paramètre affecte les niveaux service et transport de journalisation des messages.

- Nombre de messages maximal à enregistrer (attribut `maxMessagesToLog`) : cette valeur spécifie le nombre maximal de messages à enregistrer. Tous les messages (service, transport et messages erronés) sont comptabilisés en fonction de cette limite. Une fois cette limite atteinte, un message de suivi est généré et aucun message supplémentaire n'est enregistré. La valeur par défaut est 10 000.

- Taille maximale de messages à enregistrer (attribut `maxSizeOfMessageToLog`) : cette valeur spécifie en octets la taille maximale de messages à enregistrer. Les messages qui dépassent cette taille ne sont pas enregistrés et aucune opération les concernant n'est exécutée. Ce paramètre affecte tous les niveaux de suivi. Si le suivi ServiceModel est activé, un message d'avertissement de suivi est généré au premier point d'enregistrement (ServiceModelSend * ou TransportReceive) pour informer l'utilisateur de ce dépassement. La valeur par défaut pour les messages de niveau de service et de niveau de transport est 256K, alors que la valeur par défaut pour les messages erronés est 4K.

  > [!CAUTION]
  > La taille de message calculée pour être comparée à `maxSizeOfMessageToLog` est celle présente dans la mémoire avant la sérialisation. Cette taille peut différer de la taille de chaîne des messages effectivement enregistrée et est, dans de nombreux cas, supérieure à leur grandeur réelle. Par conséquent, certains messages peuvent ne pas être enregistrés. Vous pouvez compenser ce phénomène en augmentant la valeur de l'attribut `maxSizeOfMessageToLog` de 10 %. En outre, si des messages erronés sont enregistrés, l'espace disque réel utilisé par les journaux de message peut atteindre jusqu'à 5 fois la valeur spécifiée par `maxSizeOfMessageToLog`.

Si aucun écouteur de suivi n'est défini dans le fichier de configuration, aucune sortie d'enregistrement n'est générée, quel que soit le niveau d'enregistrement spécifié.

Les options de journalisation des messages, telles que les attributs présentés de cette section, peuvent être changées en cours d'exécution à l'aide de Windows Management Instrumentation (WMI). Cela peut être fait en accédant à l’instance [AppDomainInfo,](./wmi/appdomaininfo.md) qui expose ces propriétés Boolean: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`et `LogMalformedMessages`. Par conséquent, si vous configurez un écouteur de suivi pour l'enregistrement des messages, mais affectez la valeur `false` à ces options dans la configuration, vous pourrez leur affecter ultérieurement la valeur `true` pendant l'exécution de l'application. Ceci permet en fait d'activer l'enregistrement des messages pendant l'exécution. De la même façon, si vous activez l'enregistrement des messages dans votre fichier de configuration, vous pouvez le désactiver pendant l'exécution à l'aide de WMI. Pour plus d’informations, voir [Utiliser l’instrumentation de gestion Windows pour les diagnostics](./wmi/index.md).

Le champ `source` d'un journal de message indique le contexte de journalisation des messages : envoi / réception d'un message de demande, demande-réponse ou demande unidirectionnelle au niveau de la couche de modèle de service ou de transport, ou message mal formé.

Pour les messages `source` malformés, est égal à `Malformed`. Dans les autres cas, la valeur de ce champ varie en fonction du contexte.

Dans le cadre d'une demande-réponse

||Envoyer la demande|Recevoir la demande|Envoyer la réponse|Recevoir la réponse|
|-|------------------|---------------------|----------------|-------------------|
|Dans le cadre d'une couche de modèle de service|Service<br /><br /> Level<br /><br /> Envoyer<br /><br /> Requête|Service<br /><br /> Level<br /><br /> Recevoir<br /><br /> Requête|Service<br /><br /> Level<br /><br /> Envoyer<br /><br /> Répondre|Service<br /><br /> Level<br /><br /> Recevoir<br /><br /> Répondre|
|Dans le cadre d'une couche de transport|Transport<br /><br /> Envoyer|Transport<br /><br /> Recevoir|Transport<br /><br /> Envoyer|Transport<br /><br /> Recevoir|

Dans le cadre d'une demande unidirectionnelle

||Envoyer la demande|Recevoir la demande|
|-|------------------|---------------------|
|Dans le cadre d'une couche de modèle de service|Service<br /><br /> Level<br /><br /> Envoyer<br /><br /> Datagramme|Service<br /><br /> Level<br /><br /> Recevoir<br /><br /> Datagramme|
|Dans le cadre d'une couche de transport|Transport<br /><br /> Envoyer|Transport<br /><br /> Recevoir|

## <a name="message-filters"></a>Filtres de message

Les filtres de message sont définis dans l'élément de configuration `messageLogging` de la section de configuration `diagnostics`. Ils sont appliqués aux niveaux service et transport. Lorsqu'un ou plusieurs filtres sont définis, seuls les messages qui correspondent au moins à l'un des filtres sont enregistrés. Si aucun filtre n'est défini, tous les messages passent.

Les filtres prennent en charge la syntaxe XPath complète et s'appliquent dans l'ordre dans lequel ils apparaissent dans le fichier de configuration. Un filtre syntaxiquement incorrect provoque la levée d'une exception de configuration.

Les filtres fournissent également une fonctionnalité de sécurité qui utilise l’attribut `nodeQuota` et qui limite le nombre maximal de nœuds dans XPath DOM pouvant être examinés pour comparaison avec les filtres définis.

L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.

```xml
<messageLogging logEntireMessage="true"
    logMalformedMessages="true"
    logMessagesAtServiceLevel="true"
    logMessagesAtTransportLevel="true"
    maxMessagesToLog="420">
    <filters>
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
                 /soap:Envelope/soap:Header
        </add>
     </filters>
</messageLogging>
```

Les filtres ne peuvent pas être appliqués au corps d'un message. Les filtres qui tentent de manipuler le corps d'un message sont supprimés de la liste des filtres. Un événement signalant cette suppression est également déclenché. L'exemple de filtre suivant serait supprimé de la table de filtres.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Configuration d'un écouteur personnalisé

Vous pouvez également configurer un écouteur personnalisé en utilisant d'autres options. Un écouteur personnalisé peut être utile pour filtrer les éléments PII spécifiques à l'application des messages avant leur enregistrement. L'exemple de code suivant contient une configuration d'écouteur personnalisé.

```xml
<system.diagnostics>
   <sources>
     <source name="System.ServiceModel.MessageLogging">
           <listeners>
             <add name="MyListener"
                    type="YourCustomListener"
                    initializeData="c:\logs\messages.svclog"
                    maxDiskSpace="1000"/>
           </listeners>
     </source>
   </sources>
</system.diagnostics>
```

N'oubliez pas que l'attribut `type` doit avoir la valeur « nom d'assembly qualifié de ce type ».

## <a name="see-also"></a>Voir aussi

- [\<messageLogging>](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Journalisation des messages](message-logging.md)
- [Paramètres recommandés pour le suivi et l'enregistrement des messages](./tracing/recommended-settings-for-tracing-and-message-logging.md)
