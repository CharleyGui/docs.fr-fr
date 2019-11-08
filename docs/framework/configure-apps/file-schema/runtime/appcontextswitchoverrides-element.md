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
ms.openlocfilehash: 881b9fedfaa42ffb402e226a6b271f47feb20617
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736811"
---
# <a name="appcontextswitchoverrides-element"></a>\<élément AppContextSwitchOverrides >
Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<AppContextSwitchOverrides** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`value`|Attribut requis.<br /><br /> Définit un ou plusieurs noms de commutateur et leurs valeurs booléennes associées.|  
  
### <a name="value-attribute"></a>Attribut de valeur  
  
|valeur|Description|  
|-----------|-----------------|  
|« nom = valeur »|Nom de commutateur prédéfini avec sa valeur (`true` ou `false`). Plusieurs paires nom/valeur de commutateur sont séparées par des points-virgules (« ; »). Pour obtenir la liste des noms de commutateur prédéfinis pris en charge par le .NET Framework, consultez la section Notes.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun(e).  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 À partir de la .NET Framework 4,6, l’élément `<AppContextSwitchOverrides>` dans un fichier de configuration permet aux appelants d’une API de déterminer si leur application peut tirer parti de nouvelles fonctionnalités ou préserver la compatibilité avec les versions précédentes d’une bibliothèque. Par exemple, si le comportement d’une API a changé entre deux versions d’une bibliothèque, l’élément `<AppContextSwitchOverrides>` permet aux appelants de cette API de refuser le nouveau comportement sur les versions de la bibliothèque qui prennent en charge la nouvelle fonctionnalité. Pour les applications qui appellent des API dans le .NET Framework, l’élément `<AppContextSwitchOverrides>` peut également autoriser des appelants dont les applications ciblent une version antérieure du .NET Framework à accepter de nouvelles fonctionnalités si leur application s’exécute sur une version du .NET Framework qui inclut ses.  
  
 L’attribut `value` de l’élément `<AppContextSwitchOverrides>` se compose d’une chaîne unique qui se compose d’une ou de plusieurs paires nom/valeur délimitées par des points-virgules.  Chaque nom identifie un commutateur de compatibilité, et sa valeur correspondante est une valeur booléenne (`true` ou `false`) qui indique si le commutateur est défini. Par défaut, le commutateur est `false`et les bibliothèques fournissent les nouvelles fonctionnalités. Ils fournissent uniquement les fonctionnalités précédentes si le commutateur est défini (autrement dit, si sa valeur est `true`). Cela permet aux bibliothèques de fournir un nouveau comportement pour une API existante tout en permettant aux appelants qui dépendent du comportement précédent de refuser les nouvelles fonctionnalités.  
  
 Le .NET Framework prend en charge les commutateurs suivants :  
  
