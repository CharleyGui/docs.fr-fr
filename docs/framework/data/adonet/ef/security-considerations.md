---
title: Considérations sur la sécurité (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 84758642-9b72-4447-86f9-f831fef46962
ms.openlocfilehash: 90422ebd0f313bfa64b446159d27bcf44024f247
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552269"
---
# <a name="security-considerations-entity-framework"></a>Considérations sur la sécurité (Entity Framework)
Cette rubrique décrit les considérations relatives à la sécurité qui sont spécifiques au développement, au déploiement et à l’exécution d’applications Entity Framework. Vous devez également suivre les recommandations relatives à la création d’applications .NET Framework sécurisées. Pour plus d’informations, consultez [Vue d’ensemble de la sécurité](../security-overview.md).  
  
## <a name="general-security-considerations"></a>Considérations générales sur la sécurité  
 Les considérations de sécurité suivantes s’appliquent à toutes les applications qui utilisent le Entity Framework.  
  
#### <a name="use-only-trusted-data-source-providers"></a>Utilisez uniquement des fournisseurs de sources de données approuvés.  
 Pour communiquer avec la source de données, un fournisseur doit effectuer les opérations suivantes :  
  
- Recevoir la chaîne de connexion de la Entity Framework.  
  
- traduire l’arborescence de commandes en langage de requête natif de la source de données ;  
  
- assembler et retourner des jeux de résultats.  
  
 Pendant l'opération d'ouverture de session, les informations qui sont basées sur le mot de passe de l'utilisateur sont passées au serveur via bibliothèques réseau de la source de données sous-jacente. Un fournisseur malveillant peut voler les informations d'identification de l'utilisateur, générer des requêtes malveillantes ou falsifier le jeu de résultats.  
  
#### <a name="encrypt-your-connection-to-protect-sensitive-data"></a>Chiffrez votre connexion pour protéger les données sensibles.  
 Le Entity Framework ne gère pas directement le chiffrement des données. Si les utilisateurs accèdent aux données via un réseau public, votre application doit établir une connexion chiffrée à la source de données pour augmenter la sécurité. Pour plus d'informations, voir la documentation relative à la sécurité pour votre source de données. Pour obtenir une SQL Server source de données, consultez [chiffrement des connexions à SQL Server](/previous-versions/sql/sql-server-2008-r2/ms189067(v=sql.105)).  
  
#### <a name="secure-the-connection-string"></a>Sécurisez la chaîne de connexion.  
 La protection de l'accès à votre source de données représente l'un de vos principaux objectifs lorsque vous sécurisez une application. Une chaîne de connexion présente une vulnérabilité potentielle si elle n'est pas sécurisée ou si elle n'est pas correctement construite. Lorsque vous stockez les informations de connexion au format texte brut ou que vous les conservez dans la mémoire, vous risquez de compromettre l'ensemble de votre système. Les méthodes recommandées pour sécuriser des chaînes de connexion sont les suivantes :  
  
- Utilisez l'authentification Windows avec une source de données SQL Server.  
  
     Lorsque vous utilisez l'authentification Windows pour vous connecter à une source de données SQL Server, la chaîne de connexion ne contient pas d'informations d'ouverture de session et de mot de passe.  
  
- Chiffrez les sections du fichier de configuration à l'aide d'une configuration protégée.  
  
     ASP.NET fournit une nouvelle fonctionnalité, appelée « configuration protégée », qui vous permet de chiffrer les informations sensibles dans un fichier de configuration. Bien qu'elle ait été conçue à l'origine pour ASP.NET, vous pouvez utiliser la configuration protégée pour chiffrer les sections des fichiers de configuration dans des applications Windows. Pour obtenir une description détaillée des nouvelles fonctionnalités de configuration protégée, consultez [chiffrement des informations de configuration à l’aide de la configuration protégée](/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
- Stockez les chaînes de connexion dans des fichiers de configuration sécurisés.  
  
     Vous ne devez jamais incorporer des chaînes de connexion dans votre code source. Vous pouvez stocker des chaînes de connexion dans des fichiers de configuration, ce qui évite d'avoir à les incorporer dans le code de votre application. Par défaut, l'Assistant EDM stocke les chaînes de connexion dans le fichier de configuration de l'application. Vous devez sécuriser ce fichier pour empêcher l'accès non autorisé.  
  
- Utilisez des générateurs de chaînes de connexion lors de la création dynamique de connexions.  
  
     Si vous devez construire des chaînes de connexion au moment de l'exécution, utilisez la classe <xref:System.Data.EntityClient.EntityConnectionStringBuilder>. Cette classe du générateur de chaînes permet d'empêcher les attaques par injection de chaîne de connexion en validant et en plaçant dans une séquence d'échappement les informations d'entrée non valides. Pour plus d’informations, consultez [Comment : générer une chaîne de connexion EntityConnection](how-to-build-an-entityconnection-connection-string.md). Utilisez également la classe de générateur de chaînes appropriée pour construire la chaîne de connexion à la source de données qui fait partie de la chaîne de connexion Entity Framework. Pour plus d’informations sur les générateurs de chaînes de connexion pour les fournisseurs ADO.NET, consultez [générateurs de chaînes de connexion](../connection-string-builders.md).  
  
 Pour plus d’informations, consultez [Protection des informations de connexion](../protecting-connection-information.md).  
  
#### <a name="do-not-expose-an-entityconnection-to-untrusted-users"></a>N'exposez pas un EntityConnection à des utilisateurs non approuvés.  
 Un objet <xref:System.Data.EntityClient.EntityConnection> expose la chaîne de connexion de la connexion sous-jacente. Un utilisateur ayant accès à un objet <xref:System.Data.EntityClient.EntityConnection> peut également modifier l'objet <xref:System.Data.ConnectionState> de la connexion sous-jacente. La classe <xref:System.Data.EntityClient.EntityConnection> n'est pas thread-safe.  
  
#### <a name="do-not-pass-connections-outside-the-security-context"></a>Ne passez pas de connexions à l'extérieur du contexte de sécurité.  
 Après avoir établi une connexion, vous ne devez pas la passer à l'extérieur du contexte de sécurité. Par exemple, un thread bénéficiant de l'autorisation nécessaire pour ouvrir une connexion ne doit pas stocker la connexion dans un emplacement global. Si la connexion est disponible dans un emplacement global, un autre thread malveillant peut utiliser la connexion ouverte sans que cette autorisation lui soit explicitement accordée.  
  
#### <a name="be-aware-that-logon-information-and-passwords-may-be-visible-in-a-memory-dump"></a>Gardez à l'esprit que les informations de connexion et les mots de passe peuvent être visibles dans un vidage de la mémoire.  
 Lorsque les informations d’ouverture de session et de mot de passe de la source de données sont fournies dans la chaîne de connexion, ces informations sont conservées en mémoire jusqu’à ce que le garbage collection récupère les ressources. Il est par conséquent impossible de déterminer quand une chaîne de mot de passe n'est plus en mémoire. Si une application se bloque, un fichier de vidage de la mémoire peut contenir des informations sensibles sur la sécurité, et l'utilisateur qui exécute l'application ainsi que tout utilisateur disposant d'un accès en tant qu'administrateur à l'ordinateur peuvent consulter le fichier de vidage de la mémoire. Utilisez l'authentification Windows pour les connexions à Microsoft SQL Server.  
  
#### <a name="grant-users-only-the-necessary-permissions-in-the-data-source"></a>Accordez aux utilisateurs uniquement les autorisations nécessaires dans la source de données.  
 Un administrateur de source de données doit accorder uniquement les autorisations nécessaires aux utilisateurs. Même si [!INCLUDE[esql](../../../../../includes/esql-md.md)] ne prend pas en charge les instructions DML qui modifient les données, telles qu'INSERT, UPDATE ou DELETE, les utilisateurs peuvent néanmoins accéder à la connexion à la source de données. Un utilisateur malveillant pourrait utiliser cette connexion pour exécuter des instructions DML dans le langage natif de la source de données.  
  
#### <a name="run-applications-with-the-minimum-permissions"></a>Exécutez les applications avec les autorisations minimales.  
 Lorsque vous autorisez une application managée à s’exécuter avec une autorisation de confiance totale, le .NET Framework ne limite pas l’accès de l’application à votre ordinateur. De ce fait, une faille de sécurité dans votre application risque de compromettre l'ensemble de votre système. Pour utiliser la sécurité d’accès du code et d’autres mécanismes de sécurité dans le .NET Framework, vous devez exécuter des applications à l’aide d’autorisations de confiance partielle et avec l’ensemble minimal d’autorisations nécessaires pour permettre à l’application de fonctionner. Les autorisations d’accès au code suivantes sont les autorisations minimales dont votre application Entity Framework a besoin :  
  
- <xref:System.Security.Permissions.FileIOPermission> : <xref:System.Security.Permissions.FileIOPermissionAccess.Write> pour ouvrir les fichiers de métadonnées spécifiés ou <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery> pour rechercher des fichiers de métadonnées dans un répertoire.  
  
- <xref:System.Security.Permissions.ReflectionPermission> : <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess> pour prendre en charge des requêtes LINQ to Entities.  
  
- <xref:System.Transactions.DistributedTransactionPermission>: <xref:System.Security.Permissions.PermissionState.Unrestricted> pour s'inscrire dans un objet <xref:System.Transactions><xref:System.Transactions.Transaction>.  
  
- <xref:System.Security.Permissions.SecurityPermission> : <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> pour sérialiser des exceptions à l'aide de l'interface <xref:System.Runtime.Serialization.ISerializable>.  
  
- Autorisation d’ouvrir une connexion de base de données et d’exécuter des commandes sur la base de données, par exemple <xref:System.Data.SqlClient.SqlClientPermission> pour une base de données SQL Server.  
  
 Pour plus d'informations, consultez [Code Access Security and ADO.NET](../code-access-security.md).  
  
#### <a name="do-not-install-untrusted-applications"></a>N'installez pas d'applications non approuvées.  
 L’Entity Framework n’applique aucune autorisation de sécurité et appelle le code d’objet de données fourni par l’utilisateur dans le processus, qu’il soit approuvé ou non. Assurez-vous que l'authentification et l'autorisation du client sont effectuées par la banque de données et par votre application.  
  
#### <a name="restrict-access-to-all-configuration-files"></a>Limitez l'accès à tous les fichiers de configuration.  
 Un administrateur doit limiter l’accès en écriture à tous les fichiers qui spécifient la configuration d’une application, y compris à enterprisesec.config, à security.config, à machine. conf et au fichier de configuration de l’application \<*application*>.exe.config.  
  
 Le nom invariant du fournisseur est modifiable dans le app.config. L’application cliente doit prendre la responsabilité d’accéder au fournisseur sous-jacent par le biais du modèle de fabrique de fournisseurs standard en utilisant un nom fort.  
  
#### <a name="restrict-permissions-to-the-model-and-mapping-files"></a>Limitez les autorisations aux fichiers de modèle et de mappage.  
 Un administrateur doit limiter l'accès en écriture aux fichiers de modèle et de mappage (.edmx, .csdl, .ssdl et .msl) uniquement aux utilisateurs qui modifient le modèle ou les mappages. Le Entity Framework nécessite uniquement un accès en lecture à ces fichiers au moment de l’exécution. Un administrateur doit également limiter l’accès aux fichiers de code source de la couche objet et de la vue précompilée qui sont générés par les outils de Entity Data Model.  
  
## <a name="security-considerations-for-queries"></a>Considérations sur la sécurité pour les requêtes  
 Vous devez tenir compte des considérations sur la sécurité suivantes lors de l'interrogation d'un modèle conceptuel. Ces considérations s'appliquent aux requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] utilisant EntityClient et aux requêtes d'objet utilisant LINQ, [!INCLUDE[esql](../../../../../includes/esql-md.md)] et les méthodes du Générateur de requêtes.  
  
#### <a name="prevent-sql-injection-attacks"></a>Empêchez les attaques par injection de code SQL.  
 Les applications reçoivent fréquemment des entrées externes (provenant d'un utilisateur ou d'un autre agent externe) et exécutent des actions en fonction de ces entrées. Toute entrée qui provient directement ou indirectement d'un utilisateur ou d'un agent externe doit avoir un contenu qui utilise la syntaxe du langage cible afin d'exécuter des actions non autorisées. Lorsque le langage cible est un langage SQL (SQL), tel que Transact-SQL, cette manipulation est appelée « attaque par injection de SQL ». Un utilisateur malveillant peut injecter des commandes directement dans la requête et déposer une table de base de données, provoquer un déni de service ou modifier d’une manière ou d’une autre la nature de l’opération en cours.  
  
- Attaques par injection [!INCLUDE[esql](../../../../../includes/esql-md.md)] :  
  
     Les attaques par injection de code SQL peuvent être effectuées dans [!INCLUDE[esql](../../../../../includes/esql-md.md)] en fournissant une entrée malveillante à des valeurs qui sont utilisées dans un prédicat de requête et dans les noms de paramètres. Pour éviter le risque d'injection de code SQL, vous ne devez jamais associer une entrée d'utilisateur à un texte de commande [!INCLUDE[esql](../../../../../includes/esql-md.md)].  
  
     Les requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] acceptent des paramètres partout où des littéraux sont admis. Vous devez utiliser des requêtes paramétrables plutôt que d'injecter des littéraux directement dans la requête à partir d'un agent externe. Vous devez également envisager d’utiliser les [méthodes du générateur de requêtes](/previous-versions/dotnet/netframework-4.0/bb896238(v=vs.100)) pour construire Entity SQL en toute sécurité.  
  
- Attaques par injection de LINQ to Entities :  
  
     Bien que la composition des requêtes soit possible dans LINQ to Entities, elle est effectuée via l’API du modèle objet. Contrairement aux [!INCLUDE[esql](../../../../../includes/esql-md.md)] requêtes, LINQ to Entities requêtes ne sont pas composées à l’aide de la manipulation ou de la concaténation de chaînes, et elles ne sont pas sujettes à des attaques par injection SQL traditionnelles.  
  
#### <a name="prevent-very-large-result-sets"></a>Évitez les jeux de résultats très volumineux.  
 Un jeu de résultats très volumineux pourrait entraîner l'arrêt du système client si le client effectue des opérations qui consomment des ressources proportionnelles à la taille du jeu de résultats. Les jeux de résultats volumineux inattendus peuvent se produire dans les conditions suivantes :  
  
- dans les requêtes qui n'incluent pas de conditions de filtre appropriées sur une base de données volumineuse ;  
  
- dans les requêtes qui créent des jointures cartésiennes sur le serveur ;  
  
- dans les requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] imbriquées.  
  
 Lorsque vous acceptez une entrée d'utilisateur, vous devez vous assurer que l'entrée ne peut pas générer des jeux de résultats plus volumineux que ce que le système peut gérer. Vous pouvez également utiliser la <xref:System.Linq.Queryable.Take%2A> méthode dans LINQ to Entities ou l’opérateur [Limit](./language-reference/limit-entity-sql.md) dans [!INCLUDE[esql](../../../../../includes/esql-md.md)] pour limiter la taille du jeu de résultats.  
  
