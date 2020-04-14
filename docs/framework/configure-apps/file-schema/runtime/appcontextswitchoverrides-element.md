---
title: AppContextSwitchOverrides Élément
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 95ae438e9fb52cc584d18a981bffb66147eb4a77
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242814"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> élément

Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<AppContextSwitchOverrides>**

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

### <a name="value-attribute"></a>attribut de valeur

|Valeur|Description|
|-----------|-----------------|
|"nom-valeur"|Un nom de commutateur prédéfini`true` `false`avec sa valeur ( ou ). Plusieurs paires de noms/valeurs de commutateur sont séparées par des semi-colons («;»). Pour une liste de noms de commutateur prédéfinis pris en charge par le cadre .NET, voir la section Remarques.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|

## <a name="remarks"></a>Notes
 En commençant par le cadre .NET `<AppContextSwitchOverrides>` 4.6, l’élément d’un fichier de configuration permet aux appelants d’une API de déterminer si leur application peut tirer parti de nouvelles fonctionnalités ou préserver la compatibilité avec les versions précédentes d’une bibliothèque. Par exemple, si le comportement d’une API a changé `<AppContextSwitchOverrides>` entre deux versions d’une bibliothèque, l’élément permet aux appelants de cette API de se retirer du nouveau comportement sur les versions de la bibliothèque qui prennent en charge la nouvelle fonctionnalité. Pour les applications qui appellent les API dans le cadre .NET, l’élément `<AppContextSwitchOverrides>` peut également permettre aux appelants dont les applications ciblent une version antérieure du cadre .NET d’opter pour de nouvelles fonctionnalités si leur application est en cours d’exécution sur une version du cadre .NET qui inclut cette fonctionnalité.

 L’attribut `value` `<AppContextSwitchOverrides>` de l’élément se compose d’une seule chaîne qui se compose d’un ou plusieurs paires de nom/valeur délimitées par des pointémilons.  Chaque nom identifie un commutateur de compatibilité, et`true` sa `false`valeur correspondante est un Boolean ( ou ) qui indique si le commutateur est défini. Par défaut, le `false`commutateur est, et les bibliothèques fournissent la nouvelle fonctionnalité. Ils ne fournissent la fonctionnalité précédente que si le commutateur `true`est défini (c’est-à-dire que sa valeur est). Cela permet aux bibliothèques de fournir un nouveau comportement pour une API existante tout en permettant aux appelants qui dépendent du comportement précédent de se retirer de la nouvelle fonctionnalité.

 Le cadre .NET prend en charge les commutateurs suivants :

