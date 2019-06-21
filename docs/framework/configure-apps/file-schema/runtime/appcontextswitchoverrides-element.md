---
title: Élément <AppContextSwitchOverrides>
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04f31748fd53fe3281102fcadcc1e56ea3cc1109
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307090"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides > élément
Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.  
  
 \<configuration>  
 \<runtime>  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`value`|Attribut requis.<br /><br /> Définit un ou plusieurs noms de commutateur et leurs valeurs Boolean associées.|  
  
### <a name="value-attribute"></a>valeur d’attribut  
  
|Value|Description|  
|-----------|-----------------|  
|"name=value"|Un nom de commutateur prédéfinis ainsi que sa valeur (`true` ou `false`). Plusieurs paires nom/valeur de commutateur sont séparés par des points-virgules (« ; »). Pour obtenir la liste de noms de commutateurs prédéfinis pris en charge par le .NET Framework, consultez la section Notes.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 En commençant par le .NET Framework 4.6, la `<AppContextSwitchOverrides>` élément dans un fichier de configuration permet aux appelants d’une API pour déterminer si son application peut tirer parti des nouvelles fonctionnalités ou préserver la compatibilité avec les versions précédentes d’une bibliothèque. Par exemple, si le comportement d’une API a changé entre deux versions d’une bibliothèque, le `<AppContextSwitchOverrides>` élément permet aux appelants de cette API pour désactiver le nouveau comportement sur les versions qui prennent en charge les nouvelles fonctionnalités de la bibliothèque. Pour les applications qui appellent les API dans le .NET Framework, le `<AppContextSwitchOverrides>` élément permettent également des appelants dont les applications ciblent une version antérieure du .NET Framework à opter pour nouvelles fonctionnalités si leur application est en cours d’exécution sur une version du .NET Framework qui inclut qui fonctionnalité.  
  
 Le `value` attribut de la `<AppContextSwitchOverrides>` élément se compose d’une chaîne unique qui se compose d’une ou plusieurs paires nom/valeur séparées par un point-virgule.  Chaque nom identifie un commutateur de compatibilité, et sa valeur correspondante est une valeur booléenne (`true` ou `false`) qui indique si le commutateur est défini. Par défaut, le commutateur est `false`, et les bibliothèques fournissent la nouvelle fonctionnalité. Ils fournissent uniquement les fonctionnalités précédentes si le commutateur est défini (autrement dit, sa valeur est `true`). Cela permet aux bibliothèques fournir le nouveau comportement pour une API existante tout en permettant aux appelants qui varient selon le comportement précédent pour désactiver la nouvelle fonctionnalité.  
  
 Le .NET Framework prend en charge les commutateurs suivants :  
  
