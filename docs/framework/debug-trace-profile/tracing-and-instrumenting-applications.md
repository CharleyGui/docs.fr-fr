---
title: Traçage et instrumentation d'applications
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework]
- debugging [.NET Framework], instrumentation
- performance monitoring, instrumentation
- instrumentation, about instrumentation
- tracing [.NET Framework], about tracing
- performance monitoring, tracing code
- Trace class, instrumentation for .NET applications
ms.assetid: 773b6fc4-9013-4322-b728-5dec7a72e743
ms.openlocfilehash: 2dcdbaf50ed053d43fc2df2c80fe7688e7b3e51f
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542609"
---
# <a name="tracing-and-instrumenting-applications"></a>Traçage et instrumentation d'applications
Le suivi est un moyen de surveiller l’exécution de votre application pendant son exécution . Vous pouvez ajouter l'instrumentation de traçage et de débogage à votre application .NET Framework au moment du développement, et utiliser cette instrumentation pendant le développement de l'application et après son déploiement. Utilisez les classes <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> et <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> pour enregistrer les informations relatives aux erreurs et à l'exécution de l'application dans des journaux, des fichiers texte ou d'autres appareils en vue d'une analyse ultérieure.  
  
 Le terme *instrumentation* fait référence à la capacité de surveiller ou de mesurer le niveau de performance d’un produit et de diagnostiquer les erreurs éventuelles. En programmation, c'est la capacité d'une application à incorporer les éléments suivants :  
  
- **Suivi de code** : réception de messages d’information sur l’exécution d’une application au moment de l’exécution.  
  
- **Débogage** : repérage et résolution des erreurs de programmation dans une application en cours de développement. Pour plus d’informations, consultez [Débogage](/visualstudio/debugger/debugger-feature-tour).  
  
- **Compteurs de performance** : composants qui vous permettent de suivre les performances de votre application. Pour plus d’informations, consultez [Compteurs de performances](performance-counters.md).  
  
- **Journaux des événements** : composants qui vous permettent de recevoir et de suivre les principaux événements liés à l’exécution de votre application. Pour plus d'informations, consultez la classe <xref:System.Diagnostics.EventLog>.  
  
 L'instrumentation de votre application, en plaçant des instructions de trace à des endroits stratégiques de votre code, est particulièrement utile pour les applications distribuées. Avec les instructions de trace, vous pouvez instrumenter une application pour afficher des informations en cas de problème, mais aussi pour surveiller les performances d'exécution de l'application.  
  
 La classe <xref:System.Diagnostics.TraceSource> fournit des fonctionnalités de suivi améliorées. Elle remplace les méthodes statiques des classes de traçage <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> plus anciennes. Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> familières sont toujours largement utilisées, mais la classe <xref:System.Diagnostics.TraceSource> est recommandée pour ses nouvelles commandes de traçage, telles que <xref:System.Diagnostics.TraceSource.TraceEvent%2A> et <xref:System.Diagnostics.TraceSource.TraceData%2A>.  
  
 Les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug> sont identiques, à ceci près que les procédures et les fonctions de la classe <xref:System.Diagnostics.Trace> ont compilées par défaut dans des versions release, mais celles de la classe <xref:System.Diagnostics.Debug> ne le sont pas.  
  
 Avec les classes <xref:System.Diagnostics.Trace> et <xref:System.Diagnostics.Debug>, vous pouvez surveiller et analyser les performances d'une application pendant le développement ou après le déploiement. Par exemple, utilisez la classe <xref:System.Diagnostics.Trace> pour suivre des actions particulières au fur et à mesure qu'elles se produisent dans une application déployée (comme la création de nouvelles connexions de base de données) et ainsi surveiller les performances de l'application.  
  
## <a name="code-tracing-and-debugging"></a>Traçage et débogage de code  
 Pendant la phase de développement, utilisez les méthodes de sortie de la classe <xref:System.Diagnostics.Debug> pour afficher des messages dans la fenêtre Sortie de l'environnement de développement intégré (IDE) de Visual Studio. Par exemple :  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
