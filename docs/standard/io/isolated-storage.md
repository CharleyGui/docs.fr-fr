---
title: Stockage isolé
description: Explorez le stockage isolé, qui est un mécanisme de stockage de données qui offre une isolation & la sécurité en définissant des méthodes standardisées pour associer du code à des données enregistrées.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data storage using isolated storage
- stores
- storing data using isolated storage
- isolated storage
- location of isolated storage in file system
- standardizing storage systems
- storing data using isolated storage, when not to use
- code, isolated storage
- isolated storage, options
- data storage using isolated storage, when not to use
- storing data using isolated storage, options
- isolated storage, when not to use
- data storage using isolated storage, options
- isolation
ms.assetid: aff939d7-9e49-46f2-a8cd-938d3020e94e
ms.openlocfilehash: 4ad7779b9810954d110af576dd834daf61888d59
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555918"
---
# <a name="isolated-storage"></a>Stockage isolé

 Pour les applications de bureau, le stockage isolé est un mécanisme de stockage de données qui offre une isolation et une sécurité en définissant des méthodes standardisées pour associer du code à des données enregistrées. La standardisation offre également d'autres avantages. Les administrateurs peuvent utiliser des outils conçus pour manipuler un stockage isolé afin de configurer l'espace de stockage du fichier, de définir des stratégies de sécurité et de supprimer des données inutilisées. Grâce au stockage isolé, votre code ne nécessite plus de chemins d'accès uniques pour spécifier des emplacements sécurisés dans le système de fichiers. En outre, les données sont protégées des autres applications qui possèdent uniquement un accès au stockage isolé. Les informations codées en dur concernant l'emplacement de la zone de stockage d'une application ne sont pas nécessaires.

> [!IMPORTANT]
> Le stockage isolé n’est pas disponible pour les applications du Windows 8. x Store. À la place, utilisez les classes de données d’application des espaces de noms `Windows.Storage` inclus dans l’API Windows Runtime pour stocker des données locales et des fichiers. Pour plus d’informations, consultez [Données d’applications](/previous-versions/windows/apps/hh464917(v=win.10)) dans le Centre de développement Windows.

<a name="data_compartments_and_stores"></a>

## <a name="data-compartments-and-stores"></a>Magasins et compartiments de données

Lorsqu'une application stocke des données dans un fichier, le nom de fichier et l'emplacement de stockage doivent être choisis avec soin afin de réduire la possibilité que l'emplacement de stockage soit connu d'une autre application et, par conséquent, vulnérable en termes d'endommagement. Sans un système standard pour gérer ces problèmes, le développement de techniques adéquates qui minimisent les conflits de stockage peut être complexe et les résultats peuvent être incertains.

Grâce au stockage isolé, les données sont toujours isolées par utilisateur et par assembly. Les informations d'identification telles que l'origine ou le nom fort de l'assembly déterminent l'identité de l'assembly. Les données peuvent également être isolées par domaine d'application, en utilisant des informations d'identification similaires.

Lors de l'utilisation du stockage isolé, votre application enregistre des données dans un seul compartiment de données associé à un aspect de l'identité du code, tel que son éditeur ou sa signature. Le compartiment de données est une abstraction et non un emplacement de stockage spécifique ; il est composé d'au moins un fichier de stockage isolé, appelé un magasin, contenant des emplacements de répertoire réels où sont stockées les données. Par exemple, une application peut comprendre un compartiment de données qui lui est associé, et un répertoire du système de fichiers implémente le magasin qui préserve réellement les données de cette application. Les données enregistrées dans le magasin peuvent être de tout type, à partir des informations sur les préférences de l'utilisateur à des informations sur l'état de l'application. Pour le développeur, l'emplacement du compartiment de données est transparent. Les magasins résident généralement sur le client, mais une application serveur peut utiliser des magasins isolés pour stocker des informations en empruntant l'identité de l'utilisateur légitime. Le stockage isolé peut également stocker des informations sur un serveur avec le profil itinérant d'un utilisateur, de sorte que les informations se déplacent avec l'utilisateur itinérant.

