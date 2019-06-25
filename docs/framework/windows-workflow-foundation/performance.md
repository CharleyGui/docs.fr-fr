---
title: Performances de Windows Workflow Foundation 4
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: 51cd5b248789c85ab06073f1bb41a83e5f97c139
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348533"
---
# <a name="windows-workflow-foundation-4-performance"></a>Performances de Windows Workflow Foundation 4

 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] inclut une révision majeure de Windows Workflow Foundation (WF) qui met l’accent dans les performances.  Cette nouvelle révision introduit des modifications de conception importantes par rapport aux versions précédentes de [!INCLUDE[wf1](../../../includes/wf1-md.md)] livrées avec .NET Framework 3.0 et [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Elle a été remodelée à partir du modèle de programmation, du runtime et des outils de base afin d'améliorer considérablement ses performances et sa facilité d'utilisation. Cette rubrique décrit les caractéristiques de performances importantes de ces révisions et les compare avec celles de la version précédente.

 Les performances des composants de workflow individuels ont augmenté considérablement entre WF3 et WF4.  Cela laisse le fossé entre codé manuellement les services Windows Communication Foundation (WCF) et des services de workflow WCF pour être relativement petite.  La latence du workflow a été considérablement réduite dans WF4.  Les performances de la persistance ont augmenté d'un facteur de 2,5 à 3.  Le contrôle d'état au moyen du suivi de workflow nécessite une charge mémoire bien moindre.  Ces raisons incontestables justifient la migration vers WF4 ou son adoption dans vos applications.

## <a name="terminology"></a>Terminologie
 La version de [!INCLUDE[wf1](../../../includes/wf1-md.md)] introduite dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] sera appelée WF4 dans le reste de cette rubrique.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] a été introduit dans .NET 3.0 et avait des révisions mineures via [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] SP1. La version [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] de Workflow Foundation sera appelée WF3 dans le reste de cette rubrique. WF3 est fourni avec [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] côte à côte avec WF4. Pour plus d’informations sur la migration des artefacts WF3 vers WF4, consultez : [Guide de Migration de Windows Workflow Foundation 4](https://go.microsoft.com/fwlink/?LinkID=153313)

 Windows Communication Foundation (WCF) est un modèle de programmation unifié de Microsoft pour la création d’applications orientées service. Il a été introduite dans le cadre de .NET 3.0 avec WF3 et est aujourd'hui un des principaux composants du .NET Framework.

 Windows Server AppFabric est un jeu de technologies intégrées permettant de générer, mettre à l'échelle et gérer facilement des applications Web et composites qui s'exécutent sur les Services Internet (IIS). Il fournit des outils pour déployer, surveiller et gérer les services et les workflows. Pour plus d’informations, consultez [Windows Server AppFabric 1.0](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)).

## <a name="goals"></a>Objectifs
 Cette rubrique a pour objectif d'illustrer les caractéristiques de performances de WF4 à l'aide des données mesurées pour différents scénarios. Elle présente également une comparaison détaillée entre WF4 et WF3, qui permet d'illustrer les grandes améliorations apportées à cette nouvelle révision. Les scénarios et données présentés dans cet article permettent de quantifier le coût sous-jacent de différents aspects de WF4 et WF3. Ces données permettent de comprendre les caractéristiques de performances générales de WF4 et peuvent s'avérer utiles pour planifier les migrations de WF3 vers WF4 ou utiliser WF4 pour le développement d'applications. Toutefois, nous vous recommandons de faire preuve de prudence lorsque vous tirez des conclusions des données présentées dans cet article. Les performances d'une application de workflow composite dépendent beaucoup de la façon dont le workflow est implémenté et de la manière dont les différents composants sont intégrés. Il est nécessaire d'évaluer chaque application afin de déterminer ses caractéristiques de performances.

## <a name="overview-of-wf4-performance-enhancements"></a>Vue d'ensemble des amélioration de performances de WF4
 WF4 a été conçu et implémenté avec soin et ses performances et son évolutivité optimales sont décrites dans les sections suivantes.

### <a name="wf-runtime"></a>Runtime WF
 À la base du runtime [!INCLUDE[wf1](../../../includes/wf1-md.md)] se trouve un planificateur asynchrone qui gère l'exécution des activités dans un workflow. Il fournit un environnement d'exécution performant et prévisible pour les activités. L'environnement dispose d'un contrat bien défini pour l'exécution, la continuation, l'achèvement, l'annulation et les exceptions, ainsi que d'un modèle de thread prévisible.

 Par rapport à WF3, le runtime WF4 est doté d'un planificateur plus efficace. Il s’appuie sur le même pool de threads d’e/s qui est utilisé pour WCF, qui est très efficace pour l’exécution des éléments de travail par lot. La file d’attente interne du planificateur d’éléments de travail est optimisée pour les modèles d’utilisation les plus courants. Le runtime WF4 gère également les États d’exécution d’une manière très léger avec synchronisation minimale et la gestion logique, tandis que WF3 dépend de l’inscription d’événement de lourdes et l’appel à effectuer une synchronisation complexe pour les transitions d’état d’événement.

### <a name="data-storage-and-flow"></a>Stockage et flux de données
 Dans WF3, les données associées à une activité sont modélisées à l'aide des propriétés de dépendance implémentées par le type <xref:System.Windows.DependencyProperty>. Le modèle de propriété de dépendance a été introduit dans Windows Presentation Foundation (WPF). En général, ce modèle est très flexible afin de faciliter la liaison de données et de prendre en charge d’autres fonctionnalités. Toutefois, ce modèle nécessite de définir les propriétés en tant que champs static dans la définition du workflow. Lorsque le runtime [!INCLUDE[wf1](../../../includes/wf1-md.md)] définit ou obtient les valeurs de propriétés, cela implique une logique de recherche lourde.

 WF4 utilise une logique claire de portée des données afin d'améliorer considérablement le traitement des données dans un workflow. Il sépare les données stockées dans une activité de celles transférées hors des limites de l’activité à l’aide de deux concepts différents : variables et arguments. En utilisant un périmètre hiérarchique clair pour les variables et arguments de « Dans/Out/InOut », la complexité de l’utilisation de données pour les activités est considérablement réduite et la durée de vie des données est automatiquement étendue. Les activités ont une signature bien définie décrite par ses arguments. Il vous suffit d'inspecter une activité pour déterminer les données qu'elle s'attend à recevoir et celles qu'elle générera suite à son exécution.

 Dans WF3, les activités étaient initialisées lors de la création d'un workflow. Dans WF 4, les activités sont initialisées seulement lorsque les activités correspondantes sont en cours d'exécution. Cela permet de simplifier le cycle de vie des activités sans effectuer d'opérations d'initialisation/d'annulation de l'initialisation lors de la création d'une nouvelle instance de workflow, et de garantir une meilleure efficacité.