|Nom du commutateur|Description|Présent|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Contrôle si Windows Presentation Foundation utilise un algorithme hérité pour la disposition du contrôle. Pour plus d’informations, consultez [Atténuation : disposition WPF](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Contrôle si l’algorithme par défaut utilisé pour la signature des parties d’un package par PackageDigitalSignatureManager est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Quand la valeur est `false`, permet le débogage de projets de workflow XAML avec Visual Studio lorsque FIPS est activé. Sans celui-ci, une <xref:System.NullReferenceException> est levée dans les appels aux méthodes de l’assembly System. Activities.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Contrôle si la somme de contrôle pour une instance de flux de travail dans le débogueur utilise MD5 ou SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Contrôle si le hachage de la somme de contrôle de workflow utilise l’algorithme SHA1 introduit comme valeur par défaut dans .NET Framework 4,7 (`true`), ou s’il utilise l’algorithme par défaut SHA256 introduit comme valeur par défaut dans .NET Framework 4,8 (`false`).<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Contrôle si les traces de pile sont obtenues lors de l’utilisation de fichiers PDB portables peuvent inclure les informations de ligne et de fichier source. `false` d’inclure les informations de ligne et de fichier source ; Sinon, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Contrôle si la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> lève une exception lorsqu’un objet <xref:System.Drawing.Icon> contient des cadres PNG. Pour plus d’informations, consultez [Atténuation : cadres PNG dans les objets Icon](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Détermine si les objets <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> sont correctement supprimés lorsqu’ils sont ajoutés à la collection par la méthode <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>. `true` pour conserver le comportement hérité ; `false` de supprimer tous les objets de police privée. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Contrôle si les performances du <xref:System.Windows.Forms.PrintPreviewDialog> sont optimisées pour les imprimantes réseau. Pour plus d’informations, consultez [vue d’ensemble du contrôle PrintPreviewDialog](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Détermine si les contrôles de plage d’années pour les ères du calendrier japonais sont appliqués. `true` pour appliquer les vérifications de plage d’années et `false` pour les désactiver (comportement par défaut). Pour plus d’informations, consultez [utilisation des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Contrôle si seul « 1 » est reconnu comme première année d’une ère de calendrier japonais dans les opérations d’analyse. `true` de reconnaître uniquement « 1 »; `false` pour reconnaître « 1 » ou gannen (comportement par défaut). Pour plus d’informations, consultez [utilisation des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Contrôle si la première année d’une ère du calendrier japonais est représentée sous la forme « 1 » ou gannen dans les opérations de mise en forme. `true` pour mettre en forme la première année de l’ère en tant que « 1 »; `false` pour le mettre en forme en tant que gannen (comportement par défaut). Pour plus d’informations, consultez [utilisation des calendriers](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Contrôle si les opérations asynchrones ne sont pas transmises à partir du contexte du thread appelant. Pour plus d’informations, consultez [CurrentCulture et CurrentUICulture Flow entre les tâches](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Contrôle si la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> tente de faire correspondre le type de revendication uniquement avec la dernière entrée DNS. Pour plus d’informations, consultez [Atténuation : X509CertificateClaimSet.FindClaims (méthode)](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Contrôle si AuthorizationContext. Empty doit être autorisé à retourner un objet mutable.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Contrôle si les chemins d’accès plus longs que `MAX_PATH` (260 caractères) lèvent une <xref:System.IO.PathTooLongException>. Pour plus d’informations, consultez [prise en charge des chemins d’accès longs](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Contrôle si les routines de système d’exploitation natives sont utilisées pour la décompression par la classe <xref:System.IO.Compression.DeflateStream>. `false` d’utiliser des API natives ; `true` d’utiliser l’implémentation de <xref:System.IO.Compression.DeflateStream>.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Utilise la barre oblique inverse («\\») au lieu de la barre oblique (« / ») comme séparateur de chemin d’accès dans la propriété <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [atténuation : séparateur de chemin ZipArchiveEntry. FullName](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Contrôle si les exceptions du système d’exploitation levées sur les threads d’arrière-plan créés avec <xref:System.IO.Ports.SerialPort> flux terminent le processus.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Contrôle si la normalisation de chemin d’accès héritée est utilisée et si les chemins d’accès URI sont pris en charge par les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>. Pour plus d’informations, consultez [atténuation : normalisation des chemins d’accès](../../../migration-guide/mitigation-path-normalization.md) et [atténuation : contrôles du chemin des deux-points](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Contrôle si un test d’égalité compare la propriété <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> d’un objet avec la propriété <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> du deuxième objet. Pour plus d’informations, consultez [implémentation incorrecte de MemberDescriptor. Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Désactive la validation de l’identificateur d’objet (EKU) de l’utilisation améliorée de la clé par certificat. Une extension EKU (utilisation améliorée de la clé) est une collection d’identificateurs d’objet indiquant les applications qui utilisent la clé.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Désactive l’exploitation du navigateur TLS 1.0 contre l’atténuation SSL/TLS (y) en désactivant l’utilisation de SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Contrôle si les classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType> peuvent utiliser le protocole SSL 3,0. Pour plus d’informations, consultez [Atténuation : protocoles TLS](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Désactive les versions SystemDefault TLS en rétablissant la valeur par défaut Tls12, Tls11, TLS.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Désactive les alertes du serveur TLS SslStream.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Contrôle si les paramètres ByRef SafeArray sur COM Interop événements sont marshalés de nouveau en code natif (`false`) ou si le marshaling vers le code natif est désactivé (`true`).|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Contrôle si le [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) sérialise des caractères de contrôle en fonction des normes ECMAScript V6 et V8. Pour plus d’informations, consultez [Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer | Microsoft Docs](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Contrôle si le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prend en charge plusieurs ajustements ou un seul ajustement pour un fuseau horaire. Si `true`, il utilise le type de <xref:System.TimeZoneInfo> pour sérialiser et désérialiser les données de date et d’heure ; dans le cas contraire, il utilise le type de <xref:System.TimeZone>, qui ne prend pas en charge plusieurs règles d’ajustement.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Contrôle si <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> utilise une taille de tableau plus grande pendant la sérialisation et la désérialisation d’un objet. Définissez ce commutateur sur `true` pour améliorer les performances de sérialisation et de désérialisation des graphiques d’objets volumineux par types tels que <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Contrôle si le constructeur de <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> définit la propriété de <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> du nouvel objet avec une référence d’objet existante. Pour plus d’informations, consultez [Atténuation : Constructeur ClaimsIdentity](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Contrôle si la tentative de réutilisation d’un déchiffreur de <xref:System.Security.Cryptography.AesCryptoServiceProvider> lève une <xref:System.Security.Cryptography.CryptographicException>. Pour plus d’informations, consultez [AesCryptoServiceProvider Decrypter fournit une transformation réutilisable](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Contrôle si la valeur de la propriété [CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) est un [IntPtr](xref:System.IntPtr) qui représente l’emplacement de mémoire d’un handle de fenêtre ou s’il s’agit d’un handle de fenêtre (HWND). Pour plus d’informations, consultez [Atténuation : CspParameters.ParentWindowHandle attend un HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Contrôle si l’utilisation de classes de chiffrement managées en mode FIPS lève une <xref:System.Security.Cryptography.CryptographicException> (`true`) ou s’appuie sur l’implémentation de bibliothèques système (`false`).|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Détermine si la valeur par défaut pour certaines opérations SignedCMS est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Contrôle si la méthode <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> gère correctement toutes les courbes nommées prises en charge par le système d’exploitation (`false`) ou retourne au comportement hérité.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Détermine si la valeur par défaut pour certaines opérations SignedXML est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Détermine si le mode de sécurité `TransportWithMessageCredential` autorise les messages avec un en-tête « to » non signé. Il s’agit d’un commutateur d’abonnement. Pour plus d’informations, consultez [modifications du runtime dans le .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Contrôle si le constructeur <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> lève une <xref:System.ArgumentException> si l’un des éléments est `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Détermine si la tentative d’utilisation de certificats X509 avec un fournisseur de stockage de clés CSG lèvent lève une exception. Pour plus d’informations, consultez [sécurité du transport WCF prend en charge les certificats stockés à l’aide de CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Lorsque vous utilisez le transport HTTP avec un service auto-hébergé, si vous définissez cette valeur sur `true`, WCF ignore une application qui ajoute l’en-tête `Connection: close` aux en-têtes de réponse pour une demande. L’affectation de la valeur `false` permet d’ajouter l’en-tête `Connection: close` aux en-têtes de réponse, ce qui entraîne la fermeture du socket de demande après l’envoi d’une réponse.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Gère les blocages qui résultent de la restriction des instances d’un service réentrant à un seul thread d’exécution à la fois.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Avec `Switch.System.Net.DontEnableSchUseStrongCrypto`, détermine si la sécurité de message WCF utilise TLS 1,1 et TLS 1,2.|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|La valeur `false` définit la configuration par défaut pour permettre au système d’exploitation de choisir le protocole. La valeur `true` affecte la valeur par défaut au protocole le plus élevé disponible. (Également disponible dans la branche maintenance des versions précédentes du Framework)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Détermine si l’algorithme de signature de messages par défaut pour les messages MSMQ dans WCF est SHA1 ou SHA256.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Contrôle si WCF utilise un hachage SHA1 ou SHA256 pour générer des noms aléatoires pour les canaux nommés.<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Contrôle s’il faut lever une [exception NullReferenceException](xref:System.NullReferenceException) lorsque le message d’exception a la valeur null.|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Contrôle si les exceptions levées au démarrage du service sont propagées à l’appelant de la méthode <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Contrôle si <xref:System.Threading.Timer> instances tirent parti des améliorations des performances pour les environnements à grande échelle. Si `true`, les améliorations des performances sont activées ; Si `false` (valeur par défaut), elles sont désactivées.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Détermine si certains caractères encodés en pourcentage qui étaient parfois décodés sont maintenant encodés de manière cohérente. Si `true`, elles sont décodées ; Sinon, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Détermine la gestion des caractères bidirectionnels Unicode dans les URI. `true` pour les supprimer des URI ; `false` pour les conserver et les pourcentager.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Détermine si Windows Presentation Foundation applique un ancien algorithme (`true`) ou un nouvel algorithme (`false`) pour allouer de l’espace aux colonnes \*. Pour plus d’informations, consultez [Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Contrôle si un sélecteur ou un contrôle onglet met toujours à jour la valeur de sa propriété valeur sélectionnée avant de déclencher l’événement de modification de la sélection.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Détermine si le rendu de sélection non-ornement est disponible pour les contrôles <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.PasswordBox> pour empêcher le texte bloqués (`false`) ou si le texte est rendu uniquement dans la couche d’ornement (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Contrôle si les indexeurs IList personnalisés sont utilisés de manière incorrecte (`false`) ou correctement (`true`) par la classe <xref:System.Windows.Data.Binding?displayProperty=nameWithType>.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Détermine si les modifications PPP se produisent sur une base par système (valeur `false`) ou par moniteur (valeur de `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Contrôle si les améliorations du dimensionnement des contrôles dans un <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> lorsque WPF est exécuté en mode de prise en charge par moniteur sont désactivés (`true`) ou activés (`false`).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Détermine si le développeur doit gérer de manière spéciale l' <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action lorsque le texte du contrôle est présent. `true` pour gérer l’action de <xref:System.Windows.Forms.DomainUpDown.UpButton> ; `false` pour que les actions de <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> et de <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> soient correctement synchronisées.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Opte pour le code qui permet à une implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personnalisée de filtrer en toute sécurité des messages sans lever d’exception lorsque la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée. Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Détermine si la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> retourne le contrôle de code source lorsque l’utilisateur ouvre le menu à partir d’un contrôle <xref:System.Windows.Forms.ToolStripMenuItem> imbriqué. `true` pour retourner `null`, le comportement hérité ; `false` pour retourner le contrôle de code source.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Contrôle si la prise en charge de l’appel d’info-bulle est désactivée (`true`) ou activée (`false`). L’activation de la prise en charge de l’appel d’info-bulle requiert également les fonctionnalités d’accessibilité héritées définies par `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`et `Switch.UseLegacyAccessibilityFeatures.3` toutes désactivées (définie à `false`).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Détermine si une pile tactile/de stylet `WM_POINTER`facultative est activée dans les applications WPF. Pour plus d’informations, consultez [atténuation : prise en charge des fonctions tactiles et de stylet basées sur des pointeurs](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Détermine si l’algorithme de hachage par défaut utilisé pour les sommes de contrôle est SHA256 (`false`) ou SHA1 (`true`).<br>En raison de problèmes de collision avec SHA-1, Microsoft recommande SHA-256.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Contrôle si une exception [NullReferenceException](xref:System.NullReferenceException) héritée est levée au lieu de l’exception qui indique plus spécifiquement la cause de l’exception (par exemple, [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) ou [FileNotFoundException](xref:System.IO.FileNotFoundException)). Il est destiné à être utilisé par du code qui dépend de la gestion de l' [exception NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Contrôle si le hachage de la somme de contrôle des fichiers XOML dans les générations de projet de workflow utilise l’algorithme MD5 (`true`) ou s’il utilise l’algorithme SHA256 introduit comme valeur par défaut dans .NET Framework 4,8.<br>En raison de problèmes de collision avec MD5, Microsoft recommande SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Contrôle si le hachage de la somme de contrôle par le SqlTrackingService utilise l’algorithme MD5 (`true`) pour les chaînes mises en cache, ou s’il utilise l’algorithme SHA256 introduit comme valeur par défaut dans .NET Framework 4,8.<br>En raison de problèmes de collision avec MD5, Microsoft recommande SHA256.|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Contrôle si le hachage de la somme de contrôle par l’exécution du workflow utilise l’algorithme MD5 (`true`) pour les définitions de flux de travail mises en cache, ou s’il utilise l’algorithme SHA256 introduit comme valeur par défaut dans .NET Framework 4,8.<br>En raison de problèmes de collision avec MD5, Microsoft recommande SHA256.|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Contrôle si les fonctionnalités d’accessibilité disponibles à partir de .NET Framework 4.7.1 sont activées ou désactivées. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Contrôle si les fonctionnalités d’accessibilité disponibles dans .NET Framework 4.7.2 sont activées (`false`) ou désactivées (`true`). Si `true`, `Switch.UseLegacyAccessibilityFeatures` doit également être `true` pour activer les fonctionnalités d’accessibilité .NET Framework 4.7.1.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Contrôle si les fonctionnalités d’accessibilité introduites dans .NET Framework 4,8 sont activées (`false`) ou désactivées (`true`). Si `true`, `Switch.UseLegacyAccessibilityFeatures` et `Switch.UseLegacyAccessibilityFeatures.2` doivent également être `true`.|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Contrôle si les info-bulles sont affichées lorsqu’un utilisateur pointe le curseur de la souris sur un contrôle WPF (`true`), ou s’ils sont affichés à la fois sur le focus clavier et via la touche de raccourci clavier (`false`, le comportement par défaut). Pour les applications qui s’exécutent sur .NET Framework 4,8, mais qui ciblent des versions antérieures du .NET Framework, l’activation du focus clavier et de la prise en charge des touches de raccourci exige que `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`et `Switch.UseLegacyAccessibilityFeatures.3` soient tous définis sur `false`.|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Contrôle si les séquences de touches vides dans les clés composées sont ignorées par la validation de schéma XSD. Pour plus d’informations, consultez [atténuation : validation de schéma XML](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
> Au lieu d’ajouter un élément `AppContextSwitchOverrides` à un fichier de configuration d’application, vous pouvez également définir les commutateurs par programmation en appelant la C#méthode de <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> `static` (dans) ou `Shared` (dans Visual Basic).  
  
 Les développeurs de bibliothèques peuvent également définir des commutateurs personnalisés pour permettre aux appelants de refuser les fonctionnalités modifiées introduites dans les versions ultérieures de leurs bibliothèques. Pour plus d'informations, consultez la classe <xref:System.AppContext>.  
  
## <a name="switches-in-aspnet-applications"></a>Commutateurs dans les applications ASP.NET

Vous pouvez configurer une application ASP.NET pour utiliser les paramètres de compatibilité en ajoutant un [\<ajouter >](../appsettings/add-element-for-appsettings.md) élément à la section [\<appSettings >](../appsettings/index.md) du fichier Web. config. 

L’exemple suivant utilise l’élément `<add>` pour ajouter deux paramètres à la section `<appSettings>` d’un fichier Web. config :

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Exemple

 L’exemple suivant utilise l’élément `AppContextSwitchOverrides` pour définir un commutateur de compatibilité d’application unique, `Switch.System.Globalization.NoAsyncCurrentCulture`, qui empêche la culture de circuler entre les threads dans les appels de méthode asynchrones.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 L’exemple suivant utilise l’élément `AppContextSwitchOverrides` pour définir deux commutateurs de compatibilité des applications, `Switch.System.Globalization.NoAsyncCurrentCulture` et `Switch.System.IO.BlockLongPaths`. Notez qu’un point-virgule sépare les deux paires nom/valeur.  
  
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
- [\<> Runtime (élément)](runtime-element.md)
- [\<configuration>, élément](../configuration-element.md)
