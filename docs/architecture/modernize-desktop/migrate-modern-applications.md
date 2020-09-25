---
title: Migration d’applications de bureau modernes
description: Tout ce que vous devez savoir sur le processus de migration pour les applications de bureau modernes.
ms.date: 05/12/2020
ms.openlocfilehash: f7862d6379eeeb737c386b5ffeaab938d258b046
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173331"
---
# <a name="migrating-modern-desktop-applications"></a>Migration d’applications de bureau modernes

Dans ce chapitre, nous explorons les problèmes et les défis les plus courants que vous pouvez rencontrer lors de la migration d’une application existante de .NET Framework à .NET Core.

Une application de bureau complexe ne fonctionne pas de manière isolée et nécessite un type d’interaction avec les sous-systèmes qui peuvent résider sur l’ordinateur local ou sur un serveur distant. Il aura probablement besoin d’un type de base de données pour se connecter en tant que stockage de persistance localement ou à distance. Avec le déclenchement d’architectures orientées services et Internet, il est courant que votre application soit connectée à une sorte de service résidant sur un serveur distant ou dans le Cloud. Vous devrez peut-être accéder au système de fichiers de l’ordinateur pour implémenter certaines fonctionnalités. Vous pouvez également utiliser une partie des fonctionnalités qui résident à l’intérieur d’un objet COM en dehors de votre application, ce qui est un scénario courant si, par exemple, vous intégrez des assemblys Office à votre application.

En outre, il existe des différences dans la surface de l’API qui est exposée par .NET Framework et .NET Core, et certaines fonctionnalités disponibles sur .NET Framework ne sont pas disponibles sur .NET Core. C’est pourquoi il est important que vous les sachiez et les prenne en compte lors de la planification d’une migration.

## <a name="configuration-files"></a>Fichiers de configuration

Les fichiers de configuration offrent la possibilité de stocker des ensembles de propriétés qui sont lus au moment de l’exécution et qui affectent le comportement de nos applications, telles que l’emplacement de la base de données ou le nombre d’exécutions d’une boucle. L’avantage de cette technique est que vous pouvez modifier certains aspects de l’application sans avoir besoin de le coder et de le recompiler. Cela est utile lorsque, par exemple, le même code d’application s’exécute sur un environnement de développement avec un certain ensemble de valeurs de configuration et en production avec un autre ensemble de valeurs de configuration.

### <a name="configuration-on-net-framework"></a>Configuration sur .NET Framework

Si vous disposez d’une application de bureau .NET Framework, il est probable que vous ayez un fichier *app.config* accessible via la <xref:System.Configuration.AppSettingsSection> classe à partir de l' `System.Configuration` espace de noms.

Dans l’infrastructure .NET Framework, il existe une hiérarchie de fichiers de configuration qui héritent des propriétés de ses parents. Vous pouvez trouver un fichier de *machine.config* qui définit de nombreuses propriétés et sections de configuration qui peuvent être utilisées ou remplacées dans n’importe quel fichier de configuration descendant.

### <a name="configuration-on-net-core"></a>Configuration sur .NET Core

Dans le monde .NET Core, il n’y a pas de fichier *machine.config* . Et même si vous pouvez continuer à utiliser l’ancien <xref:System.Configuration> espace de noms, vous pouvez envisager de passer à la version moderne <xref:Microsoft.Extensions.Configuration> , ce qui offre un bon nombre d’améliorations.

L’API de configuration prend en charge le concept de fournisseur de configuration, qui définit la source de données à utiliser pour charger la configuration. Il existe différents types de fournisseurs intégrés, tels que :

- Objets .NET en mémoire
- Fichiers INI
- Fichiers JSON
- Fichiers XML
- Arguments de ligne de commande
- Variables d'environnement
- Magasin d’utilisateurs chiffré

 Ou vous pouvez créer vos propres.

La nouvelle configuration autorise une liste de paires nom-valeur qui peuvent être regroupées dans une hiérarchie à plusieurs niveaux. Toute valeur stockée est mappée à une chaîne, et une prise en charge de liaison intégrée vous permet de désérialiser les paramètres dans un objet POCO (Plain Old CLR Object) personnalisé.

