---
title: Vue d'ensemble du profilage
ms.date: 03/30/2017
helpviewer_keywords:
- managed code, profiling API support
- unmanaged code, combining with managed code in profiling
- notification threads [.NET Framework profiling]
- unmanaged code, profiling
- profiling API [.NET Framework], and COM
- profiling API [.NET Framework], unmanaged code profiling
- profilers, writing
- profiling API [.NET Framework], call stacks
- code profilers, writing
- profiling API [.NET Framework], security considerations
- profiling API [.NET Framework], managed code support
- common language runtime, profiling
- profiling API [.NET Framework], notification threads
- call stacks [.NET Framework profiling]
- profiling API [.NET Framework], stack depth
- common language runtime, writing a profiler
- profiling API [.NET Framework], information retrieval interfaces
- shadow stacks [.NET Framework profiling]
- COM, using in the profiling API
- stack snapshots [.NET Framework profiling]
- profiling API [.NET Framework], supported features
- profiling API [.NET Framework], overview
- security, profiling API considerations
- stack depth [.NET Framework profiling]
ms.assetid: 864c2344-71dc-46f9-96b2-ed59fb6427a8
ms.openlocfilehash: aa8bff374e9698d4b7e032428ec1bdc66901e05d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860913"
---
# <a name="profiling-overview"></a>Vue d'ensemble du profilage

Un profileur est un outil qui surveille l'exécution d'une autre application. Un profileur CLR (Common Language Runtime) est une bibliothèque de liens dynamiques (DLL) qui se compose de fonctions qui reçoivent des messages du CLR et qui lui en envoient à l'aide de l'API de profilage. La DLL du profileur est chargée par le CLR au moment de l'exécution.

Les outils de profilage traditionnels se contentent sur la mesure de l'exécution de l'application. Autrement dit, ils mesurent le temps passé dans chaque fonction ou l'utilisation de la mémoire de l'application au fil du temps. L'API de profilage cible une classe plus large d'outils de diagnostic tels que les utilitaires de couverture du code et même des outils de débogage avancés. Ces utilisations relèvent du diagnostic de par leur nature. L'API de profilage non seulement mesure mais surveille également l'exécution d'une application. C'est pourquoi l'API de profilage ne doit jamais être utilisée par l'application elle-même et l'exécution de l'application ne doit pas dépendre du profileur (ni être affectée par lui).

Le profilage d'une application CLR requiert plus de support qu'un profilage de code machine compilé de manière conventionnelle. Ceci est dû au fait que le CLR introduit des concepts tels que les domaines d'application, le garbage collection, la gestion des exceptions managées, la compilation de code juste-à-temps (JIT) (conversion du code MSIL, ou Microsoft Intermediate Language, en code machine natif) et des fonctionnalités similaires. Les mécanismes de profilage conventionnels ne peuvent pas identifier ni fournir des informations utiles sur ces fonctionnalités. L'API de profilage fournit ces informations manquantes efficacement, avec un impact minimal sur les performances du CLR et l'application profilée.

La compilation JIT au moment de l'exécution offre de bonnes possibilités au profilage. L'API de profilage permet à un profileur de modifier le flux de code MSIL en mémoire par une routine avant sa compilation JIT. De cette manière, le profileur peut ajouter dynamiquement le code d'instrumentation à des routines particulières nécessitant un examen plus approfondi. Bien que cette approche soit possible dans les scénarios conventionnels, il est beaucoup plus facile à implémenter pour le CLR à l'aide de l'API de profilage.

## <a name="the-profiling-api"></a>L'API de profilage

En règle générale, l’API de profilage est utilisée pour écrire un *profileur de code*, qui est un programme qui surveille l’exécution d’une application managée.

L'API de profilage est utilisée par une DLL du profileur, chargée dans le même processus que l'application en cours de profilage. La DLL du profileur implémente une interface de rappel ([ICorProfilerCallback](icorprofilercallback-interface.md) dans le .NET Framework version 1,0 et 1,1, [ICorProfilerCallback2](icorprofilercallback2-interface.md) dans la version 2,0 et ultérieure). Le CLR appelle les méthodes dans cette interface pour notifier le profileur des événements dans le processus profilé. Le profileur peut effectuer un rappel dans le runtime en utilisant les méthodes des interfaces [ICorProfilerInfo](icorprofilerinfo-interface.md) et [ICorProfilerInfo2](icorprofilerinfo2-interface.md) pour obtenir des informations sur l’état de l’application profilée.

> [!NOTE]
> Seule la partie collecte de données de la solution du profileur doit s'exécuter dans le même processus que l'application profilée. Toutes les analyses de données et d'interface utilisateur doivent être effectuées dans un processus séparé.

