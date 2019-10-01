---
title: Modèles d’observation
description: Modèles d’observation pour les applications Cloud natives
ms.date: 09/23/2019
ms.openlocfilehash: 23320144c03278d631b8a1fcc1d1c0954e907296
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184875"
---
# <a name="observability-patterns"></a><span data-ttu-id="1ef1c-103">Modèles d’observation</span><span class="sxs-lookup"><span data-stu-id="1ef1c-103">Observability patterns</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1ef1c-104">Tout comme les modèles ont été développés pour faciliter la mise en page du code dans les applications, il existe des modèles pour les applications de fonctionnement de manière fiable.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-104">Just as patterns have been developed to aid in the layout of code in applications, there are patterns for operating applications in a reliable way.</span></span> <span data-ttu-id="1ef1c-105">Trois modèles utiles dans la gestion des applications sont apparu : journalisation, surveillance et alertes.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-105">Three useful patterns in maintaining applications have emerged: logging, monitoring, and alerts.</span></span>

## <a name="when-to-use-logging"></a><span data-ttu-id="1ef1c-106">Quand utiliser la journalisation</span><span class="sxs-lookup"><span data-stu-id="1ef1c-106">When to use logging</span></span>

<span data-ttu-id="1ef1c-107">Quelle que soit la prudence, les applications se comportent presque toujours de manière inattendue en production.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-107">No matter how careful we are, applications almost always behave in unexpected ways in production.</span></span> <span data-ttu-id="1ef1c-108">Quand les utilisateurs signalent des problèmes avec une application, il est très utile de pouvoir voir ce qui se passe avec l’application lorsque le problème s’est produit.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-108">When users report problems with an application, it's extremely useful to be able to see what was going on with the app when the problem occurred.</span></span> <span data-ttu-id="1ef1c-109">L’une des méthodes les plus éprouvées et les plus vraies pour capturer des informations sur ce que fait une application en cours d’exécution est de faire en sorte que l’application consigne ce qu’elle fait.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-109">One of the most tried and true ways of capturing information about what an application is doing while it's running is to have the application write down what it's doing.</span></span> <span data-ttu-id="1ef1c-110">Ce processus porte le nom de journalisation.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-110">This process is known as logging.</span></span> <span data-ttu-id="1ef1c-111">À chaque fois que des échecs ou des problèmes surviennent en production, l’objectif doit être de reproduire les conditions dans lesquelles les défaillances se sont produites, dans un environnement hors production.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-111">Anytime failures or problems occur in production, the goal should be to reproduce the conditions under which the failures occurred, in a non-production environment.</span></span> <span data-ttu-id="1ef1c-112">Le fait de disposer d’une bonne connexion permet aux développeurs de suivre le programme afin de dupliquer les problèmes dans un environnement qui peut être testé et expérimenté.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-112">Having good logging in place provides a roadmap for developers to follow in order to duplicate problems in an environment that can be tested and experimented with.</span></span>

### <a name="logging-in-cloud-native-applications"></a><span data-ttu-id="1ef1c-113">Journalisation dans les applications natives du Cloud</span><span class="sxs-lookup"><span data-stu-id="1ef1c-113">Logging in cloud-native applications</span></span>

<span data-ttu-id="1ef1c-114">Chaque langage de programmation dispose d’outils qui autorisent l’écriture de journaux, et la surcharge d’écriture de ces journaux est généralement faible.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-114">Every programming language has tooling that permits writing logs, and typically the overhead for writing these logs is low.</span></span> <span data-ttu-id="1ef1c-115">La plupart des bibliothèques de journalisation permettent de consigner différents types de critiques, qui peuvent être réglés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-115">Many of the logging libraries provide logging different kinds of criticalities, which can be tuned at run time.</span></span> <span data-ttu-id="1ef1c-116">Par exemple, la bibliothèque Serilog est une bibliothèque de journalisation structurée populaire pour .NET qui fournit les niveaux de journalisation suivants</span><span class="sxs-lookup"><span data-stu-id="1ef1c-116">For instance, the Serilog library is a popular structured logging library for .NET that provides the following logging levels</span></span>

* <span data-ttu-id="1ef1c-117">Verbose</span><span class="sxs-lookup"><span data-stu-id="1ef1c-117">Verbose</span></span>
* <span data-ttu-id="1ef1c-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="1ef1c-118">Debug</span></span>
* <span data-ttu-id="1ef1c-119">Information</span><span class="sxs-lookup"><span data-stu-id="1ef1c-119">Information</span></span>
* <span data-ttu-id="1ef1c-120">Warning</span><span class="sxs-lookup"><span data-stu-id="1ef1c-120">Warning</span></span>
* <span data-ttu-id="1ef1c-121">Error</span><span class="sxs-lookup"><span data-stu-id="1ef1c-121">Error</span></span>
* <span data-ttu-id="1ef1c-122">Fatal</span><span class="sxs-lookup"><span data-stu-id="1ef1c-122">Fatal</span></span>

