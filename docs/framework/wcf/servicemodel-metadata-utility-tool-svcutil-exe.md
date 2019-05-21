---
title: Outil Service Model Metadata Tool (Svcutil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 0cb14bba724b50a8a2b723fe88503fafeeea3880
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959896"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>Outil Service Model Metadata Tool (Svcutil.exe)

L’outil ServiceModel Metadata Utility est utilisé pour générer le code de modèle de service à partir de documents de métadonnées et les documents de métadonnées à partir du code de modèle de service.

## <a name="svcutilexe"></a>SvcUtil.exe

ServiceModel Metadata Utility Tool vous trouverez à l’emplacement d’installation du SDK Windows, en particulier *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin*.

### <a name="functionalities"></a>Fonctionnalités

Le tableau suivant récapitule les différentes fonctionnalités fournies par cet outil et la rubrique correspondante qui décrit son utilisation :

|Tâche|Rubrique|
|----------|-----------|
|Génère le code à partir des services en cours d'exécution ou de documents de métadonnées statiques.|[Génération d’un client WCF à partir de métadonnées de service](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|
|Exporte des documents de métadonnées à partir de code compilé.|[Guide pratique pour Utiliser Svcutil.exe pour exporter les métadonnées à partir du Code de Service compilé](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|Valide le code de service compilé.|[Guide pratique pour Utiliser Svcutil.exe pour valider le Code de Service compilé](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|Télécharge des documents de métadonnées à partir de services en cours d'exécution.|[Guide pratique pour Utiliser Svcutil.exe pour télécharger des Documents de métadonnées](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|Génère du code de sérialisation.|[Guide pratique pour Améliorer le temps de démarrage de WCF Client Applications à l’aide de XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> Svcutil remplace les fichiers existants sur un disque si les noms fournis en tant que paramètres sont identiques. Cela peut inclure des fichiers de code, la configuration ou les fichiers de métadonnées. Pour éviter ce problème lors de la génération des fichiers de code et la configuration, utilisez le `/mergeConfig` basculer.
>
> En outre, le `/r` et `/ct` sont des commutateurs pour référencer des types pour la génération de contrats de données. Ces commutateurs ne fonctionnent pas lors de l'utilisation de XmlSerializer.

### <a name="timeout"></a>Délai

L’outil a un délai d’expiration de cinq minutes lors de la récupération des métadonnées. Ce délai d'attente s'applique uniquement à la récupération des métadonnées sur le réseau. Il ne s'applique pas au traitement de ces métadonnées.

### <a name="multi-targeting"></a>Multi-ciblage

L'outil ne prend pas en charge le multi-ciblage. Si vous souhaitez générer un artefact .NET 4 à partir de *svcutil.exe*, utilisez le *svcutil.exe* à partir du Kit de développement logiciel de .NET 4. Pour générer un artefact .NET 3.5, utilisez le fichier exécutable du Kit de développement logiciel (SDK) de .NET 3.5.

### <a name="accessing-wsdl-documents"></a>Accès aux documents WSDL

Lorsque vous utilisez Svcutil pour accéder à un document WSDL qui contient une référence à un service d'émission de jeton de sécurité (STS), Svcutil effectue un appel WS-MetadataExchange call au STS. Cependant, le service peut exposer ses documents WSDL à l'aide de WS-MetadataExchange ou de HTTP GET. Par conséquent, si le STS a exposé uniquement le document WSDL à l’aide de HTTP GET, un client écrit dans WinFX échouera. Pour les clients écrits dans [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], Svcutil tente d’utiliser WS-MetadataExchange et HTTP GET pour obtenir le STS WSDL.

## <a name="using-svcutilexe"></a>Utilisation de Svcutil.exe

### <a name="common-usages"></a>Utilisations courantes

Le tableau suivant présente que certaines options couramment utilisées pour cet outil :

|Option|Description|
|------------|-----------------|
|/directory:\<directory>|Répertoire à utiliser pour la création des fichiers.<br /><br /> Par défaut : Le répertoire actif.<br /><br /> Forme abrégée : `/d`|
|/help|Affiche la syntaxe de commande et les options de l'outil.<br /><br /> Forme abrégée : `/?`|
|/noLogo|Supprime le message de copyright et de bannière.|
|/svcutilConfig:\<configFile>|Spécifie un fichier de configuration personnalisé à utiliser en remplacement du fichier App.config. Peut être utilisé pour enregistrer des extensions system.serviceModel sans modifier le fichier de configuration de l’outil.|
|/ target :\<TYPE_SORTIE >|Spécifie la sortie à générer par l'outil.<br /><br /> Les valeurs valides sont code, métadonnées ou xmlSerializer.<br /><br /> Forme abrégée : `/t`|

### <a name="code-generation"></a>Génération de code

Svcutil.exe peut générer du code pour les contrats de service, les clients et les types de données à partir de documents de métadonnées. Ces documents de métadonnées peuvent se trouver sur un stockage durable, ou encore être récupérés en ligne. La récupération en ligne suit le protocole WS-Metadata Exchange ou le protocole DISCO (pour plus d'informations, consultez la section consacrée au téléchargement de métadonnées).

Vous pouvez utiliser la *SvcUtil.exe* outil pour générer des contrats de service et de données basés sur un document WSDL prédéfini. Utilisez le commutateur /serviceContract et spécifiez une URL ou un emplacement de fichier dans lequel le document WSDL peut être téléchargé ou disponible. Cette opération génère les contrats de service et de données définis dans le document WSDL qui peut ensuite être utilisé pour implémenter un service conforme. Pour plus d'informations, voir [Procédure : Récupérer les métadonnées et implémenter un Service conforme](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).

Pour un service avec un point de terminaison BasicHttpContextBinding, *Svcutil.exe* génère un BasicHttpBinding avec le `allowCookies` attribut la valeur `true` à la place. Les cookies sont utilisés pour le contexte sur le serveur. Pour gérer le contexte sur le client lorsque le service utiliser des cookies, vous pouvez modifier manuellement la configuration pour utiliser une liaison de contexte.

> [!CAUTION]
> Svcutil.exe génère le client sur la base du WSDL ou du fichier de stratégie reçu du service. Le nom d’utilisateur principal (UPN) est généré en concaténant le nom d’utilisateur, «\@» et un nom de domaine complet (FQDN). Toutefois, ce format n'est pas valide pour les utilisateurs Active Directory, et l'UPN généré par l'outil provoque une défaillance dans l'authentification Kerberos et l'affichage du message d'erreur suivant : La tentative d'ouverture de session a échoué. Pour remédier à cela, vous devez corriger manuellement le fichier client généré par cet outil.

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|Argument|Description|
|--------------|-----------------|
|`epr`|Chemin d'accès à un fichier XML qui contient une référence de point de terminaison WS-Addressing pour un service qui prend en charge WS-Metadata Exchange. Pour plus d'informations, consultez la section consacrée au téléchargement de métadonnées.|
|`metadataDocumentPath`|Le chemin d’accès à un document de métadonnées (*wsdl* ou *xsd*) qui contient le contrat à importer dans le code (.wsdl, .xsd, .wspolicy ou .wsmex).<br /><br /> Svcutil effectue des imports et des opérations d'inclusion lorsque vous spécifiez une URL distante pour les métadonnées. Toutefois, si vous souhaitez traiter des fichiers de métadonnées sur le système de fichiers local, vous devez spécifier tous les fichiers dans cet argument. De cette façon, vous pouvez utiliser Svcutil dans un environnement de génération dans lequel vous ne pouvez pas avoir de dépendances de réseau. Vous pouvez utiliser des caractères génériques (*.xsd, \*.wsdl) pour cet argument.|
|`url`|URL d'accès à un point de terminaison de service qui fournit les métadonnées ou à un document de métadonnées hébergé en ligne. Pour plus d'informations sur la façon dont ces documents sont récupérés, consultez la section consacrée au téléchargement de métadonnées.|

|Option|Description|
|------------|-----------------|
|/async|Génère à la fois des signatures de méthode synchrones et asynchrones.<br /><br /> Valeur par défaut : génération de signatures de méthode synchrones uniquement.<br /><br /> Forme abrégée : `/a`|
|/collectionType:\<type>|Spécifie le type de collection de listes pour un client WCF.<br/><br /> Par défaut : le type de collection est System.Array. <br /><br /> Forme abrégée : `/ct`|
|/ config :\<configFile >|Spécifie le nom de fichier du fichier de configuration généré.<br /><br /> Valeur par défaut : output.config.|
|/dataContractOnly|Génère du code pour les types de contrat de données uniquement. Aucun type de contrat de service n'est généré.<br /><br /> Pour cette option, vous devez spécifier uniquement des fichiers de métadonnées locaux.<br /><br /> Forme abrégée : `/dconly`|
|/enableDataBinding|Implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged> sur tous les types de contrat de données pour activer la liaison de données.<br /><br /> Forme abrégée : `/edb`|
|/excludeType :\<type >|Spécifie un nom de type qualifié complet ou qualifié d'assembly à exclure des types de contrat référencés.<br /><br /> Lors de l'utilisation de ce commutateur avec `/r` à partir de DLL séparées, le nom complet de la classe XSD est référencé.<br /><br /> Forme abrégée : `/et`|
|/importXmlTypes|Configure le sérialiseur de contrat de données de façon à importer des types autres que le type de contrat de données en tant que types IXmlSerializable.|
|/internal|Génère des classes marquées comme internes. Valeur par défaut : génération de classes publiques uniquement.<br /><br /> Forme abrégée : `/i`|
|/Language :\<langage >|Spécifie le langage de programmation à utiliser pour la génération de code. Vous devez fournir un nom de langage enregistré dans le fichier Machine.config ou le nom qualifié complet d’une classe qui hérite de <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Valeurs: C#, cs, csharp, vb, visualbasic, c++, cpp<br /><br /> Valeur par défaut : csharp<br /><br /> Forme abrégée : `/l`|
|/mergeConfig|Fusionne la configuration générée dans un fichier existant au lieu de remplacer le fichier existant.|
|/messageContract|Génère des types de contrat de message.<br /><br /> Forme abrégée : `/mc`|
|/ namespace :\<chaîne, chaîne >|Spécifie un mappage d'un espace de noms WSDL ou XML Schema targetNamespace vers un espace de noms CLR. À l’aide de '\*' pour targetNamespace mappe tous les targetNamespaces sans mappage explicite à cet espace de noms CLR.<br /><br /> Pour vérifier que le nom de contrat du message n'entre pas en collision avec le nom d'opération, vous devez soit qualifier la référence de type avec `::`, soit vous assurer que les noms sont uniques.<br /><br /> Par défaut : Dérivé de l’espace de noms cible du document de schéma pour les contrats de données. L'espace de noms par défaut est utilisé pour tous les autres types générés.<br /><br /> Forme abrégée : `/n` **Remarque :**  Lors de la génération de types à utiliser avec XmlSerializer, uniquement un mappage d’espace de noms unique est prise en charge. Tous les types générés sera dans l’espace de noms par défaut ou l’espace de noms spécifié par ' *'.|
|/noConfig|Ne génère pas de fichiers de configuration.|
|/noStdLib|Ne référence pas les bibliothèques standard.<br /><br /> Par défaut : Mscorlib.dll et System.servicemodel.dll sont référencés.|
|/out:\<file>|Spécifie le nom de fichier du code généré.<br /><br /> Par défaut : WSDL dérivée du nom de définition WSDL, nom du service ou d’un des schémas de l’espace de noms cible.<br /><br /> Forme abrégée : `/o`|
|/ reference :\<chemin d’accès de fichier >|Référence les types contenus dans l'assembly spécifié. Lorsque vous générez des clients, utilisez cette option pour spécifier des assemblys qui peuvent contenir des types représentant les métadonnées importées.<br /><br /> Vous ne pouvez pas spécifier de contrats de message et de types <xref:System.Xml.Serialization.XmlSerializer> à l'aide de ce commutateur.<br /><br /> Si <xref:System.DateTimeOffset> est référencé, ce type est utilisé au lieu de générer un nouveau type. Si l'application est écrite à l'aide de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], SvcUtil.exe référence automatiquement <xref:System.DateTimeOffset>.<br /><br /> Forme abrégée : `/r`|
|/serializable|Génère des classes marquées avec l'attribut Serializable.<br /><br /> Forme abrégée : `/s`|
|/serviceContract|Générez le code pour les contrats de service uniquement. La classe de client et la configuration ne sont pas générées<br /><br /> Forme abrégée : `/sc`|
|/serializer:Auto|Sélectionner automatiquement le sérialiseur. Il tente d’utiliser le sérialiseur de contrat de données et utilise le XmlSerializer en cas d’échec.<br /><br /> Forme abrégée : `/ser`|
|/serializer:DataContractSerializer|Génère des types de données qui utilisent le sérialiseur de contrat de données pour la sérialisation et la désérialisation.<br /><br /> Forme abrégée : `/ser:DataContractSerializer`|
|/serializer:XmlSerializer|Génère des types de données qui utilisent le <xref:System.Xml.Serialization.XmlSerializer> pour la sérialisation et la désérialisation.<br /><br /> Forme abrégée : `/ser:XmlSerializer`|
|/targetClientVersion|Spécifiez la version du .NET Framework ciblée par l’application. Les valeurs valides sont `Version30` et `Version35`. La valeur par défaut est `Version30`.<br /><br /> Forme abrégée : `/tcv`<br /><br /> `Version30`: Utilisez `/tcv:Version30` si vous générez du code pour les clients qui utilisent WinFX.<br /><br /> `Version35`: Utilisez `/tcv:Version35` si vous générez du code pour les clients qui utilisent [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Si vous utilisez `/tcv:Version35` avec le commutateur `/async`, des méthodes asynchrones basées sur des délégués de rappel et sur des événements sont générées. De plus, la prise en charge des DataSets activés par LINQ et <xref:System.DateTimeOffset> est activée.|
|/wrapped|Contrôle l'usage de la casse appropriée pour les documents de type littéral par le biais des paramètres d'encapsulage. Utilisez le **/ encapsulé** commutateur avec la [Service Model Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil pour indiquer une casse normale.|

> [!NOTE]
> Lorsque les liaisons de service sont une des liaisons fournies par le système (consultez [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) et le <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> propriété a la valeur `None` ou `Sign`, Svcutil génère un fichier de configuration en utilisant le [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) élément au lieu de l’élément fourni par le système attendu. Par exemple, si le service utilise l'élément `<wsHttpBinding>` avec le `ProtectionLevel` défini à `Sign`, la configuration générée a `<customBinding>` dans la section bindings au lieu de `<wsHttpBinding>`. Pour plus d’informations sur le niveau de protection, consultez [niveau de Protection de présentation](../../../docs/framework/wcf/understanding-protection-level.md).

### <a name="metadata-export"></a>Exportation de métadonnées

Svcutil.exe peut exporter des métadonnées pour des services, des contrats et des types de données contenus dans des assemblys compilés. Pour exporter des métadonnées pour un service, vous devez utiliser l'option `/serviceName` afin de spécifier le service à exporter. Pour exporter tous les types de contrat de données dans un assembly, vous devez utiliser l'option `/dataContractOnly`. Par défaut, les métadonnées sont exportées pour tous les contrats de service dans les assemblys d'entrée.

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|Argument|Description|
|--------------|-----------------|
|`assemblyPath`|Spécifie le chemin d’accès à un assembly qui contient des services, des contrats ou des types de contrat de données à exporter. Des caractères génériques de ligne de la commande standard peuvent être utilisés pour fournir plusieurs fichiers en tant qu'entrée.|

|Option|Description|
|------------|-----------------|
|/serviceName:\<serviceConfigName>|Spécifie le nom de configuration d'un service à exporter. Si cette option est utilisée, un assembly exécutable avec un fichier de configuration associé doit être passé en tant qu'entrée. Svcutil.exe recherche tous les fichiers de configuration associés la configuration du service. Si les fichiers de configuration contiennent des types d’extension, les assemblys qui contiennent ces types doivent être dans le GAC ou être explicitement fournis à l’aide de l’option `/reference`.|
|/ reference :\<chemin d’accès de fichier >|Ajoute l'assembly spécifié au jeu d'assemblys utilisé pour résoudre des références de type. Si vous exportez ou validez un service qui utilise des extensions tierces (Comportements, Liaisons et BindingElements) enregistrées dans la configuration, utilisez cette option pour localiser des assemblys d’extension qui ne figurent pas dans le GAC.<br /><br /> Forme abrégée : `/r`|
|/dataContractOnly|Fonctionne uniquement sur les types de contrat de données. Les contrats de service ne sont pas traités.<br /><br /> Pour cette option, vous devez spécifier uniquement des fichiers de métadonnées locaux.<br /><br /> Forme abrégée : `/dconly`|
|/excludeType :\<type >|Spécifie le nom qualifié complet ou qualifié d'assembly d'un type à exclure de l'exportation. Cette option peut être utilisée lors de l'exportation des métadonnées d'un service (ou d'un ensemble de contrats de services) afin d'exclure certains types de l'opération d'exportation. Cette option ne peut pas être utilisée avec l'option `/dconly`.<br /><br /> Lorsqu'un assembly contient plusieurs services et que chacun d'entre eux utilise des classes séparées tout en portant le même nom XSD, vous devez spécifier le nom du service au lieu du nom de la classe XSD pour ce commutateur.<br /><br /> Les types XSD ou les types de contrat de données ne sont pas pris en charge.<br /><br /> Forme abrégée : `/et`|

### <a name="service-validation"></a>Validation de service

La validation peut être utilisée pour détecter des erreurs dans les implémentations de service sans héberger le service. Vous devez utiliser l'option `/serviceName` pour indiquer le service à valider.

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|Argument|Description|
|--------------|-----------------|
|`assemblyPath`|Spécifie le chemin d’accès à un assembly qui contient des types de service à valider. L'assembly doit posséder un fichier de configuration associé pour pouvoir fournir la configuration du service. Vous pouvez utiliser des caractères génériques de ligne de commande standard pour fournir plusieurs assemblys.|

|Option|Description|
|------------|-----------------|
|/validate|Valide une implémentation de service spécifiée par l'option `/serviceName`. Si cette option est utilisée, un assembly exécutable avec un fichier de configuration associé doit être passé en tant qu'entrée.<br /><br /> Forme abrégée : `/v`|
|/serviceName:\<serviceConfigName>|Spécifie le nom de configuration d'un service à valider. Svcutil.exe recherche tous les fichiers de configuration associés de tous les assemblys d'entrée pour la configuration du service. Si les fichiers de configuration contiennent des types d'extension, les assemblys qui contiennent ces types doivent être dans le GAC ou être explicitement fournis à l'aide de l'option `/reference`.|
|/ reference :\<chemin d’accès de fichier >|Ajoute l'assembly spécifié au jeu d'assemblys utilisé pour résoudre des références de type. Si vous exportez ou validez un service qui utilise des extensions tierces (Comportements, Liaisons et BindingElements) enregistrées dans la configuration, utilisez cette option pour localiser des assemblys d’extension qui ne figurent pas dans le GAC.<br /><br /> Forme abrégée : `/r`|
|/dataContractOnly|Fonctionne uniquement sur les types de contrat de données. Les contrats de service ne sont pas traités.<br /><br /> Pour cette option, vous devez spécifier uniquement des fichiers de métadonnées locaux.<br /><br /> Forme abrégée : `/dconly`|
|/excludeType :\<type >|Spécifie le nom qualifié complet ou qualifié d’assembly d’un type à exclure de la validation.<br /><br /> Forme abrégée : `/et`|

### <a name="metadata-download"></a>Téléchargement de métadonnées

Svcutil.exe permet de télécharger des métadonnées à partir de services en cours d'exécution et de les enregistrer dans des fichiers locaux. Pour pouvoir télécharger des métadonnées, vous devez spécifier l'option `/t:metadata`. Sinon, un code client est généré. Pour les schémas d'URL HTTP et HTTPS, Svcutil.exe essaie de récupérer les métadonnées à l'aide de WS-Metadata Exchange et DISCO. Pour tous les autres schémas d'URL, Svcutil.exe utilise uniquement WS-MetadataExchange.

Svcutil publie les requêtes de métadonnées suivantes tout en effectuant simultanément une récupération de métadonnées.

- Requête MEX (WS-Transfer) à l'adresse fournie

- Requête MEX à l'adresse fournie avec /mex ajouté

- Requête DISCO (à l'aide du DiscoveryClientProtocol d'ASMX) à l'adresse fournie.

Par défaut, Svcutil.exe utilise les liaisons définies dans la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings> pour effectuer des requêtes MEX. Pour configurer la liaison utilisée pour WS-Metadata Exchange, vous devez définir un point de terminaison client dans la configuration qui utilise le contrat IMetadataExchange. Cela peut être défini soit dans le fichier de configuration de Svcutil.exe, soit dans un autre fichier de configuration spécifié à l'aide de l'option `/svcutilConfig`.

`svcutil.exe /t:metadata  <url>* | <epr>`

|Argument|Description|
|--------------|-----------------|
|`url`|URL d'accès à un point de terminaison de service qui fournit les métadonnées ou à un document de métadonnées hébergé en ligne.|
|`epr`|Chemin d'accès à un fichier XML qui contient une référence de point de terminaison WS-Addressing pour un service qui prend en charge WS-Metadata Exchange.|

### <a name="xmlserializer-type-generation"></a>Génération de type XmlSerializer

Les applications clientes et de services qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> génèrent et compilent le code de sérialisation de ces types de données lors de l'exécution, ce qui peut provoquer des performances de démarrage lentes.

> [!NOTE]
> Le code de sérialisation prégénéré est réservé aux applications clientes, pas aux services.

Svcutil.exe peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation C# nécessaire à partir des assemblys compilés pour l'application. Pour plus d'informations, voir [Procédure : Améliorer le temps de démarrage de WCF Client Applications à l’aide de XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

> [!NOTE]
> Svcutil.exe génère uniquement le code des types utilisés par les contrats de service figurant dans les assemblys d'entrée.

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|Argument|Description|
|--------------|-----------------|
|`assemblyPath`|Spécifie le chemin d’accès à un assembly qui contient des types de contrat de service. Des types de sérialisation sont générés pour tous les types Xml sérialisables de chaque contrat.|

|Option|Description|
|------------|-----------------|
|/ reference :\<chemin d’accès de fichier >|Ajoute l'assembly spécifié au jeu d'assemblys utilisé pour résoudre des références de type.<br /><br /> Forme abrégée : `/r`|
|/excludeType :\<type >|Spécifie le nom qualifié complet ou qualifié d’assembly d’un type à exclure de l’exportation ou de la validation.<br /><br /> Forme abrégée : `/et`|
|/out:\<file>|Spécifie le nom de fichier du code généré. Cette option est ignorée lorsque plusieurs assemblys sont passés à l'outil en tant qu'entrée.<br /><br /> Par défaut : Dérivé du nom de l’assembly.<br /><br /> Forme abrégée : `/o`|
|/UseSerializerForFaults|Spécifie que <xref:System.Xml.Serialization.XmlSerializer> doit être utilisé pour lire et écrire les erreurs, au lieu du <xref:System.Runtime.Serialization.DataContractSerializer> par défaut.|

## <a name="examples"></a>Exemples

La commande suivante génère un code client à partir d'un service en cours d'exécution ou de documents de métadonnées en ligne.

`svcutil http://service/metadataEndpoint`

La commande suivante génère un code client à partir de documents de métadonnées locaux.

`svcutil *.wsdl *.xsd /language:C#`

La commande suivante génère des types de contrat de données en Visual Basic à partir de documents de schémas locaux.

`svcutil /dconly *.xsd /language:VB`

La commande suivante télécharge des documents de métadonnées à partir de services en cours d'exécution.

`svcutil /t:metadata http://service/metadataEndpoint`

La commande suivante génère des documents de métadonnées pour les contrats de service et les types associés d'un assembly.

`svcutil myAssembly.dll`

La commande suivante génère des documents de métadonnées pour un service, ainsi que tous les contrats de service et types de données associés au sein d'un assembly.

`svcutil myServiceHost.exe /serviceName:myServiceName`

La commande suivante génère des documents de métadonnées pour les types de données présents dans un assembly.

`svcutil myServiceHost.exe /dconly`

La commande suivante vérifie l'hébergement de services.

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

La commande suivante génère des types de sérialisation pour les types <xref:System.Xml.Serialization.XmlSerializer> utilisés par les contrats de service de l'assembly.

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>Quota maximal pour le nombre de caractères nametable

Lors de l'utilisation de svcutil pour générer des métadonnées pour un service, vous pouvez recevoir le message suivant :

Erreur : Impossible d’obtenir les métadonnées à partir `http://localhost:8000/somesservice/mex` le quota de nombre de caractères maximal nametable (16384) a été dépassé lors de la lecture des données XML. La structure de données nametable est utilisée pour stocker les chaînes rencontrées lors du traitement XML ; des documents XML longs comportant des noms d'éléments non répétés, des noms d'attributs et des valeurs d'attributs peuvent déclencher ce quota. Ce quota peut être augmenté en modifiant la propriété MaxNameTableCharCount sur l’objet XmlDictionaryReaderQuotas utilisé pendant la création du lecteur XML.

Cette erreur peut être causée par un service qui retourne un fichier WSDL volumineux lorsque vous demandez ses métadonnées. Le problème est lié à un dépassement du quota de caractères pour l'outil svcutil.exe. Cette valeur est définie pour empêcher les attaques par déni de service (DOS). Vous pouvez augmenter ce quota en spécifiant le fichier de configuration suivant pour svcutil.

Le fichier de configuration suivant montre comment définir les quotas du lecteur pour svcutil.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <customBinding>
                <binding name="MyBinding">
                    <textMessageEncoding>
                        <readerQuotas maxDepth="2147483647" maxStringContentLength="2147483647"
                            maxArrayLength="2147483647" maxBytesPerRead="2147483647" maxNameTableCharCount="2147483647" />
                    </textMessageEncoding>
                    <httpTransport maxReceivedMessageSize="2147483647" maxBufferSize="2147483647" />
                </binding>
            </customBinding>
        </bindings>
        <client>
            <endpoint binding="customBinding" bindingConfiguration="MyBinding"
                contract="IMetadataExchange"
                name="http" />
        </client>
    </system.serviceModel>
</configuration>
```

Créez un fichier appelé svcutil.exe.config et copiez l'exemple de code XML dans ce fichier. Puis, placez le fichier dans le même répertoire que svcutil.exe. Lors de la prochaine exécution de svcutil.exe, les nouveaux paramètres seront pris en compte.

## <a name="security-concerns"></a>Problèmes de sécurité

Vous devez utiliser la liste de contrôle d'accès appropriée pour protéger le dossier d'installation de Svcutil.exe, Svcutil.config, ainsi que les fichiers vers lesquels pointe `/svcutilConfig`. Cela peut éviter l'enregistrement et l'exécution d'extensions malveillantes.

En outre, pour réduire le risque que la sécurité soit compromise, vous ne devez pas ajouter des extensions non fiables pour faire partie du système ou utiliser des fournisseurs de code non fiable avec Svcutil.exe.

Enfin, vous ne devez pas utiliser l'outil dans la couche intermédiaire de votre application, car cela pourrait provoquer un déni de service pour le processus en cours.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Guide pratique pour Créer un Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
