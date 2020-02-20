---
title: Performances .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
ms.openlocfilehash: 47d85ae63f0594b778523425631ff54f9f3ca32f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504092"
---
# <a name="net-framework-performance"></a>Performances .NET Framework
Si vous voulez créer des applications dotées de hautes performances, vous devez concevoir et planifier les performances comme vous concevez n'importe quelle autre fonctionnalité de votre application. Vous pouvez utiliser les outils fournis par Microsoft pour mesurer les performances de votre application et, si nécessaire, apporter des améliorations à l'utilisation de la mémoire, au débit de code et à la réactivité. Cette rubrique répertorie les outils d'analyse de performance fournis par Microsoft et fournit des liens vers d'autres rubriques qui couvrent les performances dans des domaines spécifiques du développement d'applications.  
  
## <a name="designing-and-planning-for-performance"></a>Conception et planification des performances  
 Pour créer une application présentant d’excellentes performances, vous devez concevoir les performances dans votre application comme si vous conceviez n’importe quelle autre fonctionnalité. Vous devez déterminer les scénarios où les performances sont essentielles, définir des objectifs de performances et mesurer régulièrement les performances dans ces scénarios d'application. Comme chaque application est différente et possède différents chemins d'exécution aux performances critiques, le fait de déterminer précocement ces chemins et de concentrer vos efforts vous permet de maximiser votre productivité.  
  
 Il n'est pas nécessaire que votre plateforme cible vous soit complètement familière pour créer une application à hautes performances. Toutefois, vous devez chercher à comprendre quelles parties de votre plateforme cible sont coûteuses en termes de performances. Pour cela, vous pouvez mesurer les performances tôt dans votre processus de développement.  
  
 Pour déterminer les domaines essentiels pour les performances et pour établir vos objectifs de performances, prenez toujours en compte l'expérience utilisateur. Le temps de démarrage et la réactivité sont deux domaines clés qui affectent la perception qu'a l'utilisateur de votre application. Si votre application utilise beaucoup de mémoire, elle peut sembler lente à l'utilisateur ou affecter d'autres applications qui s'exécutent sur le système, ou, dans certains cas, elle peut échouer au test de soumission du Windows Store ou du Windows Phone Store. De plus, si vous déterminez quelles parties de votre code s'exécutent le plus fréquemment, vous pouvez veiller à l'optimisation de ces parties de code.  
  
## <a name="analyzing-performance"></a>Analyse des performances  
 Dans le cadre de votre plan de développement global, définissez des points durant le développement où mesurer les performances de votre application et comparer les résultats aux objectifs que vous avez définis précédemment. Mesurez votre application dans l'environnement et avec le matériel que posséderont selon vous les utilisateurs. En analysant les performances de votre application tôt et régulièrement, vous pouvez changer les décisions architecturales qui seraient coûteuses à corriger ultérieurement dans le cycle de développement. Les sections suivantes décrivent les outils de performance que vous pouvez utiliser pour analyser vos applications et traitent du suivi d'événements, qui est utilisé par ces outils.  
  
### <a name="performance-tools"></a>Outils d’analyse des performances  
 Voici certains outils de performance que vous pouvez utiliser avec vos applications .NET Framework.  
  