<span data-ttu-id="1ef1c-123">Ces différents niveaux de journalisation fournissent la granularité de la journalisation.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-123">These different log levels provide granularity in logging.</span></span> <span data-ttu-id="1ef1c-124">Lorsque l’application fonctionne correctement en production, elle peut être configurée pour enregistrer uniquement les messages importants.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-124">When the application is functioning properly in production, it may be configured to only log important messages.</span></span> <span data-ttu-id="1ef1c-125">Lorsque l’application ne fonctionne pas correctement, le niveau de journalisation peut être augmenté pour que les journaux plus détaillés soient collectés.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-125">When the application is misbehaving, then the log level can be increased so more verbose logs are gathered.</span></span> <span data-ttu-id="1ef1c-126">Cela équilibre les performances par rapport à la facilité de débogage.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-126">This balances performance against ease of debugging.</span></span>

<span data-ttu-id="1ef1c-127">Les performances élevées des outils de journalisation et le tunability de commentaires doivent inciter les développeurs à se connecter fréquemment.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-127">The high performance of logging tools and the tunability of verbosity should encourage developers to log frequently.</span></span> <span data-ttu-id="1ef1c-128">De nombreux favorisent un modèle de journalisation de l’entrée et de la sortie de chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-128">Many favor a pattern of logging the entry and exit of each method.</span></span> <span data-ttu-id="1ef1c-129">Cette approche peut sembler excessive, mais il est peu fréquent que les développeurs souhaitent moins de journalisation.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-129">This approach may sound like overkill, but it's infrequent that developers will wish for less logging.</span></span> <span data-ttu-id="1ef1c-130">En fait, il n’est pas rare d’effectuer des déploiements dans le seul but d’ajouter la journalisation autour d’une méthode problématique.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-130">In fact, it's not uncommon to perform deployments for the sole purpose of adding logging around a problematic method.</span></span> <span data-ttu-id="1ef1c-131">ERR sur le côté de la journalisation trop importante et non trop petit.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-131">Err on the side of too much logging and not on too little.</span></span> <span data-ttu-id="1ef1c-132">Notez que certains outils peuvent être utilisés pour fournir automatiquement ce type de journalisation.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-132">Note that some tools can be used to automatically provide this kind of logging.</span></span>

<span data-ttu-id="1ef1c-133">Dans les applications traditionnelles, les fichiers journaux étaient généralement stockés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-133">In traditional applications, log files were typically stored on the local machine.</span></span> <span data-ttu-id="1ef1c-134">En fait, sur les systèmes d’exploitation de type UNIX, il existe une structure de dossiers définie pour contenir tous les `/var/log`journaux, généralement sous.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-134">In fact, on Unix-like operating systems, there's a folder structure defined to hold any logs, typically under `/var/log`.</span></span> <span data-ttu-id="1ef1c-135">L’utilité de la journalisation dans un fichier plat sur un seul ordinateur est considérablement réduite dans un environnement Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-135">The usefulness of logging to a flat file on a single machine is vastly reduced in a cloud environment.</span></span> <span data-ttu-id="1ef1c-136">Les applications qui produisent des journaux peuvent ne pas avoir accès au disque local ou le disque local peut être très transitoire, car les conteneurs sont mélangés à des machines physiques.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-136">Applications producing logs may not have access to the local disk or the local disk may be highly transient as containers are shuffled around physical machines.</span></span>

<span data-ttu-id="1ef1c-137">Les applications Cloud natives développées à l’aide d’une architecture de microservices présentent également des défis pour les enregistreurs basés sur des fichiers.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-137">Cloud-native applications developed using a microservices architecture also pose some challenges for file-based loggers.</span></span> <span data-ttu-id="1ef1c-138">Les demandes de l’utilisateur peuvent maintenant s’étendre sur plusieurs services qui sont exécutés sur des ordinateurs différents et peuvent inclure des fonctions sans serveur sans accès à un système de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-138">User requests may now span multiple services that are run on different machines, and may include serverless functions with no access to a local file system at all.</span></span> <span data-ttu-id="1ef1c-139">Il serait très difficile de mettre en corrélation les journaux d’un utilisateur ou d’une session sur ces nombreux services et ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-139">It would be very challenging to correlate the logs from a user or a session across these many services and machines.</span></span>