```  
  
 Chacun de ces exemples affiche « Hello World! » dans la fenêtre Sortie quand l’application est exécutée dans le débogueur.  
  
 Cela vous permet de déboguer vos applications et d'optimiser leurs performances en fonction de leur comportement dans votre environnement de test. Déboguez votre application dans votre version debug en activant l'attribut conditionnel <xref:System.Diagnostics.Debug> pour recevoir toutes les données de sortie de débogage. Une fois que votre application est finalisée, compilez votre version release sans activer l’attribut conditionnel <xref:System.Diagnostics.Debug>. Ainsi, le compilateur n’inclura pas votre code de débogage dans le fichier exécutable final. Pour plus d’informations, consultez [Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug](how-to-compile-conditionally-with-trace-and-debug.md). Pour plus d’informations sur les différentes configurations de build de votre application, consultez [Compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
 Vous pouvez aussi tracer l'exécution du code dans une application installée, en utilisant les méthodes de la classe <xref:System.Diagnostics.Trace>. En plaçant des [Commutateurs de suivi](trace-switches.md) dans votre code, vous pouvez contrôler le traçage et son importance. Vous pouvez ainsi surveiller l’état de votre application dans un environnement de production, ce qui est particulièrement important dans une application qui utilise plusieurs composants s’exécutant sur plusieurs ordinateurs. Vous pouvez contrôler la manière dont les commutateurs sont utilisés après le déploiement par le biais du fichier de configuration. Pour plus d’informations, consultez [Guide pratique pour créer, initialiser et configurer des commutateurs de suivi](how-to-create-initialize-and-configure-trace-switches.md).  
  
 Quand vous développez une application pour laquelle vous envisagez d'utiliser la fonctionnalité de traçage, vous incluez généralement des messages de traçage et de débogage dans le code de l'application. Quand vous êtes prêt à déployer l’application, compilez votre build de mise en production sans activer l’attribut conditionnel **Debug**. Cependant, vous pouvez activer l’attribut conditionnel **Trace** pour que le compilateur inclue votre code de suivi dans le fichier exécutable. Pour plus d’informations, consultez [Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug](how-to-compile-conditionally-with-trace-and-debug.md).  
  
### <a name="phases-of-code-tracing"></a>Phases du traçage de code  
 Le traçage de code comprend les trois phases suivantes :  
  
1. **Instrumentation** : vous ajoutez le code de suivi à votre application.  
  
2. **Suivi** : le code de suivi écrit les informations vers la cible spécifiée.  
  
3. **Analyse** : vous évaluez les informations de suivi pour identifier et comprendre les problèmes potentiels dans l’application.  
  
 Durant le développement, toutes les méthodes de sortie de débogage et de traçage écrivent les informations par défaut dans la fenêtre Sortie de Visual Studio. Dans une application déployée, les méthodes écrivent les informations de traçage vers les cibles de votre choix. Pour plus d’informations sur la spécification d’une cible de sortie pour le suivi ou le débogage, consultez [Écouteurs de suivi](trace-listeners.md).  
  
 La section suivante décrit les principales étapes généralement suivies lors du traçage pour analyser et corriger des problèmes potentiels dans des applications déployées. Pour plus d'informations sur ces étapes, voir les liens appropriés.  
  
##### <a name="to-use-tracing-in-an-application"></a>Pour utiliser le traçage dans une application  
  
1. Déterminez la sortie de traçage que vous souhaitez obtenir sur place après avoir déployé l'application.  
  
2. Créez un jeu de commutateurs. Pour plus d’informations, consultez la rubrique [Procédure : configuration de commutateurs de trace](how-to-create-initialize-and-configure-trace-switches.md).  
  
3. Ajoutez les instructions de trace au code de l'application.  
  
4. Déterminez l'emplacement d'affichage de la sortie de traçage et ajoutez les écouteurs appropriés. Pour plus d’informations, consultez [Création et initialisation d’écouteurs de suivi](how-to-create-and-initialize-trace-listeners.md).  
  
5. Testez et déboguez votre application ainsi que le code de trace qu'elle contient.  
  
6. Compilez l'application en code exécutable, en suivant l'une des procédures ci-dessous :  
  
    - Utilisez le menu **Générer** et la page **Déboguer** de la boîte de dialogue **Pages de propriétés** dans l’**Explorateur de solutions**. Procédez ainsi pour compiler votre application dans Visual Studio.  
  
         \- ou -  
  
    - Utilisez les directives du compilateur **Trace** et **Debug** pour la méthode de ligne de commande de compilation. Pour plus d’informations, consultez [Compilation conditionnelle avec Trace et Debug](how-to-compile-conditionally-with-trace-and-debug.md). Procédez ainsi pour compiler votre application à partir d'une ligne de commande.  
  
7. Si un problème survient au moment de l'exécution, activez le commutateur de trace approprié. Pour plus d’informations, consultez [Configuration des commutateurs de suivi](how-to-create-initialize-and-configure-trace-switches.md).  
  
     Le code de trace écrit les messages de traçage vers la cible spécifiée (par exemple, un écran, un fichier texte ou un journal des événements). Le type d’écouteur que vous avez inclus dans la collection <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> détermine la cible.  
  
8. Analysez les messages de traçage pour identifier et comprendre les problèmes potentiels dans l'application.  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>Instrumentation de traçage pour les applications distribuées  
 Pendant la phase de création d'une application distribuée, il peut être difficile de tester l'application dans des conditions d'utilisation réelles. Les équipes de développement ont rarement la possibilité de tester toutes les combinaisons de systèmes d'exploitation ou de navigateurs web (y compris toutes les versions localisées) ou de simuler un nombre élevé d'utilisateurs qui accéderont simultanément à l'application. Vous ne pouvez donc pas tester la manière dont une application distribuée répondra à un fort trafic, à des configurations différentes et aux comportements propres à chaque utilisateur final. Par ailleurs, vous ne pouvez pas interagir directement avec toutes les parties de l'application distribuée, ni afficher leur activité, car beaucoup d'entre elles ne possèdent pas l'interface utilisateur nécessaire.  
  
 Vous pouvez cependant contourner ce problème en permettant aux applications distribuées de décrire certains événements utiles pour les administrateurs système, en particulier les problèmes rencontrés. Il vous suffit d’*instrumenter* l’application, c’est-à-dire de placer des instructions de suivi à des endroits stratégiques de votre code. Ainsi, si l'application a un comportement inattendu au moment de l'exécution (par exemple, un temps de réponse très lent), vous pouvez en déterminer la cause probable.  
  
 Grâce aux instructions de trace, vous ne perdez pas de temps à analyser, modifier et recompiler le code source d’origine, ni à essayer de reproduire l’erreur d’exécution dans l’environnement de débogage. Rappelez-vous que l'instrumentation d'une application est utile pour afficher les erreurs, mais aussi pour surveiller les performances.  
  
## <a name="strategic-placement-of-trace-statements"></a>Placement stratégique des instructions de trace  
 Vous devez apporter un soin particulier lors du placement de vos instructions de suivi à utiliser au moment de l'exécution. Vous devez réfléchir aux informations de suivi susceptibles d'être nécessaires dans une application déployée, de sorte que tous les scénarios de suivi probables soient convenablement traités. Toutefois, étant donné que les applications qui utilisent le suivi varient considérablement, il n'existe aucune recommandation générale concernant le positionnement stratégique du suivi. Pour plus d’informations sur la façon de placer des instructions de suivi, consultez [Guide pratique pour ajouter des instructions de suivi au code d’application](how-to-add-trace-statements-to-application-code.md).  
  
## <a name="output-from-tracing"></a>Sortie de trace  
 La sortie de suivi est collectée par des objets appelés *écouteurs*. Un écouteur est un objet qui reçoit la sortie de trace et qui l'écrit dans une cible de sortie (généralement une fenêtre, un journal ou un fichier texte). Quand un écouteur de la trace est créé, il est en principe ajouté à la collection <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>, ce qui permet à l’écouteur de recevoir toutes les données de sortie de trace.  
  
 Les informations de traçage sont toujours écrites au moins dans la cible de sortie <xref:System.Diagnostics.Trace> par défaut (<xref:System.Diagnostics.DefaultTraceListener>). Si, pour une raison quelconque, vous avez supprimé l'écouteur <xref:System.Diagnostics.DefaultTraceListener> sans avoir ajouté d'autres écouteurs à la collection <xref:System.Diagnostics.Trace.Listeners%2A>, vous ne recevrez plus de messages de trace. Pour plus d’informations, consultez [Écouteurs de suivi](trace-listeners.md).  
  
 Les six membres <xref:System.Diagnostics.Debug> et méthodes <xref:System.Diagnostics.Trace> qui écrivent des informations de traçage sont répertoriés dans le tableau suivant.  
  
|Méthode|Output|  
|------------|------------|  
|`Assert`|Le texte spécifié ou, si aucun texte n'est spécifié, la pile des appels. La sortie est écrite uniquement si la condition spécifiée en tant qu’argument dans l’instruction `Assert` est **false**.|  
|`Fail`|Le texte spécifié ou, si aucun texte n'est spécifié, la pile des appels.|  
|`Write`|Le texte spécifié.|  
|`WriteIf`|Texte spécifié, si la condition spécifiée en tant qu’argument dans l’instruction `WriteIf` est satisfaite.|  
|`WriteLine`|Le texte spécifié et un retour chariot.|  
|`WriteLineIf`|Le texte spécifié et un retour chariot, si la condition spécifiée en tant qu’argument dans l’instruction `WriteLineIf` est satisfaite.|  
  
 Tous les écouteurs dans la collection <xref:System.Diagnostics.Trace.Listeners%2A> reçoivent les messages décrits dans le tableau ci-dessus, mais les actions prises dépendent du type d'écouteur qui reçoit le message. Par exemple, le <xref:System.Diagnostics.DefaultTraceListener> affiche une boîte de dialogue d’assertion lorsqu’il reçoit une notification de `Fail` ou d’échec `Assert`, mais qu’un <xref:System.Diagnostics.TextWriterTraceListener> écrit simplement la sortie dans son flux.  
  
 Vous pouvez générer des résultats personnalisés en implémentant votre propre écouteur. Par exemple, créez un écouteur de la trace personnalisé qui affiche les messages dans une boîte de message ou qui se connecte à une base de données pour ajouter les messages à une table. Tous les écouteurs personnalisés doivent prendre en charge les six méthodes mentionnées ci-dessus. Pour plus d'informations sur la création d'écouteurs définis par le développeur, voir <xref:System.Diagnostics.TraceListener> dans la documentation .NET Framework.  
  
 Les méthodes `Write` et `WriteLine` écrivent toujours le texte que vous spécifiez. `Assert`, `WriteIf`et `WriteLineIf` requièrent un argument booléen qui contrôle si elles écrivent ou non le texte spécifié ; elles écrivent le texte spécifié uniquement si l’expression a la **valeur true** (pour `WriteIf` et `WriteLineIf`) ou **false** (pour `Assert`). La méthode `Fail` écrit toujours le texte spécifié. Pour plus d’informations, consultez [Guide pratique pour ajouter des instructions de suivi au code d’application](how-to-add-trace-statements-to-application-code.md) et la référence .NET Framework.  
  
## <a name="security-concerns"></a>Problèmes de sécurité  
 Si vous ne désactivez pas le traçage et le débogage avant de déployer votre application ASP.NET, celle-ci peut dévoiler des informations exploitables par un programme malveillant. Pour plus d’informations, consultez [Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug](how-to-compile-conditionally-with-trace-and-debug.md), [Compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio) et [Guide pratique pour créer, initialiser et configurer des commutateurs de suivi](how-to-create-initialize-and-configure-trace-switches.md). Vous pouvez également configurer le débogage via IIS (Internet Information Services).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- [Contrats de code](code-contracts.md)
- [Types de projets C#, F# et Visual Basic](/visualstudio/debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types)
- [Guide pratique pour ajouter des instructions de suivi au code d’application](how-to-add-trace-statements-to-application-code.md)
- [Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug](how-to-compile-conditionally-with-trace-and-debug.md)
- [Guide pratique pour créer, initialiser et configurer des commutateurs de suivi](how-to-create-initialize-and-configure-trace-switches.md)
- [Guide pratique pour créer et initialiser des sources de suivi](how-to-create-and-initialize-trace-sources.md)
- [Guide pratique pour utiliser un TraceSource et des filtres avec des écouteurs de suivi](how-to-use-tracesource-and-filters-with-trace-listeners.md)
- [Écouteurs de suivi](trace-listeners.md)
- [Commutateurs de suivi](trace-switches.md)
