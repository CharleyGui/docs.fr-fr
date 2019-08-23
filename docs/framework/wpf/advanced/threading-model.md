---
title: Modèle de thread
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 703fafad283c11e6ee5e6d9c9da3760ea4a36361
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966148"
---
# <a name="threading-model"></a>Modèle de thread
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est conçu pour épargner aux développeurs les difficultés d’utilisation des threads. Par conséquent, la majorité des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] développeurs n’auront pas à écrire une interface qui utilise plus d’un thread. Comme les programmes multithreads sont complexes et difficiles à déboguer, il est préférable de les éviter quand des solutions à thread unique existent.  
  
 Quelle que soit la façon dont l’architecture est bien [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] conçue, aucune infrastructure ne pourra jamais fournir une solution à thread unique pour chaque type de problème. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]est proche, mais il existe toujours des situations où plusieurs threads améliorent [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] la réactivité ou les performances de l’application. Après avoir présenté des informations d’ordre général, ce document explore certaines de ces situations puis se termine par une présentation de certaines informations de bas niveau.  

> [!NOTE]
> Cette rubrique décrit le Threading à l’aide <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> de la méthode pour les appels asynchrones. Vous pouvez également effectuer des appels asynchrones en <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> appelant la méthode, qui <xref:System.Action> prend <xref:System.Func%601> un ou comme paramètre.  La <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> méthode retourne un <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, qui a une <xref:System.Windows.Threading.DispatcherOperation.Task%2A> propriété. Vous pouvez utiliser le `await` mot clé avec le <xref:System.Windows.Threading.DispatcherOperation> ou le associé <xref:System.Threading.Tasks.Task>. Si vous devez attendre <xref:System.Threading.Tasks.Task> de façon synchrone le retourné par un <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, appelez la <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> méthode d’extension.  L' <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> appel de provoque un interblocage. Pour plus d’informations sur l' <xref:System.Threading.Tasks.Task> utilisation d’un pour effectuer des opérations asynchrones, consultez Parallélisme des tâches.  La <xref:System.Windows.Threading.Dispatcher.Invoke%2A> méthode a également des surcharges qui prennent <xref:System.Action> un <xref:System.Func%601> ou comme paramètre.  Vous pouvez utiliser la <xref:System.Windows.Threading.Dispatcher.Invoke%2A> méthode pour effectuer des appels synchrones en passant un délégué <xref:System.Action> , <xref:System.Func%601>ou.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Vue d’ensemble du répartiteur  
 En règle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] générale, les applications démarrent avec deux threads: une pour gérer le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]rendu et une autre pour gérer le. Le thread de rendu s’exécute efficacement en arrière-plan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pendant que le thread reçoit l’entrée, gère les événements, peint l’écran et exécute le code de l’application. La plupart des applications utilisent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] un seul thread, bien que dans certaines situations, il est préférable d’en utiliser plusieurs. Nous traitons de cet aspect plus loin avec un exemple.  
  
 Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread met en file d’attente des éléments de <xref:System.Windows.Threading.Dispatcher>travail à l’intérieur d’un objet appelé. Le <xref:System.Windows.Threading.Dispatcher> sélectionne des éléments de travail en fonction de l'ordre de priorité et exécute chacun d'eux jusqu'à leur achèvement.  Chaque [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread doit avoir au moins un <xref:System.Windows.Threading.Dispatcher>, et chaque <xref:System.Windows.Threading.Dispatcher> thread peut exécuter des éléments de travail dans un seul thread.  
  
 L’astuce pour créer des applications réactives et conviviales est d' <xref:System.Windows.Threading.Dispatcher> optimiser le débit en réduisant la taille des éléments de travail. De cette façon, les éléments ne sont jamais <xref:System.Windows.Threading.Dispatcher> périmés dans la file d’attente de traitement. Tout délai perceptible entre une entrée et sa réponse peut frustrer un utilisateur.  
  
 Comment les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont-elles censées gérer des opérations volumineuses? Que se passe-t-il si votre code implique un grand calcul ou doit interroger une base de données sur un serveur distant ? En règle générale, la réponse consiste à gérer la grande opération dans un thread distinct, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ce qui laisse le thread libre de faire <xref:System.Windows.Threading.Dispatcher> face aux éléments de la file d’attente. Lorsque la grande opération est terminée, elle peut signaler son résultat au thread pour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] l’affichage.  
  
 Historiquement, Windows n' [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] autorise l’accès aux éléments que par le thread qui les a créés. Cela signifie qu’un thread d’arrière-plan chargé des tâches d’exécution longue ne peut pas mettre à jour une zone de texte quand il est terminé. Windows effectue cela pour garantir l’intégrité des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] composants. Une zone de liste pourrait sembler étrange si son contenu était mis à jour par un thread d’arrière-plan pendant la phase de dessin.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a un mécanisme d’exclusion mutuelle intégré qui applique cette coordination. La plupart des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classes dans <xref:System.Windows.Threading.DispatcherObject>dérivent de. Lors de la <xref:System.Windows.Threading.Dispatcher> construction <xref:System.Windows.Threading.DispatcherObject> , un stocke une référence au thread en cours d’exécution. En effet, le <xref:System.Windows.Threading.DispatcherObject> associe au thread qui le crée. Pendant l’exécution du programme <xref:System.Windows.Threading.DispatcherObject> , un peut appeler <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> sa méthode publique. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>examine le <xref:System.Windows.Threading.Dispatcher> associé au thread actuel et le compare à la référence stockée pendant la <xref:System.Windows.Threading.Dispatcher> construction. Si elles ne correspondent pas <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> , lève une exception. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>est destiné à être appelé au début de chaque méthode appartenant à un <xref:System.Windows.Threading.DispatcherObject>.  
  
 Si un seul thread peut modifier le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], comment les threads d’arrière-plan interagissent-ils avec l’utilisateur? Un thread d’arrière-plan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] peut demander au thread d’effectuer une opération en son nom. Pour ce faire, il inscrit un élément <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de travail avec le du thread. La <xref:System.Windows.Threading.Dispatcher> classe fournit deux méthodes pour l’enregistrement des éléments <xref:System.Windows.Threading.Dispatcher.Invoke%2A> de <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>travail: et. Ces deux méthodes planifient un délégué pour l’exécution. <xref:System.Windows.Threading.Dispatcher.Invoke%2A>est un appel synchrone, autrement dit, il ne retourne pas tant [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que le thread n’a pas fini d’exécuter le délégué. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>est asynchrone et est retourné immédiatement.  
  
 <xref:System.Windows.Threading.Dispatcher> Trie les éléments dans sa file d’attente par priorité. Dix niveaux peuvent être spécifiés lors de l’ajout d’un élément à <xref:System.Windows.Threading.Dispatcher> la file d’attente. Ces priorités sont conservées dans <xref:System.Windows.Threading.DispatcherPriority> l’énumération. Vous trouverez des <xref:System.Windows.Threading.DispatcherPriority> informations détaillées sur les niveaux dans [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] la documentation.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Threads en action: Les exemples  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Une application à thread unique avec un calcul de longue durée  
 La plupart des interfaces utilisateur graphiques (GUI) passent une grande partie de leur temps d’inactivité lors de l’attente des événements qui sont générés en réponse aux interactions de l’utilisateur. Avec une programmation minutieuse, cette durée d’inactivité peut être utilisée de façon constructive, sans affecter [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]la réactivité de. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de thread ne permet pas à l’entrée d’interrompre une opération [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] qui se produit dans le thread. Cela signifie que vous devez être certain de revenir à <xref:System.Windows.Threading.Dispatcher> régulièrement pour traiter les événements d’entrée en attente avant qu’ils ne soient obsolètes.  
  
 Prenons l'exemple suivant :  
  
 ![Capture d’écran montrant le Threading des nombres premiers.](./media/threading-model/threading-prime-numbers.png)  
  
 Cette application simple compte à partir de trois de façon croissante, en recherchant les nombres premiers. Lorsque l’utilisateur clique sur le bouton **Démarrer** , la recherche commence. Quand le programme trouve un nombre premier, il met à jour l’interface utilisateur avec sa découverte. À tout moment, l’utilisateur peut arrêter la recherche.  
  
 Bien qu’assez simple, la recherche des nombres premiers peut être illimitée dans le temps, ce qui présente quelques difficultés.  Si nous avons géré l’intégralité de la recherche à l’intérieur du gestionnaire d’événements Click du bouton, nous [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ne donnerions jamais à ce thread la possibilité de gérer d’autres événements. Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] n’est pas en mesure de répondre aux messages d’entrée ou de traitement. Elle ne redessinerait jamais l’interface et ne répondrait jamais aux clics sur le bouton.  
  
 Nous aurions pu effectuer la recherche des nombres premiers dans un thread distinct, mais nous devrions alors faire face à des problèmes de synchronisation. Avec une approche à thread unique, nous pouvons directement mettre à jour le libellé qui indique le plus grand nombre premier trouvé.  
  
 Si nous divisons la tâche de calcul en segments gérables, nous pouvons retourner périodiquement au et <xref:System.Windows.Threading.Dispatcher> traiter les événements. Nous pouvons offrir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la possibilité de redessiner et de traiter l’entrée.  
  
 La meilleure façon de fractionner le temps de traitement entre le calcul et la gestion des événements <xref:System.Windows.Threading.Dispatcher>consiste à gérer le calcul à partir du. À l’aide <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> de la méthode, nous pouvons planifier des vérifications de nombres premiers dans [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] la même file d’attente que celle à partir de laquelle les événements sont dessinés. Dans notre exemple, nous planifions une seule vérification de nombre premier à la fois. Une fois la vérification de nombre premier terminée, nous planifions immédiatement la vérification suivante. Cette vérification se poursuit uniquement après [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] la gestion des événements en attente.  
  
 ![Capture d’écran montrant la file d’attente du répartiteur.](./media/threading-model/threading-dispatcher-queue.png)  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] effectue la vérification orthographique à l’aide de ce mécanisme. La vérification orthographique est effectuée en arrière-plan à l’aide de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] la durée d’inactivité du thread. Regardons ce code.  
  
 L’exemple suivant montre le code XAML qui crée l’interface utilisateur.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 L’exemple suivant montre le code-behind.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 L’exemple suivant montre le gestionnaire d’événements pour <xref:System.Windows.Controls.Button>le.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Outre la mise à jour du texte <xref:System.Windows.Controls.Button>sur le, ce gestionnaire est chargé de planifier la première vérification du nombre premier en ajoutant un <xref:System.Windows.Threading.Dispatcher> délégué à la file d’attente. Quelque temps après que ce gestionnaire d’événements a terminé son <xref:System.Windows.Threading.Dispatcher> travail, le sélectionne ce délégué pour l’exécution.  
  
 Comme nous l’avons mentionné <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> précédemment, <xref:System.Windows.Threading.Dispatcher> est le membre utilisé pour planifier l’exécution d’un délégué. Dans ce cas, nous choisissons <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> la priorité. Le <xref:System.Windows.Threading.Dispatcher> exécute ce délégué uniquement lorsqu’il n’y a pas d’événements importants à traiter. La réactivité de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est plus importante que la vérification des nombres. Nous passons également un nouveau délégué qui représente la routine de vérification des nombres.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Cette méthode vérifie si le nombre impair suivant est un nombre premier. S’il s’agit `bigPrime` <xref:System.Windows.Controls.TextBlock> d’un premier, la méthode met à jour directement pour refléter sa découverte. Nous pouvons procéder ainsi, car le calcul est effectué dans le même thread que celui utilisé pour créer le composant. Si nous avions choisi d’utiliser un thread distinct pour le calcul, nous devrions utiliser un mécanisme de synchronisation plus complexe et exécuter la mise à jour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le thread. Nous montrerons cette situation plus loin.  
  
 Pour obtenir le code source complet de cet exemple, consultez l' [exemple application à thread unique avec calcul de longue durée](https://go.microsoft.com/fwlink/?LinkID=160038) .  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Gestion d’une opération bloquante avec un thread d’arrière-plan  
 La gestion des opérations bloquantes dans une application graphique peuvent être difficile. Nous ne voulons pas appeler des méthodes bloquantes à partir de gestionnaires d’événements, car l’application apparaîtra figée. Nous pouvons utiliser un thread distinct pour gérer ces opérations, mais quand nous avons terminé, nous devons effectuer une synchronisation avec [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] le thread, car nous ne pouvons pas directement modifier l’interface graphique utilisateur à partir de notre thread de travail. Nous pouvons utiliser <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> pour insérer des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] délégués dans <xref:System.Windows.Threading.Dispatcher> le du thread. Finalement, ces délégués seront exécutés avec l’autorisation de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] modifier les éléments.  
  
 Dans cet exemple, nous simulons un appel de procédure distante qui récupère une prévision météorologique. Nous utilisons un thread de travail distinct pour exécuter cet appel et nous planifions une méthode de mise <xref:System.Windows.Threading.Dispatcher> à jour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le du thread lorsque nous aurons terminé.  
  
 ![Capture d’écran montrant l’interface utilisateur météo.](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Voici quelques-uns des détails à noter.  
  
- Création du gestionnaire de bouton  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Quand l’utilisateur clique sur le bouton, nous affichons le dessin de l’horloge et nous commençons son animation. Nous désactivons le bouton. Nous invoquons `FetchWeatherFromServer` la méthode dans un nouveau thread, puis nous retournons, ce <xref:System.Windows.Threading.Dispatcher> qui permet au de traiter les événements pendant que nous attendons la collecte des prévisions météorologiques.  
  
- Récupération de la météo  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Pour simplifier les choses, nous n’ajoutons pas de code pour la mise en réseau dans cet exemple. Au lieu de cela, nous simulons le délai d’accès réseau en plaçant notre nouveau thread en veille pendant quatre secondes. Dans ce temps, le thread [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] d’origine est toujours en cours d’exécution et répond aux événements. Pour illustrer ceci, nous avons laissé une animation en cours d’exécution, et les boutons pour réduire et pour agrandir continuent également de fonctionner.  
  
 Une fois le délai terminé, et que nous avons sélectionné de manière aléatoire nos prévisions météorologiques, il est temps de le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] signaler au thread. Pour ce faire, nous planifions un `UpdateUserInterface` appel à [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le thread à l' <xref:System.Windows.Threading.Dispatcher>aide de ce thread. Nous passons une chaîne décrivant la météo à cet appel de méthode planifié.  
  
- Mise à jour de la[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Quand le <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du thread a le temps, il exécute l’appel planifié à `UpdateUserInterface`. Cette méthode arrête l’animation de l’horloge et choisit une image pour décrire le temps. Il affiche cette image et restaure le bouton de récupération des prévisions météo (« fetch forecast »).  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Plusieurs fenêtres, plusieurs threads  
 Certaines [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications requièrent plusieurs fenêtres de niveau supérieur. Il est tout à fait acceptable pour un<xref:System.Windows.Threading.Dispatcher> thread/une combinaison de gérer plusieurs fenêtres, mais parfois, plusieurs threads font un meilleur travail. Ceci est particulièrement vrai s’il y a un risque que l’une des fenêtres monopolise le thread.  
  
 L’Explorateur Windows fonctionne de cette façon. Chaque nouvelle fenêtre de l’Explorateur appartient au processus d’origine, mais elle est créée sous le contrôle d’un thread indépendant.  
  
 À l’aide [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d’un <xref:System.Windows.Controls.Frame> contrôle, nous pouvons afficher des pages Web. Nous pouvons facilement créer un substitut simple d’Internet Explorer. Nous commençons par une fonctionnalité importante : la possibilité d’ouvrir une nouvelle fenêtre d’explorateur. Quand l’utilisateur clique sur le bouton « new window » (nouvelle fenêtre), nous lançons une copie de notre fenêtre dans un thread distinct. De cette façon, les opérations longues ou bloquantes dans une des fenêtres ne verrouillent pas toutes les autres fenêtres.  
  
 En réalité, le modèle de navigateur web a son propre modèle de thread complexe. Nous l’avons choisi, car la plupart des lecteurs le connaissent probablement bien.  
  
 L’exemple suivant montre le code.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Les segments suivants relatifs à la mise en œuvre des threads dans ce code sont les plus intéressants pour nous dans ce contexte :  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Cette méthode est appelée quand l’utilisateur clique sur le bouton « new window ». Elle crée un nouveau thread et le démarre de façon asynchrone.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Cette méthode est le point de départ pour le nouveau thread. Nous créons une nouvelle fenêtre sous le contrôle de ce thread. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]crée automatiquement un nouveau <xref:System.Windows.Threading.Dispatcher> pour gérer le nouveau thread. Tout ce que nous devons faire pour rendre la fenêtre fonctionnelle est de démarrer <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Détails techniques et difficultés  
  
### <a name="writing-components-using-threading"></a>Écriture de composants avec des threads  
 Le Guide du développeur Microsoft .NET Framework décrit un modèle de la façon dont un composant peut exposer le comportement asynchrone à ses clients (consultez [vue d’ensemble du modèle asynchrone basé sur les événements](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Par exemple, supposons que nous souhaitions `FetchWeatherFromServer` empaqueter la méthode dans un composant réutilisable, qui n’est pas graphique. À la suite du modèle standard Microsoft .NET Framework, cela ressemble à ce qui suit.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync` utiliserait une des techniques décrites précédemment, comme la création d’un thread d’arrière-plan, pour faire le travail de façon asynchrone, sans bloquer le thread appelant.  
  
 L’une des parties les plus importantes de ce modèle est l’appel de la méthode *MethodName* `Completed` sur le thread qui a appelé la méthode *MethodName* `Async` pour commencer. Vous pouvez le faire en [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisant assez facilement, en <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>stockant, mais le composant non graphique ne peut être utilisé que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans les applications, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pas dans les programmes ou ASP.net.  
  
 La <xref:System.Windows.Threading.DispatcherSynchronizationContext> classe répond à ce besoin: considérez-la comme une version <xref:System.Windows.Threading.Dispatcher> simplifiée de qui [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fonctionne également avec d’autres frameworks.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Pompage imbriqué  
 Parfois, il n’est pas possible de verrouiller complètement [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] le thread. Examinons la <xref:System.Windows.MessageBox.Show%2A> méthode de la <xref:System.Windows.MessageBox> classe. <xref:System.Windows.MessageBox.Show%2A>ne retourne pas tant que l’utilisateur n’a pas cliqué sur le bouton OK. Il peut cependant créer une fenêtre qui doit avoir une boucle de messages pour être interactive. Pendant que nous attendons que l’utilisateur clique sur OK, la fenêtre d’application d’origine ne répond pas aux entrées utilisateur. Elle continue cependant de traiter les messages concernant le dessin. La fenêtre d’origine se redessine elle-même quand elle est couverte et découverte.  
  
 ![Capture d’écran montrant un MessageBox avec un bouton OK](./media/threading-model/threading-message-loop.png)  
  
 Un thread doit être chargé de la fenêtre de la boîte de message. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pourrait créer un thread seulement pour la fenêtre de la boîte de message, mais ce thread ne pourrait pas dessiner les éléments désactivés dans la fenêtre d’origine (rappelez-vous de ce qui a été indiqué plus haut sur l’exclusion mutuelle). Au lieu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de cela, utilise un système de traitement des messages imbriqué. La <xref:System.Windows.Threading.Dispatcher> classe comprend une méthode spéciale appelée <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, qui stocke le point d’exécution actuel d’une application, puis commence une nouvelle boucle de message. Lorsque la boucle de messages imbriquée se termine, l’exécution reprend <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> après l’appel d’origine.  
  
 Dans ce cas, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> conserve le contexte du programme lors de l' <xref:System.Windows.MessageBox>appel<xref:System.Windows.MessageBox.Show%2A>à. et il démarre une nouvelle boucle de messages pour repeindre la fenêtre d’arrière-plan et gérer l’entrée dans la fenêtre de la boîte de message. Quand l’utilisateur clique sur OK et efface la fenêtre indépendante, la boucle imbriquée s’arrête et le contrôle reprend après l’appel à <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Événements routés périmés  
 Le système d’événements routés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de notifie les arborescences entières lorsque des événements sont déclenchés.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Lorsque le bouton gauche de la souris est enfoncé sur l' `handler2` ellipse, est exécuté. Une `handler2` fois terminé, l’événement est passé à l' <xref:System.Windows.Controls.Canvas> objet, qui utilise `handler1` pour le traiter. Cela se produit uniquement `handler2` si ne marque pas explicitement l’objet d’événement comme géré.  
  
 Cela peut prendre beaucoup `handler2` de temps pour traiter cet événement. `handler2`peut utiliser <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> pour commencer une boucle de messages imbriquée qui ne retourne pas pendant des heures. Si `handler2` ne marque pas l’événement comme géré lorsque cette boucle de messages est terminée, l’événement est passé en haut de l’arborescence même s’il est très ancien.  
  
### <a name="reentrancy-and-locking"></a>Réentrance et verrouillage  
 Le mécanisme de verrouillage du common language runtime (CLR) ne se comporte pas exactement comme vous pourriez l’imaginer. On peut s’attendre à ce qu’un thread arrête complètement l’opération lors de la demande d’un verrou. En fait, le thread continue à recevoir et à traiter les messages de priorité élevée. Ceci permet d’éviter les blocages et de rendre les interfaces un minimum réactives, mais introduit la possibilité de bogues subtils.  La grande majorité du temps, vous n’avez pas besoin d’en savoir plus sur ce sujet, mais dans de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rares circonstances (généralement impliquant des messages de fenêtre ou des composants com STA), cela peut être utile.  
  
 La plupart des interfaces ne sont pas générées avec la sécurité des threads à l’esprit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , car les développeurs travaillent en partant du principe qu’un n’est jamais accessible par plus d’un thread. Dans ce cas, ce thread unique peut apporter des modifications environnementales à des moments inattendus, ce qui <xref:System.Windows.Threading.DispatcherObject> entraîne des effets négatifs que le mécanisme d’exclusion mutuelle est supposé résoudre. Considérez le pseudocode suivant :  
  
 ![Diagramme qui illustre] la réentrance des threads. (./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")  
  
 La plupart du temps, c’est la bonne chose, mais dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] certains cas, une telle réentrance inattendue peut vraiment causer des problèmes. Ainsi, à certains moments clés, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] appelle <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, qui modifie l’instruction de verrouillage pour que ce thread utilise [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le verrou de réentrance sans réentrance, au lieu du verrou CLR habituel.  
  
 Pourquoi l’équipe CLR a-t-elle choisi ce comportement? Elle devait tenir compte des objets STA COM et du thread de finalisation. Lorsqu’un objet est récupéré par le garbage `Finalize` Collector, sa méthode est exécutée sur le thread finaliseur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dédié, et non sur le thread. Et c’est là que se trouve le problème, car un objet com STA qui [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a été créé sur le thread ne peut être [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] supprimé que sur le thread. Le CLR est l’équivalent d’un <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (dans ce cas, en `SendMessage`utilisant Win32). Toutefois, si [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] le thread est occupé, le thread finaliseur est bloqué et l’objet com STA ne peut pas être supprimé, ce qui entraîne une fuite de mémoire sérieuse. L’équipe CLR a donc fait l’appel difficile pour faire fonctionner les verrous comme c’est le cas.  
  
 La tâche pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est d’éviter la réentrance inattendue sans réintroduire la fuite de mémoire, c’est pourquoi nous ne bloquons pas la réentrance partout.  
  
## <a name="see-also"></a>Voir aussi

- [Application à thread unique avec un exemple de calcul de longue durée](https://go.microsoft.com/fwlink/?LinkID=160038)