|Outil|Description|  
|----------|-----------------|  
|Analyse des performances Visual Studio|Utilisez cet outil pour analyser l'utilisation de l'UC de vos applications .NET Framework qui seront déployées sur des ordinateurs exécutant le système d'exploitation Windows.<br /><br /> Vous trouverez cet outil dans le menu **Débogage** de Visual Studio après avoir ouvert votre projet. Pour plus d'informations, consultez [Explorateur de performances](/visualstudio/profiling/performance-explorer). **Remarque** : Utilisez l’analyse de l’application Windows Phone (voir ligne suivante) quand vous ciblez Windows Phone.|  
|Analyse de l'application Windows Phone|Utilisez cet outil pour analyser l'UC et la mémoire, le taux de transfert des données réseau, la réactivité de l'application et la consommation de la batterie dans vos applications Windows Phone.<br /><br /> Vous trouverez cet outil dans le menu **Débogage** de votre projet Windows Phone dans Visual Studio après avoir installé [Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773). Pour plus d’informations, consultez [profilage d’application pour Windows Phone 8](https://docs.microsoft.com/previous-versions/windows/apps/jj215908(v=vs.105)).|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|Utilisez ces outils pour identifier des problèmes de performances liés à l'UC et à la mémoire. Cet outil utilise le suivi d’événements pour Windows et des API de profilage du CLR pour assurer des investigations avancées de la mémoire et de l’UC, et pour fournir des informations sur le garbage collection et la compilation JIT. Pour plus d’informations sur l’utilisation de PerfView, consultez le didacticiel et les fichiers d’aide fournis dans l’application, les [didacticiels vidéo sur Channel 9](https://channel9.msdn.com/Series/PerfView-Tutorial) et les [billets de blog](https://docs.microsoft.com/archive/blogs/vancem/).<br /><br /> Pour plus d’informations sur les problèmes de mémoire, consultez le didacticiel sur l’[utilisation de PerfView pour l’examen de la mémoire](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Windows Performance Analyzer](https://www.microsoft.com/download/details.aspx?id=30652)|Utilisez cet outil pour déterminer les performances globales du système telles que l'utilisation de la mémoire et du stockage par votre application quand plusieurs applications s'exécutent sur le même ordinateur. Cet outil est disponible dans le centre de téléchargement dans le cadre du kit de déploiement et d’évaluation Windows (ADK) pour Windows 8. Pour plus d’informations, consultez [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer).|
  
### <a name="event-tracing-for-windows-etw"></a>Suivi d'événements pour Windows (ETW)  
 Le suivi d'événements pour Windows est une technique qui vous permet d'obtenir des informations de diagnostic sur le code en cours d'exécution et qui est essentielle pour un grand nombre des outils de performance mentionnés précédemment. Il crée des journaux lorsque des événements particuliers sont déclenchés par des applications .NET Framework et par Windows. Le suivi d'événements pour Windows vous permet d'activer et désactiver la journalisation de façon dynamique, et vous pouvez effectuer un traçage détaillé dans un environnement de production sans redémarrer votre application. .NET Framework propose la prise en charge des événements ETW, et le suivi d'événements pour Windows est utilisé par de nombreux outils de profilage et de performance pour générer des données de performance. Ces outils activent et désactivent souvent des événements ETW et il est utile de se familiariser avec eux. Vous pouvez utiliser des événements ETW spécifiques pour collecter des informations de performance sur des composants particuliers de votre application. Pour plus d’informations sur la prise en charge du suivi d’événements pour Windows (ETW) dans .NET Framework, consultez [Événements ETW dans le Common Language Runtime](etw-events-in-the-common-language-runtime.md) et [Événements ETW dans la bibliothèque parallèle de tâches et PLINQ](etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Performances par type d'application  
 Chaque type d'application .NET Framework possède ses propres pratiques recommandées, considérations et outils pour évaluer les performances. Le tableau ci-dessous propose des liens vers des rubriques liées aux performances pour des types d'applications .NET Framework spécifiques.  
  
|Type d’application|Consultez|  
|--------------|---------|  
|Applications .NET Framework pour toutes les plateformes|[Garbage Collection et performances](../../standard/garbage-collection/performance.md)<br /><br /> [Conseils sur les performances](performance-tips.md)|  
|Applications du Windows 8. x Store écrites C++dans C#, et Visual Basic|[Bonnes pratiques pour les performances des applications du Windows Store en C++, C# et Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh750313%28v=win.10%29)|  
|Windows Presentation Foundation (WPF)|[WPF Performance Suite](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))|  
|ASP.NET|[Vue d’ensemble des performances ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668225(v=vs.100))|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Mise en cache dans les applications .NET Framework](caching-in-net-framework-applications.md)|Décrit des techniques de mise en cache des données pour améliorer les performances dans votre application.|  
|[Initialisation tardive](lazy-initialization.md)|Décrit comment initialiser des objets selon vos besoins pour améliorer les performances, notamment au démarrage de l'application.|  
|[Fiabilité](reliability.md)|Fournit des informations sur la manière d'éviter les exceptions asynchrones dans un environnement serveur.|  
|[Conception d’applications .NET Framework complexes et réactives](writing-large-responsive-apps.md)|Fournit des conseils liés aux performances, rassemblés lors de la réécriture des compilateurs C# et Visual Basic en code managé, et inclut plusieurs exemples réels issus du compilateur C#.|