<a name="quotas"></a>

## <a name="quotas-for-isolated-storage"></a>Quotas pour le stockage isolé

Un quota représente une limite de la quantité de stockage isolé pouvant être utilisée. Le quota inclut des octets d'espace de fichier ainsi que la surcharge associée au répertoire et d'autres informations du magasin. Le stockage isolé utilise des quotas d'autorisation qui représentent des limites de stockage définies via des objets <xref:System.Security.Permissions.IsolatedStoragePermission> . Lors d'une tentative d'écriture de données qui dépassent le quota, l'exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée.  La stratégie de sécurité, modifiable à l'aide de l'outil .NET Framework Configuration  Tool (Mscorcfg.msc) détermine les autorisations accordées au code. Le code possédant une autorisation <xref:System.Security.Permissions.IsolatedStoragePermission> ne peut pas utiliser davantage de stockage que celui autorisé par la propriété <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A> . Toutefois, dans la mesure où le code peut ignorer des quotas d'autorisation en présentant diverses identités d'utilisateur, les quotas d'autorisation servent d'indications sur la façon dont le code doit se comporter et ne représentent pas une limite définitive du comportement du code.

Les quotas ne sont pas appliqués sur les magasins itinérants. C'est pourquoi, pour que le code les utilise, le niveau d'autorisation requis est un peu plus haut. Les valeurs d'énumération <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> et <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> spécifient une autorisation appropriée pour utiliser le stockage isolé lorsqu'il s'agit d'un utilisateur itinérant.

<a name="secure_access"></a>

## <a name="secure-access"></a>Accès sécurisé

Le stockage isolé permet aux applications qui ne disposent pas d'un niveau de confiance suffisant de stocker des données d'une façon contrôlée par la stratégie de sécurité de l'ordinateur. Ceci est particulièrement utile pour les composants téléchargés qu'un utilisateur doit exécuter avec précaution. La stratégie de sécurité accorde rarement ce genre d'autorisation de code lorsque vous accédez au système de fichiers en utilisant des mécanismes d'E/S standard. Toutefois, l'autorisation d'utiliser le stockage isolé est accordée par défaut au code s'exécutant à partir de l'ordinateur local, d'un réseau local ou d'Internet.

Les administrateurs peuvent limiter la quantité de stockage isolé disponible pour un utilisateur ou une application, en fonction d'un niveau de confiance approprié. En outre, les administrateurs peuvent supprimer toutes les données rendues persistantes d'un utilisateur. Pour créer le stockage isolé ou y accéder, l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> appropriée doit être accordée au code.

Pour accéder au stockage isolé, le code doit posséder tous les droits de système d'exploitation de la plateforme native. Les listes de contrôle d'accès (ACL) qui contrôlent les utilisateurs autorisés à utiliser le système de fichiers doivent être respectées. Les applications .NET Framework possèdent déjà des droits de système d'exploitation pour accéder au stockage isolé, sauf si elles effectuent un emprunt d'identité (spécifique à la plateforme). Dans ce cas, l'application doit garantir que l'identité de l'utilisateur empruntée possède les droits de système d'exploitation appropriés pour accéder au stockage isolé. Cet accès permet au code exécuté ou téléchargé à partir du Web de lire et d'écrire facilement dans une zone de stockage liée à un utilisateur particulier.

Pour contrôler l'accès au stockage isolé, le Common Language Runtime utilise des objets <xref:System.Security.Permissions.IsolatedStorageFilePermission> . Chaque objet possède des propriétés qui spécifient les valeurs suivantes :

- Utilisation autorisée, qui indique le type d'accès autorisé. Les valeurs sont des membres de l'énumération <xref:System.Security.Permissions.IsolatedStorageContainment> . Pour plus d'informations sur ces valeurs, consultez le tableau de la section suivante.

