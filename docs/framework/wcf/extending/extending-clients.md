---
title: Extension de clients
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: b3bbbdb895576b4a6d9167bcf321a99d10d378cc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249291"
---
# <a name="extending-clients"></a>Extension de clients

Dans une application appelante, la couche de modèle de service est chargée de traduire les appels de méthode du code d'application en messages sortants, de les envoyer vers les canaux sous-jacents, de retraduire les résultats en valeurs de retour et paramètres de sortie dans le code d'application, et de retourner de nouveau les résultats à l'appelant. Les extensions de modèle de service modifient ou implémentent le comportement et les fonctionnalités d’exécution ou de communication qui impliquent des fonctionnalités de répartiteur ou client, des comportements personnalisés, l’interception de messages et de paramètres, ainsi que d’autres fonctionnalités d’extensibilité.  
  
 Cette rubrique explique comment utiliser les <xref:System.ServiceModel.Dispatcher.ClientRuntime> classes et <xref:System.ServiceModel.Dispatcher.ClientOperation> dans une application cliente Windows Communication Foundation (WCF) pour modifier le comportement d’exécution par défaut d’un client WCF ou pour intercepter ou modifier des messages, des paramètres ou des valeurs de retour avant ou après l’envoi ou la récupération de ces messages à partir de la couche de canal. Pour plus d’informations sur l’extension de l’exécution du service, consultez [extension des répartiteurs](extending-dispatchers.md). Pour plus d’informations sur les comportements qui modifient et insèrent des objets de personnalisation dans l’exécution du client, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Clients  

 Sur un client, un objet client ou un canal client WCF convertit les appels de méthode en messages sortants et en messages entrants en résultats d’opération retournés à l’application appelante. (Pour plus d’informations sur les types de clients, consultez [architecture du client WCF](../feature-details/client-architecture.md).)  
  
 Les types de clients WCF ont des types d’exécution qui gèrent ce point de terminaison et les fonctionnalités au niveau de l’opération. Lorsqu'une application appelle une opération, <xref:System.ServiceModel.Dispatcher.ClientOperation> traduit les objets sortants en message, traite des intercepteurs, confirme que l'appel sortant est conforme au contrat cible, et transmet le message sortant à <xref:System.ServiceModel.Dispatcher.ClientRuntime>, qui est chargé de créer et de gérer des canaux sortants (et canaux entrants dans le cas de services duplex), de gérer le traitement des messages sortants supplémentaires (tel que la modification de l'en-tête), de traiter des intercepteurs de message dans les deux directions, et de router des appels duplex entrants vers l'objet <xref:System.ServiceModel.Dispatcher.DispatchRuntime> côté client approprié. <xref:System.ServiceModel.Dispatcher.ClientOperation> et <xref:System.ServiceModel.Dispatcher.ClientRuntime> fournissent tous deux des services similaires lorsque les messages (y compris les erreurs) sont retournés au client.  
  
 Ces deux classes d’exécution constituent l’extension principale permettant de personnaliser le traitement des objets et des canaux du client WCF. La classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> permet aux utilisateurs d'intercepter et d'étendre l'exécution du client sur l'ensemble des messages du contrat. La classe <xref:System.ServiceModel.Dispatcher.ClientOperation> permet aux utilisateurs d'intercepter et d'étendre l'exécution du client pour tous les messages d'une opération donnée.  
  
 La modification des propriétés ou l'insertion de personnalisations sont effectuées en utilisant des comportements de contrat, de point de terminaison et d'opération. Pour plus d’informations sur l’utilisation de ces types de comportements pour effectuer des personnalisations de l’exécution du client, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scénarios  

 L'extension du système client peut être justifiée pour un certain nombre de raisons, dont les suivantes :  
  
- Validation personnalisée des messages. Un utilisateur souhaite s'assurer qu'un message est valide pour un schéma spécifique. Cela peut être accompli en implémentant l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> et en assignant l'implémentation à la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>. Pour obtenir des exemples, consultez [Comment : inspecter ou modifier des messages sur le client](how-to-inspect-or-modify-messages-on-the-client.md) et [Comment : inspecter ou modifier des messages sur le client](how-to-inspect-or-modify-messages-on-the-client.md).  
  
- Enregistrement personnalisé des messages. Un utilisateur souhaite inspecter et enregistrer des jeux de messages d'application qui transitent par un point de terminaison. Cela peut également être accompli à l'aide des interfaces de l'intercepteur de messages.  
  
- Transformations personnalisées des messages. Plutôt que de modifier le code d'application, l'utilisateur souhaite appliquer certaines transformations au message dans l'exécution (pour le contrôle de version par exemple). Cela peut, à nouveau, être accompli à l'aide des interfaces de l'intercepteur de messages.  
  
- Modèle personnalisé de données. Un utilisateur peut souhaiter avoir un modèle de données ou de sérialisation autre que celui pris en charge par défaut dans WCF (à savoir les objets,, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> et <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> ). Cela peut être accompli en implémentant les interfaces du formateur de messages. Pour plus d'informations, consultez <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> et la propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType>.  
  
- Validation personnalisée des paramètres. Un utilisateur souhaite que les paramètres typés soient valides (par opposition à XML). Cela peut être accompli à l'aide des interfaces de l'inspecteur de paramètres. Pour obtenir un exemple, consultez [Comment : inspecter ou modifier des paramètres ou la](how-to-inspect-or-modify-parameters.md) validation du [client](../samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Utilisation de la classe ClientRuntime  

 La classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> est un point d’extensibilité auquel vous pouvez ajouter des objets d’extension qui interceptent des messages et étendent le comportement du client. Les objets d'interception peuvent traiter tous les messages d'un contrat spécifique, traiter uniquement les messages de certaines opérations, exécuter l'initialisation de canal personnalisée et implémenter un autre comportement d'application cliente personnalisé.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> retourne l'objet d'exécution de répartition pour les clients de rappel initiés par le service.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> accepte un objet de sélecteur d'opération personnalisé.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> permet d'ajouter un initialiseur de canal qui peut inspecter ou modifier le canal client.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> obtient une collection d’objets <xref:System.ServiceModel.Dispatcher.ClientOperation> auxquels vous pouvez ajouter des intercepteurs de messages personnalisés qui fournissent les fonctionnalités spécifiques aux messages de cette opération.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> permet à une application de désactiver certains en-têtes d'adressage automatique afin de contrôler directement l'adressage.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> affecte la valeur de la destination du message au niveau du transport afin de prendre en charge les intermédiaires et d'autres scénarios.  
  
- La <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> propriété obtient une collection d' <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> objets auxquels vous pouvez ajouter des intercepteurs de messages personnalisés pour tous les messages qui transitent par un client WCF.  
  
 Par ailleurs, un certain nombre d'autres propriétés récupèrent les informations de contrat :  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Si le client WCF est un client WCF duplex, les propriétés suivantes récupèrent également les informations du client WCF de rappel :  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Pour étendre l’exécution du client WCF à travers un client WCF entier, passez en revue les propriétés disponibles sur la <xref:System.ServiceModel.Dispatcher.ClientRuntime> classe pour voir si la modification d’une propriété ou l’implémentation d’une interface et son ajout à une propriété crée les fonctionnalités que vous recherchez. Après avoir choisi l'extension spécifique à générer, insérez-la dans la propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime> appropriée en implémentant un comportement client permettant d'accéder à la classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> en cas d'appel.  
  
 Vous pouvez insérer des objets d'extension personnalisés dans une collection à l'aide d'un comportement d'opération (objet qui implémente <xref:System.ServiceModel.Description.IOperationBehavior>), d'un comportement de contrat (objet qui implémente <xref:System.ServiceModel.Description.IContractBehavior>) ou d'un comportement de point de terminaison (objet qui implémente <xref:System.ServiceModel.Description.IEndpointBehavior>). L'objet de comportement installé est ajouté à la collection appropriée de comportements par programme ou de façon déclarative (en implémentant un attribut personnalisé), ou en implémentant un objet <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> personnalisé pour que le comportement soit inséré à l'aide d'un fichier de configuration d'application. Pour plus d’informations, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Pour obtenir des exemples qui illustrent l’interception sur un client WCF, consultez [Comment : inspecter ou modifier des messages sur le client](how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Utilisation de la classe ClientOperation  

 La classe <xref:System.ServiceModel.Dispatcher.ClientOperation> correspond à l’emplacement des modifications d’exécution du client et au point d’insertion des extensions personnalisées qui sont limitées à une seule opération de service. (Pour modifier le comportement d'exécution du client pour tous les messages d'un contrat, utilisez la classe <xref:System.ServiceModel.Dispatcher.ClientRuntime>.)  
  
 Utilisez la propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> pour localiser l'objet <xref:System.ServiceModel.Dispatcher.ClientOperation> qui représente une opération de service particulière. Les propriétés suivantes vous permettent d’insérer des objets personnalisés dans le système client WCF :  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> permet d'insérer une implémentation <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> personnalisée pour une opération ou de modifier le formateur actuel.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> permet d'insérer une implémentation <xref:System.ServiceModel.Dispatcher.IParameterInspector> personnalisée ou de modifier l'implémentation actuelle.  
  
 Les propriétés suivantes vous permettent de modifier le système dans l'interaction à l'aide du formateur et des inspecteurs de paramètre personnalisés :  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> permet de contrôler la sérialisation d'un message sortant.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> permet de contrôler la désérialisation d’un message entrant.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> permet de contrôler l'action WS-Addressing du message de demande.  
  
- Utilisez <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> et <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> pour spécifier les méthodes clientes WCF associées à une opération asynchrone.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> permet d’obtenir une collection contenant les types qui peuvent apparaître dans les erreurs SOAP comme type de détail.  
  
- Les propriétés <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> et <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> permettent respectivement de contrôler si une session est initiée ou détruite, lorsque l'opération est appelée.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> permet de contrôler si l'opération est monodirectionnelle.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> permet d'obtenir l'objet contenant <xref:System.ServiceModel.Dispatcher.ClientRuntime>.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> permet d'obtenir le nom de l'opération.  
  
- La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> permet de contrôler la méthode mappée à l'opération.  
  
 Pour étendre l’exécution du client WCF sur une seule opération de service, passez en revue les propriétés disponibles sur la <xref:System.ServiceModel.Dispatcher.ClientOperation> classe pour voir si la modification d’une propriété ou l’implémentation d’une interface et l’ajout de celle-ci à une propriété crée les fonctionnalités que vous recherchez. Après avoir choisi l'extension spécifique à générer, insérez-la dans la propriété <xref:System.ServiceModel.Dispatcher.ClientOperation> appropriée en implémentant un comportement client permettant d'accéder à la classe <xref:System.ServiceModel.Dispatcher.ClientOperation> en cas d'appel. Dans ce comportement, vous pouvez ensuite modifier la propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime> en fonction de vos besoins.  
  
 En général, l'implémentation d'un comportement d'opération (objet qui implémente l'interface <xref:System.ServiceModel.Description.IOperationBehavior> ) suffit, mais vous pouvez également utiliser des comportements de point de terminaison et de contrat en localisant le <xref:System.ServiceModel.Description.OperationDescription> d'une opération spécifique et en joignant le comportement à cet emplacement. Pour plus d’informations, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Pour utiliser votre comportement personnalisé à partir de la configuration, installez-le à l'aide d'un gestionnaire de section de configuration de comportement personnalisé. Vous pouvez également l'installer en créant un attribut personnalisé.  
  
 Pour obtenir des exemples qui illustrent l’interception sur un client WCF, consultez [Comment : inspecter ou modifier des paramètres](how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Procédure : inspecter ou modifier des messages sur le client](how-to-inspect-or-modify-messages-on-the-client.md)
- [Procédure : inspecter ou modifier des paramètres](how-to-inspect-or-modify-parameters.md)