#### <a name="avoid-returning-iqueryable-results-when-exposing-methods-to-potentially-untrusted-callers"></a>Évitez de retourner les résultats IQueryable lors de l'exposition de méthodes à des appelants potentiellement non fiables.  
 Évitez de retourner des types <xref:System.Linq.IQueryable%601> des méthodes exposées aux appelants potentiellement non fiables pour les raisons suivantes :  
  
- Le consommateur d'une requête qui expose un type <xref:System.Linq.IQueryable%601> pourrait appeler des méthodes qui exposent des données sécurisées ou augmentent la taille du jeu de résultats. Par exemple, considérez la signature de méthode suivante :  

    ```csharp
    public IQueryable<Customer> GetCustomer(int customerId)
    ```

    Un consommateur de cette requête pourrait appeler `.Include("Orders")` sur le `IQueryable<Customer>` retourné pour récupérer des données que la requête ne projette pas d'exposer. Cela peut être évité en modifiant le type de retour de la méthode en <xref:System.Collections.Generic.IEnumerable%601> et en appelant une méthode (telle que `.ToList()`) qui matérialise les résultats.  
  
- Parce que les requêtes <xref:System.Linq.IQueryable%601> sont exécutées lorsque les résultats sont itérés, le consommateur d'une requête qui expose un type <xref:System.Linq.IQueryable%601> pourrait intercepter des exceptions levées. Les exceptions pourraient contenir des informations non prévues pour le consommateur.  
  