L'illustration suivante montre comment la DLL du profileur interagit avec l'application en cours de profilage et le CLR.

![Capture d’écran montrant l’architecture de profilage.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Interfaces de notification

[ICorProfilerCallback](icorprofilercallback-interface.md) et [ICorProfilerCallback2](icorprofilercallback2-interface.md) peuvent être considérées comme des interfaces de notification. Ces interfaces se composent de méthodes telles que [ClassLoadStarted](icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)et [JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md). Chaque fois que le CLR charge ou décharge une classe, compile une fonction, etc., il appelle la méthode correspondante dans l'interface `ICorProfilerCallback` ou `ICorProfilerCallback2` du profileur.

Par exemple, un profileur peut mesurer les performances du code à l’aide de deux fonctions de notification : [FunctionEnter2](functionenter2-function.md) et [FunctionLeave2](functionleave2-function.md). Il horodate simplement chaque notification, cumule les résultats et génère une liste qui indique quelles fonctions ont consommé le plus de temps processeur ou de temps horloge pendant l'exécution de l'application.

### <a name="the-information-retrieval-interfaces"></a>Interfaces de récupération d'informations

Les autres interfaces principales impliquées dans le profilage sont [ICorProfilerInfo](icorprofilerinfo-interface.md) et [ICorProfilerInfo2](icorprofilerinfo2-interface.md). Le profileur appelle ces interfaces au besoin pour obtenir plus d'informations afin de faciliter son analyse. Par exemple, chaque fois que le CLR appelle la fonction [FunctionEnter2](functionenter2-function.md) , il fournit un identificateur de fonction. Le profileur peut obtenir plus d’informations sur cette fonction en appelant la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) pour découvrir la classe parente de la fonction, son nom, etc.

## <a name="supported-features"></a>Fonctionnalités prises en charge

L'API de profilage fournit des informations sur divers événements et actions qui se produisent dans le Common Language Runtime. Vous pouvez utiliser ces informations pour surveiller le fonctionnement interne des processus et analyser les performances de votre application .NET Framework.

L'API de profilage récupère des informations sur les événements et actions ci-après qui se produisent dans le CLR :

- Événements de démarrage et d'arrêt du CLR.

- Événements de création et d'arrêt de domaine d'application.

- Événements de chargement et de déchargement d'assemblys.

- Événements de chargement et de déchargement de modules.

- Événements de création et de destruction de tables vtable COM.

- Événements de compilation juste-à-temps (JIT) et de lancement de code.

- Événements de chargement et de déchargement de classes.

- Événements de création et de destruction de threads.

- Événements d'entrée et de sortie de fonction.

- Exceptions.

- Transitions entre l'exécution de code managé et non managé.

- Transitions entre des contextes d'exécution différents.

- Informations sur les suspensions du runtime.

- Informations sur l'activité du tas de mémoire du runtime et du garbage collection.

L'API de profilage peut être appelée à partir de tout langage compatible COM (non managé).

L'API est efficace en matière de consommation de processeur et de mémoire. Le profilage n'implique pas de modifications de l'application profilée suffisamment significatives pour générer des résultats trompeurs.

L'API de profilage s'avère utile à la fois pour les profileurs d'échantillonnage et de non-échantillonnage. Un *profileur d’échantillonnage* inspecte le profil à des battements d’horloge réguliers, par exemple, à une distance de 5 millisecondes. Un *profileur sans échantillonnage* est informé d’un événement de façon synchrone avec le thread qui déclenche l’événement.

### <a name="unsupported-functionality"></a>Fonctionnalités non prises en charge

L'API de profilage ne prend pas en charge les fonctionnalités suivantes :

- Code non managé, qui doit être profilé à l'aide de méthodes Win32 classiques. Toutefois, le profileur CLR inclut des événements de transition pour déterminer les limites entre code managé et non managé.

- Applications qui modifient elles-mêmes leur propre code à des fins de programmation orientée aspect par exemple.

- Vérification des limites, car l'API de profilage ne fournit pas ces informations. Le CLR assure une prise en charge intrinsèque de la vérification des limites de tout le code managé.

- Profilage distant, qui n'est pas pris en charge pour les raisons suivantes :

  - Le profilage distant allonge le temps d'exécution. Quand vous utilisez les interfaces de profilage, vous devez minimiser le temps d'exécution afin que les résultats de profilage ne soient pas indûment affectés. Cela s'avère particulièrement pertinent quand les performances de l'exécution sont analysées. Toutefois, le profilage distant n'est pas une limitation quand les interfaces de profilage sont utilisées pour analyser l'utilisation de la mémoire ou pour obtenir des informations d'exécution sur les frames de pile, les objets, etc.

  - Le profileur de code CLR doit inscrire une ou plusieurs interfaces de rappel auprès du runtime sur l'ordinateur local sur lequel s'exécute l'application profilée. Cela limite la possibilité de créer un profileur de code distant.

- Profilage dans des environnements de production avec des exigences de haute disponibilité. L'API de profilage a été créée pour prendre en charge les diagnostics au moment du développement. Elle n'a pas subi les tests rigoureux requis pour prendre en charge des environnements de production.

## <a name="notification-threads"></a>Threads de notification

Dans la plupart des cas, le thread qui génère un événement exécute également des notifications. Ces notifications (par exemple, [FunctionEnter](functionenter-function.md) et [FunctionLeave](functionleave-function.md)) n’ont pas besoin de fournir le `ThreadID`explicite. En outre, le profileur peut décider d'utiliser le stockage local des threads pour stocker et mettre à jour ses blocs d'analyse au lieu d'indexer les blocs d'analyse dans le stockage global, selon le `ThreadID` du thread affecté.

Notez que ces rappels ne sont pas sérialisés. Les utilisateurs doivent protéger leur code en créant des structures de données thread-safe et en verrouillant le code du profileur si nécessaire pour empêcher tout accès parallèle à partir de plusieurs threads. Par conséquent, dans certains cas, vous pouvez recevoir une séquence inhabituelle de rappels. Par exemple, supposons qu'une application managée engendre deux threads qui exécutent un code identique. Dans ce cas, il est possible de recevoir un événement [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) pour une fonction d’un thread et un rappel `FunctionEnter` de l’autre thread avant de recevoir le rappel [ICorProfilerCallback :: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) . Le cas échéant, l'utilisateur reçoit un rappel `FunctionEnter` pour une fonction qui n'a peut-être pas encore été entièrement compilée juste-à-temps (JIT).

## <a name="security"></a>Sécurité

Une DLL de profileur est une DLL non managée qui s'exécute dans le cadre du moteur d'exécution du Common Language Runtime. Par conséquent, le code inclus dans la DLL de profileur n'est pas soumis aux restrictions de sécurité d'accès du code managé. Les seules limitations applicables à la DLL de profileur sont celles imposées par le système d'exploitation sur l'utilisateur qui exécute l'application profilée.

Les auteurs de profileur doivent prendre les précautions appropriées pour éviter les problèmes de sécurité. Par exemple, lors de l'installation, une DLL de profileur doit être ajoutée à la liste de contrôle d'accès (ACL) afin qu'aucun utilisateur malveillant ne puisse la modifier.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Combinaison de code managé et non managé dans un profileur de code

Un profileur incorrectement écrit peut provoquer des références circulaires à lui-même, ce qui entraîne un comportement imprévisible.

Une revue de l’API de profilage CLR peut donner l’impression de pouvoir écrire un profileur contenant des composants managés et non managés qui s’appellent mutuellement via COM interop ou des appels indirects.

Bien que cela soit possible du point de vue de la conception, l'API de profilage ne prend pas en charge les composants managés. Un profileur CLR doit être entièrement non managé. Toute tentative de combiner du code managé et non managé dans un profileur CLR risque d'entraîner des violations d'accès, des échecs de programme ou des interblocages. Les composants managés du profileur déclenchent des événements sur leurs composants non managés, qui rappellent ensuite les composants managés, ce qui entraîne des références circulaires.

Le seul emplacement où un profileur CLR peut appeler du code managé en toute sécurité est le corps MSIL (Microsoft Intermediate Language) d'une méthode. La pratique recommandée pour modifier le corps MSIL consiste à utiliser les méthodes de recompilation JIT dans l’interface [ICorProfilerCallback4](icorprofilercallback4-interface.md) .

Il est également possible d'utiliser les anciennes méthodes d'instrumentation pour modifier du code MSIL. Avant la fin de la compilation juste-à-temps (JIT) d’une fonction, le profileur peut insérer des appels managés dans le corps MSIL d’une méthode, puis la compiler juste-à-temps (consultez la méthode [ICorProfilerInfo :: GetILFunctionBody,](icorprofilerinfo-getilfunctionbody-method.md) ). Cette technique peut être utilisée avec succès pour l'instrumentation sélective du code managé, ou pour collecter des statistiques et des données de performance sur la compilation JIT.

Un profileur de code peut également insérer des raccordements natifs dans le corps MSIL de chaque fonction managée appelée dans du code non managé. Cette technique peut être utilisée pour l'instrumentation et la couverture. Par exemple, un profileur de code peut insérer des raccordements d'instrumentation après chaque bloc MSIL pour vous assurer que le bloc a été exécuté. La modification du corps MSIL d'une méthode est une opération très délicate et il existe de nombreux facteurs à prendre en considération.

## <a name="profiling-unmanaged-code"></a>Profilage de code non managé

L'API de profilage CLR (Common Language Runtime) fournit la prise en charge minimale pour profiler du code non managé. Les fonctionnalités suivantes sont fournies :

- Énumération des chaînes de pile. Cette fonctionnalité permet à un profileur de code de déterminer la limite entre code managé et code non managé.

- Détermination de la nature d'une chaîne de pile, à savoir s'il s'agit de code managé ou de code natif.

Dans les versions 1.0 et 1.1 du .NET Framework, ces méthodes sont disponibles via le sous-ensemble in-process de l'API de débogage CLR. Elles sont définies dans le fichier CorDebug.idl.

Dans le .NET Framework 2,0 et versions ultérieures, vous pouvez utiliser la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) pour cette fonctionnalité.