|Nom du commutateur|Description|Introduite|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Détermine si Windows Presentation Foundation utilise hérité d’un algorithme pour contrôler la disposition. Pour plus d’informations, consultez [Atténuation : Disposition WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Contrôle si l’algorithme par défaut utilisé pour la signature des parties d’un package par PackageDigitalSignatureManager est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Lorsque la valeur `false`, permet le débogage de projets de workflow basé sur XAML avec Visual Studio lorsque FIPS est activé. Sans cela, un <xref:System.NullReferenceException> est levée dans les appels aux méthodes dans l’assembly System.Activities.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Détermine si la somme de contrôle pour une instance de flux de travail dans le débogueur utilise MD5 ou SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Détermine si le hachage de somme de contrôle de flux de travail utilise l’algorithme SHA1 présenté comme la valeur par défaut dans .NET Framework 4.7 (`true`), ou qu’elle utilise l’algorithme SHA256 par défaut introduit en tant que la valeur par défaut dans .NET Framework 4.8 (`false`).<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Contrôle si les traces de pile obtenir lors de l’utilisation des fichiers PDB portables peut inclure des informations de fichier et de ligne source. `false` Pour inclure les informations de fichier et de ligne source ; Sinon, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Contrôles si le <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> méthode lève une exception quand un <xref:System.Drawing.Icon> objet comporte des cadres PNG. Pour plus d’informations, consultez [Atténuation : Des cadres PNG dans les objets Icon](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Détermine si <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> les objets sont correctement supprimés lors de l’ajout à la collection par le <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> (méthode). `true` Pour conserver le comportement hérité ; `false` à dispose de tous les objets de polices privées. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Contrôles si les performances de la <xref:System.Windows.Forms.PrintPreviewDialog> est optimisé pour les imprimantes réseau. Pour plus d’informations, consultez [vue d’ensemble du contrôle PrintPreviewDialog](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Contrôle si la plage de l’année vérifie pour le calendrier japonais ères sont appliquées. `true` Pour appliquer la plage de l’année les vérifications, et `false` pour les désactiver (comportement par défaut). Pour plus d’informations, consultez [utilisation des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Contrôle si uniquement « 1 » est reconnu en tant que la première année d’une ère du calendrier japonais dans les opérations d’analyse. `true` pour reconnaître uniquement « 1 » ; `false` pour reconnaître des « 1 » ou Gannen du (comportement par défaut). Pour plus d’informations, consultez [utilisation des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Contrôle si la première année d’une ère du calendrier japonais est représentée en tant que « 1 » ou Gannen dans les opérations de mise en forme. `true` Pour formater la première année de l’ère « 1 » ; `false` formater en tant que Gannen du (comportement par défaut). Pour plus d’informations, consultez [utilisation des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Contrôle si les opérations asynchrones ne sont pas acheminées à partir du contexte du thread appelant. Pour plus d’informations, consultez [CurrentCulture et CurrentUICulture transmis entre des tâches](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Contrôles si le <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> méthode tente de faire correspondre le type de revendication uniquement avec la dernière entrée DNS. Pour plus d’informations, consultez [Atténuation : Méthode X509CertificateClaimSet.FindClaims](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Détermine s’il faut autoriser AuthorizationContext.Empty retourner un objet mutable.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Contrôles si chemins de plus de `MAX_PATH` (260 caractères) lèvent une <xref:System.IO.PathTooLongException>. Pour plus d’informations, consultez [prise en charge du chemin d’accès longs](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Contrôle si les commandes du système d’exploitation d’origine sont utilisées pour la décompression à la <xref:System.IO.Compression.DeflateStream> classe. `false` Pour utiliser des API natives ; `true` à utiliser le <xref:System.IO.Compression.DeflateStream> implémentation.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Utilise la barre oblique inverse («\\») au lieu de la barre oblique (« / ») comme séparateur de chemin d’accès dans le <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriété. Pour plus d’informations, consultez [atténuation : Séparateur de chemin ZipArchiveEntry.FullName](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Détermine si le fonctionnement des exceptions de système qui sont levées sur les threads d’arrière-plan créés avec <xref:System.IO.Ports.SerialPort> flux mettre fin au processus.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Détermine si la normalisation de chemin d’accès héritée est utilisée et chemins d’URI sont pris en charge par le <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> méthodes. Pour plus d’informations, consultez [Atténuation : Normalisation des chemins](../../../migration-guide/mitigation-path-normalization.md) et [atténuation : Vérifications des signes deux-points de chemin d’accès](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Détermine si un test pour l’égalité compare le <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> propriété d’un objet avec le <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> propriété du deuxième objet. Pour plus d’informations, consultez [implémentation incorrecte de MemberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Désactive la validation de l’utilisation de clé améliorée (EKU) objet identificateur (OID) des certificats. Une extension EKU (utilisation améliorée de la clé) est une collection d’identificateurs d’objet indiquant les applications qui utilisent la clé.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Désactive l’atténuation de TLS 1.0 navigateur exploiter sur SSL/TLS (BEAST) en désactivant l’utilisation de SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Contrôles si le <xref:System.Net.ServicePointManager?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes peuvent utiliser le protocole SSL 3.0. Pour plus d’informations, consultez [Atténuation : protocoles TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Désactive les versions SystemDefault TLS retour à la valeur par défaut est Tls12, Tls11, Tls.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Désactive les alertes de côté serveur SslStream TLS.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Contrôle si les paramètres ByRef SafeArray sur les événements d’interopérabilité COM marshaler en code natif (`false`) ou si le marshaling au code natif est désactivé (`true`).|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Contrôles si le [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) sérialise certains caractères de contrôle basées sur les normes ECMAScript V6 et V8. Pour plus d’informations, consultez [Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Contrôles si le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prend en charge plusieurs ajustements ou uniquement un seul réglage pour un fuseau horaire. Si `true`, il utilise le <xref:System.TimeZoneInfo> type à sérialiser et désérialiser des données de date et heure ; sinon, il utilise le <xref:System.TimeZone> type, qui ne prend pas en charge plusieurs règles d’ajustement.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Contrôles si <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> utilise une plus grande taille de tableau pendant la sérialisation de l’objet et de la désérialisation. Définissez ce commutateur sur `true` pour améliorer les performances de la sérialisation et la désérialisation de graphiques d’objets volumineux en types tels que <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Contrôles si le <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> constructeur définit le nouvel objet <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> propriété avec une référence d’objet existant. Pour plus d’informations, consultez [Atténuation : Constructeur ClaimsIdentity](../../../migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Contrôles si la tentative de réutiliser une <xref:System.Security.Cryptography.AesCryptoServiceProvider> déchiffreur lève un <xref:System.Security.Cryptography.CryptographicException>. Pour plus d’informations, consultez [le déchiffreur AesCryptoServiceProvider fournit une transformation réutilisable](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Contrôles si la valeur de la [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) propriété est un [IntPtr](xref:System.IntPtr) que représente l’emplacement de mémoire d’une fenêtre Gérer, ou s’il s’agit d’un handle de fenêtre (HWND). Pour plus d’informations, consultez [Atténuation : CspParameters.ParentWindowHandle attend un HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Contrôle si les classes de l’utilisation du chiffrement géré dans FIPS mode lève un <xref:System.Security.Cryptography.CryptographicException> (`true`) ou s’appuie sur l’implémentation de bibliothèques système (`false`).|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Détermine si la valeur par défaut pour certaines opérations SignedCMS est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Contrôles si le <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithtype> méthode gère correctement les courbes toutes nommées pris en charge par le système d’exploitation (`false`) ou reviennent au comportement hérité.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Détermine si la valeur par défaut pour certaines opérations SignedXML est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Détermine si le `TransportWithMessageCredential` mode de sécurité permet de messages avec un en-tête « to ». Il s’agit d’une option d’activation. Pour plus d’informations, consultez [modifications du Runtime dans .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Contrôles si le <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructeur lève un <xref:System.ArgumentException> si un des éléments est `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Détermine que si la tentative d’utilisation X509 certificats avec un fournisseur de stockage de clés CSG LÈVENT une exception. Pour plus d’informations, consultez [sécurité du transport WCF prend en charge les certificats stockés à l’aide de CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Lorsque vous utilisez le transport HTTP avec un service auto-hébergé, la valeur `true` entraîne à ignorer l’ajout d’une application WCF le `Connection: close` en-tête pour les en-têtes de réponse pour une demande. La valeur `false` permettant d’ajouter le `Connection: close` en-tête pour les en-têtes de réponse, ce qui entraîne la fermeture du socket de la demande après l’envoi d’une réponse.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Gère les blocages qui résultent de restriction des instances d’un service réentrant à un seul thread d’exécution à la fois.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Avec `Switch.System.Net.DontEnableSchUseStrongCrypto`, détermine si la sécurité des messages WCF utilise TLS 1.1 et TLS 1.2.|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|La valeur `false` définit la configuration par défaut pour permettre au système d’exploitation à choisir le protocole. La valeur `true` définit la valeur par défaut pour le protocole le plus élevé disponible. (Également disponible sur la branche des précédentes versions de framework de maintenance)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Détermine si l’algorithme pour les messages MSMQ dans WCF de signature des messages de par défaut est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Contrôle si WCF utilise un SHA1 ou un hachage SHA256 pour générer des noms aléatoires pour les canaux nommés.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Indique s’il faut lever une [NullReferenceException](xref:System.NullReferenceException) lorsque le message d’exception est null.|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Contrôle si les exceptions levées au démarrage du service sont propagées à l’appelant de la <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> (méthode).|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Contrôles si <xref:System.Threading.Timer> instances tirer parti des améliorations des performances pour les environnements à grande échelle. Si `true`, les améliorations de performances sont activées ; si `false` (la valeur par défaut), elles sont désactivées.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Détermine si certains caractères encodés en pourcentage qui étaient parfois décodés sont demeurent désormais systématiquement encodés. Si `true`, ils sont décodés ; sinon, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Détermine la gestion des caractères de bidirectionnels Unicode dans les URI. `true` pour les supprimer à partir des URI ; `false` pour conserver et encodez-les-%.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Détermine si Windows Presentation Foundation s’applique à un ancien algorithme (`true`) ou un nouvel algorithme (`false`) dans l’allocation d’espace pour \*-colonnes. Pour plus d’informations, consultez [Atténuation : Allocation d’espace du contrôle de grille de colonnes en étoile](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Événement de modification de contrôles si un sélecteur ou un onglet de contrôle toujours met à jour la valeur de sa propriété valeur sélectionnée avant le déclenchement de la sélection.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Détermine si le rendu de la sélection en fonction non ornement est disponible pour le <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.PasswordBox> contrôles pour empêcher un vaisseau texte (`false`), ou si le texte est rendu uniquement dans la couche d’ornement (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Contrôle si des indexeurs IList personnalisés sont utilisés correctement (`false`) ou correctement (`true`) par le <xref:System.Windows.Data.Binding?displayProperty=nameWithtype> classe.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Détermine si les modifications de la résolution se produisent sur un système par (valeur `false`) ou par moniteur (valeur `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Contrôles si les améliorations de dimensionnement de contrôles dans un <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> quand WPF est exécutée en mode prenant en charge par moniteur sont désactivées (`true`) ou activée (`false`).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Détermine si le développeur doit gérer spécialement les <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action lorsque le texte du contrôle est présent. `true` pour gérer le <xref:System.Windows.Forms.DomainUpDown.UpButton> action ; `false` pour le <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> et <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions soit correctement synchronisée.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Refuse le code qui permet une personnalisée <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implémentation en toute sécurité filtrer les messages sans lever d’exception lorsque la <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> méthode est appelée. Pour plus d’informations, consultez [Atténuation : Implémentations IMessageFilter.PreFilterMessage personnalisées](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Détermine si le <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriété retourne le contrôle de code source lorsque l’utilisateur ouvre le menu à partir d’une liste imbriquée <xref:System.Windows.Forms.ToolStripMenuItem> contrôle. `true` pour retourner `null`, le comportement hérité ; `false` pour retourner le contrôle de code source.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Contrôle si la prise en charge d’appel info-bulle est désactivé (`true`) ou activée (`false`). L’activation de prise en charge des info-bulle appel nécessite également les fonctionnalités d’accessibilité hérités définies par `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, et `Switch.UseLegacyAccessibilityFeatures.3` tous être désactivée (valeur `false`).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Détermine si un texte facultatif `WM_POINTER`-pile tactile/de stylet en est activé dans les applications WPF. Pour plus d’informations, consultez [Atténuation : Pointeur tactile et prise en charge du stylet](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Détermine si l’algorithme de hachage par défaut utilisé pour les sommes de contrôle est SHA256 (`false`) ou SHA1 (`true`).<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Détermine si un héritage [NullReferenceException](xref:System.NullReferenceException) est levée au lieu de l’exception qui indique plus précisément la cause de l’exception (comme un [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) ou un [ FileNotFoundException](xref:System.IO.FileNotFoundException). Il est destiné à utiliser par le code qui dépend de la gestion de la [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Les contrôles si le hachage de somme de contrôle des fichiers XOML dans le projet de flux de travail génère utilisent l’algorithme MD5 (`true`), ou qu’ils utilisent l’algorithme SHA256 présenté comme la valeur par défaut dans .NET Framework 4.8.<br>En raison de problèmes de collision avec MD5, Microsoft vous recommande de SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Détermine si le hachage de somme de contrôle par le service SqlTrackingService utilise l’algorithme MD5 (`true`) pour les chaînes de mise en cache, ou qu’elle utilise l’algorithme SHA256 présenté comme la valeur par défaut dans .NET Framework 4.8.<br>En raison de problèmes de collision avec MD5, Microsoft vous recommande de SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Détermine si le hachage de somme de contrôle par le Runtime de Workflow utilise l’algorithme MD5 (`true`) pour les définitions de flux de travail mis en cache, ou qu’elle utilise l’algorithme SHA256 présenté comme la valeur par défaut dans .NET Framework 4.8.<br>En raison de problèmes de collision avec MD5, Microsoft vous recommande de SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Contrôles si disponible à partir de .NET Framework 4.7.1 de fonctionnalités d’accessibilité sont activées ou désactivées. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Contrôles si fonctionnalités disponibles dans .NET Framework 4.7.2 d’accessibilité sont activées (`false`) ou désactivé (`true`). Si `true`, `Switch.UseLegacyAccessibilityFeatures` doit également être `true` pour activer les fonctionnalités d’accessibilité de .NET Framework 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Contrôles si les fonctionnalités d’accessibilité introduite dans .NET Framework 4.8 sont activés (`false`) ou désactivé (`true`). Si `true`, `Switch.UseLegacyAccessibilityFeatures` et `Switch.UseLegacyAccessibilityFeatures.2` doit également être `true`.|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Contrôles si les info-bulles sont affichées lorsqu’un utilisateur pointe la souris sur un contrôle WPF (`true`), ou si elles s’affichent à la fois sur le focus clavier et via la touche de raccourci clavier (`false`, le comportement par défaut). Pour les applications s’exécutant sur .NET Framework 4.8 mais ciblant des versions antérieures du .NET Framework, l’activation à la fois le focus clavier et la prise en charge de la clé contextuel requiert que `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, et `Switch.UseLegacyAccessibilityFeatures.3` toutes être définies aux `false`.|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Contrôle si les séquences de touches vides dans les clés composées sont ignorés par la validation de schéma XSD. Pour plus d’informations, consultez [Atténuation : Validation de schéma XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Au lieu d’ajouter un `AppContextSwitchOverrides` élément à un fichier de configuration d’application, vous pouvez également définir les commutateurs par programmation en appelant le `static` (en c#) ou `Shared` (en Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> (méthode).  
  
 Les développeurs de bibliothèque peuvent également définir des commutateurs pour autoriser les appelants à refuser la fonctionnalité modifiée introduite dans les versions ultérieures de leurs bibliothèques. Pour plus d'informations, consultez la classe <xref:System.AppContext>.  
  
## <a name="switches-in-aspnet-applications"></a>Commutateurs dans les applications ASP.NET

Vous pouvez configurer une application ASP.NET pour utiliser les paramètres de compatibilité en ajoutant un [ \<Ajouter >](../../../configure-apps/file-schema/appsettings/add-element-for-appsettings.md) élément à la [ \<appSettings >](../../../configure-apps/file-schema/appsettings/index.md) section du fichier web.config. 

L’exemple suivant utilise le `<add>` élément à ajouter deux paramètres à la `<appSettings>` section d’un fichier web.config :

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Exemple

 L’exemple suivant utilise le `AppContextSwitchOverrides` élément pour définir un commutateur de compatibilité d’application unique, `Switch.System.Globalization.NoAsyncCurrentCulture`, culture qui empêche de circuler entre les threads d’appels de méthode asynchrones.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 L’exemple suivant utilise le `AppContextSwitchOverrides` élément pour définir les deux commutateurs de compatibilité d’application, `Switch.System.Globalization.NoAsyncCurrentCulture` et `Switch.System.IO.BlockLongPaths`. Notez qu’un point-virgule sépare les deux paires nom/valeur.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<runtime > élément](runtime-element.md)
- [\<configuration>, élément](../configuration-element.md)