## <a name="security-considerations-for-entities"></a>Considérations sur la sécurité pour les entités  
 Les considérations sur la sécurité suivantes s'appliquent lors de la génération et l'utilisation de types d'entités.  
  
#### <a name="do-not-share-an-objectcontext-across-application-domains"></a>Ne partagez pas un ObjectContext entre des domaines d'application.  
 Le partage d'un objet <xref:System.Data.Objects.ObjectContext> avec plusieurs domaines d'application peut exposer des informations dans la chaîne de connexion. Il est préférable de transférer les objets sérialisés ou les graphiques d'objets à l'autre domaine d'application, puis d'attacher ces objets à un objet <xref:System.Data.Objects.ObjectContext> dans ce domaine d'application. Pour plus d’informations, consultez [sérialisation d’objets](/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
#### <a name="prevent-type-safety-violations"></a>Évitez les violations de la cohérence des types.  
 Si la sécurité de type n’est pas respectée, le Entity Framework ne peut pas garantir l’intégrité des données dans les objets. Les violations de la cohérence des types peuvent se produire si vous permettez à des applications non approuvées de s'exécuter avec une sécurité d'accès du code d'un niveau de confiance totale.  
  
#### <a name="handle-exceptions"></a>Traitez les exceptions.  
 Accédez aux méthodes et aux propriétés d'un <xref:System.Data.Objects.ObjectContext> dans un bloc try-catch. L'interception d'exceptions empêche des exceptions non gérées d'exposer aux utilisateurs de votre application des entrées dans <xref:System.Data.Objects.ObjectStateManager> ou dans les informations de modèle (telles que les noms de tables).  
  