- Quota de stockage, comme décrit dans la section précédente.

Le runtime exige l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> lors de la première tentative d'ouverture d'un magasin par le code. Il détermine s’il doit ou non accorder cette autorisation, en fonction du niveau de fiabilité du code. Si l'autorisation est accordée, l'utilisation autorisée et les valeurs de quota de stockage sont déterminées par la stratégie de sécurité et par la demande du code de l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission>. La configuration de la stratégie de sécurité est définie à l'aide de l'outil .NET Framework Configuration Tool (Mscorcfg.msc). Tous les appelants de la pile des appels sont vérifiés pour garantir que chaque appelant possède au moins l'utilisation autorisée appropriée. Le runtime vérifie également le quota imposé au code qui a ouvert ou créé le magasin dans lequel le fichier doit être enregistré. Si ces conditions sont remplies, l'autorisation est accordée. Le quota est revérifié à chaque fois qu'un fichier est écrit dans le magasin.

Le code d'application n'est pas nécessaire pour demander l'autorisation, car le Common Language Runtime accorde l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> appropriée selon la stratégie de sécurité. Toutefois, il existe de bonnes raisons de demander des autorisations spécifiques nécessaires à votre application, notamment l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission>.

<a name="allowed_usage"></a>

## <a name="allowed-usage-and-security-risks"></a>Utilisation autorisée et risques pour la sécurité

L'utilisation autorisée spécifiée par l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> détermine le degré d'autorisation du code pour créer et utiliser le stockage isolé. Le tableau suivant illustre la correspondance entre l'utilisation autorisée spécifiée dans l'autorisation et les types d'isolation. En outre, il résume les problèmes de sécurité associés à chaque utilisation autorisée.

|Utilisation autorisée|Types d'isolation|Impact sur la sécurité|
|-------------------|---------------------|---------------------|
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|Aucune utilisation de stockage isolé n'est autorisée.|Aucun impact sur la sécurité.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|Isolation par utilisateur, par domaine et par assembly. Chaque assembly possède un sous-magasin distinct dans le domaine. Les magasins utilisant cette autorisation sont également implicitement isolés par l'ordinateur.|Ce niveau d'autorisation laisse les ressources ouvertes à une surutilisation non autorisée, même si les quotas appliqués rendent cette surutilisation plus difficile. C'est une attaque de refus de service.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|Identique à `DomainIsolationByUser`, mais le magasin est enregistré à un emplacement itinérant si les profils utilisateurs itinérants sont activés et si les quotas ne sont pas appliqués.|Dans la mesure où les quotas doivent être désactivés, les ressources de stockage sont plus vulnérables à une attaque de refus de service.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|Isolation par utilisateur et par assembly. Les magasins utilisant cette autorisation sont également implicitement isolés par l'ordinateur.|Les quotas sont appliqués à ce niveau pour empêcher une attaque de refus de service. Un assembly identique d'un autre domaine peut accéder à ce magasin, ce qui permet la divulgation d'informations entre des applications.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|Identique à `AssemblyIsolationByUser`, mais le magasin est enregistré à un emplacement itinérant si les profils utilisateurs itinérants sont activés et si les quotas ne sont pas appliqués.|Identique à `AssemblyIsolationByUser`, mais le risque d'attaque par déni de service augmente sans les quotas.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|Isolation par utilisateur. Généralement, seuls les outils d'administration ou de débogage utilisent ce niveau d'autorisation.|L'accès avec cette autorisation permet au code d'afficher ou de supprimer un fichier de stockage isolé d'un utilisateur ou des répertoires (sans tenir compte de l'isolation d'assembly). Les risques comprennent notamment une divulgation d'informations et une perte de données.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|Isolation par tous les utilisateurs, domaines et assemblys. Généralement, seuls les outils d'administration ou de débogage utilisent ce niveau d'autorisation.|Cette autorisation permet un compromis total de tous les magasins isolés pour tous les utilisateurs.|