|Nom de commutateur|Description|Introduit|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Contrôle si Windows Presentation Foundation utilise l’héritage d’un algorithme pour la mise en page de contrôle. Pour plus d’informations, consultez [Atténuation : disposition WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Contrôle si l’algorithme par défaut utilisé pour signer des parties d’un paquet par PackageDigitalSignatureManager est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Lorsqu’il `false`est réglé sur , permet de déboguer des projets de flux de travail basés sur XAML avec Visual Studio lorsque FIPS est activé. Sans elle, <xref:System.NullReferenceException> a est jeté dans les appels aux méthodes dans l’assemblage System.Activities.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Contrôle si le contrôleur d’une instance de flux de travail dans le débruceur utilise MD5 ou SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Contrôle si le hachage de workflow checksum utilise l’algorithme SHA1 introduit`true`comme par défaut dans .NET Framework 4.7 ( ), ou`false`s’il utilise l’algorithme PAR défaut SHA256 introduit comme par défaut dans .NET Framework 4.8 ( ).<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Contrôle si les traces de pile obtiennent lors de l’utilisation des BDP portatifs peuvent inclure des informations de fichier source et de ligne. `false`d’inclure des renseignements sur les fichiers sources et les lignes; autrement, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Contrôle si <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> la méthode lance <xref:System.Drawing.Icon> une exception lorsqu’un objet a des cadres PNG. Pour plus d’informations, consultez [Atténuation : cadres PNG dans les objets Icon](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Détermine si <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> les objets sont correctement éliminés lorsqu’ils sont ajoutés à la collection par la <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> méthode. `true`pour maintenir le comportement hérité; `false` pour disposer de tous les objets de police privés. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Contrôle si les <xref:System.Windows.Forms.PrintPreviewDialog> performances de la est optimisée pour les imprimantes réseau. Pour plus d’informations, voir [Aperçu du contrôle PrintPreviewDialog](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Contrôle si les contrôles de portée d’année pour les ères de calendrier japonais sont appliqués. `true`d’appliquer les contrôles `false` de portée d’année, et de les désactiver (le comportement par défaut). Pour plus d’informations, voir [Travailler avec des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Contrôle si seulement "1" est reconnu comme la première année d’une ère de calendrier japonais dans les opérations d’analyse. `true`ne reconnaître que "1"; `false` reconnaître soit "1" ou Gannen (le comportement par défaut). Pour plus d’informations, voir [Travailler avec des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Contrôle si la première année d’une ère de calendrier japonais est représentée comme «1» ou Gannen dans les opérations de formatage. `true`pour formater la première année de l’époque comme «1»; `false` pour le formater comme Gannen (le comportement par défaut). Pour plus d’informations, voir [Travailler avec des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Contrôle si les opérations asynchrones ne découlent pas du contexte du fil d’appel. Pour plus d’informations, voir [CurrentCulture et CurrentUICulture flux à travers les tâches](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Contrôle si <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> la méthode tente de faire correspondre le type de réclamation uniquement avec la dernière entrée DNS. Pour plus d’informations, consultez [Atténuation : X509CertificateClaimSet.FindClaims (méthode)](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Contrôle s’il y a permis à AuthorizationContext.Empty de renvoyer un objet mutable.|.NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|Contrôle si les `MAX_PATH` chemins plus longs que <xref:System.IO.PathTooLongException>(260 caractères) jeter un . Pour plus d’informations, voir [Long Path Support](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Contrôle si les routines D’OS indigènes <xref:System.IO.Compression.DeflateStream> sont utilisées pour la décompression par la classe. `false`utiliser les API indigènes; `true` d’utiliser <xref:System.IO.Compression.DeflateStream> la mise en œuvre.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Utilise la barre oblique inverse (« »\\plutôt que la barre oblique <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> avant (« /») comme séparateur de chemin dans la propriété. Pour plus d’informations, voir [Mitigation: ZipArchiveEntry.FullName Path Separator](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Contrôle si les exceptions du système d’exploitation qui sont jetées sur les fils de fond créés avec <xref:System.IO.Ports.SerialPort> des flux mettent fin au processus.|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Contrôle si la normalisation des chemins hérités est <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> utilisée et les voies d’URI sont soutenues par les méthodes et les méthodes. Pour plus d’informations, voir [Mitigation: Path Normalization](../../../migration-guide/mitigation-path-normalization.md) and [Mitigation: Path Colon Checks](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Contrôle si un critère d’égalité compare <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> la <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> propriété d’un objet à la propriété du deuxième objet. Pour plus d’informations, voir [mise en œuvre incorrecte de MemberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Validation de l’identifiant d’objet d’utilisation améliorée de l’utilisation des clés (EKU). Une extension EKU (utilisation améliorée de la clé) est une collection d’identificateurs d’objet indiquant les applications qui utilisent la clé.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Désactiver TLS1.0 Browser Exploit Against SSL/TLS (BEAST) atténuation en désactivant l’utilisation de SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Contrôle si <xref:System.Net.ServicePointManager?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> les classes et les classes peuvent utiliser le protocole SSL 3.0. Pour plus d’informations, consultez [Atténuation : protocoles TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Désactiver les versions SystemDefault TLS revenant à un défaut de Tls12, Tls11, Tls.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Désactive les alertes SslStream TLS côté serveur.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Contrôle si byRef SafeArray paramètres sur les événements com`false`interop marshal retour au code`true`natif ( ) ou si le marshaling retour au code natif est désactivé ( ).|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Contrôle si le [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) sérialise certains caractères de contrôle en fonction des normes ECMAScript V6 et V8. Pour plus d’informations, consultez [Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer | Microsoft Docs](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Contrôle si <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> les réglages multiples de prise en charge ou un seul ajustement pour un fuseau horaire. Si, `true`il <xref:System.TimeZoneInfo> utilise le type pour sérialiser et déséialiser les données de date et d’heure; autrement, il <xref:System.TimeZone> utilise le type, qui ne prend pas en charge les règles d’ajustement multiples.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Contrôle <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> si utilise une plus grande taille de tableau pendant la sérialisation et la désétérialisation d’objet. Définissez ce `true` commutateur pour améliorer les performances de la sérialisation et <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>de la désétérialisation des graphiques de grands objets par des types tels que . |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Contrôle si <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29> le constructeur définit la <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> propriété du nouvel objet avec une référence d’objet existante. Pour plus d’informations, consultez [Atténuation : Constructeur ClaimsIdentity](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Contrôle si la tentative <xref:System.Security.Cryptography.AesCryptoServiceProvider> de réutilisation <xref:System.Security.Cryptography.CryptographicException>d’un décrypteur jette un . Pour plus d’informations, voir [AesCryptoServiceProvider décrypteur fournit une transformation réutilisable](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Contrôle si la valeur de la propriété [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) est un [IntPtr](xref:System.IntPtr) qui représente l’emplacement de la mémoire d’une poignée de fenêtre, ou s’il s’agit d’une poignée de fenêtre (un HWND). Pour plus d’informations, consultez [Atténuation : CspParameters.ParentWindowHandle attend un HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Contrôle si l’utilisation de classes de cryptographie <xref:System.Security.Cryptography.CryptographicException> `true`gérée en mode FIPS jette`false`un ( ) ou s’appuie sur la mise en œuvre de bibliothèques système ( ).|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Détermine si le défaut de certaines opérations SignedCMS est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Contrôle si <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> la méthode gère correctement toutes les courbes nommées prises en charge par le système d’exploitation (`false`) ou revient au comportement hérité.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Détermine si le défaut de certaines opérations SignedXML est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Détermine si `TransportWithMessageCredential` le mode de sécurité permet aux messages d’en-tête non signés de « to » . Il s’agit d’un commutateur d’opt-in. Pour plus d’informations, voir [Changements de temps d’exécution dans le cadre .NET 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Contrôle si <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> le constructeur <xref:System.ArgumentException> jette un si `null`l’un des éléments est .|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Détermine si la tentative d’utiliser des certificats X509 avec un fournisseur de stockage à clé CSG fait exception. Pour plus d’informations, voir [les certificats de sécurité de transport WCF stockés à l’aide de GNC](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Lors de l’utilisation du transport HTTP avec un `true` service auto-hébergé, la `Connection: close` fixation de cette valeur pour amener WCF à ignorer une application ajoutant l’en-tête aux en-têtes de réponse pour une demande. Définir cette `false` valeur pour `Connection: close` permettre d’ajouter l’en-tête aux en-têtes de réponse, ce qui entraîne la fermeture de la prise de demande après l’envoi d’une réponse.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Gère les impasses qui résultent de la restriction des cas d’un service de réinsurminateur à un seul fil d’exécution à la fois.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Avec `Switch.System.Net.DontEnableSchUseStrongCrypto`, détermine si la sécurité des messages WCF utilise TLS 1.1 et TLS 1.2.|.NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Une valeur `false` de définit la configuration par défaut pour permettre au système d’exploitation de choisir le protocole. Une valeur `true` de définit la valeur par défaut au protocole le plus élevé disponible. (Également disponible sur la branche de service des versions-cadres précédentes)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Détermine si l’algorithme de signature de messages par défaut pour les messages MSMQ dans WCF est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Contrôle si WCF utilise un SHA1 ou un hachage SHA256 pour générer des noms aléatoires pour les tuyaux nommés.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Contrôle s’il faut lancer un [NullReferenceException](xref:System.NullReferenceException) lorsque le message d’exception est nul.|.NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Contrôle si les exceptions prévues sur le démarrage du <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> service sont propagées à l’appelant de la méthode.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Contrôle <xref:System.Threading.Timer> si les instances tirent parti des améliorations de performance pour les environnements à grande échelle. Si, `true`les améliorations de performance sont activées ; si `false` (la valeur par défaut), ils sont désactivés.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Détermine si certains caractères codés en pourcentage qui ont parfois été décodés sont maintenant constamment codés. Si, `true`ils sont décodés; autrement, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Détermine la manipulation des caractères bidirectionnels Unicode dans les URI. `true`pour les dépouiller des ITI; `false` pour les préserver et les encoder en pourcentage.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Détermine si Windows Presentation Foundation applique`true`un ancien algorithme`false`( ) ou \*un nouvel algorithme ( ) en allouant de l’espace à -colonnes. Pour plus d’informations, consultez [Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Contrôle si un sélecteur ou un contrôle d’onglet met toujours à jour la valeur de sa propriété de valeur sélectionnée avant d’augmenter l’événement modifié de sélection.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Détermine si un rendu de sélection non-Adorner <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> est disponible pour le et`false`les contrôles pour prévenir le texte occluded (), ou si le texte est rendu uniquement dans la couche Adorner (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Contrôle si les indexeurs IList`true`personnalisés sont`false`utilisés <xref:System.Windows.Data.Binding?displayProperty=nameWithType> incorrectement ( ) ou correctement ( ) par la classe.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Détermine si les modifications apportées à l’IDD se produisent selon un système (valeur de `false`) ou par moniteur (valeur de `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Contrôle si les améliorations apportées <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> au dimensionnement des commandes dans un`true`moment OÙ`false`le FMM est exécuté en mode conscient par moniteur sont désactivées ( ) ou activées ( ).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Détermine si le développeur doit <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> gérer spécialement l’action lorsque le texte de contrôle est présent. `true`pour gérer <xref:System.Windows.Forms.DomainUpDown.UpButton> l’action; `false` pour <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> que <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> les actions et les actions soient correctement synchronisées.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Opte hors du code qui <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> permet à une implémentation <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> personnalisée de filtrer en toute sécurité les messages sans jeter une exception lorsque la méthode est appelée. Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Détermine si <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> la propriété retourne le contrôle source lorsque l’utilisateur ouvre le menu à partir d’un contrôle imbriqué. <xref:System.Windows.Forms.ToolStripMenuItem> `true`pour `null`revenir , le comportement hérité; `false` pour retourner le contrôle source.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Contrôle si le support d’invocation d’outiltip est désactivé (`true`) ou activé (`false`). L’activation du support d’invocation d’outils `Switch.UseLegacyAccessibilityFeatures.3` nécessite également des `false`caractéristiques d’accessibilité héritées définies par `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`et toutes sont désactivées (réglées à ).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Détermine si une `WM_POINTER`pile tactile/stylet basée en option est activée dans les applications WPF. Pour plus d’informations, voir [Mitigation: Pointer-based Touch and Stylus Support](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Détermine si l’algorithme de hachage par défaut utilisé`false`pour les`true`checksums est SHA256 ( ) ou SHA1 ( ).<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Contrôle si un héritage [NullReferenceException](xref:System.NullReferenceException) est jeté au lieu de l’exception qui indique plus précisément la cause de l’exception (comme un [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) ou un [FileNotFoundException](xref:System.IO.FileNotFoundException). Il est destiné à une utilisation par code qui dépend de la manipulation de la [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Contrôle si le hachage de chèques des fichiers XOML dans`true`les builds de projet de flux de travail utilise l’algorithme MD5 (), ou s’ils utilisent l’algorithme SHA256 introduit comme par défaut dans .NET Framework 4.8.<br>En raison de problèmes de collision avec MD5, Microsoft recommande SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Contrôle si le hachage de checksum par le SqlTrackingService utilise l’algorithme MD5 (`true`) pour les chaînes mises en cache, ou s’il utilise l’algorithme SHA256 introduit comme par défaut dans .NET Framework 4.8.<br>En raison de problèmes de collision avec MD5, Microsoft recommande SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Contrôle si le hachage de checksum par le Workflow Runtime utilise l’algorithme MD5 (`true`) pour les définitions de flux de travail mis en cache, ou s’il utilise l’algorithme SHA256 introduit comme par défaut dans .NET Framework 4.8.<br>En raison de problèmes de collision avec MD5, Microsoft recommande SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Contrôle si les fonctionnalités d’accessibilité disponibles à partir du cadre .NET 4.7.1 sont activées ou désactivées. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Contrôle si les caractéristiques d’accessibilité disponibles dans .NET`false`Framework 4.7.2 sont activées ( ) ou désactivées (`true`). Si `true` `Switch.UseLegacyAccessibilityFeatures` , doit `true` également être d’activer .NET Framework 4.7.1 caractéristiques d’accessibilité.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Contrôle si les caractéristiques d’accessibilité introduites dans`false`.NET`true`Framework 4.8 sont activées ( ) ou désactivées ( ). Si `true` `Switch.UseLegacyAccessibilityFeatures` , `Switch.UseLegacyAccessibilityFeatures.2` et `true`doit également être .|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Contrôle si les outils sont affichés lorsqu’un utilisateur plane sur`true`le curseur de la souris au-dessus d’un contrôle WPF (), ou s’ils sont affichés à la fois sur la mise au point du clavier et via la clé de raccourci clavier (`false`, le comportement par défaut). Pour les applications fonctionnant sur .NET Framework 4.8 mais ciblant les versions précédentes `Switch.UseLegacyAccessibilityFeatures`du `Switch.UseLegacyAccessibilityFeatures.2`cadre `Switch.UseLegacyAccessibilityFeatures.3` .NET, `false`permettant à la fois la mise au point clavier et le support clé raccourci nécessite que , et tous être fixés à .|.NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Contrôle si les séquences de clés vides dans les touches composées sont ignorées par la validation du schéma XSD. Pour plus d’informations, voir [Mitigation: XML Schema Validation](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|

> [!NOTE]
> Au lieu `AppContextSwitchOverrides` d’ajouter un élément à un fichier de configuration d’application, vous pouvez également définir les commutateurs de manière programmatique en appelant la `static` méthode (en C) ou `Shared` (en base visuelle). <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>

 Les développeurs de bibliothèques peuvent également définir des commutateurs personnalisés pour permettre aux appelants de se retirer des fonctionnalités modifiées introduites dans les versions ultérieures de leurs bibliothèques. Pour plus d'informations, consultez la classe <xref:System.AppContext>.

## <a name="switches-in-aspnet-applications"></a>Commutateurs dans les applications ASP.NET

Vous pouvez configurer une application ASP.NET pour utiliser [ \<](../appsettings/add-element-for-appsettings.md) les paramètres de compatibilité en ajoutant un élément Add>aux [ \<appSettings>](../appsettings/index.md) section du fichier web.config.

L’exemple suivant `<add>` utilise l’élément `<appSettings>` pour ajouter deux paramètres à la section d’un fichier web.config :

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Exemple

 L’exemple suivant `AppContextSwitchOverrides` utilise l’élément pour définir `Switch.System.Globalization.NoAsyncCurrentCulture`un commutateur de compatibilité d’application unique, , qui empêche la culture de circuler à travers les fils dans les appels de méthode asynchrone.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 L’exemple suivant `AppContextSwitchOverrides` utilise l’élément pour définir `Switch.System.Globalization.NoAsyncCurrentCulture` deux `Switch.System.IO.BlockLongPaths`commutateurs de compatibilité d’application, et . Un point-virgule sépare les deux paires de noms/valeur.

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
- [\<élément> de temps d’exécution](runtime-element.md)
- [\<configuration> Element](../configuration-element.md)