## <a name="using-com"></a>Utilisation de COM

Bien que les interfaces de profilage soient définies en tant qu'interfaces COM, le Common Language Runtime (CLR) n'initialise pas réellement COM pour utiliser ces interfaces. La raison est de ne pas avoir à définir le modèle de thread à l’aide de la fonction [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) avant que l’application managée ait pu spécifier son modèle de thread souhaité. De même, le profileur lui-même ne doit pas appeler `CoInitialize`, car il risque de choisir un modèle de thread qui n'est pas compatible avec l'application en cours de profilage, ce qui risque d'entraîner l'échec de l'application.

## <a name="call-stacks"></a>Piles des appels

L'API de profilage fournit deux méthodes pour obtenir des piles des appels : une méthode d'instantané de pile, qui permet la collecte fragmentée des piles des appels et une méthode de pile cachée, qui effectue le suivi de la pile des appels à chaque instant.

### <a name="stack-snapshot"></a>Instantané de pile

Un instantané de pile est une trace de la pile d'un thread à un instant précis. L'API de profilage prend en charge le traçage des fonctions managées sur la pile, mais elle laisse le traçage des fonctions non managées au propre analyseur de pile du profileur.

Pour plus d’informations sur la façon de programmer le profileur pour parcourir les piles managées, consultez la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) dans cet ensemble de documentation et [parcours de la pile du profileur dans le .NET Framework 2,0 : notions de base et au-delà](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).

