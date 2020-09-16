---
title: Remarques sur les performances (Entity Framework)
description: En savoir plus sur les caractéristiques de performances de l’Entity Framework ADO.NET et des considérations pour améliorer les performances des applications Entity Framework.
ms.date: 03/30/2017
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
ms.openlocfilehash: 2bdf088309dd178c1eef4cfb0b7e093b1f6be606
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557461"
---
# <a name="performance-considerations-entity-framework"></a>Remarques sur les performances (Entity Framework)
Cette rubrique décrit les caractéristiques de performance d'ADO.NET Entity Framework et fournit des points à prendre en considération pour vous aider à améliorer les performances des applications Entity Framework.  
  
## <a name="stages-of-query-execution"></a>Étapes de l'exécution des requêtes  
 Pour mieux comprendre les performances des requêtes dans Entity Framework, il est utile de comprendre les opérations qui se produisent lorsqu’une requête s’exécute sur un modèle conceptuel et retourne des données sous la forme d’objets. Le tableau ci-dessous décrit cette série d'opérations.  
  
|Opération|Coût relatif|Fréquence|Commentaires|  
|---------------|-------------------|---------------|--------------|  
|Chargement des métadonnées|Modéré|Une fois dans chaque domaine d'application.|Les métadonnées de modèle et de mappage utilisées par Entity Framework sont chargées dans un <xref:System.Data.Metadata.Edm.MetadataWorkspace>. Ces métadonnées sont mises en cache globalement et sont disponibles pour d'autres instances d'<xref:System.Data.Objects.ObjectContext> dans le même domaine d'application.|  
|Ouverture de la connexion de base de données|Modéré<sup>1</sup>|Autant que nécessaire.|Étant donné qu’une connexion ouverte à la base de données consomme une ressource précieuse, le Entity Framework s’ouvre et ferme la connexion à la base de données uniquement si nécessaire. Vous pouvez également ouvrir explicitement la connexion. Pour plus d’informations, consultez [gestion des connexions et des transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).|  
|Génération d'affichages|Élevé|Une fois dans chaque domaine d'application. (Ils peuvent être prégénérés.)|Avant qu’Entity Framework puisse exécuter une requête sur un modèle conceptuel ou enregistrer des modifications apportées à la source de données, il doit générer un ensemble d’affichages des requêtes locaux pour accéder à la base de données. En raison du coût élevé de la génération de ces affichages, vous pouvez prégénérer les affichages et les ajouter au projet au moment du design. Pour plus d’informations, consultez [procédure : prégénérer des vues pour améliorer les performances des requêtes](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).|  
|Préparation de la requête|Modéré<sup>2</sup>|Une fois pour chaque requête individuelle.|Inclut les coûts relatifs à la composition de la commande de requête, à la génération d’une arborescence de commandes basée sur les métadonnées de modèle et de mappage et à la définition de la forme des données retournées. Comme les commandes de requête Entity SQL et LINQ sont à présent mises en cache, il est possible d'exécuter ultérieurement une même requête pour économiser du temps. Vous pouvez toujours utiliser des requêtes LINQ compilées pour réduire ce coût dans les exécutions ultérieures et les requêtes compilées peuvent être plus efficaces que les requêtes LINQ qui sont automatiquement mises en cache. Pour plus d’informations, consultez [requêtes compilées (LINQ to Entities)](./language-reference/compiled-queries-linq-to-entities.md). Pour obtenir des informations générales sur l’exécution des requêtes LINQ, consultez [LINQ to Entities](./language-reference/linq-to-entities.md). **Remarque :**  LINQ to Entities les requêtes qui appliquent l' `Enumerable.Contains` opérateur aux collections en mémoire ne sont pas automatiquement mises en cache. Le paramétrage des collections en mémoire dans les requêtes LINQ compilées n’est pas autorisé.|  
|Exécution de la requête|Faible<sup>2</sup>|Une fois pour chaque requête.|Coût de l'exécution de la commande sur la source de données à l'aide du fournisseur de données ADO.NET. Comme la plupart des sources de données mettent en cache les plans de requête, les exécutions ultérieures des mêmes requêtes permettent d'économiser du temps.|  
|Chargement et validation de types|Faible<sup>3</sup>|Une fois pour chaque instance <xref:System.Data.Objects.ObjectContext>.|Les types sont chargés et validés par rapport aux types que le modèle conceptuel définit.|  
|Suivi|Faible<sup>3</sup>|Une fois pour chaque objet retourné par une requête. <sup>4</sup>|Si une requête utilise l’option de fusion <xref:System.Data.Objects.MergeOption.NoTracking>, cette étape n’affecte pas les performances.<br /><br /> Si la requête utilise l’option de fusion <xref:System.Data.Objects.MergeOption.AppendOnly>, <xref:System.Data.Objects.MergeOption.PreserveChanges> ou <xref:System.Data.Objects.MergeOption.OverwriteChanges>, les résultats de la requête sont suivis dans le <xref:System.Data.Objects.ObjectStateManager>. Une clé <xref:System.Data.EntityKey> est générée pour chaque objet de suivi que la requête retourne et est utilisée pour créer une entrée <xref:System.Data.Objects.ObjectStateEntry> dans le <xref:System.Data.Objects.ObjectStateManager>. Si un <xref:System.Data.Objects.ObjectStateEntry> existant est trouvé pour <xref:System.Data.EntityKey>, l'objet existant est retourné. Si l'option <xref:System.Data.Objects.MergeOption.PreserveChanges> ou <xref:System.Data.Objects.MergeOption.OverwriteChanges> est utilisée, l'objet est mis à jour avant d'être retourné.<br /><br /> Pour plus d’informations, consultez [résolution d’identité, gestion d’État et change Tracking](/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
|Matérialisation des objets|Modéré à<sup>3</sup>|Une fois pour chaque objet retourné par une requête. <sup>4</sup>|Processus de lecture de l'objet <xref:System.Data.Common.DbDataReader> retourné, de création d'objets et de définition des valeurs de propriété basées sur les valeurs dans chaque instance de la classe <xref:System.Data.Common.DbDataRecord>. Si l’objet existe déjà dans <xref:System.Data.Objects.ObjectContext> et que la requête utilise les options de fusion <xref:System.Data.Objects.MergeOption.AppendOnly> ou <xref:System.Data.Objects.MergeOption.PreserveChanges>, cette étape n’affecte pas les performances. Pour plus d’informations, consultez [résolution d’identité, gestion d’État et change Tracking](/previous-versions/dotnet/netframework-4.0/bb896269(v=vs.100)).|  
  
 <sup>1</sup> lorsqu’un fournisseur de sources de données implémente le regroupement de connexions, le coût de l’ouverture d’une connexion est réparti dans le pool. Le fournisseur .NET pour SQL Server prend en charge le regroupement de connexions.  
  
 <sup>2</sup> augmentation des coûts avec une complexité accrue des requêtes.  
  
 <sup>3</sup> le coût total augmente proportionnellement au nombre d’objets retournés par la requête.  
  
 <sup>4</sup> cette surcharge n’est pas requise pour les requêtes EntityClient, car les requêtes EntityClient retournent un <xref:System.Data.EntityClient.EntityDataReader> objet au lieu d’objets. Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="additional-considerations"></a>Considérations supplémentaires  
 D’autres considérations pouvant affecter les performances des applications Entity Framework sont exposées ci-dessous.  
  
### <a name="query-execution"></a>Exécution des requêtes  
 Comme les requêtes peuvent consommer beaucoup de ressources, considérez à quel point dans votre code et sur quel ordinateur une requête est exécutée.  
  
#### <a name="deferred-versus-immediate-execution"></a>Exécution différée / exécution immédiate  
 Lorsque vous créez une requête <xref:System.Data.Objects.ObjectQuery%601> ou LINQ, la requête peut ne pas être exécutée immédiatement. L’exécution de la requête est différée jusqu’à ce que les résultats soient requis, comme par exemple lors d’une énumération `foreach` (C#) ou `For Each` (Visual Basic) ou lorsqu’elle est affectée pour remplir une collection <xref:System.Collections.Generic.List%601>. L'exécution de la requête commence immédiatement lorsque vous appelez la méthode <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> sur un <xref:System.Data.Objects.ObjectQuery%601> ou lorsque vous appelez une méthode LINQ qui retourne une requête singleton, telle que <xref:System.Linq.Enumerable.First%2A> ou <xref:System.Linq.Enumerable.Any%2A>. Pour plus d’informations, consultez [requêtes d’objet](/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)) et exécution de [requêtes (LINQ to Entities)](./language-reference/query-execution.md).  
  
#### <a name="client-side-execution-of-linq-queries"></a>Exécution côté client de requêtes LINQ  
 Bien que l'exécution d'une requête LINQ se produise sur l'ordinateur qui héberge la source de données, certaines parties d'une requête LINQ peuvent être évaluées sur l'ordinateur client. Pour plus d’informations, consultez la section relative à l’exécution d’une requête dans le magasin d’exécution [(LINQ to Entities)](./language-reference/query-execution.md).  
  
### <a name="query-and-mapping-complexity"></a>Complexité des requêtes et du mappage  
 La complexité des requêtes individuelles et du mappage dans le modèle d'entité aura un effet significatif sur les performances des requêtes.  
  
#### <a name="mapping-complexity"></a>Complexité du mappage  
 Les modèles qui sont plus complexes qu'un mappage un-à-un simple entre des entités dans le modèle conceptuel et des tables dans le modèle de stockage génèrent des commandes plus complexes que les modèles qui ont un mappage un-à-un.  
  
#### <a name="query-complexity"></a>Complexité des requêtes  
 Les requêtes qui requièrent un grand nombre de jointures dans les commandes exécutées sur la source de données ou qui retournent une grande quantité de données peuvent affecter les performances des façons suivantes :  
  
- Des requêtes sur un modèle conceptuel qui paraissent simples peuvent provoquer l'exécution de requêtes plus complexes sur la source de données. Cela peut se produire parce qu’Entity Framework traduit une requête sur un modèle conceptuel en une requête équivalente sur la source de données. Lorsqu'un jeu d'entités individuel dans le modèle conceptuel est mappé à plusieurs tables dans la source de données ou lorsqu'une relation entre des entités est mappée à une table de jointures, la commande de requête exécutée sur la requête de source de données peut requérir une ou plusieurs jointures.  
  
    > [!NOTE]
    > Utilisez la méthode <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> des classes <xref:System.Data.Objects.ObjectQuery%601> ou <xref:System.Data.EntityClient.EntityCommand> pour consulter les commandes exécutées sur la source de données pour une requête donnée. Pour plus d’informations, consultez [Comment : afficher les commandes du Windows Store](/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
- Les requêtes Entity SQL imbriquées peuvent créer des jointures sur le serveur et peuvent retourner un grand nombre de lignes.  
  
     Vous trouverez ci-dessous un exemple de requête imbriquée dans une clause de projection :  
  
    ```sql  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     En outre, de telles requêtes provoquent la création par le pipeline de requête d'une requête individuelle avec la duplication d'objets sur l'ensemble des requêtes imbriquées. En raison de cela, une colonne individuelle peut être dupliquée plusieurs fois. Sur certaines bases de données, notamment SQL Server, cela peut provoquer une augmentation très importante de la taille de la table TempDB, ce qui peut réduire les performances du serveur. Vous devez faire très attention lorsque vous exécutez des requêtes imbriquées.  
  
- Toutes les requêtes qui retournent une grande quantité de données peuvent provoquer une diminution des performances si le client effectue des opérations qui consomment des ressources d'une façon proportionnelle à la taille du jeu de résultats. Dans de tels cas, vous devez envisager de limiter la quantité de données retournées par la requête. Pour plus d’informations, consultez [Comment : paginer à travers les résultats de la requête](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
 Toutes les commandes générées automatiquement par Entity Framework peuvent être plus complexes que des commandes semblables écrites explicitement par un développeur de base de données. Si vous avez besoin d'un contrôle explicite sur les commandes exécutées sur votre source de données, envisagez de définir un mappage à une fonction table ou à une procédure stockée.  
  
#### <a name="relationships"></a>Relations  
 Pour obtenir des performances de requête optimales, vous devez définir des relations entre les entités en tant qu'associations dans le modèle d'entité et entant que relations logiques dans la source de données.  
  
### <a name="query-paths"></a>Chemins d’accès des requêtes  
 Par défaut, lorsque vous exécutez une requête <xref:System.Data.Objects.ObjectQuery%601>, les objets connexes ne sont pas retournés (bien que les objets qui représentent les relations elles-mêmes le soient). Vous pouvez charger les objets connexes de l'une des trois manières suivantes :  
  
1. Définissez le chemin d’accès de la requête <xref:System.Data.Objects.ObjectQuery%601> avant qu’elle soit exécutée.  
  
2. Appelez la méthode `Load` au niveau de la propriété de navigation exposée par l'objet.  
  
3. Affectez à l'option <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> de l'objet <xref:System.Data.Objects.ObjectContext> la valeur `true`. Notez que cette opération est effectuée automatiquement lorsque vous générez le code de couche objet avec le [Concepteur de Entity Data Model](/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)). Pour plus d’informations, consultez [vue d’ensemble du code généré](/previous-versions/dotnet/netframework-4.0/cc982041(v=vs.100)).  
  
 Au moment de choisir l'option à utiliser, sachez qu'il y a une corrélation entre le nombre de demandes adressées à la base de données et la quantité de données retournées dans une requête individuelle. Pour plus d’informations, consultez [chargement d’objets connexes](/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
#### <a name="using-query-paths"></a>Utilisation des chemins d’accès de requête  
 Les chemins d'accès de requête définissent le graphique des objets qu'une requête retourne. Lorsque vous définissez un chemin d’accès de requête, il suffit d’adresser une demande unique à la base de données pour que tous les objets définis par le chemin d’accès soient retournés. L’utilisation de chemins d’accès de requête peut se traduire par l’exécution de commandes complexes sur la source de données à partir de requêtes d’objet d’apparence simple. Cela s'explique par le fait qu'une ou plusieurs jointures sont nécessaires pour qu'une même requête retourne des objets connexes. Cette complexité est plus prononcée dans le cas de requêtes exécutées sur un modèle d’entité complexe, par exemple, une entité avec héritage ou un chemin d’accès qui inclut des relations plusieurs-à-plusieurs.  
  
> [!NOTE]
> Utilisez la méthode <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> pour voir la commande qui sera générée par un <xref:System.Data.Objects.ObjectQuery%601>. Pour plus d’informations, consultez [Comment : afficher les commandes du Windows Store](/previous-versions/dotnet/netframework-4.0/bb896348(v=vs.100)).  
  
 Lorsqu’un chemin d’accès de requête comprend un trop grand nombre d’objets connexes ou que les objets contiennent une trop grande quantité de données de ligne, la source de données peut ne pas être en mesure de faire aboutir la requête. Cela se produit si la requête a besoin d'un stockage temporaire intermédiaire qui dépasse les capacités de la source de données. En pareil cas, vous pouvez réduire la complexité de la requête de source de données en chargeant explicitement les objets connexes.  
  
#### <a name="explicitly-loading-related-objects"></a>Chargement explicite d'objets connexes  
 Vous pouvez charger explicitement des objets connexes en appelant la méthode `Load` sur une propriété de navigation qui retourne <xref:System.Data.Objects.DataClasses.EntityCollection%601> ou <xref:System.Data.Objects.DataClasses.EntityReference%601>. Le chargement explicite d'objets requiert un aller-retour à la base de données chaque fois que la méthode `Load` est appelée.  
  
> [!NOTE]
> Si vous appelez `Load` tout en effectuant une boucle sur une collection d’objets retournés, comme par exemple lorsque vous utilisez l’instruction `foreach` (`For Each` en Visual Basic), le fournisseur spécifique à la source de données doit prendre en charge plusieurs jeux de résultats actifs sur une même connexion. Pour une base de données SQL Server, vous devez spécifier la valeur `MultipleActiveResultSets = true` dans la chaîne de connexion du fournisseur.  
  
 Vous pouvez également utiliser la méthode <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> en l'absence de propriétés <xref:System.Data.Objects.DataClasses.EntityCollection%601> ou <xref:System.Data.Objects.DataClasses.EntityReference%601> sur les entités. Cela peut s'avérer utile lorsque vous utilisez des entités POCO.  
  
 Bien que le chargement explicite d'objets connexes réduise le nombre de jointures ainsi que la quantité de données redondantes, la méthode `Load` requiert des connexions répétées à la base de données, ce qui peut devenir coûteux lors du chargement explicite d'un grand nombre d'objets.  
  
### <a name="saving-changes"></a>Enregistrement des modifications  
 Lorsque vous appelez la méthode <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> sur <xref:System.Data.Objects.ObjectContext>, une commande distincte de création, mise à jour ou suppression est générée pour chaque objet ajouté, mis à jour ou supprimé dans le contexte. Ces commandes sont exécutées sur la source de données dans une transaction unique. Comme avec les requêtes, les performances des opérations de création, mise à jour et suppression dépendent de la complexité du mappage dans le modèle conceptuel.  
  
### <a name="distributed-transactions"></a>Transactions distribuées  
 Des opérations dans une transaction explicite qui requièrent des ressources gérées par DTC (Distributed Transaction Coordinator) seront beaucoup plus coûteuses qu’une opération semblable qui ne requiert pas DTC. La promotion DTC se produira dans les situations suivantes :  
  
- Transaction explicite avec une opération sur une base de données SQL Server 2000 ou une autre source de données qui effectue toujours une promotion DTC des transactions explicites.  
  
- Transaction explicite avec une opération sur SQL Server 2005 lorsque la connexion est gérée par le Entity Framework. Cela est dû au fait que SQL Server 2005 promeut à un DTC chaque fois qu’une connexion est fermée et rouverte dans une transaction unique, ce qui correspond au comportement par défaut du Entity Framework. Cette promotion DTC n'a pas lieu lors de l'utilisation de SQL Server 2008. Pour éviter cette promotion lors de l'utilisation de SQL Server 2005, vous devez ouvrir et fermer explicitement la connexion dans la transaction. Pour plus d’informations, consultez [gestion des connexions et des transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
 Une transaction explicite est utilisée lorsqu'une ou plusieurs opérations sont exécutées au sein d'une transaction <xref:System.Transactions>. Pour plus d’informations, consultez [gestion des connexions et des transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="strategies-for-improving-performance"></a>Stratégies pour l'amélioration des performances  
 Vous pouvez améliorer les performances globales des requêtes dans Entity Framework en utilisant les stratégies ci-dessous.  
  
#### <a name="pre-generate-views"></a>Prégénérer des affichages  
 La génération d'affichages basés sur un modèle d'entité représente un coût significatif la première fois qu'une application exécute une requête. Utilisez l'utilitaire EdmGen.exe pour prégénérer des affichages sous la forme d'un fichier de code Visual Basic ou C# qui peut être ajouté au projet pendant la conception. Vous pouvez aussi utiliser un modèle Text Template Transformation Toolk pour générer des vues précompilées. Les vues prégénérées sont validées au moment de l'exécution pour garantir qu'elles sont cohérentes avec la version actuelle du modèle d'entité spécifié. Pour plus d’informations, consultez [procédure : prégénérer des vues pour améliorer les performances des requêtes](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).
  
 Tenez compte des éléments suivants lors de l'utilisation de très grands modèles :  
  
 Le format des métadonnées .NET limite le nombre de caractères de la chaîne utilisateur dans un binaire donné à 16,777,215 (0xFFFFFF). Si vous générez des vues pour un modèle très volumineux et que le fichier de vue atteint cette limite de taille, vous obtiendrez le « pas d’espace logique restant pour la création de chaînes utilisateur supplémentaires ». erreur de compilation. Cette limitation s'applique à tous les binaires gérés. Pour plus d’informations, consultez le [blog](/archive/blogs/appfabriccat/solving-the-no-logical-space-left-to-create-more-user-strings-error-and-improving-performance-of-pre-generated-views-in-visual-studio-net4-entity-framework) qui montre comment éviter l’erreur lors de l’utilisation de modèles volumineux et complexes.  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>Envisager d’utiliser l’option de fusion NoTracking pour les requêtes  
 Effectuer le suivi des objets retournés dans le contexte de l'objet a un coût obligatoire. Les objets doivent être joints à une instance <xref:System.Data.Objects.ObjectContext> pour que les modifications apportées aux objets soient détectées et pour garantir que plusieurs demandes pour la même entité logique retournent la même instance de l'objet. Si vous n’envisagez pas de mettre à jour ou de supprimer des objets et que vous n’avez pas besoin de la gestion des identités, envisagez d’utiliser les <xref:System.Data.Objects.MergeOption.NoTracking> options de fusion lorsque vous exécutez des requêtes.  
  
#### <a name="return-the-correct-amount-of-data"></a>Retourner la quantité appropriée de données  
 Dans certains scénarios, il est beaucoup plus rapide de spécifier un chemin d'accès de requête à l'aide de la méthode <xref:System.Data.Objects.ObjectQuery%601.Include%2A> car cela requiert moins d'allers-retours à la base de données. Toutefois, dans d'autres scénarios, des allers-retours supplémentaires à la base de données pour charger des objets connexes peuvent être plus rapides, car des requêtes plus simples avec moins de jointures entraînent une redondance de données moins importante. De ce fait, nous vous recommandons de tester les performances des différentes méthodes de récupération des objets connexes. Pour plus d’informations, consultez [chargement d’objets connexes](/previous-versions/dotnet/netframework-4.0/bb896272(v=vs.100)).  
  
 Pour éviter de retourner trop de données dans une même requête, envisagez de paginer les résultats de la requête en groupes plus maniables. Pour plus d’informations, consultez [Comment : paginer à travers les résultats de la requête](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)).  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>Limiter l'étendue d'ObjectContext  
 Dans la plupart des cas, vous devez créer une instance <xref:System.Data.Objects.ObjectContext> dans une instruction `using` (`Using…End Using` en Visual Basic). Cela peut augmenter les performances en garantissant la suppression automatique des ressources associées au contexte de l'objet à la fin de l'exécution d'un bloc d'instructions. Toutefois, lorsque des contrôles sont liés aux objets gérés par le contexte de l'objet, l'instance <xref:System.Data.Objects.ObjectContext> doit être conservée aussi longtemps que la liaison est requise, puis supprimée manuellement. Pour plus d’informations, consultez [gestion des connexions et des transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
#### <a name="consider-opening-the-database-connection-manually"></a>Envisager d'ouvrir la connexion de base de données manuellement  
 Lorsque votre application exécute une série de requêtes d’objet ou appelle fréquemment <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> pour conserver les opérations de création, de mise à jour et de suppression dans la source de données, le Entity Framework doit ouvrir et fermer continuellement la connexion à la source de données. En pareils cas, envisagez d'ouvrir manuellement la connexion au démarrage de ces opérations et de fermer ou supprimer la connexion une fois les opérations terminées. Pour plus d’informations, consultez [gestion des connexions et des transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).  
  
## <a name="performance-data"></a>Données de performance  
 Certaines données de performances de la Entity Framework sont publiées dans les publications suivantes sur le blog de l' [équipe ADO.net](/archive/blogs/adonet/):  
  
- [Exploration des performances d'ADO.NET Entity Framework – partie 1](/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-1)  
  
- [Exploration des performances d'ADO.NET Entity Framework – partie 2](/archive/blogs/adonet/exploring-the-performance-of-the-ado-net-entity-framework-part-2)  
  
- [Comparaison des performances d'ADO.NET Entity Framework](/archive/blogs/adonet/ado-net-entity-framework-performance-comparison)  
  
## <a name="see-also"></a>Voir aussi

- [Points à prendre en considération pour le développement et le déploiement](development-and-deployment-considerations.md)