## <a name="security-considerations-for-aspnet-applications"></a>Considérations sur la sécurité pour les applications ASP.NET  

Tenez compte des éléments suivants lorsque vous utilisez des chemins d’accès dans des applications ASP.NET.  
  
#### <a name="verify-whether-your-host-performs-path-checks"></a>Vérifiez si votre hôte effectue des contrôles de chemin d’accès.  
 Lorsque la `|DataDirectory|` chaîne de substitution (placée dans les symboles de la barre verticale) est utilisée, ADO.net vérifie que le chemin d’accès résolu est pris en charge. Par exemple, « .. » n'est pas autorisé derrière `DataDirectory`. Cette vérification pour la résolution de l’opérateur racine de l’application Web ( `~` ) est effectuée par le processus qui héberge ASP.net. IIS effectue ce contrôle ; toutefois, les hôtes autres qu'IIS ne peuvent pas vérifier que le chemin d'accès résolu est pris en charge. Vous devez connaître le comportement de l’hôte sur lequel vous déployez une application Entity Framework.  
  
#### <a name="do-not-make-assumptions-about-resolved-path-names"></a>Ne faites pas de suppositions sur les noms de chemins d’accès résolus.  
 Bien que les valeurs auxquelles l’opérateur racine ( `~` ) et la `DataDirectory` chaîne de substitution résolvent restent constantes pendant le runtime de l’application, le Entity Framework ne limite pas l’hôte à la modification de ces valeurs.  
  
