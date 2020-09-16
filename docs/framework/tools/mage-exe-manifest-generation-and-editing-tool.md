---
title: Mage.exe (outil Manifest Generation and Editing)
description: Prise en main de Mage.exe, le Outil Manifest Generation and Editing. Cet outil prend en charge la création et la modification de manifestes d’application et de déploiement.
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: bca26e359c25bf0dfae70f0ddfdc0c75b2081458
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556321"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (outil Manifest Generation and Editing)

L’outil Manifest Generation and Editing (*Mage.exe*) est un outil en ligne de commande qui prend en charge la création et la modification de manifestes de déploiement et d’application. En tant qu’outil en ligne de commande, *Mage.exe* peut être exécuté à partir de scripts de commandes par lot et d’autres applications Windows, notamment les applications ASP.NET.

Vous pouvez également utiliser *MageUI.exe*, une application graphique, au lieu de *Mage.exe*. Pour plus d'informations, consultez [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’Invite de commandes développeur pour Visual Studio. Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

Deux versions de *Mage.exe* et *MageUI.exe* sont founies avec Visual Studio. Pour afficher les informations de version, exécutez *MageUI.exe* et sélectionnez **Aide / ?**, puis **À propos de**. Cette documentation décrit la version 4.0. x. x de *Mage.exe* et *MageUI.exe*.

## <a name="syntax"></a>Syntaxe

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Paramètres

Le tableau suivant présente les commandes prises en charge par *Mage.exe*. Pour plus d'informations sur les options prises en charge par ces commandes, consultez [Options des commandes New et Update](#new-and-update-command-options) et [Options de la commande Sign](#sign-command-options).

|Commande|Description|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Efface le cache d'application téléchargé de toutes les applications en ligne uniquement.|
|**-n, -New** *fileType [newOptions]*|Crée un nouveau fichier du type donné. Les types valides sont :<br /><br /> -   `Deployment`: crée un manifeste de déploiement.<br />-   `Application`: crée un manifeste de l'application.<br /><br /> Si vous ne spécifiez pas de paramètres supplémentaires avec cette commande, elle crée un fichier du type approprié, avec les valeurs d’attributs et étiquettes par défaut adéquates.<br /><br /> Utilisez l’option **-ToFile** (voir le tableau ci-dessous) pour spécifier le nom de fichier et le chemin du nouveau fichier.<br /><br /> Utilisez l’option **-FromDirectory** (voir le tableau ci-dessous) pour créer un manifeste d’application avec tous les assemblys d’une application ajoutés à la \<dependency> section du manifeste.|
|**-u, -Update** *[filePath] [updateOptions]*|Apporte une ou plusieurs modifications à un fichier manifeste. Vous n'avez pas à spécifier le type de fichier que vous modifiez. Mage.exe examinera le fichier en utilisant un jeu de paramètres heuristiques et déterminera s'il s'agit d'un manifeste de déploiement ou d'un manifeste d'application.<br /><br /> Si vous avez déjà signé un fichier avec un certificat, **-Update** supprime le bloc de signature de clé. En effet, la signature de clé contient un hachage du fichier, et la modification du fichier rend le hachage non valide.<br /><br /> Utilisez l’option **-ToFile** (voir le tableau ci-dessous) pour spécifier un nouveau nom et chemin de fichier au lieu de remplacer le fichier existant.|
|**-s, -Sign** `[signOptions]`|Utilise une paire de clés ou un certificat X509 pour signer un fichier. Les signatures sont insérées en tant qu'éléments XML dans les fichiers.<br /><br /> Vous devez être connecté à Internet lors de la signature d’un manifeste qui spécifie une valeur **-TimestampUri** .|
|**-ver, -Verify** *[nom-fichier-manifeste]*|Vérifie que le manifeste est correctement signé. Non combinable avec d’autres commandes. <br/><br/>**Disponible dans .NET Framework 4.7 (et versions ultérieures).**|
|**-h, -?, -Help** *[verbose]*|Décrit toutes les commandes disponibles et leurs options. Spécifiez `verbose` pour obtenir une aide détaillée.|

## <a name="new-and-update-command-options"></a>Options des commandes New et Update

Le tableau suivant affiche les options prises en charge par les commandes `-New` et `-Update` :

