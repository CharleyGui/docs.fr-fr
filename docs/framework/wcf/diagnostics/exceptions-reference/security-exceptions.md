---
title: Exceptions de sécurité
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: e96c317862867b9e461eb2d13dce6ede5b30cf13
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348241"
---
# <a name="security-exceptions"></a>Exceptions de sécurité

Cette rubrique répertorie toutes les exceptions de sécurité.

## <a name="exception-list"></a>Liste des exceptions

|Code de la ressource|Chaîne de la ressource|
|-------------------|---------------------|
|AnonymousLogonsAreNotAllowed|Le service ne vous autorise pas à ouvrir une session anonyme.|
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|Le message de demande doit être protégé. Cela est requis par une opération du contrat spécifié. La protection doit être fournie par la liaison spécifiée.|
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Le message de réponse doit être protégé. Cela est requis par une opération du contrat spécifié. La protection doit être fournie par la liaison spécifiée.|
|AtMostOnePrimarySignatureInReceiveSecurityHeader|Une seule signature principale est autorisée dans un en-tête de sécurité.|
|BadContextTokenFaultReason|Le jeton de contexte de sécurité a expiré ou n'est pas valide. Le message n'a pas été traité.|
|BadEncryptionState|L'élément EncryptedData ou EncryptedKey présente un état non valide pour cette opération.|
|BasicHttpMessageSecurityRequiresCertificate|La liaison BasicHttp exige que le type BasicHttpBinding.Security.Message.ClientCredentialType soit équivalent à celui des informations d'identification BasicHttpMessageCredentialType.Certificate pour les messages sécurisés. Sélectionnez la sécurité TransportWithMessageCredential ou Transport pour les informations d'identification UserName.|
|BasicTokenCannotBeWrittenWithoutEncryption|Le jeton de base ne peut pas être écrit sans chiffrement.|
|BindingDoesNotSupportProtectionForRst|La liaison spécifiée pour le contrat spécifié est configurée avec SecureConversation, mais le mode d’authentification n’est pas en mesure de fournir l’intégrité et la confidentialité demande/réponse requises pour la négociation.|
|BindingDoesNotSupportWindowsIdenityForImpersonation|L'opération de contrat spécifiée requiert l'identité Windows pour l'emprunt d'identité automatique. Une identité Windows qui représente l'appelant n'est pas fournie par la liaison spécifiée pour le contrat spécifié.|
|CachedNegotiationStateQuotaReached|Le service ne peut pas mettre l'état de la négociation en mémoire cache car la capacité spécifiée est atteinte. Faites une nouvelle tentative pour cette demande.|
|CacheQuotaReached|Ajout de l'élément impossible. La taille maximale de la mémoire cache est spécifiée.|
|CannotDetermineSPNBasedOnAddress|Le client ne peut pas déterminer le nom de principal du service (SPN) basé sur l'identité dans l'adresse cible spécifiée pour les besoins de SspiNegotiation/Kerberos. L’identité de l’adresse cible doit être une identité UPN (comme acmedomain\\\alice) ou une identité SPN (comme Host/bobs-machine).|
|CannotFindCert|Impossible de trouver le certificat X.509 à l'aide des critères de recherche spécifiés : StoreName, StoreLocation, FindType, FindValue.|
|CannotFindCertForTarget|Impossible de trouver le certificat X.509 à l'aide des critères de recherche spécifiés : StoreName, StoreLocation, FindType, FindValue pour la cible spécifiée.|
|CannotFindCorrelationStateForApplyingSecurity|Impossible de trouver l'état de corrélation pour appliquer la sécurité et répliquer au répondeur.|
|CannotFindNegotiationState|Impossible de trouver l'état de négociation pour le contexte spécifié.|
|CannotFindSecuritySession|Impossible de trouver la session de sécurité avec l'ID spécifié.|
|CannotImportProtectionLevelForContract|La stratégie d'importation d'un processus ne peut pas importer de liaison pour le contrat spécifié. Les exigences en matière de protection pour la liaison ne sont pas compatibles avec une liaison déjà importée pour le contrat. Vous devez reconfigurer la liaison.|
|CannotImportSupportingTokensForOperationWithoutRequestAction|Échec de l'importation de la stratégie de sécurité. Cette stratégie de sécurité contient les exigences de jeton prises en charge dans le cadre de l’opération. La description du contrat ne précise pas l'action pour le message de demande qui est associé à cette opération.|
|CannotIssueRstTokenType|Émission du type de jeton spécifié impossible.|
|CannotObtainIssuedTokenKeySize|Impossible de déterminer la taille de la clé du jeton émis.|
|CannotPerformImpersonationOnUsernameToken|L'emprunt d'identité par le biais du jeton client est impossible. La liaison spécifiée pour le contrat spécifié utilise le jeton de sécurité du nom d’utilisateur pour l’authentification client avec un fournisseur d’appartenances inscrit. Utilisez un type de jeton de sécurité différent pour le client.|
|CannotPerformS4UImpersonationOnPlatform|La liaison spécifiée pour le contrat spécifié prend en charge l’emprunt d’identité uniquement sur Windows Server 2003 et la version plus récente de Windows. Utilisez l’authentification SspiNegotiated et une liaison avec SecureConversation dont l’annulation est activée.|
|CannotReadKeyIdentifier|Lecture de l'élément KeyIdentifier impossible à partir de l'élément spécifié avec l'espace de noms spécifié.|
|CannotReadToken|Lecture du jeton impossible à partir de l'élément spécifié avec le nom d'espace spécifié pour BinarySecretSecurityToken, avec un élément ValueType spécifié . S'il est prévu que cet élément soit valide, assurez-vous que la sécurité est configurée pour consommer des jetons dotés du nom, de l'espace de noms et du type valeur spécifiés.|
|CertificateUnsupportedForHttpTransportCredentialOnly|L'authentification client basée sur les certificats n'est pas prise en charge dans le mode de sécurité TransportCredentialOnly. Sélectionnez le mode de sécurité Transport.|
|ClaimTypeCannotBeEmpty|La valeur de claimType ne peut pas être une chaîne de caractères vide.|
|ClientCertificateNotProvided|Le certificat pour le client n'a pas été fourni. Il peut être défini sur ClientCredentials ou sur ServiceCredentials.|
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType.None n'est pas valide pour le mode de sécurité TransportWithMessageCredential. Indiquez un type d'informations d'identification de message ou utilisez un mode de sécurité différent.|
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Le schéma de configuration est insuffisant pour décrire la configuration non standard de l’élément de liaison de sécurité suivant :|
|DerivedKeyTokenGenerationAndLengthTooHigh|La génération et la longueur spécifiées de la clé dérivée aboutissent à un décalage de dérivation de clé supérieur au décalage maximal autorisé.|
|DnsIdentityCheckFailedForIncomingMessage|La vérification d'identité a échoué pour le message entrant. L'identité DNS attendue du point de terminaison distant a été spécifiée. Le point de terminaison distant a fourni la revendication DNS spécifiée. S'il s'agit d'un point de terminaison distant légitime, vous pouvez résoudre le problème en spécifiant l'identité DNS comme propriété d'identité d'EndpointAddress lors de la création du proxy de canal.|
|DnsIdentityCheckFailedForOutgoingMessage|Échec de la vérification d’identité pour le message sortant. Le point de terminaison distant doit avoir l’identité système de nom de domaine spécifiée. Le point de terminaison distant a fourni la revendication DNS. S'il s'agit d'un point de terminaison distant légitime, vous pouvez résoudre le problème en spécifiant de manière explicite l'identité DNS comme propriété Identity d'EndpointAddress lors de la création du proxy de canal.|
|DuplicateIdInMessageToBeVerified|L’ID spécifié s’est produit deux fois dans le message qui est fourni pour vérification.|
|EmptyBase64Attribute|Une valeur vide a été trouvée pour le nom d'attribut et l'espace de noms en base 64 requis.|
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|L'exportation de la stratégie de sécurité a échoué. La liaison contient à la fois un élément AsymmetricSecurityBindingElement et un élément de liaison de transport sécurisé. L'exportation de stratégie pour une telle liaison n'est pas prise en charge.|
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|L'exportation de la stratégie de sécurité a échoué. La liaison contient à la fois un élément SymmetricSecurityBindingElement et un élément de liaison de transport sécurisé. L'exportation de stratégie pour une telle liaison n'est pas prise en charge.|
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|L'exportation de la stratégie de sécurité a échoué. La liaison contient un élément TransportSecurityBindingElement, mais pas d’élément de transport qui implémente l’interface ITransportTokenAssertionProvider. L'exportation de stratégie pour une telle liaison n'est pas prise en charge. Vérifiez que l’élément de liaison de transport de la liaison implémente l’interface ITransportTokenAssertionProvider.|
|FoundMultipleCerts|Plusieurs certificats X.509 ont été trouvés en utilisant les critères de recherche spécifiés : StoreName, StoreLocation, FindType, FindValue. Indiquez une valeur de recherche plus précise.|
|FoundMultipleCertsForTarget|Plusieurs certificats X.509 ont été trouvés en utilisant les critères de recherche spécifiés : StoreName, StoreLocation, FindType, FindValue pour la cible spécifiée. Indiquez une valeur de recherche plus précise.|
|HeaderDecryptionNotSupportedInWsSecurityJan2004|SecurityVersion.WSSecurityJan2004 ne prend pas en charge le déchiffrement d'en-tête. Utilisez SecurityVersion.WsSecurityXXX2005 et les versions ultérieures ou bien utilisez la sécurité de transport pour chiffrer la totalité du message.|
|IdentityCheckFailedForIncomingMessage|La vérification d'identité a échoué pour le message entrant. L'identité attendue est spécifiée pour le point de terminaison cible.|
|IdentityCheckFailedForOutgoingMessage|La vérification d'identité a échoué pour le message sortant. L'identité attendue est spécifiée pour le point de terminaison cible.|
|IncorrectSpnOrUpnSpecified|L'authentification SSPI (Security Support Provider Interface) a échoué. Il est possible que le serveur ne s'exécute pas avec un compte dont l'identité est spécifiée. Si le serveur s'exécute avec un compte de service (par exemple Service réseau), spécifiez l'élément ServicePrincipalName du compte en tant qu'identité dans l'élément EndpointAddress pour le serveur. Si le serveur s'exécute avec un compte d'utilisateur, spécifiez l'élément UserPrincipalName du compte en tant qu'identité dans l'élément EndpointAddress pour le serveur.|
|InvalidAttributeInSignedHeader|L'en-tête signé spécifié contient l'attribut spécifié. L'attribut attendu est spécifié.|
|InvalidCloseResponseAction|Une réponse de fermeture de session de sécurité a été reçue avec l'action non valide spécifiée.|
|InvalidQName|L'élément QName est non valide.|
|InvalidRenewResponseAction|Une réponse de renouvellement de session de sécurité a été reçue avec l'action non valide spécifiée.|
|InvalidSspiNegotiation|La négociation de l'interface du fournisseur de la prise en charge de sécurité a échoué.|
|IssuerBindingNotPresentInTokenRequirement|Le gestionnaire de jetons de sécurité impose que l’élément de liaison de sécurité de démarrage soit spécifié dans l’exigence de jeton qui décrit la conversation sécurisée. La spécification de jeton est spécifiée comme suit.|
|KeyLengthMustBeMultipleOfEight|La longueur de clé spécifiée n'est pas un multiple de 8 pour les clés symétriques.|
|LsaAuthorityNotContacted|Erreur SSL interne (pour plus d'informations, consultez le code d'état Win32). Vérifiez le certificat du serveur pour déterminer s'il lui est possible d'échanger des clés.|
|MaximumPolicyRedirectionsExceeded|La limite de récupération de stratégie récursive a été atteinte. Effectuez des vérifications pour déterminer s'il y a une boucle dans la chaîne du service de fédération.|
|MessagePartSpecificationMustBeImmutable|La spécification des parties d'un message doit être déclarée constante avant d'être définie.|
|MissingCustomCertificateValidator|X509CertificateValidationMode.Custom requiert CustomCertificateValidator. Spécifiez la propriété CustomCertificateValidator.|
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode.Custom requiert CustomUserNamePasswordValidator. Spécifiez la propriété CustomUserNamePasswordValidator.|
|MissingMembershipProvider|UserNamePasswordValidationMode.MembershipProvider requiert MembershipProvider. Spécifiez la propriété MembershipProvider.|
|NoBinaryNegoToSend|Aucune négociation binaire n'a été envoyée à l'autre correspondant.|
|NoEncryptionPartsSpecified|Aucune partie de message de chiffrement n'a été spécifiée avec l'action spécifiée.|
|NoKeyInfoInEncryptedItemToFindDecryptingToken|La valeur de KeyInfo n'a pas été trouvée dans l'élément chiffré pour rechercher le jeton de déchiffrement.|
|NonceLengthTooShort|La valeur à usage unique spécifiée est trop courte. La longueur minimale obligatoire est de 4 octets.|
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Aucune adresse EndpointAddress sortante n'est disponible pour vérifier l'identité sur un message à envoyer.|
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Aucune adresse EndpointAddress sortante n'est disponible pour vérifier l'identité sur un message reçu.|
|NoPartsOfMessageMatchedPartsToSign|Aucune signature n'a été créée car aucune partie du message ne correspondait à la spécification fournie pour les parties du message.|
|NoPrincipalSpecifiedInAuthorizationContext|Aucune principal de sécurité personnalisée n'est spécifiée dans le contexte d'autorisation.|
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Aucune signature n'est disponible dans l'en-tête de sécurité pour fournir la valeur unique pour la détection de relecture.|
|NoSignaturePartsSpecified|Aucune partie de message de signature n'a été spécifiée pour des messages avec l'action spécifiée.|
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Aucun jeton de signature n'est disponible pour effectuer une vérification d'identité entrante.|
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Aucun horodatage n'est disponible dans l'en-tête de sécurité pour effectuer la détection de relecture.|
|NoTransportTokenAssertionProvided|L'exportation de la stratégie de sécurité a échoué. L'assertion de jeton de transport fournie de type spécifié n'a pas créé une assertion de jeton de transport pour inclure l'assertion de stratégie de sécurité sp:TransportBinding.|
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Le protocole de sécurité symétrique peut être configuré avec un fournisseur de jeton symétrique et un authentificateur de jeton symétrique, ou bien avec un fournisseur de jeton asymétrique. Il ne peut pas être configuré avec les deux ensemble.|
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Cette opération ne peut pas être effectuée sur les en-têtes de sécurité du récepteur.|
|OperationDoesNotAllowImpersonation|L'opération de service spécifiée qui appartient au contrat avec le nom et l'espace de noms spécifiés n'autorise pas l'emprunt d'identité.|
|PolicyRequiresConfidentialityWithoutIntegrity|La stratégie de sécurité de message pour l'action spécifiée requiert la confidentialité sans l'intégrité. La confidentialité sans l'intégrité n'est pas prise en charge.|
|PrimarySignatureIsRequiredToBeEncrypted|La signature principale doit être chiffrée.|
|PropertySettingErrorOnProtocolFactory|La propriété requise sur la fabrication de protocole de sécurité spécifiée n'est pas définie ou a une valeur non valide.|
|ProtocolFactoryCouldNotCreateProtocol|La fabrication de protocole ne peut pas créer de protocole.|
|PublicKeyNotRSA|La clé publique n'est pas une clé RSA.|
|RequiredMessagePartNotEncrypted|La partie du message requise spécifiée n'a pas été chiffrée.|
|RequiredMessagePartNotEncryptedNs|La partie du message requise spécifiée n'a pas été chiffrée.|
|RequiredMessagePartNotSigned|La partie du message requise spécifiée n'a pas été signée.|
|RequiredMessagePartNotSignedNs|La partie du message requise spécifiée n'a pas été signée.|
|RequiredSecurityHeaderElementNotSigned|L’élément d’en-tête de sécurité spécifié avec l’ID spécifié doit être signé.|
|RequiredSecurityTokenNotEncrypted|Le jeton de sécurité spécifié dont le mode d'attache est spécifié doit être chiffré.|
|RequiredSecurityTokenNotSigned|Le jeton de sécurité spécifié dont le mode d'attache est spécifié doit être signé.|
|RequiredSignatureMissing|La signature doit être dans l'en-tête de sécurité.|
|RequireNonCookieMode|La liaison spécifiée avec l’espace de noms spécifié est configuré pour émettre des jetons de contexte de sécurité des cookies. Les services d'intégration COM+ ne prennent pas en charge les jetons de contexte de sécurité des cookies.|
|RevertingPrivilegeFailed|L'opération de rétablissement a échoué avec l'exception spécifiée.|
|RSTRAuthenticatorIncorrect|CombinedHash de RequestSecurityTokenResponse est incorrect.|
|SecureConversationCancelNotAllowedFaultReason|Une annulation de conversation sécurisée n'est pas autorisée par la liaison.|
|SecureConversationDriverVersionDoesNotSupportSession|La version configurée de SecureConversation ne prend pas en charge les sessions. Utilisez WSSecureConversationFeb2005 ou ultérieur.|
|SecureConversationRequiredByReliableSession|Impossible d'établir une session fiable sans conversation sécurisée. Activez la conversation sécurisée.|
|SecurityAuditFailToLoadDll|Le chargement de la bibliothèque de liens dynamiques (DLL) spécifié a échoué.|
|SecurityAuditNotSupportedOnChannelFactory|SecurityAuditBehavior n'est pas pris en charge sur la fabrication de canal.|
|SecurityAuditPlatformNotSupported|L'écriture de messages d'audit dans le journal de sécurité n'est pas prise en charge par la plateforme actuelle. Vous devez écrire les messages d'audit dans le journal des applications.|
|SecurityBindingElementCannotBeExpressedInConfig|Une stratégie de sécurité a été importée pour le point de terminaison. La stratégie de sécurité contient des exigences qui ne peuvent pas être représentées dans une configuration Windows Communication Foundation. Recherchez un commentaire sur les paramètres SecurityBindingElement qui sont nécessaires dans le fichier de configuration généré. Créez l’élément de liaison correct avec le code. La configuration de liaison figurant dans le fichier de configuration n'est pas sécurisée.|
|SecurityBindingSupportsOneWayOnly|SecurityBinding pour la liaison spécifiée du contrat spécifié prend en charge l'opération OneWay uniquement.|
|SecurityContextDoesNotAllowImpersonation|Impossible de démarrer l'emprunt d'identité car SecurityContext pour le rôle UltimateReceiver du message de demande avec l'action spécifiée n'est pas mappé à une identité Windows.|
|SecurityListenerClosing|L'écouteur n'accepte pas de nouvelle conversation sécurisée car il est en cours de fermeture.|
|SecurityListenerClosingFaultReason|Le serveur n'accepte pas de nouvelle conversation sécurisée car il est en cours de fermeture. Réessayez ultérieurement.|
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|La fabrication de protocoles de sécurité doit être définie avant l'exécution de cette opération.|
|SecuritySessionAbortedFaultReason|La session de sécurité a été interrompue. Ceci est peut-être dû au fait qu'aucun message n'a été reçu sur la session pendant trop longtemps.|
|SecuritySessionKeyIsStale|La clé de session doit être renouvelée avant de pouvoir sécuriser les messages d'application.|
|SecuritySessionLimitReached|Impossible de créer une session de sécurité. Réessayez ultérieurement.|
|SecuritySessionNotPending|Aucune session de sécurité avec l’ID spécifié n’est en attente.|
|SecurityTokenParametersHasIncompatibleInclusionMode|La liaison spécifiée est configurée à l’aide d’un paramètre de jeton de sécurité dont le mode d’inclusion de jetons de sécurité spécifié n’est pas compatible. Spécifiez un autre mode d'inclusion de jeton de sécurité.|
|SecurityVersionDoesNotSupportEncryptedKeyBinding|La liaison spécifiée du contrat spécifié a été configurée à l’aide d’une version de sécurité non compatible qui ne prend pas en charge les références non liées à EncryptedKeys. Utilisez la version de sécurité spécifiée ou ultérieure pour la liaison.|
|SecurityVersionDoesNotSupportSignatureConfirmation|La SecurityVersion spécifiée ne prend pas en charge la confirmation de signature. Utilisez une SecurityVersion ultérieure.|
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|La liaison spécifiée du contrat spécifié a été configurée à l'aide d'une version de sécurité qui ne prend pas en charge les références externes aux jetons X.509 utilisant la valeur d'empreinte numérique du certificat. Utilisez la version de sécurité spécifiée ou ultérieure pour la liaison.|
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Les paramètres de jeton de sécurité doivent être spécifiés avec les jetons associés pour chaque message.|
|ServerCertificateNotProvided|Le destinataire n'a pas fourni son certificat. Ce certificat est exigé par le protocole TLS. Les deux parties doivent avoir accès à leur certificat.|
|SignatureConfirmationNotSupported|La SecurityVersion configurée ne prend pas en charge la confirmation de signature. Utilisez WSSecurityXXX2005 ou version ultérieure.|
|SignatureConfirmationRequiresRequestReply|La fabrication de protocoles doit prendre en charge la sécurité Demande/Réponse pour offrir une confirmation de signature.|
|SignatureNotExpected|Aucune signature n'est attendue pour ce message.|
|SigningTokenHasNoKeys|Le jeton de signature spécifié ne contient aucune clé. Le jeton de sécurité est utilisé dans un contexte qui lui impose d'effectuer des opérations de chiffrement, mais il ne contient aucune clé de chiffrement. Le type de jeton ne prend pas en charge les opérations de chiffrement ou l'instance particulière du jeton ne contient pas de clé de chiffrement. Vérifiez dans votre configuration que les types de jeton dont le chiffrement est désactivé (par exemple, UserNameSecurityToken) ne sont pas spécifiés dans un contexte qui impose des opérations de chiffrement (par exemple, un jeton de prise en charge d'endossement).|
|SpnegoImpersonationLevelCannotBeSetToNone|L'interface SSPI ne prend pas en charge le niveau d'emprunt d'identité « None ». Spécifiez le niveau Identification, Impersonation ou Delegation.|
|SslClientCertMustHavePrivateKey|Le certificat spécifié doit avoir une clé privée. Le processus doit disposer de droits d'accès à la clé privée.|
|SslServerCertMustDoKeyExchange|Le certificat spécifié doit contenir une clé privée capable d'échange de clé. Le processus doit disposer de droits d'accès à la clé privée.|
|StandardsManagerCannotWriteObject|Le jeton Serializer ne peut pas sérialiser l'objet spécifié.  S'il s'agit d'un type personnalisé, vous devez fournir un sérialiseur personnalisé.|
|TimeStampHasCreationAheadOfExpiry|L'horodatage de sécurité n'est pas valide car son heure de création est supérieure ou égale à son heure d'expiration.|
|TimeStampHasCreationTimeInFuture|L'horodatage de sécurité n'est pas valide car son heure de création est dans le futur. Le temps actuel est spécifié et l'inclinaison autorisée de l'horloge est spécifiée.|
|TimeStampHasExpiryTimeInPast|L'horodatage de sécurité est périmé car son heure d'expiration est dans le passé. Le temps actuel est spécifié et l'inclinaison autorisée de l'horloge est spécifiée.|
|TimeStampWasCreatedTooLongAgo|L'horodatage de sécurité est périmé car son heure de création est trop lointaine dans le passé. Le temps actuel, la durée de vie maximale de l'horodatage et l'inclinaison autorisée de l'horloge sont spécifiés.|
|TokenProviderCannotGetTokensForTarget|Le fournisseur de jetons ne peut pas obtenir de jeton pour la cible spécifiée.|
|TooManyIssuedSecurityTokenParameters|Une section de la chaîne de sécurité fédérée contient plusieurs IssuedSecurityTokenParameters. Windows CardSpace ne prend en charge qu'un élément IssuedSecurityTokenParameters par section.|
|TransportDoesNotProtectMessage|La liaison spécifiée pour le contrat spécifié est configurée avec un mode d’authentification qui nécessite une intégrité et une confidentialité de niveau de transport. Le transport ne peut toutefois pas fournir l'intégrité et la confidentialité.|
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 ne prend pas en charge l'émission de certificats X.509 ou d'éléments EncryptedKey. Utilisez WsTrustFeb2005 ou une version ultérieure.|
|TrustDriverVersionDoesNotSupportSession|La version de Trust configurée ne prend pas en charge les sessions. Utilisez WSTrustFeb2005 ou une version ultérieure.|
|UnableToCreateICryptoFromTokenForSignatureVerification|Impossible de créer une interface ICrypto à partir du jeton spécifié pour la vérification de la signature.|
|UnableToCreateSymmetricAlgorithmFromToken|Impossible de créer l'algorithme symétrique spécifié à partir du jeton.|
|UnableToDeriveKeyFromKeyInfoClause|La clause KeyInfo spécifiée a été résolue au jeton spécifié, qui ne contient pas de clé symétrique pouvant être utilisée pour une dérivation.|
|UnableToFindTokenAuthenticator|Impossible de trouver un authentificateur de jeton pour le type de jeton spécifié. Les jetons de ce type ne peuvent pas être acceptés conformément aux paramètres de sécurité actuels.|
|UnableToLoadCertificateIdentity|Impossible de charger l'identité de certificat X.509 spécifiée dans la configuration.|
|UnexpectedEmptyElementExpectingClaim|L'élément spécifié de l'espace de noms spécifié est vide et ne spécifie pas une revendication d'identité valide.|
|UnknownEncodingInBinarySecurityToken|Un encodage non reconnu s'est produit lors de la lecture du jeton de sécurité binaire.|
|UnsecuredMessageFaultReceived|Une erreur non sécurisée ou incorrectement sécurisée a été reçue de l'autre partie. Voir le FaultException interne pour le code et les détails de l'erreur.|
|UnsupportedPasswordType|Le jeton de nom d'utilisateur spécifié a un type de mot de passe non pris en charge.|
|UnsupportedSecureConversationBootstrapProtectionRequirements|Impossible d'importer la stratégie de sécurité. Les exigences de protection de la liaison de démarrage avec conversation sécurisée ne sont pas prises en charge. Les exigences de protection du démarrage avec conversation sécurisée doivent imposer la signature et le chiffrement de la demande et de la réponse.|
|UnsupportedSecurityPolicyAssertion|Une assertion de stratégie de sécurité non prise en charge a été détectée pendant l'importation de la stratégie de sécurité spécifiée.|