L' <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> objet vous permet d’ajouter autant de fournisseurs de configuration dont vous pouvez avoir besoin pour votre application, en utilisant une règle de précédence pour résoudre la préférence. Ainsi, le dernier fournisseur que vous ajoutez dans votre code remplacera les autres. Il s’agit d’une fonctionnalité intéressante pour la gestion de différents environnements en vue de leur exécution, car vous pouvez définir des configurations différentes pour les environnements de développement, de test et de production, et les gérer sur une seule fonction à l’intérieur de votre code.

### <a name="migrating-configuration-files"></a>Migration des fichiers de configuration

Vous pouvez continuer à utiliser votre fichier app.config XML existant. Toutefois, vous pouvez prendre cette occasion de migrer votre configuration pour tirer parti des nombreuses améliorations apportées à .NET Core.

Pour migrer d’un ancien *app.config* vers un nouveau fichier de configuration, vous devez choisir entre un format XML et un format JSON.

Si vous choisissez XML, la conversion est simple. Étant donné que le contenu est identique, il vous suffit de renommer le fichier *app.config* dans un fichier avec l’extension XML. Ensuite, modifiez le code qui référence AppSettings pour utiliser la `ConfigurationBuilder` classe. Cette modification doit être facile.

Si vous souhaitez utiliser un format JSON et que vous ne souhaitez pas migrer manuellement, il existe un outil appelé [dotnet-config2json](https://www.nuget.org/packages/dotnet-config2json/) disponible sur .net Core, qui peut convertir un fichier *app.config* en fichier de configuration JSON.

Vous pouvez également rencontrer certains problèmes lors de l’utilisation des sections de configuration qui ont été définies dans le fichier *machine.config* . Par exemple, considérez la configuration suivante :

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

Si vous utilisez cette configuration dans .NET Core, vous obtenez une exception :

Section de configuration non reconnue System. Diagnostics

Cette exception se produit parce que cette section et l’assembly responsable de la gestion de cette section ont été définis dans le fichier *machine.config* , qui n’existe pas.

Pour résoudre facilement le problème, vous pouvez copier la définition de la section à partir de votre ancien *machine.config* vers votre nouveau fichier de configuration :

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a>Accès aux bases de données

Presque toutes les applications de bureau ont besoin d’un type de base de données. Pour les ordinateurs de bureau, il est courant de trouver des architectures client-serveur avec une connexion directe entre l’application de bureau et le moteur de base de données. Ces bases de données peuvent être locales ou distantes selon la nécessité de partager des informations entre différents utilisateurs.

Du point de vue du code, de nombreuses technologies et infrastructures ont été créées pour permettre au développeur de se connecter, d’interroger et de mettre à jour une base de données.

Les exemples les plus courants de base de données que vous pouvez trouver lorsque vous parlez de l’application de bureau Windows sont Microsoft Access et Microsoft SQL Server. Si vous avez plus de 20 ans d’expérience dans la programmation pour le bureau, des noms comme ODBC, OLEDB, RDO, ADO, ADO.NET, LINQ et Entity Framework vous paraîtront familiers.

### <a name="odbc"></a>ODBC

Vous pouvez continuer à utiliser ODBC sur .NET Core, car Microsoft fournit la `System.Data.Odbc` bibliothèque compatible avec .NET Standard 2,0.

### <a name="ole-db"></a>OLE DB

[OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))   est un excellent moyen d’accéder à diverses sources de données de manière uniforme. Mais il était basé sur COM, qui est une technologie Windows uniquement et, comme cela n’était pas le mieux adapté pour une technologie multiplateforme telle que .NET Core. Il n’est pas non plus pris en charge dans les versions 2014 et ultérieures de SQL Server. Pour ces raisons, OLE DB ne sera pas pris en charge par .NET Core.

### <a name="adonet"></a>ADO.NET

Vous pouvez toujours utiliser ADO.NET à partir de votre code de bureau existant sur .NET Core. Vous devez simplement mettre à jour certains packages NuGet.

### <a name="ef-core-vs-ef6"></a>EF Core et EF6

Il existe deux versions actuellement prises en charge de Entity Framework (EF), Entity Framework 6 (EF6) et EF Core.