### <a name="control-flow"></a>Flux de contrôle
 Comme dans tout autre langage de programmation, [!INCLUDE[wf1](../../../includes/wf1-md.md)] fournit la prise en charge des flux de contrôle pour les définitions de workflow en introduisant un ensemble d'activités de flux de contrôle pour la mise en séquence, les boucles, les branchements et autres modèles. Dans WF3, lorsque la même activité doit être exécutée à nouveau, un <xref:System.Workflow.ComponentModel.ActivityExecutionContext> est créé et l'activité est clonée à l'aide d'une logique de sérialisation et de désérialisation lourde basée sur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Les performances des flux de contrôle itératif sont généralement bien plus lentes que lors de l'exécution d'une séquence d'activités.

 WF4 traite cela de façon très différente. Il utilise le modèle d'activité pour créer un nouvel objet ActivityInstance qu'il ajoute à la file d'attente du planificateur. Ce processus implique la création d’objet explicite uniquement et est très légère.

### <a name="asynchronous-programming"></a>Programmation asynchrone
 Les performances et l'évolutivité des applications sont généralement meilleures grâce à la programmation asynchrone pour les opérations à durée d'exécution longue et bloquantes telles que les opérations d'E/S ou de traitement distribué. WF4 fournit la prise en charge asynchrone à l'aide des types d'activité de base <xref:System.Activities.AsyncCodeActivity> et <xref:System.Activities.AsyncCodeActivity%601>. Le runtime comprend les activités asynchrones en mode natif et peut donc placer automatiquement l'instance dans une zone sans persistance pendant que le travail asynchrone est en attente. Les activités personnalisées peuvent ainsi dériver de ces types pour effectuer un travail asynchrone sans maintenir le thread du service de planification de workflow. Elles peuvent également bloquer toute activité qui peut s'exécuter en parallèle.