## <a name="safety-of-isolated-storage-components-with-regard-to-untrusted-data"></a>Sécurité des composants de stockage isolé en ce qui concerne les données non approuvées

__Cette section s’applique aux frameworks suivants :__

- .NET Framework (toutes les versions)
- .NET Core 2.1 +
- .NET 5.0 +

.NET Framework et .NET Core offrent un stockage isolé comme un mécanisme permettant de conserver les données d’un utilisateur, d’une application ou d’un composant. Il s’agit d’un composant hérité principalement conçu pour les scénarios de sécurité d’accès du code dépréciés.

Diverses API et outils de stockage isolé peuvent être utilisés pour lire les données au-delà des limites d’approbation. Par exemple, la lecture de données à partir d’une étendue à l’échelle de l’ordinateur peut agréger des données à partir d’autres comptes d’utilisateurs, éventuellement moins fiables, sur l’ordinateur. Les composants ou les applications qui lisent à partir des étendues de stockage isolé à l’échelle de l’ordinateur doivent être conscients des conséquences de la lecture de ces données.

### <a name="security-sensitive-apis-that-can-read-from-the-machine-wide-scope"></a>API sensibles à la sécurité qui peuvent lire à partir de l’étendue à l’échelle de l’ordinateur

Les composants ou les applications qui appellent les API suivantes lisent à partir de l’étendue à l’échelle de l’ordinateur :

* [IsolatedStorageFile. GetEnumerator](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getenumerator), en passant une étendue qui comprend l’indicateur IsolatedStorageScope. machine
* [IsolatedStorageFile. GetMachineStoreForApplication](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getmachinestoreforapplication)
* [IsolatedStorageFile. GetMachineStoreForAssembly](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getmachinestoreforassembly)
* [IsolatedStorageFile. GetMachineStoreForDomain](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getmachinestorefordomain)
* [IsolatedStorageFile. GetStore](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.getstore), passant une portée qui comprend l’indicateur IsolatedStorageScope. machine
* [IsolatedStorageFile. Remove](/dotnet/api/system.io.isolatedstorage.isolatedstoragefile.remove), passage d’une étendue incluant l' `IsolatedStorageScope.Machine` indicateur

L' [outil de stockage isolé](../../framework/tools/storeadm-exe-isolated-storage-tool.md) `storeadm.exe` est affecté s’il est appelé avec le `/machine` commutateur, comme illustré dans le code suivant :

```txt
storeadm.exe /machine [any-other-switches]
```

L’outil Isolated Storage est fourni avec Visual Studio et le kit de développement logiciel (SDK) .NET Framework.

Si l’application n’implique pas d’appels aux API précédentes, ou si le flux de travail n’implique pas `storeadm.exe` d’appel de cette manière, ce document n’est pas applicable.

### <a name="impact-in-multi-user-environments"></a>Impact dans les environnements multi-utilisateurs

Comme mentionné précédemment, l’impact sur la sécurité de ces API résulte de la lecture des données écrites à partir d’un environnement de confiance dans un environnement de confiance différent. Le stockage isolé utilise généralement l’un des trois emplacements suivants pour lire et écrire des données :