|Options|Valeur par défaut|S'applique à|Description|
|-------------|-------------------|----------------|-----------------|
|**-a, -Algorithm**|sha1RSA|Manifestes d'application.<br /><br /> Manifestes de déploiement.|Définit l'algorithme avec lequel générer des compactés de dépendance. La valeur doit être "sha256RSA" ou "sha1RSA".<br /><br /> N'utilisez pas avec l'option "-Update". Cette option est ignorée avec l'utilisation de l'option "-Sign".|
|**-appc, -AppCodeBase** `manifestReference`||Manifestes de déploiement.|Insère une référence d'URL ou de chemin d'accès au fichier manifeste d'application. Cette valeur doit représenter le chemin d’accès complet au manifeste d’application.|
|**-appm, -AppManifest** `manifestPath`||Manifestes de déploiement.|Insère une référence au manifeste d'application d'un déploiement dans son manifeste de déploiement.<br /><br /> Le fichier indiqué par `manifestPath` doit exister, sans quoi *Mage.exe* génère une erreur. Si le fichier référencé par `manifestPath` n’est pas un manifeste d’application, *Mage.exe* génère une erreur.|
|**-cf, -CertFile** `filePath`||Tous les types de fichiers.|Spécifie l'emplacement d'un certificat numérique X509 permettant de signer un manifeste ou un fichier de licence. Vous pouvez utiliser cette option avec l’option **-Password** si le certificat exige un mot de passe pour les fichiers PFX (Personal Information Exchange). À partir de .NET Framework 4.7, si le fichier ne contient pas de clé privée, l’association des options **- CryptoProvider** et **- KeyContainer** est obligatoire.<br/><br/>À partir de .NET Framework 4.6.2, *Mage.exe* signes les manifestes avec des certificats CNG et CAPI.|
|**-ch, -CertHash** `hashSignature`||Tous les types de fichiers.|Hachage d'un certificat numérique stocké dans le magasin de certificats personnel de l'ordinateur client. Il correspond à la chaîne d'empreinte numérique d'un certificat numérique affiché dans la console Certificats Windows.<br /><br /> `hashSignature` peut être en majuscules ou en minuscules et fourni en tant que chaîne unique ou avec chaque octet de l'empreinte numérique séparé par des espaces et l'empreinte numérique complète entre guillemets.|
|**-csp, -CryptoProvider** `provider-name`||Tous les types de fichiers.|Spécifie le nom d’un fournisseur de services de chiffrement (CSP) contenant le conteneur de clés privées. L’option **- KeyContainer** est requise.<br/><br/>Disponible à partir de .NET Framework 4.7.|
|**-fd, -FromDirectory** `directoryPath`||Manifestes d'application.|Remplit le manifeste d'application avec les descriptions de tous les assemblys et fichiers trouvés dans `directoryPath`, y compris tous les sous-répertoires, `directoryPath` étant le répertoire qui contient l'application à déployer. Pour chaque fichier du répertoire, *Mage.exe* détermine si le fichier est un assembly ou un fichier statique. Si c'est un assembly, il ajoute une balise `<dependency>` et un attribut `installFrom` à l'application avec le nom de l'assembly, la base de code et la version. S'il s'agit d'un fichier statique, il ajoute une balise `<file>` . *Mage.exe* utilise également un simple ensemble d’heuristiques pour détecter le fichier exécutable principal de l’application et le marque comme point d’entrée de l’application ClickOnce dans le manifeste.<br /><br /> *Mage.exe* ne marquera jamais automatiquement un fichier en tant que fichier de « données ». Vous devez faire cela manuellement. Pour plus d'informations, consultez [How to: Include a Data File in a ClickOnce Application](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* génère également un hachage pour chaque fichier en fonction de sa taille. ClickOnce utilise ces hachages pour éviter toute falsification des fichiers du déploiement après la création du manifeste. Si l’un des fichiers de votre déploiement change, vous pouvez exécuter *Mage.exe* avec la commande **-Update** et l’option **-FromDirectory**. Cela mettra à jour les hachages et les versions des assemblys de tous les fichiers référencés.<br /><br /> **-FromDirectory** inclut tous les fichiers de tous les sous-répertoires trouvés dans `directoryPath`.<br /><br /> Si vous utilisez **-FromDirectory** avec la commande **-Update**, *Mage.exe* supprime tous les fichiers du manifeste d’application qui n’existent plus dans le répertoire.|
|**-if, -IconFile**  `filePath`||Manifestes d'application.|Spécifie le chemin d'accès complet à un fichier icône .ICO. Cette icône s'affiche à côté du nom de votre application dans le menu Démarrage et dans son entrée Ajout/Suppression de programmes. Si aucune icône n'est fournie, une icône par défaut est utilisée.|
|**-ip, -IncludeProviderURL**  `url`|true|Manifestes de déploiement.|Indique si le manifeste du déploiement inclut la valeur de l’emplacement de la mise à jour définie par **-ProviderURL**.|
|**-i, -Install** `willInstall`|true|Manifestes de déploiement.|Indique si l'application ClickOnce doit être installée ou non sur l'ordinateur local ou si elle doit s'exécuter à partir du Web. Lorsqu'une application est installée, elle figure dans le menu **Démarrer** de Windows. Les valeurs valides sont "true" ou "t", et "false" ou "f".<br /><br /> Si vous spécifiez l’option **-MinVersion** et qu’un utilisateur dispose d’une version antérieure à la version **-MinVersion** installée, ceci force l’installation de l’application, indépendamment de la valeur passée à **-Install**.<br /><br /> Cette option ne peut pas être utilisée avec l’option **-BrowserHosted** . Toute tentative de spécifier ces deux options pour le même manifeste générera une erreur.|
|**-kc, -KeyContainer** `name`||Tous les types de fichiers.|Spécifie le conteneur de clés contenant le nom de la clé privée. L’option **CryptoProvider** est nécessaire.<br/><br/>Disponible à partir de .NET Framework 4.7.|
|**-mv, -MinVersion**  `[version]`|Version répertoriée dans le manifeste de déploiement ClickOnce telle que spécifiée par l’indicateur **-Version** .|Manifestes de déploiement.|Version minimale de cette application qu'un utilisateur peut exécuter. Cet indicateur rend obligatoire la mise à jour avec la version nommée de votre application. Si vous publiez une version de votre produit avec une mise à jour corrigeant une rupture ou une vulnérabilité de sécurité critique, vous pouvez utiliser cet indicateur pour spécifier que cette mise à jour doit être installée et que l’utilisateur ne peut pas continuer à exécuter des versions antérieures.<br /><br /> `version` a la même sémantique que l’argument pour l’indicateur **-Version** .|
|**-n,-Name**`nameString`|Déployer|Tous les types de fichiers.|Nom utilisé pour identifier l'application. ClickOnce utilise ce nom pour identifier l'application dans le menu **Démarrer** (si l'application est configurée pour s'installer) et dans les boîtes de dialogue Permission Elevation. **Remarque :**  Si vous mettez à jour un manifeste existant et que vous ne spécifiez pas de nom d’éditeur avec cette option, *Mage.exe* met à jour le manifeste avec le nom de l’Organisation défini sur l’ordinateur. Pour utiliser un nom différent, veillez à utiliser cette option et spécifiez le nom voulu pour l'éditeur.|
|**-pwd, -Password** `passwd`||Tous les types de fichiers.|Mot de passe utilisé pour signer un manifeste avec un certificat numérique. Cette option doit être utilisée conjointement avec l’option **-CertFile** .|
|**-p, Processor** `processorValue`|Msil|Manifestes d'application.<br /><br /> Manifestes de déploiement.|Architecture de microprocesseur sur laquelle cette distribution s'exécutera. Cette valeur est obligatoire si vous préparez une ou plusieurs installations dont les assemblys ont été précompilés pour un microprocesseur spécifique. Les valeurs valides sont `msil`, `x86`, `ia64` et `amd64`. `msil` est le langage intermédiaire Microsoft, ce qui signifie que tous vos assemblys sont indépendants des plateformes et que le Common Language Runtime (CLR) les compile juste-à-temps quand votre application est exécutée pour la première fois.|
|**-pu,** **-ProviderURL** `url`||Manifestes de déploiement.|Spécifie l'URL vérifiée par ClickOnce pour les mises à jour d'application.|
|**-pub, -Publisher** `publisherName`||Manifestes d'application.<br /><br /> Manifestes de déploiement.|Ajoute le nom de l'éditeur à l'élément de description du manifeste de déploiement ou d'application. Quand il est utilisé sur un manifeste d’application, **-UseManifestForTrust** doit également être spécifié avec la valeur « true » ou « t » ; sinon, ce paramètre génère une erreur.|
|**-s, -SupportURL**  `url`||Manifestes d'application.<br /><br /> Manifestes de déploiement.|Spécifie le lien dans lequel s'affiche Ajout/Suppression de programmes pour l'application ClickOnce.|
|**-ti, -TimestampUri** `uri`||Manifestes d'application.<br /><br /> Manifestes de déploiement.|L'URL d'un service d'horodatage numérique. Horodater les manifestes vous évite d'avoir à signer de nouveau les manifestes si votre certificat numérique expire avant le déploiement de la version suivante de votre application. Pour plus d’informations, consultez [Configurer des racines de confiance et des certificats non autorisés](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t, -ToFile** `filePath`|-   New :<br />-   Déploiement : deploy.application<br />-   Application : application.exe.manifest<br />-   Update :<br />-   Fichier d'entrée.|Tous les types de fichiers.|Spécifie le chemin de sortie du fichier créé ou modifié.<br /><br /> Si **-ToFile** n’est pas fourni quand vous utilisez **-New**, la sortie est écrite dans le répertoire de travail actuel. Si **-ToFile** n’est pas fourni quand vous utilisez **-Update**, *Mage.exe* réécrit le fichier dans le fichier d’entrée.|
|**-tr, -TrustLevel** `level`|Selon la zone dans laquelle réside l'URL de l'application.|Manifestes d'application.|Niveau de confiance à accorder à l'application sur les ordinateurs clients. Les valeurs possibles sont "Internet", "Intranet" et "FullTrust".|
|**-um, -UseManifestForTrust** `willUseForTrust`|Faux|Manifestes d'application.|Spécifie si la signature numérique du manifeste d'application sera utilisée pour prendre des décisions d'approbation lorsque l'application s'exécute sur le client. Spécifier "true" ou "t" indique que le manifeste d'application sera utilisé pour les décisions d'approbation. Spécifier "false" ou "f" indique que la signature du manifeste de déploiement sera utilisée.|
|**-v,-version**`versionNumber`|1.0.0.0|Manifestes d'application.<br /><br /> Manifestes de déploiement.|Version du déploiement. L’argument doit être une chaîne de version valide au format «*N.N.N.N*», où «*N*» est un entier 32 bits non signé.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|false|Manifestes d'application.<br /><br /> Manifestes de déploiement.|Utilisez cet indicateur uniquement si l'application est une application Windows Presentation Foundation (WPF) qui sera hébergée dans Internet Explorer et n'est pas un exécutable autonome. Les valeurs valides sont "true" ou "t", et "false" ou "f".<br /><br /> Pour les manifestes d'application, insère l'attribut `hostInBrowser` sous l'élément `entryPoint` du manifeste d'application.<br /><br /> Pour les manifestes de déploiement, affecte la valeur false à l'attribut `install` sur l'élément `deployment` et enregistre le manifeste de déploiement avec une extension .xbap. La spécification de cet argument avec l’argument **-Install** génère une erreur car une application hébergée par le navigateur ne peut pas être une application hors ligne installée.|

## <a name="sign-command-options"></a>Options de la commande Sign

Le tableau suivant affiche les options prises en charge par la commande `-Sign` applicables à tous les types de fichiers.

|Options|Description|
|-------------|-----------------|
|**-cf, -CertFile** `filePath`|Spécifie l'emplacement d'un certificat numérique servant à signer un manifeste. Vous pouvez utiliser cette option avec l’option **-Password** si le certificat exige un mot de passe pour les fichiers PFX (Personal Information Exchange). À partir de .NET Framework 4.7, si le fichier ne contient pas de clé privée, l’association des options **- CryptoProvider** et **- KeyContainer** est obligatoire.<br/><br/>À partir de .NET Framework 4.6.2, *Mage.exe* signes les manifestes avec des certificats CNG et CAPI.|
|**-ch, -CertHash** `hashSignature`|Hachage d'un certificat numérique stocké dans le magasin de certificats personnel de l'ordinateur client. Il correspond à la propriété d'empreinte numérique d'un certificat numérique affiché dans la console Certificats Windows.<br /><br /> `hashSignature` peut être en majuscules ou en minuscules et fourni en tant que chaîne unique ou avec chaque octet de l'empreinte numérique séparé par des espaces et l'empreinte numérique complète entre guillemets.|
**-csp, -CryptoProvider** `provider-name`|Spécifie le nom d’un fournisseur de services de chiffrement (CSP) contenant le conteneur de clés privées. L’option **- KeyContainer** est requise.<br/><br/>Disponible à partir de .NET Framework 4.7.|
|**-kc, -KeyContainer** `name`|Spécifie le conteneur de clés contenant le nom de la clé privée. L’option **CryptoProvider** est nécessaire.<br/><br/>Disponible à partir de .NET Framework 4.7.|
|**-pwd, -Password** `passwd`|Mot de passe utilisé pour signer un manifeste avec un certificat numérique. Cette option doit être utilisée conjointement avec l’option **-CertFile** .|
|**-t, -ToFile** `filePath`|Spécifie le chemin de sortie du fichier créé ou modifié.|

## <a name="remarks"></a>Notes

Tous les arguments de *Mage.exe* ne respectent pas la casse. Les commandes et options peuvent être précédées d'un tiret (-) ou d'une barre oblique (/).

Tous les arguments utilisés avec la commande **-Sign** peuvent être toujours utilisés avec les commandes **-New** ou **-Update** . Les commandes suivantes sont équivalentes.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> À compter de la version 4.6.2 du .NET Framework, les certificats CNG sont également pris en charge.

 La signature est la dernière tâche à effectuer, car un document signé utilise un hachage du fichier afin de vérifier la validité de la signature pour le document. Si vous modifiez d'une quelconque façon un fichier signé, vous devez le signer de nouveau. Si vous signez un document qui a été précédemment signé, *Mage.exe* remplace l’ancienne signature par le nouveau.

 Quand vous utilisez l’option **-AppManifest** pour remplir un manifeste de déploiement, *Mage.exe* suppose que votre manifeste d’application se trouve dans le même répertoire que le manifeste de déploiement dans un sous-répertoire nommé d’après la version de déploiement actuelle et configure votre manifeste de déploiement de manière appropriée. Si votre manifeste d’application doit se trouver ailleurs, utilisez l’option **-AppCodeBase** pour définir l’autre emplacement.

 Vos manifestes de déploiement et de l'application doivent être signés avant de déployer votre application. Pour obtenir des instructions sur la signature des manifestes, consultez [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

 L’option **-TrustLevel** pour les manifestes d’application décrit le jeu d’autorisations dont une application a besoin pour s’exécuter sur l’ordinateur client. Par défaut, un niveau de confiance basé sur la *zone* dans laquelle leur URL réside est assigné aux applications. Les applications déployées sur un réseau d'entreprise sont généralement placées dans la zone Intranet tandis que celles déployées sur Internet sont placées dans la zone Internet. Les deux zones de sécurité placent des restrictions sur l'accès de l'application aux ressources locales, la zone Intranet étant un peu moins stricte que la zone Internet. La zone FullTrust donne aux applications l'accès complet aux ressources locales d'un ordinateur. Si vous utilisez l’option **-trustLevel** pour placer une application dans cette zone, le composant Gestionnaire de confiance du CLR invite l’utilisateur à décider s’il souhaite accorder ce niveau de confiance supérieur. Si vous déployez votre application sur un réseau d'entreprise, vous pouvez utiliser le déploiement d'applications approuvées pour élever le niveau de confiance de l'application sans affichage d'une invite utilisateur.

 Les manifestes d'application prennent également en charge des sections Trust personnalisées. Cela permet à votre application de respecter le principe de sécurité qui consiste à accorder des autorisations minimales. Vous pouvez ainsi configurer le manifeste pour demander uniquement les autorisations nécessaires à l'exécution de l'application. *Mage.exe* ne prend pas directement en charge l’ajout d’une section Trust personnalisée. Vous pouvez en ajouter une à l’aide d’un éditeur de texte, d’un analyseur XML ou de l’outil graphique *MageUI.exe*. Pour plus d’informations sur l’utilisation de *MageUI.exe* pour ajouter des sections Trust personnalisées, consultez [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 inclut la version 4.6.1 de *Mage.exe*. Les manifestes créés avec cette version de *Mage.exe* ciblent .NET Framework 4. Pour cibler des versions antérieures du .NET Framework, utilisez une version antérieure de *Mage.exe*.

Lors de l’ajout ou de la suppression d’assemblys dans un manifeste existant, ou lors de la nouvelle signature d’un manifeste existant, *Mage.exe* ne met pas à jour le manifeste pour cibler .NET Framework 4.

Les tableaux suivants contiennent ces fonctionnalités et restrictions :

|Version du manifeste|Opération|Mage v2.0|Mage v4.0|
|----------------------|---------------|---------------|---------------|
|Manifeste pour les applications qui ciblent la version 2.0 ou 3.x du .NET Framework|Ouvrir|Ok|Ok|
||Fermer|Ok|Ok|
||Enregistrer|Ok|Ok|
||Nouvelle signature|Ok|Ok|
||Nouveau|Ok|Non pris en charge|
||Mise à jour (voir ci-dessous)|Ok|Ok|
|Manifeste pour les applications qui ciblent la version 4 du .NET Framework|Ouvrir|Ok|Ok|
||Fermer|Ok|Ok|
||Enregistrer|Ok|Ok|
||Nouvelle signature|Ok|Ok|
||Nouveau|Non pris en charge|Ok|
||Mise à jour (voir ci-dessous)|Non pris en charge|Ok|

|Version du manifeste|Détails de l'opération de mise à jour|Mage v2.0|Mage v4.0|
|----------------------|------------------------------|---------------|---------------|
|Manifeste pour les applications qui ciblent la version 2.0 ou 3.x du .NET Framework|Modifier un assembly|Ok|Ok|
||Ajouter un assembly|Ok|Ok|
||Supprimer un assembly|Ok|Ok|
|Manifeste pour les applications qui ciblent la version 4 du .NET Framework|Modifier un assembly|Non pris en charge|Ok|
||Ajouter un assembly|Non pris en charge|Ok|
||Supprimer un assembly|Non pris en charge|Ok|

 Mage.exe crée de nouveaux manifestes qui ciblent le profil client .NET Framework 4. Les applications ClickOnce qui ciblent le profil client .NET Framework 4 peuvent s’exécuter à la fois sur le profil client .NET Framework 4 et sur la version complète du .NET Framework 4. Si votre application cible la version complète du .NET Framework 4 et ne peut pas s’exécuter sur le .NET Framework 4 Client Profile, supprimez l’élément client à `<framework>` l’aide d’un éditeur de texte et signez à nouveau le manifeste.

Voici un exemple d' `<framework>` élément qui cible le profil Client .NET Framework 4 :

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Exemples

L’exemple suivant ouvre l’interface utilisateur de Mage (*MageUI.exe*).

```console
mage
```

Les exemples suivants créent un manifeste de déploiement et un manifeste d'application par défaut. Ces fichiers sont tous créés dans le répertoire de travail en cours et ils sont nommés respectivement deploy.application et application.exe.manifest.

```console
mage -New Deployment
mage -New Application
```

L’exemple suivant crée un manifeste d’application contenant tous les assemblys et fichiers de ressources du répertoire actif.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0
```

L'exemple suivant prend la suite de l'exemple précédent en spécifiant le nom du déploiement et le microprocesseur cible. Il spécifie également une URL en fonction de laquelle ClickOnce doit rechercher des mises à jour.

```console
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/
```

L'exemple suivant montre comment créer une paire de manifestes pour déployer une application WPF qui sera hébergée dans Internet Explorer.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true
```

L’exemple suivant crée un manifeste d’application contenant tous les assemblys et fichiers de ressources du répertoire actif et signe.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -KeyContainer keypair.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

L'exemple suivant met à jour un manifeste de déploiement avec les informations d'un manifeste d'application et définit la base de code pour l'emplacement du manifeste d'application.

```console
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy
```

L'exemple suivant modifie le manifeste de déploiement pour forcer une mise à jour de la version installée de l'utilisateur.

```console
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0
```

L'exemple suivant indique au manifeste de déploiement de récupérer le manifeste d'application d'un autre répertoire.

```console
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/
```

L'exemple suivant signe un manifeste de déploiement existant à l'aide d'un certificat numérique dans le répertoire de travail actif.

```console
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>
```

L'exemple suivant signe un manifeste de déploiement existant à l'aide d'un certificat numérique et d’une clé privée dans le répertoire de travail actif.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Voir aussi

- [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Procédure pas à pas : déploiement manuel d’une application ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Outil Manifest Generation and Editing, client graphique)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