La technologie la plus récente publiée dans le cadre du monde de la .NET Framework est Entity Framework, 6,4 étant la dernière version. Avec le lancement de .NET Core, Microsoft a également publié une nouvelle pile d’accès aux données basée sur Entity Framework et appelée Entity Framework Core.

Vous pouvez utiliser EF 6,4 et EF Core à la fois à partir de .NET Framework et de .NET Core. Alors, quels sont les facteurs décisionnels qui vous aideront à décider entre les deux ?

EF 6,3 est la première version de EF6 qui peut s’exécuter sur .NET Core et travailler sur plusieurs plateformes. En fait, l’objectif principal de cette version était de faciliter la migration des applications existantes qui utilisent EF6 vers .NET Core.

EF Core a été conçu pour fournir une expérience de développement similaire à EF6. La plupart des API de niveau supérieur restent les mêmes ; EF Core semblera donc familier aux développeurs EF6.

Bien que compatible, il existe des différences au niveau de l’implémentation que vous devez vérifier avant de prendre une décision.
Pour plus d’informations, consultez [comparer EF Core & EF6](/ef/efcore-and-ef6/).

La recommandation consiste à utiliser EF Core dans les cas suivants :

* L’application a besoin des fonctionnalités de .NET Core.
* EF Core prend en charge toutes les fonctionnalités requises par l’application.

Utilisez plutôt EF6 si les deux conditions suivantes sont remplies :

* L’application s’exécute sur Windows et .NET Framework 4,0 ou version ultérieure.
* EF6 prend en charge toutes les fonctionnalités requises par l’application.

### <a name="relational-databases"></a>Bases de données relationnelles

#### <a name="sql-server"></a>SQL Server

SQL Server a été l’une des bases de données de choix si vous développez pour le bureau il y a quelques années. Avec l’utilisation de <xref:System.Data.SqlClient> dans .NET Framework, vous pouvez accéder à des versions de SQL Server, qui encapsule des protocoles spécifiques à la base de données.

Dans .NET Core, vous pouvez trouver une nouvelle `SqlClient` classe, entièrement compatible avec celle qui existe dans le .NET Framework, mais qui se trouve dans la <xref:Microsoft.Data.SqlClient> bibliothèque. Il vous suffit d’ajouter une référence au package NuGet [Microsoft. Data. SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) et de renommer les espaces de noms pour que tout fonctionne comme prévu.

#### <a name="microsoft-access"></a>Microsoft Access

Microsoft Access a été utilisé depuis des années lorsque le SQL Server sophistiqué et le plus évolutif n’était pas nécessaire. Vous pouvez toujours vous connecter à Microsoft Access à l’aide de la <xref:System.Data.Odbc> bibliothèque.

## <a name="consuming-services"></a>Utilisation des services

Avec l’augmentation des architectures orientées service, les applications de bureau ont commencé à évoluer d’un modèle client-serveur à l’approche à trois couches. Dans l’approche client-serveur, une connexion directe à la base de données est établie à partir du client qui détient la logique métier généralement à l’intérieur d’un seul fichier EXE. En revanche, l’approche à trois couches établit une couche de service intermédiaire qui implémente la logique métier et l’accès aux bases de données, ce qui permet de renforcer la sécurité, l’extensibilité et la réutilisation. Au lieu de travailler directement avec les jeux de données de données, l’approche de couche s’appuie sur un ensemble de services qui implémentent des contrats et des objets de type comme un moyen d’implémenter le transfert de données.

Si vous disposez d’une application de bureau à l’aide d’un service WCF et que vous souhaitez la migrer vers .NET Core, vous devez prendre en compte certains éléments.

La première chose à faire est de résoudre la configuration pour accéder au service. Étant donné que la configuration est différente sur .NET Core, vous devez effectuer certaines mises à jour dans votre fichier de configuration.

Deuxièmement, vous devez régénérer le client de service avec les nouveaux outils présents sur Visual Studio 2019. Dans cette étape, vous devez envisager d’activer la génération des opérations synchrones pour rendre le client compatible avec votre code existant.

