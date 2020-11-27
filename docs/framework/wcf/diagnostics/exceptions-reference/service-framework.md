---
title: Infrastructure de service
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 1fb39f2106e027cc5d4125cfb0bc89f3e5983cec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285718"
---
# <a name="service-framework"></a>Infrastructure de service

Cette rubrique répertorie toutes les exceptions générées par les données d'infrastructure de service.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Une instance de liaison a déjà été associée pour l’écoute de l’URI spécifié. Si deux points de terminaison veulent partager la même adresse ListenUri, ils doivent également partager la même instance de l'objet de liaison. Les deux points de terminaison en conflit ont soit été spécifiés dans des appels AddServiceEndpoint() au niveau d'un fichier de configuration, soit été une combinaison de AddServiceEndpoint() et de la configuration.|  
|AChannelServiceEndpointIsNull0|Un point de terminaison de canal ou de service est de valeur null.|  
|AChannelServiceEndpointSContractSNameIsNull0|Un nom de contrat de point de terminaison de canal ou de service est de valeur null ou vide.|  
|AChannelServiceEndpointSContractSNamespace0|Un espace de noms de contrat de point de terminaison de c anal ou de service est de valeur null.|  
|BaseAddressCannotHaveFragment|Une adresse de base ne peut pas contenir de fragment d'URI.|  
|BaseAddressCannotHaveQuery|Une adresse de base ne peut pas contenir de chaîne de requête d'URI.|  
|BaseAddressCannotHaveUserInfo|Une adresse de base ne peut pas contenir de section d'information utilisateur d'URI.|  
|BaseAddressDuplicateScheme|Cette collection contient déjà une adresse avec le schéma spécifié. Une seule adresse est autorisée pour chaque schéma dans cette collection.|  
|BaseAddressMustBeAbsolute|Seul un URI absolu peut être utilisé comme adresse de base.|  
|BindingDoesnTSupportAnyChannelTypes1|La liaison spécifiée ne gère pas la création de types de canaux. Les éléments BindingElements dans une liaison personnalisée ont été empilés de façon incorrecte ou sont dans le mauvais ordre. Un élément de transport est requis au bas de la pile. L'ordre recommandé pour les éléments de liaison est : TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.|  
|BindingDoesnTSupportDuplexButContractRequires1|Le contrat exige le mode Duplex. La liaison spécifiée ne le prend pas en charge ou elle n'est pas configurée correctement pour cela.|  
|BindingDoesnTSupportOneWayButContractRequires1|Le contrat exige le mode OneWay. La liaison spécifiée ne le prend pas en charge ou elle n'est pas configurée correctement pour cela.|  
|BindingDoesnTSupportRequestReplyButContract1|Le contrat exige le mode Request/Reply. La liaison spécifiée ne le prend pas en charge ou elle n'est pas configurée correctement pour cela.|  
|BindingDoesnTSupportSessionButContractRequires1|Le contrat exige le mode Session.  La liaison spécifiée ne le prend pas en charge ou elle n'est pas configurée correctement pour cela.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Le contrat exige le mode TwoWay (soit demande-réponse, soit duplex). La liaison spécifiée ne le prend pas en charge ou elle n'est pas configurée correctement pour cela.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|DeliveryRequirementsAttribute n'autorise pas QueuedDelivery. La liaison pour le point de terminaison avec le contrat spécifié prend cet élément en charge.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|DeliveryRequirementsAttribute requiert QueuedDelivery. La liaison pour le point de terminaison avec le contrat spécifié ne le prend pas en charge ou elle n’est pas configurée correctement pour cela.|  
|channelDoesNotHaveADuplexSession0|Le canal actuel ne prend pas en charge la fermeture de la session de sortie. Ce canal n’implémente pas ISessionChannel \<IDuplexSession> .|  
|ClientRuntimeRequiresFormatter0|Le ClientOperation spécifié requiert un formateur car SerializeRequest et DeserializeReply ne sont pas tous les deux false.|  
|CommunicationObjectAborted1|L'objet de communication spécifié ne peut pas être utilisé pour la communication car il a été arrêté.|  
|CommunicationObjectAbortedStack2|L’objet de communication spécifié ne peut pas être utilisé pour la communication car il a été arrêté : {1}|  
|CommunicationObjectBaseClassMethodNotCalled|L’objet de communication spécifié a remplacé la fonction virtuelle, {1} mais il n’appelle pas la version définie dans la classe de base.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Le contrat spécifié contient une ou plusieurs opérations IsTerminating ou non-IsInitiating. Sa propriété SessionMode n'a pas la valeur SessionMode.Required. Les attributs IsInitiating et IsTerminating peuvent être utilisés uniquement dans le contexte d'une session.|  
|CouldnTCreateChannelForChannelType2|Le type de canal spécifié a été demandé, mais la liaison spécifiée ne le prend pas en charge ou n'est pas configurée correctement pour cela.|  
|DispatchRuntimeRequiresFormatter0|Le DispatchOperation spécifié requiert un formateur car DeserializeRequest et SerializeReply ne sont pas tous les deux false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|La méthode End ne peut pas être utilisée avec OperationContractAttribute lors de l’utilisation du modèle de conception IAsyncResult. Seule la méthode Begin correspondante peut être utilisée avec OperationContractAttribute. Cet attribut s'applique à la paire de méthodes Begin-End.|  
|EndpointListenerRequirementsCannotBeMetBy3|Les exigences ChannelDispatcher ne peuvent pas être satisfaites par l’élément IChannelListener pour la liaison spécifiée car le contrat requiert la prise en charge de l’un de ces types de canaux spécifiés. Or la liaison ne prend en charge que ces types de canaux spécifiés.|  
|EndpointsMustHaveAValidBinding0|Les points de terminaison doivent avoir une liaison valide.|  
|InvalidOrUnrecognizedAction|Le message ne peut pas être traité car l'action spécifiée est non valide ou non reconnue.|  
|MultipleMebesInParameters|Plusieurs éléments MessageEncodingBindingElement ont été trouvés dans les paramètres BindingParameters du contexte BindingContext. CustomBinding ne peut pas avoir plusieurs MessageEncodingBindingElements. Supprimez tous ces éléments sauf un.|  
|MultipleStreamUpgradeProvidersInParameters|Plusieurs éléments IStreamUpgradeProviderElement ont été trouvés dans les paramètres BindingParameters du contexte BindingContext. CustomBinding ne peut pas avoir plusieurs IStreamUpgradeProviderElements. Supprimez tous ces éléments sauf un.|  
|NoChannelBuilderAvailable|La liaison ne peut pas être utilisée pour créer une fabrication de canal ou un écouteur de canal car elle n’a pas de TransportBindingElement. Chaque liaison doit avoir au moins un élément de liaison qui dérive de TransportBindingElement.|  
|NotAllBindingElementsBuilt|Certains des éléments de liaison dans cette liaison n'ont pas été utilisés lors de la génération de la fabrication de canal et de l'écouteur de canal. Les éléments de liaison ne sont pas ordonnés correctement. L'ordre recommandé pour les éléments de liaison est : TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.  Notez que le TransportBindingElement doit être mentionné en dernier. Les éléments de liaison spécifiés n’ont pas été générés.|  
|RuntimeRequiresInvoker0|L'opération de répartition requiert un demandeur.|  
|ServiceHasZeroAppEndpoints|Le service spécifié ne possède aucun point de terminaison d'application (non infrastructure). Cela peut être dû au fait qu'aucun fichier de configuration n'a été trouvé pour votre application, qu'aucun élément de service correspondant au nom du service n'a été trouvé dans le fichier de configuration ou qu'aucun point de terminaison n'a été défini dans l'élément de service.|  
|SFxActionMismatch|Impossible de créer un message typé en raison d'une incompatibilité d'action. L'action spécifiée était attendue, mais une autre a été rencontrée.|  
|SFxAnonymousTypeNotSupported|La partie spécifiée dans le message spécifié ne peut pas être exportée avec RPC ou encodée car son type est anonyme.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|L'URL fournie à ServiceMetadataBehavior via la propriété ExternalMetadataLocation ou l'attribut externalMetadataLocation dans la section serviceMetadata de la configuration était une URL relative et aucune adresse de base n'est disponible pour la résoudre.|  
|SFxBadMetadataMustBePolicy|Vous devez fournir un XmlElement de stratégie qui a l'espace de noms et le nom spécifiés. Ce XmlElement a l'espace de noms et le nom spécifiés.|  
|SFxBodyObjectTypeCannotBeInherited|Le type spécifié ne peut hériter d'aucune classe autre que l'objet à utiliser en tant qu'objet corps dans le style RPC.|  
|SFxBodyObjectTypeCannotBeInterface|Le type spécifié implémente l'interface spécifiée, qui n'est pas prise en charge pour l'objet corps dans le style RPC.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|CallbackBehaviorAttribute peut être exécuté uniquement en tant que comportement sur un point de terminaison avec un contrat duplex. Le contrat spécifié n'est pas duplex car il ne contient aucune opération de rappel.|  
|SFxCallbackRequestReplyInOrder1|La réponse à cette opération ne peut pas être reçue tant que le traitement du message en cours n'est pas terminé. Si vous souhaitez autoriser le traitement des messages dans le désordre, spécifiez ConcurrencyMode de Reentrant ou Multiple sur le spécifié.|  
|SfxCallbackTypeCannotBeNull|Pour utiliser le contrat spécifié avec DuplexChannelFactory, le contrat doit spécifier un contrat de rappel valide. Si votre contrat a un contrat de rappel, utilisez ChannelFactory au lieu de DuplexChannelFactory.|  
|SFxCannotGetMetadataFromLocation|MetadataExchangeClient peut obtenir des métadonnées uniquement à partir d'emplacements MetadataLocations http et https. Il ne peut pas obtenir de métadonnées à partir de l'adresse spécifiée.|  
|SFxCannotHttpGetMetadataFromAddress|MetadataExchangeClient peut obtenir des métadonnées uniquement à partir d'adresses HTTP et HTTPS lors de l'utilisation de MetadataExchangeClientMode HttpGet. Il ne peut pas obtenir de métadonnées à partir de l'adresse spécifiée.|  
|SFxCannotImportAsParameters_Bare|Génération d'un contrat de message car l'opération spécifiée n'est ni RPC, ni encapsulée dans un document.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Génération d'un contrat de message car le nom du wrapper du message spécifié ne correspond pas à la valeur par défaut.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Génération d'un contrat de message car l'espace de nom du wrapper du message spécifié ne correspond pas à la valeur par défaut.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Génération d'un contrat de message car le nom d'élément spécifié de l'espace de noms spécifié n'est pas marqué nillable.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Génération d'un contrat de message car le message spécifié a des en-tête.|  
|SFxCannotImportAsParameters_Message|Génération d’un contrat de message car l’opération spécifiée a un message non typé comme argument ou type de retour.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Génération d'un contrat de message car le message spécifié requiert une protection.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Génération d'un contrat de message car l'espace de nom de la partie du message spécifiée ne correspond pas à la valeur par défaut.|  
|SFxCannotRequireBothSessionAndDatagram3|Le contrat spécifié spécifie SessionMode.NotAllowed et le contrat spécifié spécifie SessionMode.Required. Modifiez l'une des valeurs SessionMode ou spécifiez une adresse différente, ou ListenURI, pour chaque point de terminaison.|  
|SFxCannotSetExtensionsByIndex|Cette collection ne prend pas en charge la définition d’extensions par index. Utilisez les méthodes InsertItem ou RemoveItem.|  
|SFxChannelDispatcherDifferentHost0|Le ChannelDispatcher n'est pas actuellement attaché au ServiceHost fourni.|  
|SFxChannelDispatcherMultipleHost0|Le ChannelDispatcher ne peut pas être ajouté à plusieurs ServiceHost.|  
|SFxChannelDispatcherNoHost0|Le ChannelDispatcher ne peut pas être ouvert car il n'est pas attaché à un ServiceHost.|  
|SfxChannelFactoryDisposed|Ce ChannelFactory ne peut pas être ouvert car le ChannelFactory a déjà été éliminé. Créez à nouveau le ChannelFactory avant de l'utiliser.|  
|SFxChannelFactoryNoBinding|Le ChannelFactory ne peut pas être ouvert car aucune liaison n'a été associée à son point de terminaison. Spécifiez une liaison avec le constructeur ou la propriété de point de terminaison.|  
|SFxChannelTerminated0|Une opération marquée comme IsTerminating a déjà été appelée sur ce canal, provoquant l'interruption de la connexion du canal. Aucune opération supplémentaire ne peut être appelée sur ce canal. Créez à nouveau le canal pour poursuivre la communication.|  
|SFxCloseTimedOut1|L'opération de fermeture de ServiceHost s'est arrêtée après le spécifié. Ceci peut être dû à un client qui n'a pas fermé un canal de session dans le délai imparti. Le temps alloué à cette opération fait peut-être partie d'un délai d'attente plus long.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|Le processus de fermeture a dépassé le délai imparti en attendant la fin de la distribution du service.|  
|SFxCodeGenIsNotAssignableFrom|Le spécifié ne peut pas être assigné.|  
|SFxConfigChannelConfigurationNotFound|L'élément de point de terminaison avec le nom et le contrat spécifiés dans la section de configuration client ServiceModel est introuvable.|  
|SFxConflictingGlobalElement|L'élément Extensible Markup Language de niveau supérieur avec le nom spécifié dans l'espace de noms spécifié ne peut pas faire référence au type spécifié. Il fait déjà référence à un type différent. Utilisez un autre nom d'opération ou MessageBodyMemberAttribute pour spécifier un autre nom pour le message ou les parties de message.|  
|SFxContractHasZeroInitiatingOperations|Un contrat doit avoir au moins une opération IsInitiating=true.|  
|SFxContractHasZeroOperations|Un contrat doit avoir au moins une opération.|  
|SFxContractInheritanceRequiresInterfaces|La classe de service du type spécifié définit un ServiceContract et hérite d'un ServiceContract du type spécifié. L'héritage de contrat est utilisable uniquement parmi les types d'interface. Si une classe est marquée avec ServiceContractAttribute, elle doit être le seul type de la hiérarchie avec ServiceContractAttribute.  Déplacez l'attribut ServiceContractAttribute sur le type spécifié vers une interface distincte implémentée par le type spécifié.|  
|SFxCreateDuplexChannel1|Le contrat de rappel du contrat spécifié n'existe pas ou ne définit pas d'opérations. S'il ne s'agit pas d'un contrat duplex, utilisez ChannelFactory au lieu de DuplexChannelFactory.|  
|SFxCreateDuplexChannelNoCallback|Cette surcharge de CreateChannel ne peut pas être appelée sur cette instance de DuplexChannelFactory. DuplexChannelFactory n'a pas été initialisé avec un InstanceContext. Appelez la surcharge CreateChannel qui prend un InstanceContext.|  
|SFxCreateDuplexChannelNoCallback1|Cette surcharge de CreateChannel ne peut pas être appelée sur cette instance de DuplexChannelFactory. DuplexChannelFactory a été initialisé avec un Type et aucun InstanceContext valide n'a été fourni. Appelez la surcharge CreateChannel qui prend un InstanceContext.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Cette surcharge de CreateChannel ne peut pas être appelée sur cette instance de DuplexChannelFactory. L'InstanceContext fourni au DuplexChannelFactory ne contient pas de UserObject valide.|  
|SFxCreateNonDuplexChannel1|ChannelFactory ne prend pas en charge le contrat spécifié. ChannelFactory définit un contrat de rappel avec une ou plusieurs opérations. Utilisez DuplexChannelFactory au lieu de ChannelFactory.|  
|SFxCustomBindingNeedsTransport1|CustomBinding sur le ServiceEndpoint avec le contrat spécifié ne contient pas de TransportBindingElement. Chaque liaison doit avoir au moins un élément de liaison qui dérive de TransportBindingElement.|  
|SFxCustomBindingWithoutTransport|Le schéma ne peut pas être calculé pour cette liaison car cette liaison personnalisée ne contient pas de TransportBindingElement. Chaque liaison doit avoir au moins un élément de liaison qui dérive de TransportBindingElement.|  
|SFxDataContractSerializerDoesNotSupportBareArray|DataContractSerializer ne prend pas en charge la collection spécifiée sur l'élément spécifié.|  
|SFxDictionaryIsEmpty|L'opération ne peut pas être exécutée car le dictionnaire est vide.|  
|SFxDocEncodedNotSupported|Erreur lors de la réflexion du spécifié. Document-Encoded n'est pas pris en charge. Modifiez 'Use' à Literal ou 'style' à RPC.|  
|SFxDuplicateInitiatingActionAtSameVia|Ce service possède plusieurs points de terminaison qui écoutent le spécifié. Les points de terminaison partagent la même action de départ spécifiée. Les messages comportant cette action seront supprimés, car le distributeur ne pourra pas déterminer le point de terminaison correct pour le traitement du message.|  
|SFXEndpointBehaviorUsedOnWrongSide|L'IEndpointBehavior spécifié ne peut pas être utilisé sur le serveur. Ce comportement ne peut s'appliquer qu'à des clients.|  
|SFxEndpointNoMatchingScheme|L'adresse de base qui correspond au schéma spécifié pour le point de terminaison à la liaison spécifiée est introuvable. Les schémas d'adresse de base inscrits sont spécifiés.|  
|SFxErrorCreatingMtomReader|Une erreur s'est produite lors de la création d'un lecteur pour le message du mécanisme d'optimisation de transmission de message.|  
|SFxErrorDeserializingFault|Le serveur a retourné une erreur de protocole SOAP non valide. Pour plus d’informations, consultez InnerException. »|  
|SFxErrorDeserializingHeader|Une erreur s'est produite lors de la désérialisation de l'un des en-têtes dans le message spécifié. Consultez InnerException pour plus de détails.|  
|SFxErrorReflectingOnMethod3|Une erreur s'est produite lors du chargement de l'attribut spécifié sur la méthode spécifiée dans le type spécifié.  Pour plus d’informations, consultez InnerException. »|  
|SFxErrorReflectingOnParameter4|Une erreur s'est produite lors du chargement de l'attribut spécifié sur le paramètre spécifié de la méthode spécifiée dans le type spécifié. Pour plus d’informations, consultez InnerException. »|  
|SFxErrorReflectingOnType2|Une erreur s'est produite lors du chargement de l'attribut spécifié sur le type spécifié.  Pour plus d’informations, consultez InnerException. »|  
|SFxErrorSerializingBody|Une erreur s'est produite lors de la sérialisation du corps du message spécifié. Pour plus d’informations, consultez InnerException. »|  
|SFxErrorSerializingHeader|Une erreur s'est produite lors de la sérialisation de l'un des en-têtes dans le message spécifié. Pour plus d’informations, consultez InnerException. »|  
|SFxExpectedIMethodCallMessage|Erreur interne. Le message doit être un IMethodCallMessage valide.|  
|SFxExportMustHaveType|La partie spécifiée dans l'opération spécifiée ne peut pas être exportée car elle n'a pas de type CLR valide.|  
|SFxHeaderNotUnderstood|Le message n'a pas été traité. L'en-tête spécifié de l'espace de noms spécifié n'a pas été compris par le destinataire de ce message. Cette erreur indique en général que l'expéditeur de ce message a activé un protocole de communication que le récepteur ne peut pas traiter. Vérifiez que la configuration de la liaison du client correspond à la liaison du service.|  
|SFxHeadersAreNotSupportedInEncoded|Le message spécifié ne doit pas contenir d'en-tête à utiliser dans le style encodé RPC.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Toutes les parties du message dans l'opération spécifiée doivent contenir un type ou un élément.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|Le style spécifié déduit des messages dans l’opération spécifiée ne correspond pas au style attendu spécifié indiqué via les liaisons.|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult n'est pas fourni ou est du type incorrect.|  
|SFxInvalidMessageBody|OperationFormatter a rencontré un corps de message non valide. Le type de nœud 'Element' avec le nom et l'espace de noms spécifiés était attendu. Le type de nœud spécifié avec le nom et l'espace de noms spécifiés a été trouvé.|  
|SFxInvalidMessageBodyEmptyMessage|L'OperationFormatter ne peut pas désérialiser d'informations du message car le message est vide.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Une erreur s'est produite lors de la tentative de désérialisation du paramètre spécifié. Consultez InnerException pour plus de détails.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Une erreur s'est produite lors de la tentative de sérialisation du paramètre spécifié. Le message InnerException a été spécifié.  Pour plus d’informations, consultez InnerException. »|  
|SFxInvalidMessageBodyUnexpectedNode|Le nœud inattendu spécifié de l'espace de noms spécifié a été rencontré lors de la désérialisation des paramètres.|  
|SFxInvalidMessageContractSignature|L’opération spécifiée a un paramètre ou un type de retour marqué avec le MessageContractAttribute. Lors de l'utilisation d'un contrat de message pour représenter un message de demande, l'opération doit avoir un paramètre unique marqué avec le MessageContractAttribute. Lors de l'utilisation d'un contrat de message pour représenter le message de réponse, la valeur de retour de l'opération doit être un type marqué avec le MessageContractAttribute. L'opération ne peut pas contenir de paramètres 'out' ou 'ref'.|  
|SFxInvalidReplyAction|Le message de réponse sortant pour l'opération a l'Action spécifiée, mais le contrat pour cette opération spécifie un autre ReplyAction. L'Action spécifiée dans le message doit correspondre au ReplyAction dans le contrat, ou le contrat d'opération doit spécifier ReplyAction= '*'.|  
|SFxInvalidRequestAction|Le message de demande sortant pour l'opération a l'Action spécifiée, mais le contrat pour cette opération spécifie un autre RequestAction. L'Action spécifiée dans le message doit correspondre au RequestAction dans le contrat, ou le contrat d'opération doit spécifier RequestAction= '*'.|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|La méthode statique CreateChannel ne peut pas être utilisée avec le contrat spécifié car ce dernier définit un contrat de rappel. Utilisez l’une des surcharges CreateChannel statiques sur DuplexChannelFactory \<TChannel> .|  
|SFxInvalidStreamInRequest|Pour que la demande dans l'opération spécifiée soit un flux, l'opération doit avoir un paramètre unique dont le type est Stream.|  
|SFxInvalidStreamInResponse|Pour que la réponse dans l'opération spécifiée soit un flux, l'opération doit avoir un paramètre de sortie ou une valeur de retour unique dont le type est Stream.|  
|SFxInvalidStreamInTypedMessage|Pour utiliser des flux avec le modèle de programmation Contrat de message, le type spécifié doit avoir un membre MessageBody unique dont le type est Stream.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|PrimitiveOperationFormatter ne prend pas en charge un paramètre ou un type de retour qui lui a été attribué.|  
|SFxMessageContractBaseTypeNotValid|Le type spécifié définit un MessageContract et dérive d'un type spécifié qui ne définit pas de MessageContract. Tous les objets dans la hiérarchie d'héritage spécifiée doivent définir un MessageContract.|  
|SFxMethodNotSupported1|La méthode spécifiée n'est pas prise en charge sur cet objet. Cela peut arriver si la méthode n'est pas marquée avec OperationContractAttribute ou si le type d'interface n'est pas marqué avec ServiceContractAttribute.|  
|SFxMethodNotSupportedByType2|Le type d'implémentation ServiceHost spécifié n'implémente pas le contrat de service spécifié.|  
|SFxMethodNotSupportedOnCallback1|La méthode de rappel spécifiée n'est pas prise en charge. Cela peut arriver si la méthode n'est pas marquée avec OperationContractAttribute ou si son type d'interface n'est pas la cible du CallbackContract ServiceContractAttribute.|  
|SFxMismatchedOperationParent|Une opération DispatchOperation (ou ClientOperation) peut être ajoutée uniquement à son parent DispatchRuntime (ou ClientRuntime).|  
|SFxNameCannotBeEmpty|La propriété Name ne peut pas être une chaîne vide.|  
|SfxNoTypeSpecifiedForParameter|Aucun type CLR n'a été spécifié pour le paramètre, ce qui empêche l'opération d'être générée.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute peut aller uniquement sur la classe de service. Il ne peut pas être mis sur l'interface de ServiceContract. La méthode spécifiée sur le type spécifié ne respecte pas cette condition.|  
|SFxOperationContractOnNonServiceContract|La méthode spécifiée est marquée avec OperationContractAttribute, mais le type spécifié englobant n'est pas marqué avec ServiceContractAttribute. OperationContractAttribute peut être utilisé uniquement sur les méthodes dans les types ServiceContractAttribute ou sur leurs types CallbackContract.|  
|SFxParameterCountMismatch|Une incompatibilité entre le nombre d'arguments fournis et le nombre d'arguments attendus s'est produite. Spécifiquement, l’argument spécifié a le nombre d’éléments spécifié, alors que l’argument attendu a le nombre d’éléments spécifié.|  
|SFxPartNameMustBeUniqueInRpc|Le nom de partie de message spécifié n'est pas unique dans un message RPC.|  
|SFxReplyActionMismatch3|Un message de réponse a été reçu pour l'opération spécifiée avec l'action spécifiée. Toutefois, votre code client requiert l'action spécifiée.|  
|SFxRequestReplyNone|Un message a été reçu avec un en-tête WS-Addressing ReplyTo ou FaultTo ciblé sur l'adresse « None ». Ces valeurs ne sont pas valides pour les opérations demande-réponse. Utilisez une opération monodirectionnelle ou activez ManualAddressing si vous devez prendre en charge les valeurs ReplyTo ou FaultTo définies sur « None ».|  
|SFxRequestTimedOut1|Cette opération de demande n'a pas reçu de réponse dans le délai imparti. Le temps alloué fait peut-être partie d'un délai d'attente plus long. Ceci peut être dû au fait que le service est toujours en cours de traitement de l'opération ou qu'il n'a pas pu envoyer un message de réponse.|  
|SFxRequestTimedOut2|L'opération de demande envoyée à l'emplacement spécifié n'a pas reçu de réponse dans le délai imparti. Le temps alloué fait peut-être partie d'un délai d'attente plus long. Ceci peut être dû au fait que le service est toujours en cours de traitement de l'opération ou qu'il n'a pas pu envoyer un message de réponse.|  
|SFxSchemaDoesNotContainType|Le schéma avec l'espace de noms cible spécifié ne contient pas de type avec le nom spécifié.|  
|SfxServiceContractAttributeNotFound|Le type de contrat spécifié n'est pas attribué avec ServiceContractAttribute. Pour définir un contrat valide, le type spécifié doit être attribué avec ServiceContractAttribute. Le type peut être une interface de contrat ou une classe de service.|  
|SFxServiceContractGeneratorConfigRequired|Pour générer des informations de configuration à l'aide de la méthode GenerateServiceEndpoint, l'instance ServiceContractGenerator doit être initialisée avec un objet Configuration valide.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|Les points de terminaison ne peuvent pas être ajoutés après que le ServiceHost a été dans l'un des états suivants :<br /><br /> -Ouvert<br />-Erreur<br />-Terminé<br />-Fermé|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Les points de terminaison ne peuvent pas être ajoutés avant que la propriété Description ne soit initialisée.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|La propriété HttpGetEnabled de ServiceMetadataBehavior a la valeur true et la propriété HttpGetUrl est une adresse relative, mais il n'y a aucune adresse de base HTTP. Fournissez une adresse de base HTTP ou définissez HttpGetUrl en tant qu'adresse absolue.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|La propriété HttpsGetEnabled de ServiceMetadataBehavior a la valeur true et la propriété HttpsGetUrl est une adresse relative, mais il n'y a aucune adresse de base HTTPS. Fournissez une adresse de base HTTPS ou définissez HttpsGetUrl en tant qu'adresse absolue.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|L'URL de comportement doit être un URI relatif ou un URI absolu avec le schéma spécifié. L'URL spécifié est un URI absolu avec le schéma spécifié.|  
|SFxStreamRequestMessageClosed|Le message qui contient ce flux a été fermé. Les flux de demande ne sont pas accessibles après le renvoi de l'opération de service.|  
|SFxStreamResponseMessageClosed|Le message qui contient ce flux a été fermé.|  
|SFxTerminateRequestProcessingException|Une extension dans le pipeline d’opération doit quitter le traitement de ce message.|  
|SFxTerminatingOperationAlreadyCalled1|Ce canal ne peut plus envoyer de messages car l'opération IsTerminating a été appelée.|  
|SFxThrottleLimitMustBeGreaterThanZero0|La limite d'accélérateur doit être supérieure à zéro. Pour la désactiver, définissez-la sur Int32.MaxValue.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|Lors de l'utilisation du style encodé RPC, les types de contrat de message ou le type System.ServiceModel.Channels.Message ne peuvent pas être utilisés si l'opération ne contient aucun paramètre ou contient une valeur de retour vide. Ajoutez un type de contrat de message vierge en tant que paramètre ou type de retour à l’opération spécifiée.|  
|SFxUserCodeThrewException|L'opération d'utilisateur spécifiée a levé une exception qui n'est pas prise en charge dans le code utilisateur. S'il s'agit d'un problème récurrent, cela peut indiquer une erreur dans l'implémentation de la méthode spécifiée.|  
|SfxUseTypedMessageForCustomAttributes|Le paramètre spécifié ne peut pas être mappé au paramètre d'opération car il requiert des attributs supplémentaires.|  
|SFxVersionMismatchInOperationContextAndMessage2|Impossible d'ajouter des en-têtes sortants au message car MessageVersion dans OperationContext.Current ne correspond pas à la version d'en-tête de message qui est traitée.|  
|SFxWellKnownNonSingleton0|Pour utiliser l'un des constructeurs ServiceHost qui prend une instance de service, l'InstanceContextMode du service doit être défini sur InstanceContextMode.Single. Ceci peut être configuré via ServiceBehaviorAttribute. Sinon, utilisez les constructeurs ServiceHost qui prennent un argument Type.|  
|SFxWrapperTypeHasMultipleNamespaces|Le type de wrapper du message spécifié ne peut pas être projeté comme type de contrat de données car il contient plusieurs espaces de noms. Utilisez le XmlSerializer.|  
|UriMustBeAbsolute|L'URI doit être absolu.|