### <a name="messaging"></a>Messagerie
 Initialement, WF3 offrait une prise en charge de la messagerie limitée au moyen d'événements externes ou d'appels de services Web. Dans .NET 3.5, des flux de travail peut être implémenté en tant que clients WCF ou exposées en tant que services WCF via <xref:System.Workflow.Activities.SendActivity> et <xref:System.Workflow.Activities.ReceiveActivity>. Dans WF4, le concept de programmation de messagerie basée sur les flux de travail a été encore renforcé grâce à l’intégration étroite de WCF logique de messagerie dans WF.

 Le pipeline de traitement de messagerie unifiée fourni dans WCF dans .NET 4 permet des services WF4 sont bien meilleures performances et évolutivité que WF3. WF4 fournit également une prise en charge plus riche de la programmation de messagerie qui peut modéliser des modèles d’échange de messages (MEP, message exchange patterns) complexes. Les développeurs peuvent utiliser des contrats de service typés pour faciliter la programmation ou non typés pour améliorer les performances sans coûts de sérialisation. La prise en charge de la mise en cache côté client à l'aide de la classe <xref:System.ServiceModel.Activities.SendMessageChannelCache> dans WF4 permet aux développeurs de créer des applications rapides avec un minimum d'effort. Pour plus d’informations, consultez [changement des niveaux de partage de Cache pour les activités d’envoi](../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Programmation déclarative
 WF4 fournit une structure de programmation déclarative nette et simple permettant de modéliser les processus et services d'entreprise. Le modèle de programmation prend en charge la composition entièrement déclarative des activités, sans code-beside, ce qui simplifie considérablement la création de workflow. Dans [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], la structure de programmation déclarative basée sur XAML a été unifiée dans l'assembly unique System.Xaml.dll afin de prendre en charge WPF et WF.

 Dans WF4, XAML fournit une expérience véritablement déclarative et permet de définir l'intégralité du workflow dans le balisage XML, en référençant les activités et les types créés à l'aide de .NET. Il était difficile de le faire dans WF3 avec le format XOML sans impliquer une logique code-behind personnalisée. La nouvelle pile XAML dans .NET 4 a bien meilleures performances dans les artefacts de flux de travail de sérialisation/désérialisation et rend la programmation déclarative plus intéressante et fiable.

### <a name="workflow-designer"></a>Concepteur de flux de travail
 La prise en charge de la programmation entièrement déclarative pour WF4 impose explicitement des exigences supérieures en matière de performances au moment de la conception pour les grands workflows. L'évolutivité du concepteur de workflow de WF4 pour les grands workflows est bien supérieure à celle du concepteur de WF3. La prise en charge de la virtualisation de l'interface permet au concepteur de charger facilement un grand workflow de 1000 activités en quelques secondes, alors qu'il est presque impossible de charger un workflow de quelques centaines d'activités avec le concepteur de WF3.

## <a name="component-level-performance-comparisons"></a>Comparaisons des performances au niveau des composants
 Cette section contient des données sur des comparaisons directes entre les activités individuelles dans les workflows de WF3 et de WF4.  Des domaines clés tels que la persistance ont un impact plus profond sur les performances que les composants d'activité individuels.  Les améliorations de performances des composants individuels dans WF4 sont toutefois importantes, car les composants sont désormais suffisamment rapides pour pouvoir être comparés avec une logique d'orchestration codée manuellement.  Un exemple de ce qui est couverte dans la section suivante : « Scénario de Composition de Service. »

### <a name="environment-setup"></a>Configuration de l'environnement
 ![Configuration de l’environnement pour la mesure de performances de flux de travail](./media/performance/performance-test-environment.gif)

 La figure ci-dessus illustre la configuration de l'ordinateur utilisée pour la mesure des performances au niveau du composant. Un serveur unique et cinq clients connectés par le biais d'une interface réseau Ethernet de 1 Gbit/s. Pour faciliter les mesures, le serveur est configuré pour utiliser un seul cœur d'un serveur double processeur/quatre cœurs exécutant Windows Server 2008 x86. L'utilisation de l'UC système est maintenue aux alentours de 100 %.

### <a name="test-details"></a>Détails du test
 <xref:System.Workflow.Activities.CodeActivity> de WF3 est sans doute l'activité la plus simple pouvant être utilisée dans un workflow WF3.  Cette activité appelle une méthode du code-behind où le programmeur de workflow peut entrer du code personnalisé.  Dans WF4, il n'existe aucun équivalent direct à <xref:System.Workflow.Activities.CodeActivity> de WF3 qui fournit les mêmes fonctionnalités.  Notez que WF4 contient une classe de base <xref:System.Activities.CodeActivity> qui n'est pas liée à <xref:System.Workflow.Activities.CodeActivity> de WF3.  Les auteurs de workflow sont encouragés à créer des activités personnalisées et à concevoir des workflows en XAML uniquement.  Dans les tests ci-dessous, une activité appelée `Comment` est utilisée à la place d'une <xref:System.Workflow.Activities.CodeActivity> vide dans les workflows WF4.  Le code de l'activité `Comment` est le suivant :

```csharp
[ContentProperty("Body")]
    public sealed class Comment : CodeActivity
    {
        public Comment()
            : base()
        {
        }

        [DefaultValue(null)]
        public Activity Body
        {
            get;
            set;
        }

        protected override void Execute(CodeActivityContext context)
        {
        }
    }
```

### <a name="empty-workflow"></a>Workflow vide
 Ce test utilise un workflow en séquences sans activités enfants.

### <a name="single-activity"></a>Activité unique
 Ce workflow est un workflow en séquences contenant une activité enfant.  L'activité est une <xref:System.Workflow.Activities.CodeActivity> sans code dans le cas de WF3 et une activité `Comment` dans le cas de WF4.

### <a name="while-with-1000-iterations"></a>While avec 1000 itérations
 Le workflow en séquences contient une activité <xref:System.Activities.Statements.While> avec une activité enfant dans la boucle qui n'exécute aucun travail.

### <a name="replicator-compared-to-parallelforeach"></a>Replicator comparé à ParallelForEach
 <xref:System.Workflow.Activities.ReplicatorActivity> de WF3 a des modes d'exécution séquentiels et parallèles.  En mode séquentiel, les performances de l'activité sont similaires à celles de <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> est surtout utile pour l'exécution parallèle.  L'équivalent WF4 de ceci est l'activité <xref:System.Activities.Statements.ParallelForEach%601>.

 Le diagramme suivant montre les workflows utilisés pour ce test. Le workflow WF3 est représenté sur la gauche et le workflow WF4 sur la droite.

 ![ReplicatorActivity WF3 et ParallelForEach WF4](./media/performance/replicator-parallel-wf3-wf4.gif)

### <a name="sequential-workflow-with-five-activities"></a>Workflow séquentiel avec cinq activités.
 Ces tests visent à montrer le résultat de l'exécution de plusieurs activités en séquences.  La séquence inclut cinq activités.

### <a name="transaction-scope"></a>Étendue de transaction
 Le test d’étendue de transaction est légèrement différent des autres tests en ceci qu’une nouvelle instance de workflow n’est pas créée pour chaque itération.  Au lieu de cela, le workflow est structuré avec une boucle while comprenant une activité <xref:System.Activities.Statements.TransactionScope> qui contient une activité unique qui n'effectue aucun travail.  Chaque exécution d'un lot de 50 itérations dans la boucle while est comptée comme une opération unique.

### <a name="compensation"></a>Compensation
 Le workflow WF3 contient une activité compensable unique appelée `WorkScope`.  L'activité implémente simplement l'interface <xref:System.Workflow.ComponentModel.ICompensatableActivity> :

```csharp
class WorkScope :
        CompositeActivity, ICompensatableActivity
    {
        public WorkScope() : base() { }

        public WorkScope(string name)
        {
            this.Name = name;
        }

        public ActivityExecutionStatus Compensate(
            ActivityExecutionContext executionContext)
        {
            return ActivityExecutionStatus.Closed;
        }
    }
```

 Le gestionnaire d'erreur cible l'activité `WorkScope`. Le workflow WF4 est tout aussi simple.  Une <xref:System.Activities.Statements.CompensableActivity> possède un corps et un gestionnaire de compensation.  La séquence suivante contient une compensation explicite.  L'activité de corps et le gestionnaire de compensation sont des implémentations vides :

```
public sealed class CompensableActivityEmptyCompensation : CodeActivity
    {
        public CompensableActivityEmptyCompensation()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
    public sealed class CompensableActivityEmptyBody : CodeActivity
    {
        public CompensableActivityEmptyBody()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
```

Le diagramme suivant illustre le flux de travail de base de compensation. Le workflow WF3 est représenté sur la gauche et le workflow WF4 sur la droite.

![Flux de travail de base de compensation WF3 et WF4](./media/performance/basic-compensation-workflows-wf3-wf4.gif)

### <a name="performance-test-results"></a>Résultats des test de performances

 ![Tableau montrant les données de résultats de test de performances](./media/performance/performance-test-data.gif)

 ![Histogramme de comparaison de données de test de performances WF3 et WF4](./media/performance/performance-test-chart.gif)

 Tous les tests sont mesurés en workflows par seconde à l'exception du test d'étendue de transaction.  Comme vous pouvez le constater ci-dessus, les performances du runtime [!INCLUDE[wf1](../../../includes/wf1-md.md)] se sont améliorées dans le tableau, en particulier dans les domaines qui nécessitent plusieurs exécutions de la même activité comme la boucle while.

## <a name="service-composition-scenario"></a>Scénario de composition de service
 Comme indiqué dans la section précédente, « comparaisons des performances au niveau des composants », une réduction significative de la surcharge entre WF3 et WF4 a eu lieu.  Services de workflow WCF peuvent désormais à égaler quasiment les performances des services WCF codé manuellement tout en conservant tous les avantages de la [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime.  Ce scénario de test compare un service WCF par rapport à un service de workflow WCF dans WF4.

### <a name="online-store-service"></a>Service de magasin en ligne
 Un des atouts de Windows Workflow Foundation est la capacité à composer des processus à l’aide de plusieurs services.  Dans cet exemple, un service de magasin en ligne organise deux appels de service pour passer une commande.  La première étape consiste à valider la commande par le biais d'un service de validation des commandes.  La seconde étape consiste à satisfaire la commande à l'aide d'un service d'entrepôt .

 Les deux services backend, de validation des commandes et d'entrepôt, sont les mêmes pour les deux tests.  La partie qui change est le service de magasin en ligne qui effectue l'orchestration.  Dans le premier cas, le service est codé manuellement comme service WCF.  Pour les autres cas, le service est écrit comme un service de workflow WCF dans WF4. Les fonctionnalités spécifiques à [!INCLUDE[wf1](../../../includes/wf1-md.md)], telles que le suivi et la persistance, sont désactivées pour ce test.

### <a name="environment"></a>Environnement
![Configuration de l’environnement pour les mesures de performances](./media/performance/performance-test-environment.gif)

 Les demandes du client sont transmises au service de magasin en ligne via HTTP à partir de plusieurs ordinateurs.  Un ordinateur unique héberge les trois services.  La couche de transport entre le service de magasin en ligne et les services backend est TCP ou HTTP.  La mesure des opérations/seconde est basée sur le nombre d'appels `PurchaseOrder` passés au service de magasin en ligne.  Le regroupement de canaux est une nouvelle fonctionnalité disponible dans WF4.  Dans WCF partie de ce regroupement de canaux de test n’est pas fourni prêt à l’emploi pour une implémentation codée manuellement d’une technique de regroupement simple a été utilisée dans le Service Store en ligne.

### <a name="performance"></a>Performances
![Histogramme affichant les performances de Service de Store en ligne](./media/performance/online-store-performance-graph.gif)

 En se connectant aux services TCP backend sans regroupement de canaux, le service [!INCLUDE[wf1](../../../includes/wf1-md.md)] a un impact de 17,2 % sur le débit.  Avec le regroupement de canaux, la pénalité est d'environ 23,8 %.  Pour HTTP, l’impact est moindre : 4,3 % sans regroupement et 8,1 % avec le regroupement.  Il est important de noter que le regroupement de canaux présente très peu d'avantages lors de l'utilisation de HTTP.

 Bien qu’une surcharge de l’exécution de WF4 par rapport à un service WCF codé manuellement dans ce test, on peut considérer le pire scénario.  Les deux services backend dans ce test exécutent très peu de travail.  Dans un scénario de bout en bout réel, ces services effectueraient des opérations plus coûteuses telles que des appels de base de données, ce qui réduirait l'impact de la couche de transport sur les performances.  Tout cela ajouté aux avantages des fonctionnalités disponibles dans WF4 fait de Workflow Foundation un choix viable pour la création de services d’orchestration.

## <a name="key-performance-considerations"></a>Considérations sur les performances clés
 Les fonctionnalités abordées dans cette section, à l’exception de l’interopérabilité, ont radicalement changé entre WF3 et WF4.  Cela affecte la conception des applications de workflow ainsi que les performances.

#### <a name="workflow-activation-latency"></a>Latence de l'activation de workflow
 Dans une application de service de workflow WCF, la latence pour démarrer un nouveau workflow ou le chargement d’un workflow existant est importante car elle peut provoquer des blocages.  Ce cas de test compare un hôte XOML WF3 à un hôte XAMLX WF4 dans un scénario classique.

##### <a name="environment-setup"></a>Configuration de l'environnement
 ![Configuration de l'environnement pour les tests de latence et de débit](./media/performance/latency-throughput-environment-setup.gif)

##### <a name="test-setup"></a>Configuration du test
 Dans le scénario, un ordinateur client contacte un service de workflow WCF à l’aide de la corrélation basée sur le contexte.  La corrélation de contexte nécessite une liaison de contexte spéciale et utilise un en-tête ou un cookie de contexte pour lier les messages à l’instance de workflow correcte.  Elle offre un avantage en termes de performances, car dans la mesure où l'ID de corrélation se trouve dans l'en-tête du message, il n'est pas nécessaire d'analyser le corps du message.

 Le service crée un nouveau workflow avec la demande et envoie une réponse immédiate de sorte que la mesure de la latence n'inclut pas le temps d'exécution du workflow.  Le workflow WF3 est au format XOML avec un code-behind et le workflow WF4 est entièrement au format XAML.  Voici un exemple de workflow WF4 :

 ![Workflow de la portée de corrélation de WF4](./media/performance/wf4-correlationscope-workflow.gif)

 L'activité <xref:System.ServiceModel.Activities.Receive> crée l'instance de workflow.  Une valeur passée dans le message reçu est répercutée dans le message de réponse.  Une séquence qui suit la réponse contient le reste du workflow.  Dans le cas ci-dessus, un seule activité de commentaire est représentée.  Le nombre d'activités de commentaire est modifié pour simuler la complexité de workflow.  Une activité de commentaire est équivalente à un <xref:System.Workflow.Activities.CodeActivity> WF3 qui n'effectue aucune tâche. Pour plus d’informations sur l’activité de commentaire, consultez la section « comparaisons des performances au niveau des composants » plus haut dans cet article.

##### <a name="test-results"></a>Résultats des tests

 Latence à froid et à chaude pour les services de workflow WCF :

 ![Histogramme affichant la latence à froid et à chaude pour les services WCF à l’aide de WF3 et WF4](./media/performance/latency-results-graph.gif)

 Dans le graphique précédent, « froid » correspond au cas où il n’existe aucun <xref:System.ServiceModel.WorkflowServiceHost> pour le flux de travail donné.  En d'autres termes, la latence à froid correspond au cas dans lequel le workflow est utilisé pour la première fois et le XOML ou le XAML doit être compilé.  La latence à chaud correspond à la création d'une nouvelle instance de workflow lorsque le type de workflow a déjà été compilé.  La complexité du workflow a très peu d'impact dans le cas de WF4, mais a une progression linéaire dans le cas de WF3.

#### <a name="correlation-throughput"></a>Débit de corrélation
 WF4 introduit une nouvelle fonctionnalité de corrélation basée sur le contenu.  WF3 offrait seulement la corrélation basée sur le contexte.  Corrélation basée sur le contexte peut être effectuée uniquement sur les liaisons de canal WCF spécifiques.  L’ID de workflow est inséré dans l’en-tête de message lors de l’utilisation de ces liaisons.  Le runtime WF3 pouvait seulement identifier un workflow par son ID.  Avec la corrélation basée sur le contenu, l'auteur de workflow peut créer une clé de corrélation à partir de données pertinentes telles qu'un numéro de compte ou un ID client.

 La corrélation basée sur le contexte offre un avantage en matière de performances en ceci que la clé de corrélation se trouve dans l'en-tête du message.  La clé peut être lue à partir du message sans désérialisation/copie du message.  Avec la corrélation basée sur le contenu, la clé de corrélation est stockée dans le corps du message.  Une expression XPath est utilisée pour rechercher la clé.  Le coût de ce traitement supplémentaire dépend de la taille du message, de la profondeur de la clé dans le corps et du nombre de clés.  Ce test compare la corrélation basée sur le contexte à celle basée sur le contenu et montre également la détérioration des performances lors de l'utilisation de plusieurs clés.

#### <a name="environment-setup"></a>Configuration de l'environnement
![Configuration de l’environnement de test de performances de flux de travail](./media/performance/performance-test-environment.gif)

#### <a name="test-setup"></a>Configuration du test
![Flux de travail de Test de débit corrélation](./media/performance/correlation-throughput-workflow.gif "le programme d’installation de corrélation débit workflow test")

 Le workflow précédent est identique à celle utilisée dans le [persistance](#persistence) section. Pour les tests de corrélation sans persistance, il n’existe aucun fournisseur de persistance installé dans le runtime. Corrélation se produit dans deux emplacements : CreateOrder et CompleteOrder.

#### <a name="test-results"></a>Résultats des tests
![Débit de corrélation](./media/performance/correlation-throughput-graph.gif "graphique de débit de corrélation")

 Ce graphique illustre une baisse des performances au fur et à mesure que le nombre de clés utilisées dans la corrélation basée sur le contenu augmente.  La similarité entre les courbes de TCP et HTTP indique la charge mémoire associée à ces protocoles.

#### <a name="correlation-with-persistence"></a>Corrélation et persistance.
 Avec un workflow rendu persistant, la pression sur l'UC de la corrélation basée sur le contenu passe du runtine de workflow à la base de données SQL.  Les procédures stockées dans le fournisseur de persistance SQL font correspondre les clés pour rechercher le workflow approprié.

 ![Graphique en courbes affichant les résultats de corrélation et persistance](./media/performance/correlation-persistence-graph.gif)

 La corrélation basée sur le contexte est toujours plus rapide que la corrélation basée sur le contenu.  Toutefois, la différence est moins prononcée, car la persistance a plus d'impact sur les performances que la corrélation.

### <a name="complex-workflow-throughput"></a>Débit de workflow complexe
 La complexité d'un workflow ne se mesure pas uniquement au nombre d'activités.  Les activités composites peuvent contenir de nombreux enfants, qui peuvent aussi être des activités composites.  Au fur et à mesure que le nombre de niveaux d'imbrication augmente, il en va de même pour le nombre d'activités pouvant avoir l'état Exécution et le nombre de variables pouvant avoir cet état.  Ce test compare les débits de WF3 et de WF4 lors de l'exécution de workflows complexes.

### <a name="test-setup"></a>Configuration du test
 Ces tests ont été exécutés sur un ordinateur Intel Xeon X5355 2,66 GHz quatre cœurs avec 4 Go de RAM exécutant Windows Server 2008 x64.  Le code de test exécute un processus unique avec un thread par cœur pour atteindre une utilisation de l'UC de 100 %.

 Les workflows générés pour ce test contiennent deux variables principales : profondeur et nombre d'activités dans chaque séquence.  Chaque niveau de profondeur inclut une activité parallèle, pendant la boucle, les décisions, les affectations et les séquences.  Dans le concepteur WF4 illustré ci-dessous, l'organigramme de niveau supérieur est représenté.  Chaque activité d'organigramme ressemble au diagramme principal.  Il peut s'avérer utile de considérer une fractale pour illustrer ce workflow, dans lequel la profondeur est limitée aux paramètres du test.

 Le nombre d'activités dans un test donné est déterminé par la profondeur et nombre d'activités par séquence.  L'équation suivante calcule le nombre d'activités dans le test de WF4 :

 ![Équation pour calculer le nombre d'activités](./media/performance/number-activities-equation.gif)

 Le nombre d'activités du test de WF3 peut être calculé à l'aide d'une équation un peu différente à cause d'une séquence supplémentaire :

 ![Équation de calcul du nombre d’activités de WF3](./media/performance/wf3-number-activities-equation.gif)

 Où d correspond à la profondeur et a au nombre d'activités par séquence.  La logique qui sous-tend ces équations est que la première constante, multipliée par a, correspond au nombre de séquences et la seconde constante correspond au nombre statique d'activités dans le niveau actuel.  Chaque organigramme inclut trois activités enfant.  Au niveau de profondeur inférieur, ces organigrammes sont vides, mais les autres niveaux contiennent des copies de l'organigramme principal.  Le nombre d'activités dans la définition de workflow de chaque variation de test est indiqué dans le tableau suivant :

 ![Une table qui affiche le nombre d’activités utilisées dans chaque test](./media/performance/workflow-variation-compare-table.gif)

 Le nombre d'activités dans la définition de workflow augmente nettement avec chaque niveau de profondeur.  Toutefois, un seul chemin par point de décision est exécuté dans une instance de workflow donnée. Par conséquent, seul un petit sous-ensemble des activités réelles est exécuté.

 ![Organigramme du flux de travail complexes de débit](./media/performance/complex-workflow-throughput-workflow.gif)

 Un workflow équivalent a été créé pour WF3. Le concepteur de WF3 montre l'intégralité du workflow dans la zone de conception au lieu de l'imbriquer, et il est donc trop volumineux pour s'afficher dans cette rubrique. Un extrait du workflow est présenté ci-dessous.

 ![Extrait de l’organigramme du flux de travail WF3](./media/performance/wf3-workflow-snippet.gif)

 Pour effectuer l'imbrication dans un cas extrême, un autre workflow inclus dans ce test utilise 100 séquences imbriquées.  La séquence la plus profonde contient une activité `Comment` ou <xref:System.Workflow.Activities.CodeActivity> unique.

 ![Organigramme d’une séquence imbriquée](./media/performance/nested-sequence-workflow.gif)

 Le suivi et la persistance ne sont pas utilisés dans ce test.

### <a name="test-results"></a>Résultats des tests
 ![Histogramme affichant les résultats des performances de débit](./media/performance/throughput-performance-results.gif)

 Même dans le cas de workflows complexes avec de nombreux niveaux de profondeur et un grand nombre d'activités, les résultats des performances sont cohérents avec d'autres nombres de débit indiqués plus haut dans cet article.  Le débit de WF4 est beaucoup plus rapide et doit être comparé sur une échelle logarithmique.

### <a name="memory"></a>Mémoire
 La charge mémoire de Windows Workflow Foundation est mesurée dans deux domaines clés : complexité de workflow et nombre de définitions de workflow.  Les mesures de mémoire proviennent d'une station de travail Windows 7 64 bits.  Il existe de nombreuses façons d’obtenir la mesure de l’utilisation de taille de jeu telles que la surveillance des compteurs de performances, interrogation d’Environment.WorkingSet ou à l’aide d’un outil comme VMMap disponible sur [VMMap](/sysinternals/downloads/vmmap). Une combinaison de méthodes a été utilisée pour obtenir et vérifier les résultats de chaque test.

### <a name="workflow-complexity-test"></a>Test de complexité de workflow
 Les test de complexité de workflow mesure la différence du jeu de travail en fonction de la complexité du workflow.  Outre les workflows complexes utilisés dans la section précédente, de nouvelles variations sont ajoutées pour couvrir deux cas de base : un workflow à activité unique et une séquence avec 1 000 activités.  Pour ces tests, les workflows sont initialisés et exécutés jusqu'à la fin dans une boucle sérielle unique pour une période d'une minute.  Chaque variation de test est exécutée trois fois et les données enregistrées correspondent à la moyenne de ces trois exécutions.

 Les workflows des deux nouveaux tests de base ressemblent à ceux-ci :

 ![Flux de travail complexe pour WF3 et WF4](./media/performance/complex-workflow-wf3-wf4.gif)

 Dans le workflow WF3 représenté ci-dessus, des activités <xref:System.Workflow.Activities.CodeActivity> vides sont utilisées.  Le workflow WF4 ci-dessus utilise des activités `Comment`.  L'activité `Comment` a été décrite dans la section « Comparaisons des performances au niveau des composants » plus haut dans cet article.

 ![Graphique à colonnes indiquant l’utilisation de la mémoire des flux de travail complexes pour les workflows WF3 et WF4](./media/performance/complex-memory-usage-wf3-wf4.gif)

 Une des tendances nettes à noter dans ce graphique est que l'imbrication a un impact relativement minime sur l'utilisation de la mémoire dans WF3 et WF4.  L'impact le plus important sur la mémoire vient du nombre d'activités dans un workflow donné.  Compte tenu des données de la séquence 1000, les variations de la séquence 5 de profondeur 5 complexe et de la séquence 1 de profondeur 7 complexe, il est clair que lorsque le nombre d'activités se compte en milliers, l'augmentation de l'utilisation de la mémoire devient plus notable.  Dans le cas extrême (séquence 1 de profondeur 7) qui contient environ 29 000 activités, WF4 utilise presque 79 % moins de mémoire que WF3.

### <a name="multiple-workflow-definitions-test"></a>Test de plusieurs définitions de workflow
 La mesure de la mémoire par définition de workflow fait l'objet de deux tests différents à cause des options disponibles pour l'hébergement de workflows dans WF3 et WF4.  Les tests sont exécutés de manière différente du test de complexité de workflow en ceci qu'un workflow donné est instancié et exécuté seulement une fois par définition.  Ceci est dû au fait que la définition de workflow et son hôte restent en mémoire pour la durée de vie de l'AppDomain.  La mémoire utilisée pour l'exécution d'une instance de workflow donnée doit être nettoyée lors de l'opération garbage collection.  Les conseils de migration pour WF4 contiennent des informations plus détaillées sur les options d'hébergement. Pour plus d’informations, consultez [Guide de Migration WF : Hébergement de flux de travail](https://go.microsoft.com/fwlink/?LinkID=153313).

 Plusieurs méthodes permettent de créer de nombreuses définitions de workflow pour un test de définition de workflow.  Par exemple, la génération de code permet de créer 1000 workflows identiques, sauf en ce qui concerne leurs noms et d'enregistrer chaque workflow dans un fichier distinct.  Cette approche a été choisie pour le test hébergé sur console.  Dans WF3, la classe <xref:System.Workflow.Runtime.WorkflowRuntime> a été utilisée pour exécuter les définitions de workflow.  WF4 peut utiliser <xref:System.Activities.WorkflowApplication> pour créer une instance unique de workflow ou pour utiliser directement <xref:System.Activities.WorkflowInvoker> pour exécuter l'activité comme s'il s'agissait d'un appel de méthode.  <xref:System.Activities.WorkflowApplication> est l'hôte d'une instance de workflow unique et a une parité de fonctions plus proche de <xref:System.Workflow.Runtime.WorkflowRuntime> et a donc été utilisé dans ce test.

 En cas d'hébergement de workflows dans IIS, il est possible d'utiliser un <xref:System.Web.Hosting.VirtualPathProvider> pour créer un nouveau <xref:System.ServiceModel.WorkflowServiceHost> au lieu de générer tous les fichiers XAMLX ou XOML.  Le <xref:System.Web.Hosting.VirtualPathProvider> traite la demande entrante et répond avec un « fichier virtuel » qui peut être chargé à partir d’une base de données ou, dans ce cas, généré à la volée.  Il n'est donc pas nécessaire de créer 1000 fichiers physiques.

 Les définitions de workflow utilisées dans ce test de console étaient des workflows séquentiels simples à activité unique.  L'activité unique était une <xref:System.Workflow.Activities.CodeActivity> vide pour le cas WF3 et une activité `Comment` pour le cas WF4.  Le cas hébergé dans IIS utilisait des workflows qui commençaient lors de la réception d'un message et s'achevaient lors de l'envoi d'une réponse :

L’illustration suivante montre un workflow WF3 avec ReceiveActivity et un workflow WF4 avec modèle demande/réponse :

 ![Services de flux de travail dans WF3 et WF4](./media/performance/workflow-receive-activity.gif)

 Le tableau suivant montre le delta dans le jeu de travail entre une définition de workflow unique et 1001 définitions :

|Options d'hébergement|Delta de jeu de travail WF3|Delta de jeu de travail WF4|
|---------------------|---------------------------|---------------------------|
|Workflows hébergés d'application console|18 MB|9 Mo|
|Services de workflow hébergés par IIS|446 Mo|364 MB|

 Hébergement des définitions de workflow dans IIS consomme beaucoup plus de mémoire en raison du <xref:System.ServiceModel.WorkflowServiceHost>, détaillées artefacts de service WCF et la logique associée à l’hôte de traitement des messages.

 Pour l'hébergement sur console dans WF3 les workflows étaient implémentés dans le code plutôt que dans le format XOML.  Dans WF4, XAML est utilisé par défaut.  Le XAML est stocké en tant que ressource incorporée dans l'assembly et compilé pendant l'exécution afin de fournir l'implémentation du workflow.  Une charge mémoire est associée à ce processus.  Pour une comparaison équitable entre WF3 et WF4, des workflows codés ont été utilisés au lieu de worflows XAML.  Un exemple d'un des workflows WF4 vous est proposé ci-après.

```csharp
public class Workflow1 : Activity
{
    protected override Func<Activity> Implementation
    {
        get
        {
            return new Func<Activity>(() =>
            {
                return new Sequence
                {
                    Activities = {
                        new Comment()
                    }
                };
            });
        }
        set
        {
            base.Implementation = value;
        }
    }
}
```

 Beaucoup d'autres facteurs peuvent affecter la consommation de mémoire. Le même conseil pour tous les programmes gérés est toujours applicable.  Dans les environnements hébergés par IIS, l'objet <xref:System.ServiceModel.WorkflowServiceHost> créé pour une définition de workflow reste en mémoire jusqu'à ce que le pool d'application soit recyclé.  Il ne faut pas l'oublier lors de l'écriture d'extensions.  En outre, il est préférable d’éviter des variables « globales » (variables étendues au flux de travail entière) et de limiter la portée des variables dans la mesure du possible.

## <a name="workflow-runtime-services"></a>Services d'exécution de workflow

### <a name="persistence"></a>Persistance
 WF3 et WF4 sont fournis avec un fournisseur de persistance SQL.  Le fournisseur de persistance SQL de WF3 est une implémentation simple qui sérialise l'instance de workflow et la stocke dans un blob.  Pour cette raison, les performances de ce fournisseur dépendent fortement de la taille de l'instance de workflow.  Dans WF3, la taille de l'instance pouvait augmenter pour de nombreuses raisons, comme indiqué précédemment dans cet article.  De nombreux clients choisissent de ne pas utiliser le fournisseur de persistance SQL par défaut, car le stockage d'une instance sérialisée dans une base de données ne donne aucune visibilité sur l'état du workflow.  Pour trouver un workflow particulier sans connaître son ID, il faudrait désérialiser chaque instance persistante et examiner son contenu.  Beaucoup de développeurs préfèrent écrire leurs propres fournisseurs de persistance afin de surmonter cet obstacle.

 Le fournisseur de persistance SQL de WF4 SQL a tenté de régler ces problèmes.  Les tables de persistance exposent des informations telles que les signets actifs et les propriétés pouvant être promues.  La nouvelle fonctionnalité de corrélation basée sur le contenu de WF4 ne fonctionnerait pas correctement avec l’approche de persistance SQL de WF3, qui a entraîné des modifications dans l’organisation de l’instance de workflow persistante.  Cela rend le travail du fournisseur de persistance plus complexe et augmente le stress sur la base de données.

### <a name="environment-setup"></a>Configuration de l'environnement
![Configuration de l’environnement de test de performances de flux de travail](./media/performance/performance-test-environment.gif)

### <a name="test-setup"></a>Configuration du test
 Même avec un jeu de fonctionnalités amélioré et une meilleure gestion d’accès concurrentiel, le fournisseur de persistance SQL de WF4 est plus rapide que celui de WF3.  Pour illustrer cela, deux workflows qui exécutent des opérations identiques pour l'essentiel dans WF3 et WF4 sont comparés ci-dessous.

 ![Workflow de persistance de WF3 à gauche et de WF4 à droite](./media/performance/persist-workflow-wf3-wf4.gif)

 Les deux workflows sont créés par un message reçu.  Une fois la réponse initiale envoyée, le workflow est persistant.  Dans le cas de WF3, une <xref:System.Workflow.ComponentModel.TransactionScopeActivity> vide est utilisée pour initier la persistance.  La même opération peut être effectuée dans WF3 en marquant une activité avec « persister lors de la fermeture ».  Un second message corrélé termine le workflow.  Les workflows sont persistants mais pas déchargés.

### <a name="test-results"></a>Résultats des tests
 ![Persistance de débit de colonne graphique montrant](./media/performance/throughput-persistence-graph.gif)

 Lorsque le transport entre le client et le niveau intermédiaire est HTTP, la persistance dans WF4 présente une amélioration de 2,6 fois.  Avec le transport TCP, ce facteur est de 3 fois.  Dans tous le cas, l'utilisation de l'UC sur le niveau intermédiaire est de 98 % ou supérieure.  Le débit est plus élevé dans WF4 à cause du runtime de workflow plus rapide.  La taille de l'instance sérialisée est petite dans les deux cas et n'est pas un élément contributif majeur dans cette situation.

 Les workflows WF3 et WF4 de ce test utilisent une activité pour indiquer explicitement quand la persistance doit avoir lieu.  Cela a pour avantage de faire persister le workflow sans le décharger.  Dans WF3, il est également possible de le faire persister à l'aide de la fonctionnalité <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>, mais cela décharge l'instance de workflow de la mémoire.  Si un développeur utilisant WF3 veut s'assurer qu'un workflow persiste à certains points, il doit modifier la définition du workflow ou payer le coût du déchargement et du rechargement de l'instance de workflow.  Une nouvelle fonctionnalité de WF4 permet la persistance sans déchargement : <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Cette fonctionnalité permet de faire persister l’instance de workflow en cas de période d’inactivité, mais de la conserver dans la mémoire jusqu’à ce que le seuil de <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> soit atteint ou que l’exécution reprenne.

 Notez que le fournisseur de persistance SQL de WF4 effectue davantage de travail dans la couche de base de données.  La base de données SQL peut se transformer en goulot d'étranglement, il est donc important de surveiller l'utilisation du processeur et du disque à cet endroit.  Assurez-vous d’inclure les compteurs de performance suivants de la base de données SQL lors d’un test de performance des applications de workflow :

- Disque physique\\temps de lecture du disque

- Disque physique\\% temps du disque

- Disque physique\\temps d’écriture sur disque de %

- Disque physique\\% moy. Longueur de file d'attente disque

- PhysicalDisk\Long. moy. de file d'attente lecture disque

- PhysicalDisk\Long. moy. de file d'attente écriture disque

- PhysicalDisk\Longueur actuelle de la file d'attente du disque

- Informations sur le processeur\\% temps processeur

- SQLServer : Verrous internes\Durée d'attente moyenne d'un verrou interne (ms)

- SQLServer : Verrous internes\Attentes de verrous NP internes/s

### <a name="tracking"></a>Suivi
 Le suivi de workflow permet de suivre la progression d'un workflow.  Les informations incluses dans les événements de suivi sont déterminées par un modèle de suivi.  Plus le modèle de suivi est complexe, plus cette opération est coûteuse.

 WF3 était fourni avec un service de suivi SQL.  Ce service fonctionnait en mode batch et non-batch.  En mode non-batch, les événements de suivi sont écrits directement dans la base de données.  En mode batch, les événements de suivi sont regroupés dans le même lot que l'état de l'instance de workflow.  Le mode batch offre les meilleures performances pour l'éventail de conceptions de workflow le plus large.  Toutefois, le traitement par lots peut avoir un impact négatif sur les performances si le workflow exécute de nombreuses activités sans persistance et que ces activités sont suivies.  Cela se produit généralement dans les boucles et la meilleure façon d'éviter ce scénario consiste à concevoir de grandes boucles pour contenir un point de persistance.  L'introduction d'un point de persistance dans une boucle peut également avoir un impact négatif sur les performances. Il est donc important de mesurer les coûts de chaque élément et d'atteindre un équilibre.

 WF4 n'est pas fourni avec un service de suivi SQL.  Enregistrement des informations de suivi dans une base de données SQL peuvent être plus facile à gérer à partir d’un serveur d’applications plutôt qu’intégrés dans le .NET Framework. Par conséquent, le suivi SQL est désormais géré par AppFabric.  Le fournisseur de suivi prédéfini de WF4 est basé sur ETW (suivi d'événements Windows).

 ETW est un système d'événement de niveau noyau à faible latence intégré à Windows.  Il utilise un modèle fournisseur/consommateur qui permet d'encourir la pénalité liée au suivi d'événements seulement lorsqu'il y a réellement un consommateur.  Outre les événements de noyau tels que l'utilisation du processeur, du disque, de la mémoire et du réseau, de nombreuses applications tirent également parti d'ETW.  Les événements ETW sont plus puissants que les compteurs de performance en ceci que les événements peuvent être personnalisés pour l'application.  Un événement peut contenir du texte tel qu'un ID de workflow ou un message d'information.  En outre, les événements sont classés à l'aide de masque de bits, de sorte que l'utilisation d'un sous-ensemble d'événements donné aura moins d'impact sur les performances que la capture de tous les événements.

 Les avantages de l'utilisation d'ETW pour le suivi au lieu de SQL sont les suivants :

- La collection d’événements de suivi peut être séparée dans un processus distinct.  Cela augmente la flexibilité de l'enregistrement des événements.

- Événements de suivi ETW sont combinés facilement avec les événements ETW de WCF ou d’autres fournisseurs ETW tel qu’un fournisseur de noyau ou de SQL Server.

- Les auteurs de workflow n'ont pas besoin de modifier un workflow pour qu'il fonctionne mieux avec une implémentation de suivi particulière, telle que le mode batch du service de suivi SQL de WF3.

- Un administrateur peut activer ou désactiver le suivi sans recycler le processus hôte.

 Les avantages en matière de performances pour le suivi ETW s'accompagnent d'un inconvénient.  Les événements ETW peuvent être perdus si le système subit une pression intense sur les ressources.  Le traitement des événements n'est pas destiné à bloquer l'exécution normale du programme et il n'est donc pas garanti que tous les événements ETW seront diffusés à leurs abonnés.  Le suivi ETW est donc idéal pour le contrôle d'état, mais il n'est pas approprié pour l'audit.

 Contrairement à WF4, AppFabric est doté d'un fournisseur de suivi SQL.  L'approche de suivi d'AppFabric consiste à s'abonner aux événements ETW à l'aide d'un service Windows qui traite les événements par lots et les écrit dans une table SQL conçue pour des insertions rapides.  Un travail séparé extrait les données de cette table et les restitue dans des tables de rapports pouvant être affichées sur le tableau de bord AppFabric.  Cela signifie qu'un lot d'événements de suivi est traité indépendamment du workflow dont il provient et qu'il ne doit pas attendre un point de persistance pour être enregistré.

 Les événements ETW peuvent être enregistrés à l’aide d’outils tels que logman ou xperf.  Le fichier ETL compact peut être affiché avec un outil tel que xperfview ou converti dans un format plus lisible, tel que XML, à l’aide de tracerpt.  Dans WF3, la seule option permettant d'obtenir des événements de suivi sans base de données SQL consiste à créer un service de suivi personnalisé. Pour plus d’informations sur ETW, consultez [Services WCF et le suivi d’événements pour Windows](../wcf/samples/wcf-services-and-event-tracing-for-windows.md) et [suivi d’événements - les applications Windows](/windows/desktop/etw/event-tracing-portal).

 L'activation du suivi de workflow affecte les performances à des degrés divers.  Le test d'évaluation ci-dessous emploie l'outil logman pour consommer les événements de suivi ETW et les enregistrer dans un fichier ETL.  Le coût du suivi SQL dans AppFabric n'est pas couvert dans cet article.  Le modèle de suivi de base, également utilisé dans AppFabric, est décrit dans ce test d'évaluation.  Ce test inclut également le coût du suivi des événements de contrôle d'état uniquement.  Ces événements sont utiles pour résoudre les problèmes et déterminer le débit moyen du système.

### <a name="environment-setup"></a>Configuration de l'environnement
 ![Configuration de l’environnement de test de performances de flux de travail](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Résultats des tests

 ![Histogramme affichant les flux de travail suivre les coûts](./media/performance/workflow-tracking-costs.gif)

 Le contrôle d'état a un impact d'environ 3 % sur le débit.  Le coût du modèle de base est d'environ 8 %.

## <a name="interop"></a>Interop
 WF4 a été presque entièrement réécrit à partir de [!INCLUDE[wf1](../../../includes/wf1-md.md)], c'est pourquoi les workflows et les activités de WF3 ne sont pas directement compatibles avec WF4.  De nombreux clients qui ont adopté très tôt de Windows Workflow Foundation aura les définitions de workflow en interne ou par des tiers et des activités personnalisées pour WF3.  Une façon de faciliter la transition vers WF4 consiste à utiliser l'activité Interop, qui peut exécuter des activités WF3 à partir d'un workflow WF4.  Il est recommandé d'utiliser l'activité <xref:System.Activities.Statements.Interop> seulement si nécessaire. Pour plus d’informations sur la migration vers WF4 extraire le [conseils de migration vers WF4](https://go.microsoft.com/fwlink/?LinkID=153313).

### <a name="environment-setup"></a>Configuration de l'environnement
 ![Configuration de l’environnement de test de performances de flux de travail](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Résultats des tests
 
Le tableau suivant montre les résultats de l’exécution d’un workflow contenant cinq activités d’une séquence dans différentes configurations.

|Tester|Débit (workflows/s)|
|----------|-----------------------------------|
|Séquence WF3 dans le runtime WF3|1,576|
|Séquence WF3 dans le runtime WF4 utilisant Interop|2,745|
|Séquence WF4|153,582|

 On constate une amélioration notable lors de l'utilisation d'Interop par rapport à WF3 simple.  Toutefois, par rapport aux activités WF4, l'augmentation est négligeable.

## <a name="summary"></a>Récapitulatif
 Les lourds efforts consacrés aux performances pour WF4 ont payé dans de nombreux domaines cruciaux.  Dans certains cas, les performances des composants de workflow individuels sont des centaines de fois plus rapides dans WF4 que dans WF3 grâce à un runtime [!INCLUDE[wf1](../../../includes/wf1-md.md)] plus léger.  Les chiffres de latence sont également considérablement meilleurs.  Cela signifie que la baisse des performances pour l’utilisation de [!INCLUDE[wf1](../../../includes/wf1-md.md)] par opposition à codage manuel d’orchestration de WCF services est très faible, envisagez les avantages supplémentaires liés à l’aide de [!INCLUDE[wf1](../../../includes/wf1-md.md)].  Les performances de la persistance ont augmenté d'un facteur de 2,5 à 3.  Le contrôle d'état au moyen du suivi de workflow nécessite désormais très peu de charge mémoire.  Un ensemble complet de guides de migration est disponible pour les utilisateurs qui envisagent de passer de WF3 à WF4.  Pour toutes ces raisons, WF4 constitue une option avantageuse pour l'écriture d'applications complexes.