#### <a name="verify-the-path-length-before-deployment"></a>Vérifiez la longueur du chemin d’accès avant le déploiement.  
 Avant de déployer une application Entity Framework, vous devez vous assurer que les valeurs de l’opérateur racine (~) et de la `DataDirectory` chaîne de substitution ne dépassent pas les limites de la longueur du chemin d’accès dans le système d’exploitation. Les fournisseurs de données ADO.NET ne garantissent pas que la longueur du chemin d’accès est comprise dans les limites valides.  
  
## <a name="security-considerations-for-adonet-metadata"></a>Considérations sur la sécurité pour les métadonnées ADO.NET  
 Les considérations sur la sécurité suivantes s'appliquent lors de la génération et de l'utilisation de fichiers de modèle et de mappage.  
  
#### <a name="do-not-expose-sensitive-information-through-logging"></a>N'exposez pas d'informations sensibles via la journalisation.  
Les composants du service de métadonnées ADO.NET ne consignent aucune information privée. Si des résultats ne peuvent pas être retournés à cause de restrictions d'accès, les systèmes de gestion de base de données et les systèmes de fichiers doivent retourner zéro résultat au lieu de lever une exception qui pourrait contenir des informations sensibles.  
  
#### <a name="do-not-accept-metadataworkspace-objects-from-untrusted-sources"></a>N'acceptez pas d'objets MetadataWorkspace provenant de sources non fiables.  
 Les applications ne doivent pas accepter les instances de la classe <xref:System.Data.Metadata.Edm.MetadataWorkspace> provenant de sources non fiables. Il est préférable de construire et de remplir explicitement un espace de travail à partir d'une telle source.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Considérations relatives au déploiement](deployment-considerations.md)
- [Considérations relatives à la migration](migration-considerations.md)