<span data-ttu-id="1ef1c-140">Enfin, le nombre d’utilisateurs dans certaines applications Cloud natives est élevé.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-140">Finally, the number of users in some cloud-native applications is high.</span></span> <span data-ttu-id="1ef1c-141">Imaginez que chaque utilisateur génère une centaine de messages de journalisation lorsqu’il se connecte à une application.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-141">Imagine that each user generates a hundred lines of log messages when they log into an application.</span></span> <span data-ttu-id="1ef1c-142">En isolation, cela est gérable, mais multipliez-vous par plus de 100 000 utilisateurs et le volume des journaux devient important.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-142">In isolation, that is manageable, but multiply that over 100,000 users and the volume of logs becomes large.</span></span>

<span data-ttu-id="1ef1c-143">Heureusement, il existe des alternatives fantastiques à l’utilisation de la journalisation basée sur le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-143">Fortunately, there are some fantastic alternatives to using file system-based logging.</span></span> <span data-ttu-id="1ef1c-144">Un serveur de journalisation centralisé dans lequel tous les journaux sont envoyés, résout tous ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-144">A centralized log server to which all logs are sent, fixes all these problems.</span></span> <span data-ttu-id="1ef1c-145">Les journaux sont collectés par les applications et expédiés à une application de journalisation centralisée qui indexe et stocke les journaux.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-145">Logs are collected by the applications and shipped to a central logging application which indexes and stores the logs.</span></span> <span data-ttu-id="1ef1c-146">Cette classe de système peut ingérer des dizaines de gigaoctets de journaux tous les jours.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-146">This class of system can ingest tens of gigabytes of logs every day.</span></span>

<span data-ttu-id="1ef1c-147">Il est également utile de suivre certaines pratiques standard lors de la création d’une journalisation qui s’étend sur de nombreux services.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-147">It's also helpful to follow some standard practices when building logging that spans many services.</span></span> <span data-ttu-id="1ef1c-148">Par exemple, la génération d’un [ID de corrélation](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) au début d’une interaction longue, puis son enregistrement dans chaque message associé à cette interaction facilite la recherche de tous les messages associés.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-148">For instance, generating a [correlation ID](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) at the start of a lengthy interaction, and then logging it in each message that is related to that interaction, makes it easier to search for all related messages.</span></span> <span data-ttu-id="1ef1c-149">Il suffit de rechercher un seul message et d’extraire l’ID de corrélation pour trouver tous les messages associés.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-149">One need only find a single message and extract the correlation ID to find all the related messages.</span></span> <span data-ttu-id="1ef1c-150">Un autre exemple consiste à s’assurer que le format de journal est le même pour tous les services, quel que soit le langage ou la bibliothèque de journalisation qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-150">Another example is ensuring that the log format is the same for every service, whatever the language or logging library it uses.</span></span> <span data-ttu-id="1ef1c-151">Cette normalisation facilite grandement la lecture des journaux.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-151">This standardization makes reading logs much easier.</span></span> <span data-ttu-id="1ef1c-152">La figure 7-1 montre comment une architecture de microservices peut tirer parti de la journalisation centralisée dans le cadre de son flux de travail.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-152">Figure 7-1 demonstrates how a microservices architecture can leverage centralized logging as part of its workflow.</span></span>

<span data-ttu-id="1ef1c-153">![Les journaux provenant de différentes sources sont ingérés dans un magasin de journaux centralisé. **Figure 7-1**. ](./media/centralized-logging.png)
</span><span class="sxs-lookup"><span data-stu-id="1ef1c-153">![Logs from various sources are ingested into a centralized log store.](./media/centralized-logging.png)
**Figure 7-1**.</span></span> <span data-ttu-id="1ef1c-154">Les journaux provenant de différentes sources sont ingérés dans un magasin de journaux centralisé.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-154">Logs from various sources are ingested into a centralized log store.</span></span>

## <a name="when-to-use-monitoring"></a><span data-ttu-id="1ef1c-155">Quand utiliser l’analyse</span><span class="sxs-lookup"><span data-stu-id="1ef1c-155">When to use monitoring</span></span>