### <a name="shadow-stack"></a>Pile cachée

L'utilisation trop fréquente de la méthode d'instantané de pile peut rapidement créer un problème de performances. Si vous souhaitez prendre fréquemment des traces de pile, votre profileur doit plutôt générer une pile cachée à l’aide des rappels d’exception [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), [FunctionTailcall2](functiontailcall2-function.md)et [ICorProfilerCallback2](icorprofilercallback2-interface.md) . La pile cachée est toujours actuelle et peut rapidement être copiée vers le stockage, chaque fois qu'un instantané de pile est nécessaire.

Une pile cachée peut obtenir des arguments de fonction, des valeurs de retour et des informations sur les instanciations génériques. Ces informations sont uniquement disponibles via la pile cachée et peuvent être obtenues quand le contrôle est transmis à une fonction. Toutefois, ces informations peuvent devenir indisponibles lors de l'exécution ultérieure de la fonction.

## <a name="callbacks-and-stack-depth"></a>Rappels et profondeur de la pile

Les rappels du profileur peuvent être émis dans des circonstances où la pile est contrainte. De plus, un débordement de la pile dans un rappel du profileur entraîne une sortie immédiate du processus. Un profileur doit veiller à utiliser une pile aussi petite que possible en réponse à des rappels. Si le profileur est prévu pour être utilisé avec des processus robustes face à un débordement de pile, il doit également éviter lui-même de déclencher un débordement de pile.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Configuration d’un environnement de profilage](setting-up-a-profiling-environment.md)|Explique comment initialiser un profileur, définir des notifications d'événements et profiler un service Windows.|
|[Interfaces de profilage](profiling-interfaces.md)|Décrit les interfaces non managées que l'API de profilage utilise.|
|[Fonctions statiques globales de profilage](profiling-global-static-functions.md)|Décrit les fonctions statiques globales non managées que l'API de profilage utilise.|
|[Énumérations de profilage](profiling-enumerations.md)|Décrit les énumérations non managées utilisées par l'API de profilage.|
|[Structures de profilage](profiling-structures.md)|Décrit les structures non managées utilisées par l'API de profilage.|