Après la migration, si vous constatez qu’il existe des bibliothèques dont vous avez besoin et qui ne sont pas présentes sur .NET Core, vous pouvez ajouter une référence au package NuGet [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et voir si les fonctions manquantes y sont.

Si vous utilisez la <xref:System.Net.WebRequest> classe pour effectuer des appels de service Web, il se peut que vous trouviez des différences sur .net core. La recommandation consiste à utiliser System .net. http. HttpClient à la place.

## <a name="consuming-a-com-object"></a>Utilisation d’un objet COM

Actuellement, il n’existe aucun moyen d’ajouter une référence à un objet COM à partir de Visual Studio 2019 pour l’utiliser avec .NET Core. Par conséquent, vous devez modifier manuellement le fichier projet.

Insérez une `COMReference` structure à l’intérieur du fichier projet, comme dans l’exemple suivant :

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a>Autres éléments à prendre en compte

Plusieurs technologies disponibles pour les bibliothèques de .NET Framework ne sont pas disponibles pour .NET Core. Si votre code s’appuie sur certaines de ces technologies, tenez compte des autres approches décrites dans cette section.

Le [Pack de compatibilité Windows](../../core/porting/windows-compat-pack.md) fournit un accès aux API qui étaient auparavant disponibles uniquement pour les .NET Framework. Il peut être utilisé sur des projets .NET Core et .NET Standard.

Pour plus d’informations sur la compatibilité des API, consultez la documentation sur les modifications avec rupture et les API déconseillées/héritées à l’adresse <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> .

### <a name="appdomains"></a>AppDomains

Les domaines d’application (AppDomains) isolent les applications les unes des autres. Les AppDomains nécessitent une prise en charge du runtime et sont coûteux. La création de domaines d’application supplémentaires n’est pas prise en charge. Pour l’isolation du code, nous recommandons d’utiliser des processus distincts ou des conteneurs à la place. Pour le chargement dynamique d’assemblys, nous vous recommandons d’utiliser la nouvelle  <xref:System.Runtime.Loader.AssemblyLoadContext> classe.

Pour faciliter la migration du code .NET Framework, .NET Core expose une partie de la surface de l’API AppDomain. Certaines des API fonctionnent normalement (par exemple,  <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> ), certains membres ne font rien (par exemple,  <xref:System.AppDomain.SetCachePath%2A> ), et certains lèvent <xref:System.PlatformNotSupportedException> (par exemple,  <xref:System.AppDomain.CreateDomain%2A> ).

### <a name="remoting"></a>Communication à distance

.NET Remoting a été utilisé pour la communication entre AppDomains, qui n’est plus prise en charge. Par ailleurs, Remoting requiert la prise en charge du runtime, dont la maintenance est coûteuse. Pour ces raisons, .NET Remoting n’est pas pris en charge sur .NET Core.

Pour la communication entre les processus, vous devez considérer les mécanismes de communication entre processus (IPC) comme une alternative à la communication à distance, telle que la <xref:System.IO.Pipes?displayProperty=nameWithType> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> classe ou.

Pour la communication entre ordinateurs, utilisez plutôt une solution réseau. De préférence, utilisez un protocole en texte clair à faible surcharge, tel que HTTP. Le serveur web Kestrel, utilisé par ASP.NET Core, est une possibilité.

### <a name="code-access-security-cas"></a>Sécurité d'accès du code

Le sandboxing, qui s’appuie sur le runtime ou l’infrastructure pour contraindre les ressources qu’une application ou une bibliothèque managée utilise ou exécute, n’est pas pris en charge sur .NET Core.

Utilisez les limites de sécurité fournies par le système d’exploitation, telles que la virtualisation, les conteneurs ou les comptes d’utilisateur pour l’exécution des processus avec l’ensemble minimal de privilèges.

### <a name="security-transparency"></a>Transparence de la sécurité

Tout comme la sécurité d’accès du code, la transparence de la sécurité sépare le code sandbox du code critique de sécurité d’une manière déclarative, mais n’est plus prise en charge en tant que limite de sécurité.

Utilisez les limites de sécurité fournies par le système d’exploitation, telles que la virtualisation, les conteneurs ou les comptes d’utilisateur pour l’exécution des processus avec le plus petit ensemble de privilèges.

>[!div class="step-by-step"]
>[Précédent](whats-new-dotnet-core.md ) 
> [Suivant](windows-migration.md)