<span data-ttu-id="1ef1c-156">Certaines applications ne sont pas critiques.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-156">Some applications aren't mission-critical.</span></span> <span data-ttu-id="1ef1c-157">Ils sont peut-être utilisés en interne uniquement et, lorsqu’un problème survient, l’utilisateur peut contacter l’équipe responsable et l’application peut être redémarrée.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-157">Maybe they're only used internally, and when a problem occurs, the user can contact the team responsible and the application can be restarted.</span></span> <span data-ttu-id="1ef1c-158">Toutefois, les clients ont souvent des attentes plus élevées pour les applications qu’ils consomment.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-158">However, customers often have higher expectations for the applications they consume.</span></span> <span data-ttu-id="1ef1c-159">Si vous avez besoin de savoir quand des problèmes se produisent avec votre application *avant que* les utilisateurs ne le fassent, ou avant que les utilisateurs vous informent, vous devez surveiller son état actuel.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-159">If you need to know when problems occur with your application *before* users do, or before users notify you, you need to monitor its current state.</span></span> <span data-ttu-id="1ef1c-160">Correctement implémentés, la surveillance peut vous informer des conditions qui peuvent entraîner des problèmes, vous permettant de répondre aux conditions sous-jacentes avant qu’elles n’aient un impact sur l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-160">Implemented properly, monitoring can let you know about conditions that will lead to problems, letting you address underlying conditions before they result in any user impact.</span></span>

## <a name="monitoring-considerations"></a><span data-ttu-id="1ef1c-161">Surveillance - Éléments à prendre en compte</span><span class="sxs-lookup"><span data-stu-id="1ef1c-161">Monitoring considerations</span></span>

<span data-ttu-id="1ef1c-162">Certains systèmes de journalisation centralisée prennent le rôle supplémentaire de collecter les données de télémétrie en dehors des journaux purs.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-162">Some centralized logging systems take on an additional role of collecting telemetry outside of pure logs.</span></span> <span data-ttu-id="1ef1c-163">Ils peuvent collecter des mesures, telles que le temps nécessaire à l’exécution d’une requête de base de données, le temps de réponse moyen d’un serveur Web, et même les moyennes de charge du processeur et la sollicitation de la mémoire, comme indiqué par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-163">They can collect metrics, such as time to run a database query, average response time from a web server, and even CPU load averages and memory pressure as reported by the operating system.</span></span> <span data-ttu-id="1ef1c-164">Conjointement avec les journaux, ces systèmes peuvent fournir une vue holistique de l’intégrité des nœuds du système et de l’application dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-164">In conjunction with the logs, these systems can provide a holistic view of the health of nodes in the system and the application as a whole.</span></span>

<span data-ttu-id="1ef1c-165">Les fonctionnalités de collecte des mesures des outils de surveillance peuvent également être alimentées manuellement à partir de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-165">The metric gathering capabilities of the monitoring tools can also be fed manually from within the application.</span></span> <span data-ttu-id="1ef1c-166">Les flux d’activités qui présentent un intérêt particulier, tels que les nouveaux utilisateurs qui s’inscrivent ou les commandes en cours de placement, peuvent être instrumentés de telle sorte qu’ils incrémentent un compteur dans le système de surveillance central.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-166">Business flows that are of particular interest such as new users signing up or orders being placed, may be instrumented such that they increment a counter in the central monitoring system.</span></span> <span data-ttu-id="1ef1c-167">Cela déverrouille les outils de surveillance pour non seulement surveiller l’intégrité de l’application, mais aussi l’intégrité de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-167">This unlocks the monitoring tools to not only monitor the health of the application but the health of the business.</span></span>

<span data-ttu-id="1ef1c-168">Les requêtes peuvent être créées dans les outils d’agrégation de journaux pour rechercher certaines statistiques ou certains modèles, qui peuvent ensuite être affichés sous forme graphique, sur des tableaux de bord personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-168">Queries can be constructed in the log aggregation tools to look for certain statistics or patterns, which can then be displayed in graphical form, on custom dashboards.</span></span> <span data-ttu-id="1ef1c-169">Souvent, les équipes investiront dans des affichages de grande taille et montés sur un mur qui font pivoter les statistiques relatives à une application.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-169">Frequently, teams will invest in large, wall-mounted displays that rotate through the statistics related to an application.</span></span> <span data-ttu-id="1ef1c-170">De cette façon, il est facile de voir les problèmes à mesure qu’ils se produisent.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-170">This way, it's simple to see the problems as they occur.</span></span>

## <a name="when-to-use-alerts"></a><span data-ttu-id="1ef1c-171">Quand utiliser des alertes</span><span class="sxs-lookup"><span data-stu-id="1ef1c-171">When to use alerts</span></span>