1. `%LOCALAPPDATA%\IsolatedStorage\`: Par exemple, `C:\Users\<username>\AppData\Local\IsolatedStorage\` pour l' `User` étendue.
2. `%APPDATA%\IsolatedStorage\`: Par exemple, `C:\Users\<username>\AppData\Roaming\IsolatedStorage\` pour l' `User|Roaming` étendue.
3. `%PROGRAMDATA%\IsolatedStorage\`: Par exemple, `C:\ProgramData\IsolatedStorage\` pour l' `Machine` étendue.

Les deux premiers emplacements sont isolés par utilisateur. Windows garantit que différents comptes d’utilisateur sur le même ordinateur ne peuvent pas accéder aux dossiers de profil utilisateur de l’autre. Deux comptes d’utilisateur différents qui utilisent `User` les `User|Roaming` magasins ou ne voient pas les données de l’autre et ne peuvent pas interférer avec les données de l’autre.

Le troisième emplacement est partagé entre tous les comptes d’utilisateur sur l’ordinateur. Différents comptes peuvent lire et écrire à cet emplacement, et ils peuvent voir les données de chacun.

Les chemins d’accès précédents peuvent différer selon la version de Windows utilisée.

Considérons maintenant un système multi-utilisateur avec deux utilisateurs inscrits _Mallory_ et _Bob_. Mallory a la possibilité d’accéder à son répertoire de profil utilisateur `C:\Users\Mallory\` et peut accéder à l’emplacement de stockage partagé à l’ensemble de l’ordinateur `C:\ProgramData\IsolatedStorage\` . Elle ne peut pas accéder au répertoire du profil utilisateur de Bob `C:\Users\Bob\` .

Si Mallory souhaite attaquer Bob, il peut écrire des données dans l’emplacement de stockage à l’intérieur de l’ordinateur, puis tenter d’influencer Bob dans la lecture à partir du magasin à l’intérieur de l’ordinateur. Quand Bob exécute une application qui lit à partir de ce magasin, cette application fonctionnera sur les données que Mallory y a placées, mais à partir du contexte du compte d’utilisateur de Bob. Le reste de ce document présente différents vecteurs d’attaque et les étapes que les applications peuvent effectuer pour réduire les risques liés à ces attaques.

__Remarque :__ Pour qu’une telle attaque ait lieu, Mallory requiert :

* Un compte d’utilisateur sur l’ordinateur.
* Capacité de placer un fichier dans un emplacement connu sur le système de fichiers.
* Savoir que Bob va à un moment donné exécuter une application qui tente de lire ces données.

Il ne s’agit pas de vecteurs de menace qui s’appliquent aux environnements de bureau à utilisateur unique standard, tels que les ordinateurs personnels ou les stations de travail d’entreprise à un seul employé.

#### <a name="elevation-of-privilege"></a>Élévation de privilège

Une attaque par __élévation de privilèges__ se produit lorsque l’application de Bob lit le fichier de Mallory et tente automatiquement d’entreprendre une action en fonction du contenu de cette charge utile. Prenons l’exemple d’une application qui lit le contenu d’un script de démarrage à partir du magasin de l’ordinateur et transmet ce contenu à `Process.Start` . Si Mallory peut placer un script malveillant à l’intérieur du magasin de l’ordinateur, quand Bob lance son application :

* Son application analyse et lance le script malveillant de Mallory _dans le contexte du profil utilisateur de Bob_.
* Mallory accède au compte de Bob sur l’ordinateur local.

#### <a name="denial-of-service"></a>Denial of service (déni de service)

Une attaque par __déni de service__ se produit lorsque l’application de Bob lit le fichier et les blocages de Mallory, ou s’arrête de fonctionner correctement. Reprenons l’application mentionnée précédemment, qui tente d’analyser un script de démarrage à partir du magasin de l’ordinateur. Si Mallory peut placer un fichier dont le contenu est incorrect dans le magasin de l’ordinateur, il peut :

* Oblige l’application de Bob à lever une exception tôt dans le chemin de démarrage.
* Empêcher le lancement de l’application en raison de l’exception.

Elle a ensuite refusé à Bob la possibilité de lancer l’application sous son propre compte d’utilisateur.

#### <a name="information-disclosure"></a>Divulgation d’informations

Une attaque de __Divulgation d’informations__ se produit lorsque Mallory peut inciter Bob à divulguer le contenu d’un fichier auquel Mallory n’a normalement pas accès. Supposons que Bob a un fichier de secret *C:\Users\Bob\secret.txt* que Mallory souhaite lire. Elle connaît le chemin d’accès à ce fichier, mais elle ne peut pas la lire, car Windows lui interdit d’accéder au répertoire du profil utilisateur de Bob.

Au lieu de cela, Mallory place un lien physique dans le magasin à l’intérieur de l’ordinateur. Il s’agit d’un type spécial de fichier qui ne contient pas de contenu, mais il pointe vers un autre fichier sur le disque. La tentative de lecture du fichier de liaison physique aura pour effet de lire le contenu du fichier ciblé par le lien. Une fois le lien physique créé, Mallory ne peut toujours pas lire le contenu du fichier, car il n’a pas accès à la cible ( `C:\Users\Bob\secret.txt` ) du lien. Toutefois _, Bob a_ accès à ce fichier.

Lorsque l’application de Bob lit à partir du magasin de l’ordinateur, elle lit par inadvertance le contenu de son fichier, de la même `secret.txt` façon que si le fichier lui-même était présent dans le magasin de l’ordinateur. Lorsque l’application de Bob s’arrête, si elle tente de réenregistrer le fichier dans le magasin de l’ordinateur, elle finit par placer une copie réelle du fichier dans le répertoire * C:\ProgramData\IsolatedStorage \* . Étant donné que ce répertoire est lisible par n’importe quel utilisateur sur l’ordinateur, Mallory peut maintenant lire le contenu du fichier.

### <a name="best-practices-to-defend-against-these-attacks"></a>Meilleures pratiques pour la protection contre ces attaques

__Important :__ Si votre environnement a plusieurs utilisateurs mutuellement non approuvés, __n’appelez pas__ l’API `IsolatedStorageFile.GetEnumerator(IsolatedStorageScope.Machine)` ou appelez l’outil `storeadm.exe /machine /list` . Les deux partent du principe qu’ils fonctionnent avec des données approuvées. Si une personne malveillante peut amorcer une charge malveillante dans le magasin de l’ordinateur, cette charge utile peut mener à une attaque par élévation de privilège dans le contexte de l’utilisateur qui exécute ces commandes.

En cas de fonctionnement dans un environnement multi-utilisateur, reconsidérez l’utilisation des fonctionnalités de stockage isolé qui ciblent la portée de l' _ordinateur_ . Si une application doit lire les données à partir d’un emplacement au niveau de l’ordinateur, préférez lire les données à partir d’un emplacement accessible en écriture uniquement par les comptes d’administrateur. Le `%PROGRAMFILES%` répertoire et la `HKLM` ruche de Registre sont des exemples d’emplacements accessibles en écriture par les administrateurs et accessibles en lecture par tout le monde. Les données lues à partir de ces emplacements sont donc considérées comme dignes de confiance.

Si une application doit utiliser la portée de l' _ordinateur_ dans un environnement multi-utilisateur, validez le contenu des fichiers que vous lisez à partir du magasin de l’ordinateur. Si l’application désérialise des graphiques d’objets à partir de ces fichiers, envisagez d’utiliser des sérialiseurs plus sûrs comme `XmlSerializer` au lieu de sérialiseurs dangereux comme `BinaryFormatter` ou `NetDataContractSerializer` . Soyez vigilant avec les graphiques d’objets profondément imbriqués ou les graphiques d’objets qui effectuent l’allocation des ressources en fonction du contenu du fichier.

<a name="isolated_storage_locations"></a>

## <a name="isolated-storage-locations"></a>Emplacements de stockage isolé

Il est parfois utile de vérifier une modification apportée au stockage isolé en utilisant le système de fichiers du système d'exploitation. Vous devrez peut-être également avoir besoin de connaître l'emplacement des fichiers de stockage isolé. Cet emplacement dépend du système d'exploitation. Le tableau suivant illustre les emplacements racine du stockage isolé sur quelques systèmes d'exploitation courants. Examinez les répertoires Microsoft\IsolatedStorage sous cet emplacement racine. Vous devez modifier les paramètres de dossier pour afficher les fichiers et les dossiers cachés afin de visualiser le stockage isolé dans le système de fichiers.

|Système d’exploitation|Emplacement dans le système de fichiers|
|----------------------|-----------------------------|
|Windows 2000, Windows XP, Windows Server 2003 (mise à niveau de Windows NT 4.0)|Magasins itinérants =<br /><br /> \<SYSTEMROOT>\Profiles \\<utilisateur \> \Application Data<br /><br /> Magasins non itinérants =<br /><br /> \<SYSTEMROOT>\Profiles \\<utilisateur \> \Local Settings\Application Data|
|Windows 2000 - Nouvelle installation (et mises à niveau de Windows 98 et Windows NT 3.51)|Magasins itinérants =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings \\<utilisateur \> \Application Data<br /><br /> Magasins non itinérants =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings \\<utilisateur \> \Local Settings\Application Data|
|Windows XP, Windows Server 2003 - Nouvelle installation (et mises à niveau de Windows 2000 et Windows 98)|Magasins itinérants =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings \\<utilisateur \> \Application Data<br /><br /> Magasins non itinérants =<br /><br /> \<SYSTEMDRIVE>\Documents and Settings \\<utilisateur \> \Local Settings\Application Data|
|Windows 8, Windows 7, Windows Server 2008, Windows Vista|Magasins itinérants =<br /><br /> \<SYSTEMDRIVE>\Utilisateurs \\<utilisateur \> \AppData\Roaming<br /><br /> Magasins non itinérants =<br /><br /> \<SYSTEMDRIVE>\Utilisateurs \\<utilisateur \> \AppData\Local|

<a name="isolated_storage_tasks"></a>

## <a name="creating-enumerating-and-deleting-isolated-storage"></a>Création, énumération et suppression du stockage isolé

Le .NET Framework fournit trois classes dans l'espace de noms <xref:System.IO.IsolatedStorage> pour vous aider à exécuter des tâches qui impliquent le stockage isolé :

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, qui dérive de <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType> , assure la gestion de base des fichiers d'application et d'assembly stockés. Une instance de la classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> représente un magasin unique situé dans le système de fichiers.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> , qui dérive de <xref:System.IO.FileStream?displayProperty=nameWithType> , donne accès aux fichiers d'un magasin.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope> est une énumération qui vous permet de créer et de sélectionner un magasin avec un type d'isolation approprié.

Les classes de stockage isolé vous permettent de créer, d'énumérer et de supprimer le stockage isolé. Les méthodes permettant d'effectuer ces tâches sont disponibles par l'intermédiaire de l'objet <xref:System.IO.IsolatedStorage.IsolatedStorageFile> . Avec certaines opérations, vous devez disposer de l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> qui représente le droit d'administrer le stockage isolé ; vous pouvez également être amené à disposer de droits de système d'exploitation pour accéder au fichier ou au répertoire.

Pour obtenir une série d’exemples illustrant les tâches de stockage isolé courantes, consultez les rubriques « comment » sous [Rubriques connexes](#related_topics).

<a name="scenarios_for_isolated_storage"></a>

## <a name="scenarios-for-isolated-storage"></a>Scénarios de stockage isolé

Le stockage isolé est utile dans de nombreuses situations, notamment dans ces quatre scénarios :

- Contrôles téléchargés. Les contrôles de code managé téléchargés à partir d'Internet ne sont pas autorisés à écrire sur le disque dur via les classes E/S ordinaires, mais ils peuvent utiliser le stockage isolé pour rendre persistants les paramètres des utilisateurs et les états des applications.

- Stockage de composant partagé. Les composants partagés entre plusieurs applications peuvent utiliser le stockage isolé pour fournir un accès contrôlé aux magasins de données.

- Stockage serveur. Les applications serveur peuvent utiliser le stockage isolé pour fournir des magasins individuels à de nombreux utilisateurs qui effectuent des demandes à l'application. Dans la mesure où le stockage isolé est toujours isolé par l'utilisateur, le serveur doit emprunter l'identité de l'utilisateur qui effectue la demande. Dans ce cas, les données sont isolées en fonction de l'identité de l'entité de sécurité, qui est identique à l'identité utilisée par l'application pour établir une distinction entre ses utilisateurs.

- Profil itinérant. Les applications peuvent également utiliser le stockage isolé avec des profils d'utilisateur itinérant. Ainsi, les magasins isolés d'un utilisateur peuvent être itinérants avec le profil.

Vous ne devez pas utiliser le stockage isolé dans les situations suivantes :

- Pour stocker des secrets de grande valeur, tels que des clés ou des mots de passe non chiffrés, car le stockage isolé n'est pas protégé contre le code à niveau de confiance extrêmement élevé, contre le code non managé ou contre les utilisateurs de confiance de l'ordinateur.

- Pour stocker du code.

- Pour enregistrer les paramètres de configuration et de déploiement, qui sont contrôlés par les administrateurs. (les préférences de l'utilisateur ne sont pas considérées comme des paramètres de configuration car les administrateurs ne les contrôlent pas).

De nombreuses applications utilisent une base de données pour stocker et isoler des données. Dans ce cas, une ou plusieurs lignes d'une base de données peuvent représenter le stockage d'un utilisateur spécifique. Vous pouvez utiliser le stockage isolé plutôt qu'une base de données lorsque le nombre d'utilisateurs est petit, lorsque la surcharge de l'utilisation d'une base de données est significative ou lorsque aucune base de données n'existe. Le stockage isolé peut également être utilisé lorsque l'application nécessite un stockage plus flexible et plus complexe que celui proposé par une ligne d'une base de données.

<a name="related_topics"></a>

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Types d'isolation](types-of-isolation.md)|Décrit les divers types d'isolation.|
|[Procédure : obtenir des magasins pour le stockage isolé](how-to-obtain-stores-for-isolated-storage.md)|Donne un exemple d'utilisation de la classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> pour obtenir un magasin isolé par utilisateur et par assembly.|
|[Procédure : énumérer des magasins pour le stockage isolé](how-to-enumerate-stores-for-isolated-storage.md)|Indique comment utiliser la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> pour calculer la taille de tout le stockage isolé de l'utilisateur.|
|[Procédure : supprimer des magasins dans le stockage isolé](how-to-delete-stores-in-isolated-storage.md)|Indique comment utiliser la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> de deux façons différentes pour supprimer des magasins isolés.|
|[Procédure : anticiper des conditions d’espace insuffisant avec le stockage isolé](how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|Illustre comment mesurer l'espace restant dans un magasin isolé.|
|[Procédure : créer des fichiers et des répertoires dans un stockage isolé](how-to-create-files-and-directories-in-isolated-storage.md)|Propose plusieurs exemples pour créer des fichiers et des répertoires dans un magasin isolé.|
|[Procédure : rechercher des fichiers et des répertoires existants dans un stockage isolé](how-to-find-existing-files-and-directories-in-isolated-storage.md)|Illustre comment lire la structure de répertoire et les fichiers dans le stockage isolé.|
|[Procédure : lire et écrire des fichiers dans un stockage isolé](how-to-read-and-write-to-files-in-isolated-storage.md)|Fournit un exemple d'écriture d'une chaîne dans un fichier de stockage isolé et de sa lecture ultérieure.|
|[Procédure : supprimer des fichiers et des répertoires dans un stockage isolé](how-to-delete-files-and-directories-in-isolated-storage.md)|Indique comment supprimer des fichiers et des répertoires d'un stockage isolé|
|[E/s de fichier et de flux](index.md)|Explique comment accéder aux flux de données et de fichiers de façon synchrone et asynchrone.|

<a name="reference"></a>

## <a name="reference"></a>Informations de référence

- <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
