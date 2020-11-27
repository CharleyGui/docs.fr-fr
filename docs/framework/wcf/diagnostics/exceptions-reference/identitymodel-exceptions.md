---
title: Exceptions IdentityModel
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: 08d81f4eb35d0f4bda3997d6ab4dfd0ec10407e1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275035"
---
# <a name="identitymodel-exceptions"></a>Exceptions IdentityModel

Cette rubrique répertorie toutes les exceptions générées par IdentityModel.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne actuelle|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|La valeur de cet argument doit être l’un de ces deux types.|  
|SAMLSubjectNameIdentifierRequiresNameValue|La valeur de 'Name' spécifiée pour un élément SamlNameIdentifier ne peut ni être null, ni être de longueur 0.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|IssuanceTokenProvider a achevé la négociation de sécurité.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Une nouvelle clé de session de sécurité a été émise par le serveur.|  
|SAMLAttributeMissingNameAttributeOnRead|La valeur de 'Name' pour l'élément SamlAttribute qui est lu est manquante ou de longueur 0.|  
|UnknownICryptoType|L'implémentation ICrypto n'est pas prise en charge.|  
|TraceCodeSecurityTokenProviderClosed|Le fournisseur de jetons de sécurité a été fermé.|  
|SAMLUnableToLoadAdvice|Échec du chargement de l' \<saml:advice> élément.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|L'attribut 'AuthenticationMethod' qui est lu pour un élément SamlAuthenticationStatement est manquant ou de longueur 0.|  
|UnsupportedTransformAlgorithm|Algorithme de canonisation ou de transformation non pris en charge.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Un élément SamlAudienceRestrictionCondition doit contenir au moins un élément Audience (URI).|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence doit référencer au moins une entité SamlAssertion par ID ou par référence.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Une valeur de l'élément SamlAudienceRestrictionCondition qui est lu est manquante dans l'élément 'Audience'.|  
|X509ChainBuildFail|Échec de la constitution de la chaîne du certificat X.509 spécifique. Le certificat qui a été utilisé est doté d'une chaîne d'approbation impossible à vérifier. Remplacez ce certificat ou modifiez l'élément certificateValidationMode.|  
|XDCannotFindValueInDictionaryString|ID de valeur spécifique introuvable dans la chaîne de dictionnaire.|  
|TraceCodeImportSecurityChannelBindingEntry|Démarrage de Security ImportChannelBinding.|  
|PrivateKeyExchangeNotSupported|La clé privée ne prend pas en charge l'échange KeySpec.|  
|TokenProviderUnableToGetToken|Le fournisseur de jetons spécifique était dans l'incapacité de fournir un jeton de sécurité.|  
|SAMLEntityCannotBeNullOrEmpty|L'entité SamlAssertion spécifique ne peut ni être null, ni être vide.|  
|SAMLAssertionRequireOneStatement|Un élément SamlAssertion requiert au moins une instruction. Vérifiez que vous avez ajouté au moins une instruction SamlStatement à l'élément SamlAssertion que vous créez.|  
|AESInvalidInputBlockSize|La taille d'entrée doit être un multiple d'octets spécifiques.|  
|AESCryptAcquireContextFailed|Échec de l'acquisition du contexte CSP.|  
|SAMLAssertionRequireOneStatementOnRead|L'élément SamlAssertion qui est lu ne contenait aucune instruction SamlStatement. Un élément SamlAssertion doit contenir au moins une instruction SamlStatement.|  
|TraceCodeSecuritySessionClosedFaultReceived|La session de sécurité client a reçu une erreur de fermeture de session en provenance du serveur.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|IssuanceTokenProvider a appliqué un en-tête de redirection.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Échec lors de l'envoi d'une erreur de fermeture de session de sécurité au client.|  
|ValueMustBeZero|La valeur de cet argument doit être 0.|  
|SAMLUnableToResolveSignatureKey|Impossible de résoudre SecurityKeyIdentifier trouvé dans la signature SamlAssertion. Cette signature ne peut pas être validée pour l'émetteur spécifique.|  
|X509IsNotInTrustedStore|Le certificat X.509 spécifique ne se trouve pas dans un magasin de personnes de confiance.|  
|SAMLElementNotRecognized|L'élément spécifique n'est pas pris en charge.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|L'attribut 'Resource' pour l'élément SamlAuthorizationDecisionStatement qui est lu est manquant ou de longueur 0.|  
|SamlTokenMissingSignature|L'élément SamlAssertion n'est pas signé. Il peut être signé en définissant l'élément SigningCredentials.|  
|ExpectedElementMissing|L'élément attendu avec l'espace de noms spécifique est manquant.|  
|NoKeyIdentifierClauseFound|Aucune clause du type spécifique n'a été trouvée dans l'élément SecurityKeyIdentifier.|  
|MissingPrivateKey|La clé privée n'est pas présente dans le certificat X.509.|  
|UnexpectedEOFFromReader|EOF inattendu depuis le lecteur XML.|  
|UnsupportedKeyDerivationAlgorithm|L'algorithme de dérivation de clé spécifique n'est pas pris en charge.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|Le jeton spécifique ne prend pas en charge la création de clause d'identificateur de clé spécifique.|  
|LastMessageNumberExceeded|Détection d'une violation du protocole de nombre de séquences.|  
|SymmetricKeyLengthTooShort|La longueur de la clé symétrique spécifiée est trop courte.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|L'élément SamlAuthorityBinding qui est lu s'est avéré contenir un élément 'AuthorityKind' manquant ou de longueur 0.  Cette opération n’est pas autorisée.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer est vide.|  
|InvalidXmlQualifiedName|Un nom complet XML était attendu, mais un nom non valide a été trouvé.|  
|SAMLAuthorityKindMissingName|L'élément XmlQualifiedName qui représente l'entité 'AuthorityKind' dans l'élément SamlAuthorityBinding ne peut ni être null, ni être de longueur 0.|  
|AESCryptEncryptFailed|Échec du chiffrement des données spécifiques.|  
|AuthorizationContextCreated|Création du contexte d'autorisation avec l'ID spécifique.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|L'élément SamlSerializer ne contient aucun élément SecurityTokenSerializer capable de lire l'entité SecurityKeyIdentifier. Si vous utilisez une entité SecurityKeyIdentifier personnalisée, vous devez fournir un élément SecurityTokenSerializer personnalisé.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|IssuanceTokenProvider a réduit le cache de jetons de service.|  
|TraceCodeSecurityTokenProviderOpened|Le fournisseur de jetons de sécurité a été ouvert.|  
|PublicKeyNotRSA|La clé publique n'est pas une clé RSA.|  
|InvalidReaderState|L'état spécifique est non valide pour le lecteur d'entrée fourni.|  
|UnableToResolveReferenceUriForSignature|Impossible de résoudre l'URI spécifique dans la signature pour calculer le message condensé.|  
|EmptyBase64Attribute|Une valeur vide a été trouvée pour l'espace de noms et le nom d'attribut en base64 requis.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|L'élément SAML SubjectConfirmation nécessite une méthode de confirmation lorsque les données de confirmation ou les informations de clé sont spécifiées.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|L'élément SamlAudienceRestrictionCondition qui est lu doit contenir au moins une valeur 'Audience'. Aucune n'a été trouvée.|  
|TokenProviderUnableToRenewToken|Le fournisseur de jetons spécifique était dans l'incapacité de renouveler le jeton de sécurité.|  
|AESIVLengthNotSupported|Le vecteur d'initialisation (IV) de bits spécifique n'est pas pris en charge. Seul le vecteur d'initialisation de 128 bits est pris en charge.|  
|SAMLAuthorityBindingMissingAuthorityKind|Un élément SamlAuthorityBinding doit contenir un élément 'AuthorityKind' non null.|  
|TraceCodeSecuritySessionDemuxFailure|Le message entrant ne fait pas partie d'une session de sécurité existante.|  
|TokenRenewalNotSupported|Le fournisseur de jetons spécifique ne prend pas en charge le renouvellement de jetons.|  
|AtLeastOneReferenceRequired|Au moins une référence est requise dans une signature.|  
|SAMLSignatureAlreadyRead|La signature est déjà lue dans l'assertion SAML.|  
|AlgorithmAndPrivateKeyMisMatch|L'algorithme spécifié et la clé privée ne correspondent pas.|  
|EmptyTransformChainNotSupported|La chaîne de transformation vide n'est pas prise en charge.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper :: EncryptDecryptHelper&#124; 'offset’est hors limites.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper :: EncryptDecryptHelper&#124; 'size’est hors limites. SecurityTokenManagerCannotCreateAuthenticatorForRequirement=Le gestionnaire de jetons de sécurité ne peut pas créer d’authentificateur de jeton pour l’exigence spécifique.|  
|UnableToCreateKeyedHashAlgorithm|Création d'un élément KeyedHashAlgorithm impossible à partir de la valeur spécifique pour l'algorithme de signature spécifique.|  
|SAMLUnableToLoadAssertion|Échec du chargement de l' \<saml:assertion> élément.|  
|X509FindValueMismatchMulti|L’élément X509FindType spécifique requiert que le type de l’argument findValue soit l’une des 2 valeurs. L’argument findValue est d’un autre type.|  
|TraceCodeSecurityIdentityDeterminationSuccess|L'identité a été déterminée pour un élément EndpointAddress.|  
|UndefinedUseOfPrefixAtElement|Aucun espace de noms n'est défini pour le préfixe spécifique utilisé au niveau de l'élément.|  
|TraceCodeSecuritySessionResponderOperationFailure|Échec de l'opération de session sur le serveur.|  
|CannotFindCert|Impossible de trouver le certificat X.509 à l'aide des critères de recherche spécifiés : StoreName, StoreLocation, FindType, FindValue.|  
|X509InvalidUsageTime|Le temps d'utilisation du certificat X.509 spécifique est non valide. Ce temps d'utilisation n'est pas compris dans la plage NotBefore time et NotAfter time.|  
|TraceCodeSecurityIdentityDeterminationFailure|L'identité ne peut pas être déterminée pour un élément EndpointAddress.|  
|AsyncObjectAlreadyEnded|La méthode End a déjà été appelée sur cet objet de résultat asynchrone.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|Le dictionnaire externe ne contient pas de définition pour toutes les chaînes requises. La chaîne spécifique n'est pas disponible dans le dictionnaire distant.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|La session de sécurité du client a reçu une erreur de renouvellement de clé du serveur.|  
|SAMLActionNameRequired|La chaîne qui représente l'élément SamlAction ne peut ni être null, ni être de longueur 0.|  
|SignatureVerificationFailed|Échec de la vérification de la signature.|  
|TraceCodeSecurityContextTokenCacheFull|Le cache de SecurityContextSecurityToken est plein.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|L'attribut MajorVersion pour l'élément SamlAssertion qui est lu est manquant ou de longueur 0.|  
|SamlAttributeClaimRightShouldBePossessProperty|Ce constructeur SamlAttribute requiert que la valeur du Droit de la revendication soit définie sur System.IdentityModel.Claims.Rights.PossessProperty.|  
|AuthorizationPolicyEvaluated|Évaluation de la stratégie avec l'ID spécifique.|  
|SAMLUnableToLoadCondtions<!-- the misspelling here is deliberate. -->|Échec du chargement de l' \<saml:conditions> élément.|  
|AESKeyLengthNotSupported|La clé de bits spécifique n'est pas prise en charge. Seule la clé de 128, 192 et 256 bits est prise en charge.|  
|UserNameCannotBeEmpty|Le nom d'utilisateur ne peut pas être vide.|  
|AlgorithmAndPublicKeyMisMatch|L'algorithme spécifié et la clé publique ne correspondent pas.|  
|SAMLUnableToLoadCondtion<!-- the misspelling here is deliberate. -->|Échec du chargement de l' \<saml:conditions> élément.|  
|SamlAssertionMissingSigningCredentials|La valeur de SigningCredentials n'est pas définie sur l'élément SamlAssertion. SamlAssertions doit être signé, définissez cette valeur pour poursuivre.|  
|SspiPayloadNotEncrypted|Les données binaires n'ont pas été chiffrées avec le contexte de sécurité SSPI.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|L'élément SamlAuthorizationDecisionStatement qui est lu ne contient aucun SamlAction.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Le protocole de sécurité ne peut pas sécuriser le message sortant.|  
|UndefinedUseOfPrefixAtAttribute|Aucun espace de noms n'est défini pour le préfixe spécifique utilisé au niveau de l'attribut spécifique.|  
|NoInputIsSetForCanonicalization|Aucune entrée n'est définie pour l'écriture d'une sortie rendue canonique.|  
|TraceCodeSecurityPendingServerSessionAdded|Une session de sécurité en attente est ajoutée au serveur.|  
|AsyncCallbackException|Une exception a été levée par AsyncCallback.|  
|PrivateKeyNotRSA|La clé privée n'est pas une clé RSA.|  
|TraceCodeSecurityClientSessionKeyRenewed|La session de sécurité du client a renouvelé la clé de session.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|L'attribut 'Décision' pour l'élément SamlAuthorizationDecisionStatement qui est lu est manquant ou de longueur 0.|  
|SAMLAttributeNameAttributeRequired|La valeur de 'Name' spécifiée pour un élément SamlAttribute ne peut ni être null, ni être de longueur 0.|  
|SamlSerializerRequiresExternalSerializers|L'élément SamlSerializer requiert un élément SecurityTokenSerializer pour sérialiser l'élément SecurityKeyIdentifier présent dans le jeton.|  
|UnableToResolveKeyReference|Le programme de résolution de jeton n'est pas en mesure de résoudre la référence de clé de sécurité.|  
|UnsupportedKeyWrapAlgorithm|L'algorithme de chiffrement de clé de type WRAP n'est pas pris en charge.|  
|SAMLAssertionMissingIssuerAttributeOnRead|L'attribut 'Issuer' pour l'élément SamlAssertion qui est lu est manquant ou de longueur 0.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|IssuanceTokenProvider a utilisé le jeton de service mis en cache.|  
|AESCryptGetKeyParamFailed|Échec de l'obtention du paramètre de clé spécifique.|  
|InvalidNamespaceForEmptyPrefix|L'espace de noms est non valide pour le préfixe vide.|  
|AESCipherModeNotSupported|Le mode de chiffrement spécifique n'est pas pris en charge. Seul CBC est pris en charge.|  
|ArgumentCannotBeEmptyString|L'argument doit être une chaîne non vide.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|L'attribut MinorVersion pour l'élément SamlAssertion qui est lu est manquant ou de longueur 0.|  
|SpecifiedStringNotAvailableInDictionary|La chaîne spécifiée n'est pas une entrée du dictionnaire actuel.|  
|KerberosApReqInvalidOrOutOfMemory|Le message AP-REQ (Application Request) est non valide ou la mémoire du système est insuffisante.|  
|FailLogonUser|Échec de LogonUser pour l'utilisateur spécifié. Vérifiez que l'utilisateur possède un compte Windows valide.|  
|ValueMustBeNonNegative|La valeur de cet argument doit être non négative.|  
|X509ValidationFail|Échec de la validation du certificat X.509 spécifié.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|L'opération de session de sécurité a abouti sur le client.|  
|SAMLActionNameRequiredOnRead|La chaîne qui est lue pour l'élément SamlAction est manquante ou de longueur 0.|  
|KerberosMultilegsNotSupported|L'identité est spécifiée sous forme d'UPN. L'authentification d'un service qui s'exécute sous un compte d'utilisateur requiert Kerberos « multi-leg », lequel n'est pas pris en charge.|  
|SAMLAssertionIdRequired|L'attribut 'assertionId' pour un élément SamlAssertion ne peut ni être null, ni être vide.|  
|InvalidOperationForWriterState|L'opération spécifiée est non valide dans l'état XmlWriter spécifié.|  
|CannotValidateSecurityTokenType|L'authentificateur de jetons de sécurité spécifié ne peut pas valider un jeton du type spécifié.|  
|X509FindValueMismatch|L’élément X509FindType spécifié requiert que le type de l’argument findValue soit la valeur spécifiée. L’argument findValue est d’un autre type.|  
|TraceCodeSecurityClientSessionCloseSent|Un message fermé a été envoyé par la session de sécurité du client.|  
|SuiteDoesNotAcceptAlgorithm|L'algorithme spécifié n'est pas accepté pour l'opération spécifiée par la suite algorithmique spécifiée|  
|TraceCodeSecuritySessionRequestorOperationFailure|Échec de l'opération de session de sécurité client.|  
|SAMLUnableToLoadStatement|Échec du chargement d'un élément SamlStatement.|  
|InnerReaderMustBeAtElement|Le lecteur interne doit se trouver au niveau de l'élément.|  
|UnableToCreateTokenReference|Création d'une référence de jeton de sécurité impossible.|  
|TraceCodeSecurityBindingIncomingMessageVerified|Le protocole de sécurité a vérifié le message entrant.|  
|ObjectIsReadOnly|L'objet est en lecture seule.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|La session de sécurité du client a ignoré la clé de session précédente.|  
|SAMLTokenTimeInvalid|L'élément SamlToken n'est pas compris dans la limite de validité. Le temps actuel se situe en dehors des valeurs des délais de validité et d'expiration du jeton.|  
|TraceCodeSecurityIdentityVerificationSuccess|La vérification d'identité a réussi.|  
|SigningTokenHasNoKeys|Le jeton de signature spécifié ne contient aucune clé.|  
|TraceCodeSecurityIdentityVerificationFailure|Échec de la vérification d'identité.|  
|AESCryptImportKeyFailed|Échec de l'importation de la clé.|  
|FailInitializeSecurityContext|Échec de InitializeSecurityContent. Vérifiez que le nom de principal du service est correct.|  
|TraceCodeStreamSecurityUpgradeAccepted|La mise à niveau de la sécurité du flux s'est correctement déroulée.|  
|SAMLAuthorityBindingRequiresLocation|L'attribut 'Location' spécifié sur l'élément SamlAuthorityBinding ne peut ni être null, ni être de longueur 0.|  
|PublicKeyNotDSA|La clé publique n'est pas une clé DSA.|  
|ImpersonationLevelNotSupported|Les modes d'authentification qui utilisent Kerberos ne prennent pas en charge le niveau d'emprunt d'identité spécifié. Spécifiez un niveau d'identification ou d'emprunt d'identité valide.|  
|RequiredTargetNotSigned|L'élément avec l'ID spécifié doit être signé, mais il ne l'était pas.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|L'attribut 'AuthenticationInstant' qui est lu pour un élément SamlAuthenticationStatement est manquant ou de longueur 0.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|L'élément SamlEvidence qui est lu ne contenait pas d'entité SamlAssertion imbriquée ni de référence vers celle-ci.|  
|LengthOfArrayToConvertMustGreaterThanZero|La longueur du tableau à convertir en nombre entier doit être supérieure à 0.|  
|InvalidAsyncResult|AsyncResult non valide.|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|IssuanceTokenProvider a supprimé le jeton de service expiré.|  
|IncorrectUserNameFormat|Le format du nom d'utilisateur est non valide. Le format du nom d’utilisateur doit se présenter sous la forme « username » ou « Domain \\ \username ».|  
|TraceCodeExportSecurityChannelBindingEntry|Démarrage de Security ExportChannelBinding.|  
|UnsupportedInputTypeForTransform|Le type d'entrée spécifié n'est pas pris en charge pour la transformation.|  
|CannotFindDocumentRoot|Impossible de trouver la racine du document.|  
|XmlBufferQuotaExceeded|La taille nécessaire à la mise en mémoire tampon du contenu XML a dépassé le quota de mémoire tampon.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|Échec lors de l'envoi d'une réponse de fermeture de session de sécurité au client.|  
|UnableToResolveReferenceInSamlSignature|Impossible de résoudre la référence spécifiée dans la signature SAML avec AssertionID.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|La valeur de 'NameIdentifier' ou de 'ConfirmationMethod' doit être spécifiée pou l'élément SamlSubject. Il manquait les deux.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|La valeur de 'Namespace' pour l'élément SamlAttribute qui est lu est manquante ou de longueur 0.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|'ConfirmationMethod' introuvable sur l'élément SamlSubjectConfirmation qui est lu.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|L’exigence du jeton présente un type inattendu pour la propriété spécifiée. Le type de propriété attendu est une autre valeur.|  
|TraceCodeNegotiationTokenProviderAttached|NegotiationTokenProvider a été joint.|  
|TraceCodeSpnegoClientNegotiationCompleted|SpnegoTokenProvider a terminé la négociation SSPI.|  
|SAMLUnableToLoadUnknownElement|L'entité SamlSerializer sélectionné est incapable de désérialiser l'élément. Inscrivez un SamlSerializer personnalisé pour désérialiser des éléments personnalisés.|  
|CreateSequenceRefused|La demande de la séquence création a été refusée par la destination de messagerie fiable.|  
|TraceCodeSecuritySessionRedirectApplied|La session de sécurité du client a été redirigée.|  
|SecurityTokenRequirementDoesNotContainProperty|L'exigence du jeton ne contient pas la propriété spécifiée.|  
|SAMLAttributeValueCannotBeNull|L'une des valeurs de attributeValues trouvées dans l'élément SamlAttribute s'est avérée null. Vérifiez que les valeurs des listes ne sont pas null lors de la création de l'élément SamlAttribute.|  
|ValueMustBeGreaterThanZero|La valeur de cet argument doit être supérieure à 0.|  
|TraceCodeNegotiationAuthenticatorAttached|NegotiationTokenAuthenticator a été joint.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Un élément SamlAuthorizationDecisionStatement doit comporter au moins un élément SamlAction.|  
|TraceCodeSecurityTokenAuthenticatorClosed|L'authentificateur de jetons de sécurité a été fermé.|  
|TraceCodeSecurityAuditWrittenSuccess|Le journal d'audit de sécurité est correctement écrit.|  
|PrivateKeyNotDSA|La clé privée n'est pas une clé DSA.|  
|MessageNumberRollover|Dépassement du nombre maximal de séquences pour cette séquence.|  
|AESPaddingModeNotSupported|Le mode de remplissage spécifié n'est pas pris en charge. Seuls PKCS7 et ISO10126 sont pris en charge.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Les éléments 'NameIdentifier' et 'ConfirmationMethod' requis sont introuvables pour l'élément SamlSubject qui est lu.|  
|TraceCodeSecurityAuditWrittenFailure|Échec survenu lors de l'écriture dans le journal d'audit de sécurité.|  
|UnsupportedCryptoAlgorithm|L'algorithme de chiffrement spécifié n'est pas pris en charge dans ce contexte.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|Le jeton de signature ne possède aucune clé prenant en charge la suite algorithmique spécifiée.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|La chaîne 'Identifier' pour l'élément SamlNameIdentifier qui est lu est manquante.|  
|SAMLSubjectStatementRequiresSubject|L'élément SAML Subject Statement requiert la spécification d'un élément SAML subject.|  
|TraceCodeSslClientCertMissing|Le client SSL distant n'a pas réussi à fournir un certificat requis.|  
|SAMLTokenVersionNotSupported|La version principale spécifiée et la version secondaire ne sont pas prises en charge.|  
|TraceCodeConfigurationIsReadOnly|La configuration est en lecture seule.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Échec lors de l'envoi d'une erreur de renouvellement sur la clé de session de sécurité au client.|  
|TraceCodeSecurityInactiveSessionFaulted|Une session de sécurité inactive a été prise en faute par le serveur.|  
|SAMLUnableToLoadAttribute|Échec du chargement d'un élément SamlAttribute.|  
|Psha1KeyLengthInvalid|La longueur de la clé PSHA1 spécifiée est non valide.|  
|KeyIdentifierCannotCreateKey|Cet élément SecurityKeyIdentifier ne dispose d'aucune clause pouvant créer une clé.|  
|X509IsInUntrustedStore|Le certificat X.509 spécifié se trouve dans un magasin de certificats non fiable.|  
|UnexpectedXmlChildNode|Le nœud enfant XML spécifié de type spécifié est inattendu pour l'élément spécifié.|  
|TokenDoesNotMeetKeySizeRequirements|Les conditions relatives à la taille de clé pour la suite algorithmique spécifiée ne sont pas satisfaites par le jeton spécifié.|  
|TraceCodeSecuritySessionRequestorStartOperation|Une opération de session de sécurité a démarré sur le client.|  
|InvalidHexString|Format de chaîne hexadécimale non valide.|  
|SamlAttributeClaimResourceShouldBeAString|Ce constructeur SamlAttribute requiert que la ressource de la revendication soit de type 'string'.|  
|SamlSigningTokenNotFound|L'entité SamlAssertion est signée mais le jeton qui l'a signé est introuvable. Vérifiez que l'élément SecurityTokenResolver contient le jeton qui a signé l'entité SamlAssertion.|  
|TraceCodeSecuritySpnToSidMappingFailure|Impossible de mapper ServicePrincipalName à un élément SecurityIdentifier.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Création d'un module de formatage de signature impossible pour l'algorithme spécifié à partir de la cryptographie asymétrique spécifiée.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Une session de sécurité serveur a envoyé une erreur de fermeture de session au client.|  
|UnableToFindPrefix|Impossible de trouver le préfixe pour le préfixe spécifié apparemment utilisé au niveau de l'élément spécifié.|  
|TraceCodeSecurityTokenAuthenticatorOpened|L'authentificateur de jetons de sécurité a été ouvert.|  
|RequiredAttributeMissing|L'attribut spécifié est requis sur l'élément spécifié.|  
|LocalIdCannotBeEmpty|'localId' ne peut pas être vide : spécifiez une valeur valide.|  
|ValueMustBeInRange|La valeur de cet argument doit être comprise dans la plage spécifiée.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|IssuanceTokenProvider a démarré une nouvelle négociation de sécurité.|  
|InvalidNtMapping|Mappage du certificat X.509 spécifié à un compte Windows impossible. L'autre nom du sujet UPN est requis.|  
|AESCryptSetKeyParamFailed|Échec de la définition du paramètre de clé spécifié.|  
|TraceCodeSecuritySessionClosedResponseReceived|La session de sécurité client a reçu une réponse de fermeture en provenance du serveur.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Création d'un module de déformatage de signature impossible pour l'algorithme spécifié à partir de la cryptographie asymétrique spécifiée.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Un rappel asynchrone a levé une exception.|  
|LengthMustBeGreaterThanZero|La longueur de cet argument doit être supérieure à 0.|  
|FoundMultipleCerts|Plusieurs certificats X.509 ont été trouvés en utilisant les critères de recherche spécifiés : StoreName, StoreLocation, FindType, FindValue. Indiquez une valeur de recherche plus précise.|  
|AtLeastOneTransformRequired|L'élément Transforms doit au moins contenir une transformation.|  
|SAMLTokenNotSerialized|Sérialisation de l'élément SamlAssertion en flux XML impossible. Consultez l'exception interne pour plus de détails.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|Le protocole de sécurité a sécurisé le message sortant.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Cet élément SecurityKeyIdentifierClause ne prend pas en charge la création de clé.|  
|UnableToResolveTokenReference|Le programme de résolution de jeton n'est pas en mesure de résoudre la référence de jeton spécifiée.|  
|UnsupportedEncryptionAlgorithm|L'algorithme de chiffrement spécifié n'est pas pris en charge.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|L'élément SamlSerializer ne contient aucun élément SecurityTokenSerializer capable de sérialiser l'entité SecurityKeyIdentifier donnée. Si vous utilisez une entité SecurityKeyIdentifier personnalisée, vous devez fournir un élément SecurityTokenSerializer personnalisé.|  
|SAMLAttributeShouldHaveOneValue|Aucune valeur d'attribut n'a été trouvée. Un attribut SamlAttribute doit posséder au moins une valeur d'attribut.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Le protocole de sécurité ne peut pas vérifier le message entrant.|  
|SamlSigningTokenMissing|L'entité SamlAssertion passée à l'élément SamlSecurityTokenAuthenticator ne contient pas de jeton de signature.|  
|NoPrivateKeyAvailable|Aucune clé privée n'est disponible.|  
|ValueMustBeOne|La valeur de cet argument doit être 1.|  
|TraceCodeSecurityPendingServerSessionRemoved|Une session de sécurité en attente a été activée par le serveur.|  
|TraceCodeImportSecurityChannelBindingExit|Security ImportChannelBinding terminé.|  
|X509CertStoreLocationNotValid|L'emplacement StoreLocation doit être soit LocalMachine, soit CurrentUser.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Les paramètres de l'enregistreur sont uniquement modifiables lorsque l'enregistreur se trouve dans l'état de démarrage.|  
|ArgumentInvalidCertificate|Le certificat est non valide.|  
|DigestVerificationFailedForReference|Échec de la vérification du condensat pour la référence spécifiée.|  
|SAMLAuthorityBindingRequiresBinding|L'attribut 'Binding' spécifié sur l'élément SamlAuthorityBinding ne peut ni être null, ni être de longueur 0.|  
|AESInsufficientOutputBuffer|La mémoire tampon de sortie doit être supérieure au nombre d'octets spécifié.|  
|SAMLAuthorityBindingMissingBindingOnRead|L'attribut 'Binding' pour l'élément SamlAuthorityBinding qui est lu est manquant ou de longueur 0.|  
|SAMLAuthorityBindingInvalidAuthorityKind|L'élément SamlAuthorityBinding qui est lu comporte un élément AuthorityKind non valide. Le format de AuthorityKind doit être un nom complet.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|L'élément NetworkCredentials fourni pour le jeton Kerberos n'a pas de UserName valide.|  
|SSPIPackageNotSupported|Le package SSPI spécifié n'est pas pris en charge.|  
|TokenCancellationNotSupported|Le fournisseur de jetons spécifié ne prend pas en charge l'annulation des jetons.|  
|UnboundPrefixInQName|Un préfixe indépendant est utilisé dans le nom complet spécifié.|  
|SAMLAuthorizationDecisionResourceRequired|L'élément 'resource' spécifié sur l'entité SamlAuthorizationDecisionStatement ne peut ni être null, ni être de longueur 0.|  
|TraceCodeSecurityNegotiationProcessingFailure|Échec du traitement de la négociation de sécurité des services.|  
|SAMLAssertionIssuerRequired|L'attribut 'Issuer' spécifié pour un élément SamlAssertion ne peut ni être null, ni être vide.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Création d'un élément HashAlgorithm impossible pour l'algorithme spécifié à partir de la cryptographie asymétrique spécifiée.|  
|SamlUnableToExtractSubjectKey|L'élément SecurityKeyIdentifier qui a été trouvé dans l'entité SamlSubject ne peut pas être résolu sur un élément SecurityToken. L'élément SecurityTokenResolver doit contenir un élément SecurityToken que l'entité SecurityKeyIdentifier doit résoudre.|  
|ChildNodeTypeMissing|L'élément XML spécifié n'a pas d'enfant du type spécifié.|  
|TraceCodeSecurityPendingServerSessionClosed|La session de sécurité en attente a été fermée par le serveur.|  
|TraceCodeSecuritySessionCloseResponseSent|La session de sécurité du serveur a envoyé une réponse de fermeture au client.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|Impossible de normaliser la partie HostName d'une adresse de point de terminaison.|  
|FailAcceptSecurityContext|Échec de AcceptSecurityContext.|  
|EmptyXmlElementError|L'élément spécifié ne peut pas être vide.|  
|PrefixNotDefinedForNamespace|Un préfixe pour l'espace de noms spécifié n'est pas défini dans ce contexte et il est impossible de déclarer ce contexte.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|L'entité SamlAuthorizationDecisionStatement qui est lue s'est avérée contenir plusieurs éléments Evidence. Cette opération n’est pas autorisée.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|L'élément SamlSecurityTokenAuthenticator ne peut traiter que les éléments SamlSecurityTokens. L'élément SecurityTokenType spécifié a été reçu.|  
|SAMLAttributeStatementMissingAttributeOnRead|L'élément SamlAttributeStatement qui est lu ne contient pas d'élément 'SamlAttribute'. Cette opération n’est pas autorisée.|  
|CouldNotFindNamespaceForPrefix|Impossible de rechercher le préfixe spécifié dans l'espace de noms.|  
|TraceCodeExportSecurityChannelBindingExit|Security ExportChannelBinding terminé.|  
|AESCryptDecryptFailed|Échec du déchiffrement des données spécifiées.|  
|SAMLAttributeNamespaceAttributeRequired|La valeur de 'Namespace' spécifiée pour un élément SamlAttribute ne peut ni être null, ni être de longueur 0.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator a terminé la négociation SSPI.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|La session de sécurité du serveur a envoyé une erreur de renouvellement de clé au client.|  
|AlgorithmMismatchForTransform|Une incompatibilité s'est produite sur l'algorithme pour la transformation.|  
|UserNameAuthenticationFailed|Échec de l'authentification d'un nom d'utilisateur/mot de passe à l'aide du mécanisme spécifié. L'utilisateur n'est pas authentifié.|  
|SamlInvalidSigningToken|L'entité SamlAssertion a été signée à l'aide d'un jeton qui n'a pas été validé conformément au protocole. Si vous utilisez des certificats X.509, vérifiez votre sémantique de validation.|  
|TraceCodeSecurityServerSessionKeyUpdated|La clé de session de sécurité a été mise à jour par le serveur.|  
|TraceCodeSecurityServerSessionCloseReceived|La session de sécurité du serveur a reçu un message de fermeture du client.|  
|SAMLAuthenticationStatementMissingSubject|L'élément SamlAuthenticationStatement ne possède pas l'élément SamlSubjectStatement requis.|  
|UnexpectedEndOfFile|Fin de fichier inattendue.|  
|UnsupportedAlgorithmForCryptoOperation|L'algorithme spécifié n'est pas pris en charge pour l'opération spécifiée.|  
|XmlLangAttributeMissing|L'attribut xml:lang requis est manquant.|  
|TraceCodeSecurityImpersonationSuccess|Réussite de l'emprunt d'identité de sécurité sur le serveur.|  
|SAMLAuthorityBindingMissingLocationOnRead|L'attribut 'Location' pour l'élément SamlAuthorityBinding qui est lu est manquant ou de longueur 0.|  
|SAMLAttributeStatementMissingSubjectOnRead|L'élément 'SamlSubject' pour l'entité SamlAttributeStatement est manquant.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|L'élément 'SamlSubject' pour l'entité SamlAuthorizationDecisionStatement qui est lue est manquant.|  
|SAMLBadSchema|Lors de la lecture d'une entité SamlAssertion, l'élément spécifié s'est avéré ne pas se conformer au schéma.|  
|SAMLAssertionIDIsInvalid|La chaîne 'assertionId' spécifiée pour un élément SamlAssertion doit commencer par une lettre ou par '_'.|  
|TraceCodeSecurityActiveServerSessionRemoved|Une session de sécurité active a été supprimée par le serveur.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Création d'un élément keyedHashAlgorithm impossible pour l'algorithme spécifié à partir de la cryptographie symétrique spécifiée.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|L'élément 'AuthenticationMethod' spécifié pour une entité SamlAuthenticationStatement ne peut ni être null, ni être de longueur 0.|  
|TraceCodeSecurityImpersonationFailure|Échec de l'emprunt d'identité de sécurité sur le serveur.|  
|Default|(Par défaut)|  
|UnsupportedNodeTypeInReader|Le type de nœud spécifié doté du nom spécifié n'est pas pris en charge.|