<span data-ttu-id="1ef1c-172">Si vous devez réagir à des problèmes avec votre application, vous avez besoin d’un moyen d’alerter le personnel approprié.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-172">If you need to react to problems with your application, you need some way to alert the right personnel.</span></span> <span data-ttu-id="1ef1c-173">Il s’agit du troisième modèle d’observabilité des applications natives du Cloud, qui dépend de la journalisation et de la surveillance.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-173">This is the third cloud-native application observability pattern, and depends on logging and monitoring.</span></span> <span data-ttu-id="1ef1c-174">Votre application doit se connecter pour permettre le diagnostic des problèmes et, dans certains cas, pour alimenter les outils de surveillance.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-174">Your application needs to have logging in place to allow problems to be diagnosed, and in some cases to feed into monitoring tools.</span></span> <span data-ttu-id="1ef1c-175">Il a besoin d’une analyse pour agréger les mesures d’application et les données d’intégrité au même endroit.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-175">It needs monitoring to aggregate application metrics and health data in one place.</span></span> <span data-ttu-id="1ef1c-176">Une fois que cela a été établi, des règles peuvent être créées pour déclencher des alertes lorsque certaines métriques sont situées en dehors des niveaux acceptables.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-176">Once this has been established, rules can be created that will trigger alerts when certain metrics fall outside of acceptable levels.</span></span>

## <a name="alerts"></a><span data-ttu-id="1ef1c-177">Alertes</span><span class="sxs-lookup"><span data-stu-id="1ef1c-177">Alerts</span></span>

<span data-ttu-id="1ef1c-178">Vous pouvez élaborer des requêtes sur les outils de surveillance pour rechercher des conditions d’échec connues.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-178">You can craft queries against the monitoring tools to look for known failure conditions.</span></span> <span data-ttu-id="1ef1c-179">Par exemple, les requêtes peuvent parcourir les journaux entrants pour rechercher des indications du code d’état HTTP 500, qui indique un problème sur un serveur Web.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-179">For instance, queries could search through the incoming logs for indications of HTTP status code 500, which indicates a problem on a web server.</span></span> <span data-ttu-id="1ef1c-180">Dès que l’une d’entre elles est détectée, un message électronique ou un SMS peut être envoyé au propriétaire du service d’origine, qui peut commencer à examiner.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-180">As soon as one of these is detected, then an e-mail or an SMS could be sent to the owner of the originating service who can begin to investigate.</span></span>

<span data-ttu-id="1ef1c-181">Toutefois, en règle générale, une seule erreur 500 n’est pas suffisante pour déterminer qu’un problème s’est produit.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-181">Typically though, a single 500 error isn't sufficient to determine that a problem has occurred.</span></span> <span data-ttu-id="1ef1c-182">Cela peut signifier qu’un utilisateur a mal tapé son mot de passe ou entré des données incorrectes.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-182">It could mean that a user mistyped their password or entered some malformed data.</span></span> <span data-ttu-id="1ef1c-183">Les requêtes d’alerte peuvent être conçues pour se déclencher uniquement quand un nombre supérieur au nombre moyen d’erreurs 500 est détecté.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-183">The alert queries can be crafted to only fire when a larger than average number of 500 errors are detected.</span></span>

<span data-ttu-id="1ef1c-184">L’un des modèles les plus dangereux des alertes consiste à déclencher un trop grand nombre d’alertes pour les êtres humains à examiner.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-184">One of the most damaging patterns in alerting is to fire too many alerts for humans to investigate.</span></span> <span data-ttu-id="1ef1c-185">Les propriétaires de services seront rapidement désensibilisés des erreurs qu’ils ont déjà examinées et jugées sans gravité.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-185">Service owners will rapidly become desensitized to errors that they've previously investigated and found to be benign.</span></span> <span data-ttu-id="1ef1c-186">Lorsque des erreurs vraies se produisent, elles sont perdues dans le bruit de centaines de faux positifs.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-186">When true errors occur then they'll be lost in the noise of hundreds of false positives.</span></span> <span data-ttu-id="1ef1c-187">Le parable du [garçon qui effectué Wolf](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) est souvent informé des enfants pour les avertir de ce danger.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-187">The parable of the [Boy Who Cried Wolf](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) is frequently told to children to warn them of this very danger.</span></span> <span data-ttu-id="1ef1c-188">Il est important de s’assurer que les alertes qui se déclenchent indiquent un problème réel.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-188">It's important to ensure that the alerts that do fire are indicative of a real problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ef1c-189">[Précédent](monitoring-health.md)
>[Suivant](logging-with-elastic-stack.md)</span><span class="sxs-lookup"><span data-stu-id="1ef1c-189">[Previous](monitoring-health.md)
[Next](logging-with-elastic-stack.md)</span></span>