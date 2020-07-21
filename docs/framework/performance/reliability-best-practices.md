---
title: Meilleures pratiques pour la fiabilité
description: Pour plus d’SQL Server, consultez meilleures pratiques en matière de fiabilité dans les applications serveur basées sur un hôte .NET. Empêchez les fuites de ressources ou les mises en route.
ms.date: 03/30/2017
helpviewer_keywords:
- marking locks
- rebooting databases
- denial of service attacks
- back-out code
- SQL Server [.NET Framework], reliability
- synchronization, reliability
- single-threaded COM components
- slow leaks
- suspending threads
- asynchronous exception handling
- leaked resources [.NET Framework]
- unmanaged memory
- memory, reliability
- threading [.NET Framework], reliability
- process-wide domain shared states
- shared states
- SafeHandle class, reliability
- reliability contracts [.NET Framework]
- cleanup operations
- constrained execution regions
- CERs
- finalizers, reliability
- reliability [.NET Framework]
- blocks, reliability
- finally clauses
- cross-application domain shared states
- catch blocks
- identifying locks
- writing reliable code
- impersonation
- GC.KeepAlive method
- managed threading
- locks, reliability
- STA-dependent features
- fibers
ms.assetid: cf624c1f-c160-46a1-bb2b-213587688da7
ms.openlocfilehash: 134b71153f95dffd4525f307d291ce4389e0ce60
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474239"
---
# <a name="reliability-best-practices"></a>Meilleures pratiques pour la fiabilité

Même si les règles de fiabilité suivantes concernent plus spécialement SQL Server, elles peuvent également s’appliquer à n’importe quelle application serveur basée sur l’hôte. Il est extrêmement important d’éviter que les serveurs, tels que les serveurs SQL Server, soient victimes de fuite de ressources ou de panne.  Toutefois, il est impossible de le faire en écrivant du code réécrit pour chaque méthode qui modifie l’état d’un objet.  Le but n’est pas ici d’écrire du code managé totalement fiable et capable de récupérer des erreurs partout où elles se produisent avec du code réécrit.  Cette tâche relèverait pratiquement de l’impossible.  Le Common Language Runtime (CLR) ne peut offrir suffisamment de garanties quant à la possibilité d’écrire du code managé parfait.  Notez qu’à la différence d’ASP.NET, SQL Server utilise un seul processus qui ne peut pas être recyclé sans mettre une base de données hors connexion pendant une durée inacceptable.

Compte tenu de l’insuffisance de garanties offertes et de l’exécution au sein d’un seul processus, la fiabilité est fondée sur la possibilité d’arrêter des threads ou de recycler des domaines d’application chaque fois que nécessaire et de prendre des mesures adéquates assurant l’absence de fuites de ressources de système d’exploitation telles que les handles ou la mémoire.  Même avec cette contrainte de fiabilité plus simple, il existe encore d’autres exigences importantes concernant la fiabilité :

- Il ne doit jamais y avoir de fuite de ressources du système d’exploitation.

- Tous les verrous managés, sous toutes leurs formes, doivent être identifiés pour le CLR.

- L’état partagé entre les domaines d’application ne doit jamais être interrompu pour permettre au recyclage de <xref:System.AppDomain> de se dérouler correctement.

Bien qu’il soit théoriquement possible d’écrire du code managé pour gérer des exceptions <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException> et <xref:System.OutOfMemoryException>, il est pratiquement impossible que les développeurs réussissent à écrire du code aussi robuste dans toute une application.  C’est la raison pour laquelle des exceptions hors plage mettent un terme au thread en cours d’exécution et, si le thread interrompu était en train de modifier l’état partagé (ce qui peut être déterminé par la présence d’un verrou sur le thread), <xref:System.AppDomain> est déchargé.  Quand une méthode qui modifie l’état partagé est arrêtée, l’état est endommagé parce qu’il n’est pas possible d’écrire du code réécrit fiable pour les mises à jour apportées à l’état partagé.

Dans .NET Framework version 2.0, SQL Server est le seul hôte pour lequel la fiabilité est indispensable.  Si votre assembly est exécuté sur SQL Server, vous devez faire en sorte que chaque partie de cet assembly soit fiable, même si des fonctionnalités spécifiques sont désactivées pendant leur exécution dans la base de données.  En effet, le moteur d’analyse du code examine le code au niveau de l’assembly et ne peut pas identifier du code désactivé. Un autre élément à prendre en compte dans la programmation SQL Server est le fait que SQL Server exécute tout dans un seul processus et le recyclage de <xref:System.AppDomain> est utilisé pour nettoyer toutes les ressources telles que la mémoire ou les handles du système d’exploitation.

Vous ne pouvez pas compter sur des finaliseurs, des destructeurs ou des blocs `try/finally` pour du code réécrit, car ils peuvent être interrompus ou ne pas être appelés.

Les exceptions asynchrones peuvent être levées dans des emplacements inattendus, parfois même dans chaque instruction machine : <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException> et <xref:System.OutOfMemoryException>.

Les threads gérés ne sont pas nécessairement des threads Win32 dans SQL ; il peut s’agir de fibres.

La modification sans risque de l’état partagé mutable au niveau du processus ou du domaine d’application est pratiquement impossible et doit donc être évitée dans la mesure du possible.

Les conditions de mémoire insuffisante ne sont pas rares dans SQL Server.

Si les bibliothèques hébergées dans SQL Server ne mettent pas correctement à jour leur état partagé, il est fort probable que le code ne récupère pas tant que la base de données n’a pas été redémarrée.  Dans quelques cas extrêmes, il est également possible que cela provoque l’échec du processus SQL Server, et donc le redémarrage de la base de données.  Le redémarrage de la base de données peut entraîner la mise hors service d’un site web ou affecter les opérations de la société, et donc la disponibilité.  Dans le cas d’une fuite lente des ressources du système d’exploitation, telles que la mémoire ou les handles, il se peut que le serveur ne parvienne plus à allouer des handles, sans possibilité de récupération, ou que ses performances diminuent lentement et finissent par réduire la disponibilité de l’application d’un client.  Ce sont là des scénarios qu’il faut éviter à tout prix.

## <a name="best-practice-rules"></a>Règles relatives aux meilleures pratiques

L’introduction traitait des exceptions que la revue du code managé exécuté sur le serveur devait intercepter afin d’améliorer la stabilité et la fiabilité du framework. Toutes ces vérifications sont généralement conseillées à tous les niveaux, mais sont absolument obligatoires sur le serveur.

Confronté à un blocage ou une contrainte de ressource, SQL Server abandonne un thread ou détruit un <xref:System.AppDomain>.  Quand c’est le cas, seule l’exécution de code réécrit dans une région d’exécution limitée est garantie.

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Utiliser SafeHandle pour éviter les fuites de ressources

Dans le cas d’un déchargement de <xref:System.AppDomain>, il n’est pas certain que des blocs `finally` ou des finaliseurs soient exécutés ; il est donc important d’effectuer une abstraction de l’accès à toutes les ressources du système d’exploitation via la classe <xref:System.Runtime.InteropServices.SafeHandle> au lieu de la classe <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef> ou classes similaires. Cela permet au CLR de suivre et de fermer les handles que vous utilisez même dans le cas de destruction <xref:System.AppDomain>.  <xref:System.Runtime.InteropServices.SafeHandle> utilise un finaliseur critique que le CLR exécute toujours.

Le handle du système d’exploitation est stocké dans le handle sécurisé à partir du moment où il est créé jusqu’au moment où il est libéré.  Il n’existe aucune fenêtre pendant laquelle une <xref:System.Threading.ThreadAbortException> peut se produire et provoquer une fuite du handle.  De plus, l’appel de code non managé effectue un décompte de références du handle, ce qui permet d’effectuer un suivi précis de la durée de vie du handle. Vous évitez ainsi de rencontrer un problème de sécurité liée à une condition de concurrence critique entre `Dispose` et une méthode utilisant le handle.

La plupart des classes qui ont un finaliseur chargé de nettoyer simplement un handle de système d’exploitation n’ont plus besoin du finaliseur. Au lieu de cela, le finaliseur est sur la classe dérivée <xref:System.Runtime.InteropServices.SafeHandle>.

Notez que <xref:System.Runtime.InteropServices.SafeHandle> ne remplace pas <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  La suppression explicite des ressources du système d’exploitation présente encore des avantages concernant le niveau de performance, mais aussi des risques de contention de ressources.  Vous devez simplement savoir que les blocs `finally` qui suppriment explicitement des ressources peuvent ne pas arriver au terme de leur exécution.

<xref:System.Runtime.InteropServices.SafeHandle> vous permet d’implémenter votre propre méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> destinée à libérer le handle, en passant par exemple l’état à une routine de libération du handle du système d’exploitation ou en libérant un ensemble de handles dans une boucle.  Le CLR garantit l’exécution de cette méthode.  Il incombe à l’auteur de l’implémentation de <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> de garantir la libération du handle dans toutes les circonstances. Si ce n’est pas le cas,une fuite du handle se produit, souvent associée à la fuite des ressources natives qui lui sont associées. Ainsi, il est essentiel de structurer des classes dérivées <xref:System.Runtime.InteropServices.SafeHandle> de telle sorte que l’implémentation de <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> ne nécessite pas l’allocation de ressources qui ne seront peut-être pas disponibles au moment de l’appel. Notez que l’appel à des méthodes susceptibles d’échouer dans l’implémentation de <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> est admis pour autant que votre code puisse gérer de tels échecs et achever le contrat pour libérer le handle natif. À des fins de débogage, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> a une valeur de retour de type <xref:System.Boolean> à laquelle il est possible d’affecter la valeur `false` si une erreur grave se produit et empêche la libération de la ressource. Cela active l’Assistant Débogage managé (MDA) de [releaseHandleFailed](../debug-trace-profile/releasehandlefailed-mda.md), s’il est activé, pour vous permettre d’identifier le problème. Il n’affecte le runtime d’aucune autre façon ; la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> n’est plus appelée pour la même ressource et, en conséquence, une fuite du handle se produit.

L’utilisation de <xref:System.Runtime.InteropServices.SafeHandle> n’est pas appropriée dans certains contextes.  Dans la mesure où la méthode <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> peut être exécutée sur un thread finaliseur <xref:System.GC> tous les handles qui doivent être libérés sur un thread particulier ne doivent pas être encapsulés dans <xref:System.Runtime.InteropServices.SafeHandle>.

Les wrappers RCW (Runtime Callable Wrapper) peuvent être nettoyés par le CLR sans code supplémentaire.  Pour le code qui utilise un appel de code non managé et traite un objet COM comme un `IUnknown*` ou un <xref:System.IntPtr>, le code doit être réécrit pour utiliser un RCW.  <xref:System.Runtime.InteropServices.SafeHandle> peut ne pas être adéquat pour ce scénario en raison de la possibilité d’un rappel dans le code managé par une méthode de libération non managée.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Utilisez <xref:System.Runtime.InteropServices.SafeHandle> pour encapsuler des ressources de système d’exploitation. N’utilisez pas <xref:System.Runtime.InteropServices.HandleRef> ou des champs de type <xref:System.IntPtr>.

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>S’assurer que les finaliseurs n’ont pas à s’exécuter pour empêcher la fuite des ressources du système d’exploitation

Vérifiez soigneusement vos finaliseurs pour éviter, même s’ils ne s’exécutent pas, une fuite d’une ressource du système d’exploitation critique.  Contrairement à un déchargement normal de <xref:System.AppDomain> quand l’application s’exécute dans un état stable ou qu’un serveur tel que SQL Server s’arrête, les objets ne sont pas finalisés durant un déchargement inattendu de <xref:System.AppDomain>.  Vérifiez l’absence de fuite de ressources dans le cas d’un déchargement soudain, puisque l’état correct d’une application ne peut plus être garanti, mais qu’il faut préserver l’intégrité du serveur en évitant une fuite des ressources.  Utilisez <xref:System.Runtime.InteropServices.SafeHandle> pour libérer les ressources du système d’exploitation.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Assurez-vous que les clauses finally n’ont pas besoin de s’exécuter pour empêcher la fuite des ressources du système d’exploitation

Comme rien ne garantit que les clauses `finally` puissent s’exécuter en dehors de régions d’exécution limitée, les développeurs de bibliothèque ne peuvent pas compter sur le code d’un bloc `finally` pour libérer des ressources non managées.  L’utilisation de <xref:System.Runtime.InteropServices.SafeHandle> est la solution recommandée.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Utilisez <xref:System.Runtime.InteropServices.SafeHandle> pour nettoyer des ressources de système d’exploitation au lieu de `Finalize`. N’utilisez pas <xref:System.IntPtr>, mais plutôt <xref:System.Runtime.InteropServices.SafeHandle> pour encapsuler des ressources. Si la clause finally doit être exécutée, placez-la dans une région d’exécution limitée.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Tous les verrous doivent traverser le code de verrouillage géré existant

Le CLR doit pouvoir identifier du code placé dans un verrou afin de détruire <xref:System.AppDomain> au lien d’interrompre simplement le thread.  L’abandon du thread peut être dangereux dans la mesure où les données manipulées par le thread peuvent être laissées dans un état incohérent. Ainsi, <xref:System.AppDomain> doit être recyclé dans son intégralité.  L’impossibilité d’identifier un verrou peut se traduire par des interblocages ou des résultats incorrects. Utilisez les méthodes <xref:System.Threading.Thread.BeginCriticalRegion%2A> et <xref:System.Threading.Thread.EndCriticalRegion%2A> pour identifier des régions de verrouillage.  Il s’agit de méthodes statiques sur la classe <xref:System.Threading.Thread> qui s’appliquent uniquement au thread actif, permettant d’éviter qu’un thread modifie le nombre de verrous d’un autre thread.

La notification CLR étant intégrée à <xref:System.Threading.Monitor.Enter%2A> et <xref:System.Threading.Monitor.Exit%2A> leur utilisation est recommandée de même que celle de l’[instruction lock](../../csharp/language-reference/keywords/lock-statement.md), qui utilise ces méthodes.

D’autres mécanismes de verrouillage tels que les verrouillages spinlock et <xref:System.Threading.AutoResetEvent> doivent appeler ces méthodes pour notifier le CLR de l’entrée dans une section critique.  Ces méthodes ne prennent pas de verrous ; elles informent le CLR que le code s’exécute dans une section critique et que l’abandon du thread peut provoquer un état partagé incohérent.  Si vous avez défini votre propre type de verrou, tel qu’une classe <xref:System.Threading.ReaderWriterLock> personnalisée, utilisez ces méthodes de décompte de verrous.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Marquez et identifiez tous les verrous à l’aide de <xref:System.Threading.Thread.BeginCriticalRegion%2A> et de <xref:System.Threading.Thread.EndCriticalRegion%2A>. N’utilisez pas <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A> et <xref:System.Threading.Interlocked.Decrement%2A> dans une boucle.  N’effectuez pas d’appel de code non managé des variantes Win32 de ces méthodes.  N’utilisez pas <xref:System.Threading.Thread.Sleep%2A> dans une boucle.  N’utilisez pas de champs volatils.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Le code de nettoyage doit être dans un bloc finally ou catch, et non après une commande catch

Le code de nettoyage ne doit jamais suivre un bloc `catch` ; il doit se trouver dans un bloc `finally` ou dans le bloc `catch` lui-même. Il s’agit là d’une bonne pratique à respecter. Le choix se porte généralement sur un bloc `finally` dans la mesure où il exécute le même code à la fois au moment de la levée d’une exception et à la fin escomptée du bloc `try`.  Dans le cas où une exception inattendue est levée, par exemple <xref:System.Threading.ThreadAbortException>, le code de nettoyage ne s’exécute pas.  Toutes les ressources non managées que vous nettoyez dans un bloc `finally` doivent idéalement être encapsulées dans un <xref:System.Runtime.InteropServices.SafeHandle> pour éviter des fuites.  Notez que le mot clé `using` C# permet de supprimer efficacement des objets, y compris les handles.

Bien que le recyclage de <xref:System.AppDomain> puisse nettoyer des ressources sur le thread finaliseur, il est néanmoins important de placer le code de nettoyage à l’emplacement adéquat. Notez que si un thread reçoit une exception asynchrone sans détenir de verrou, le CLR tente de terminer le thread lui-même sans devoir recycler <xref:System.AppDomain>.  Un nettoyage précoce des ressources garantit la disponibilité d’un plus grand nombre de ressources et permet de mieux gérer la durée de vie. Si vous ne fermez pas explicitement un handle d’un fichier dans un chemin de code d’erreur quelconque puis attendez que le finaliseur <xref:System.Runtime.InteropServices.SafeHandle> le nettoie, à la prochaine exécution de votre code, il est possible que sa tentative d’accès au même fichier échoue si le finaliseur ne s’est pas encore exécuté.  Pour cette raison, il est important de vérifier que le code de nettoyage existe et fonctionne correctement. Cela permet une récupération plus rapide et propre en cas de défaillance, même si ce n’est pas indispensable à proprement parler.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Le code de nettoyage après le bloc `catch` doit être dans un bloc `finally`. Placez les appels à supprimer dans un bloc finally. Les blocs `catch` doivent se terminer dans une clause throw ou rethrow. Même s’il y a des exceptions, par exemple du code qui détecte s’il est possible d’établir une connexion réseau là où un grand nombre d’exceptions peuvent se produire, tout code exigeant l’interception d’une série d’exceptions dans des circonstances normales doit indiquer si le code doit être testé pour s’assurer de son exécution correcte.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>L’état partagé mutable au niveau du processus entre des domaines d’application doit être éliminé ou utiliser une région d’exécution avec restriction

Comme mentionné dans l’introduction, il peut être très difficile d’écrire du code managé fiable pour surveiller l’état partagé au niveau du processus entre des domaines d’application.  L’état partagé au niveau du processus représente une structure de données quelconque partagée entre des domaines d’application, dans du code Win32, à l’intérieur du CLR ou dans du code managé à l’aide de la communication à distance.  Il est très difficile d’écrire un état partagé mutable correctement dans du code managé et un état partagé statique ne peut être écrit qu’en prenant de grandes précautions.  Si vous avez un état partagé au niveau du processus ou de la machine, cherchez un moyen de l’éliminer ou de le protéger à l’aide d’une région d’exécution limitée.  Notez qu’une bibliothèque avec un état partagé qui n’est pas identifiée et corrigée peut provoquer la défaillance d’un hôte, tel que SQL Server, qui exige un déchargement propre de <xref:System.AppDomain>.

Si le code utilise un objet COM, évitez de partager cet objet COM entre des domaines d’application.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Les verrous ne fonctionnent pas au niveau du processus ou entre des domaines d’application.

Auparavant, on utilisait <xref:System.Threading.Monitor.Enter%2A> et l’[instruction lock](../../csharp/language-reference/keywords/lock-statement.md) pour créer des verrous de processus globaux.  Cela se produit, par exemple, au moment d’un verrouillage sur des classes agiles <xref:System.AppDomain>, telles que des instances de <xref:System.Type> provenant d’assemblys non partagés, des objets <xref:System.Threading.Thread>, des chaînes internées et certaines chaînes partagées entre des domaines d’application à l’aide de la communication à distance.  Ces verrous ne sont plus placés au niveau du processus.  Pour identifier la présence d’un verrou de niveau processus entre domaines d’application, déterminez si le code du verrou utilise une ressource persistante externe, telle qu’un fichier sur le disque ou éventuellement une base de données.

Notez que l’acquisition d’un verrou dans un <xref:System.AppDomain> peut provoquer des problèmes si le code protégé utilise une ressource externe dans la mesure où ce code peut s’exécuter simultanément dans plusieurs domaines d’application.  Cela peut poser un problème au moment de l’écriture dans un fichier journal ou d’une liaison à un socket pour tout le processus.  Ces modifications montrent qu’il n’y a aucun moyen facile, à l’aide du code managé, d’obtenir un verrou au niveau du processus global, autre que celui consistant à utiliser une instance de <xref:System.Threading.Mutex> ou <xref:System.Threading.Semaphore> nommée.  Créez du code qui ne s’exécute pas simultanément dans deux domaines d’application ou utilisez les classes <xref:System.Threading.Mutex> ou <xref:System.Threading.Semaphore>.  Si le code existant ne peut pas être changé, n’utilisez pas un mutex Win32 nommé pour accomplir cette synchronisation. En effet, durant une exécution en mode fibre, vous ne pouvez pas garantir que le même thread de système d’exploitation acquerra et libérera un mutex.  Vous devez utiliser la classe <xref:System.Threading.Mutex> managée, un <xref:System.Threading.ManualResetEvent> nommé, <xref:System.Threading.AutoResetEvent> ou un <xref:System.Threading.Semaphore> pour synchroniser le verrou de code d’une façon reconnue par le CLR au lieu de synchroniser le verrou à l’aide de code non managé.

#### <a name="avoid-locktypeofmytype"></a>Évitez d’utiliser lock(typeof(MyType))

Les objets <xref:System.Type> privés et publics dans les assemblys partagés avec une seule copie du code partagée dans tous les domaines d’application posent également des problèmes.  Pour les assemblys partagés, il n’existe qu’une seule instance de <xref:System.Type> par processus, ce qui signifie que plusieurs domaines d’application partagent la même instance de <xref:System.Type>.  L’acquisition d’un verrou sur une instance de <xref:System.Type> place un verrou qui affecte tout le processus, et pas seulement le <xref:System.AppDomain>.  Si un <xref:System.AppDomain> acquiert un verrou sur un objet <xref:System.Type>, ce thread est subitement interrompu et ne libère pas le verrou.  Ce verrou peut provoquer ensuite l’interblocage d’autres domaines d’application.

Pour acquérir des verrous dans les méthodes statiques, une solution intéressante consiste à ajouter un objet de synchronisation interne statique au code.  Cela peut être initialisé dans le constructeur de classe s’il en existe un, sinon, de la façon suivante :

```csharp
private static Object s_InternalSyncObject;
private static Object InternalSyncObject
{
    get
    {
        if (s_InternalSyncObject == null)
        {
            Object o = new Object();
            Interlocked.CompareExchange(
                ref s_InternalSyncObject, o, null);
        }
        return s_InternalSyncObject;
    }
}
```

Ensuite, quand vous acquérez un verrou, utilisez la propriété `InternalSyncObject` pour obtenir un objet à verrouiller.  Vous n’avez pas besoin d’utiliser la propriété si vous avez initialisé l’objet de synchronisation interne dans votre constructeur de classe.  Le code d’initialisation du verrou à double contrôle doit ressembler à l’exemple suivant :

```csharp
public static MyClass SingletonProperty
{
    get
    {
        if (s_SingletonProperty == null)
        {
            lock(InternalSyncObject)
            {
                // Do not use lock(typeof(MyClass))
                if (s_SingletonProperty == null)
                {
                    MyClass tmp = new MyClass(…);
                    // Do all initialization before publishing
                    s_SingletonProperty = tmp;
                }
            }
        }
        return s_SingletonProperty;
    }
}
```

#### <a name="a-note-about-lockthis"></a>Note relative au verrouillage (this)

L’acquisition d’un verrou sur un objet individuel publiquement accessible est généralement admise.  Toutefois, si l’objet est un objet singleton susceptible de provoquer l’interblocage de l’ensemble d’un sous-système, envisagez d’utiliser également le modèle de conception précité.  Par exemple, un verrou sur l’objet <xref:System.Security.SecurityManager> peut provoquer un interblocage dans le <xref:System.AppDomain> rendant l’ensemble du <xref:System.AppDomain> inutilisable. La bonne pratique consiste à ne pas acquérir de verrou sur un objet publiquement accessible de ce type.  En revanche, l’acquisition d’un verrou sur une collection ou un tableau individuel ne doit en principe pas poser de problème.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

N’acquérez pas de verrous sur des types qui peuvent être utilisés entre domaines d’application ou qui ne possèdent pas une identité forte. N’appelez pas <xref:System.Threading.Monitor.Enter%2A> sur<xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread> ou tout objet dérivant de <xref:System.MarshalByRefObject>.

### <a name="remove-gckeepalive-calls"></a>Supprimez GC. Appels KeepAlive

Une partie importante de code existant n’utilise pas <xref:System.GC.KeepAlive%2A> quand il le devrait ou l’utilise de façon inappropriée.  Après une conversion vers <xref:System.Runtime.InteropServices.SafeHandle>, les classes n’ont pas besoin d’appeler <xref:System.GC.KeepAlive%2A>, en supposant qu’elles n’ont pas de finaliseur, mais qu’elles se fondent sur <xref:System.Runtime.InteropServices.SafeHandle> pour finaliser les handles du système d’exploitation.  Si la conservation d’un appel à <xref:System.GC.KeepAlive%2A> a effectivement un impact négligeable sur les performances, il ne faut pas croire qu’un appel à <xref:System.GC.KeepAlive%2A> est nécessaire ou suffit à résoudre un problème de durée de vie qui n’existe peut-être plus. Le code n’en serait alors que plus difficile à gérer.  Toutefois, durant l’utilisation des wrappers RCW COM Interop, <xref:System.GC.KeepAlive%2A> est encore requis par le code.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Supprimez <xref:System.GC.KeepAlive%2A>.

### <a name="use-the-hostprotection-attribute"></a>Utiliser l’attribut HostProtection

<xref:System.Security.Permissions.HostProtectionAttribute> (HPA) autorise l’utilisation d’actions de sécurité déclarative pour déterminer les exigences de protection de l’hôte, ce qui permet à l’hôte d’empêcher du code, même d’un niveau de confiance totale, d’appeler certaines méthodes qui ne conviennent pas à l’hôte donné, par exemple <xref:System.Environment.Exit%2A> ou <xref:System.Windows.Forms.MessageBox.Show%2A> pour SQL Server.

Cet attribut HPA n’affecte que les applications non managées, telles que SQL Server, qui hébergent le common language runtime et implémentent la protection de l’hôte. Quand elle s’applique, l’action de sécurité crée une demande de liaison sur la base des ressources hôte que la classe ou la méthode expose. Si le code est exécuté dans une application cliente ou sur un serveur sans protection de l’hôte, l’attribut « s’évapore » ; non détecté, il ne peut pas s’appliquer.

> [!IMPORTANT]
> Cet attribut a pour but de permettre de suivre un modèle de programmation spécifique de l’hôte et non d’adopter un comportement de sécurité.  Bien qu’une demande de liaison vérifie la conformité aux exigences en termes de modèle de programmation, <xref:System.Security.Permissions.HostProtectionAttribute> n’est pas une autorisation de sécurité.

Si l’hôte n’a pas d’exigences de ce type, il n’y a pas de demande de liaison.

Cet attribut identifie les éléments suivants :

- Méthodes ou classes qui ne correspondent pas au modèle de programmation hôte, mais sans gravité par ailleurs.

- Méthodes ou classes qui ne correspondent pas au modèle de programmation hôte et pourraient déstabiliser le code utilisateur géré par le serveur.

- Méthodes ou classes qui ne correspondent pas au modèle de programmation hôte et pourraient mener à une déstabilisation du processus serveur lui-même.

> [!NOTE]
> Si vous créez une bibliothèque de classes destinée à être appelée par des applications exécutables dans un environnement protégé par un hôte, vous devez appliquer cet attribut aux membres qui exposent des catégories de ressources <xref:System.Security.Permissions.HostProtectionResource>. Quand des membres de la bibliothèque de classes du .NET Framework ont cet attribut, seul l’appelant immédiat est vérifié.  Votre membre de bibliothèque doit également demander une vérification de son appelant immédiat de la même manière.

Pour plus d’informations sur l’attribut HPA, consultez <xref:System.Security.Permissions.HostProtectionAttribute>.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Pour SQL Server, toutes les méthodes utilisées pour introduire la synchronisation ou le threading doivent être identifiées avec l’attribut HPA. Il s’agit notamment de méthodes qui partagent l’état, qui sont synchronisées ou gèrent des processus externes. Les valeurs <xref:System.Security.Permissions.HostProtectionResource> qui concernent SQL Server sont <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization> et <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Toutefois, toute méthode exposant <xref:System.Security.Permissions.HostProtectionResource> doit être identifiée par un attribut HPA, pas seulement celles utilisant des ressources affectant SQL.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Ne pas bloquer indéfiniment dans du code non managé

Le blocage d’un thread dans du code non managé au lieu du code managé peut provoquer une attaque par déni de service, car le CLR n’est pas en mesure d’interrompre le thread.  Un thread bloqué empêche le CLR de décharger le <xref:System.AppDomain>, ou alors en exécutant des opérations très peu sécurisées.  Le blocage de l’utilisation d’une primitive de synchronisation Windows est un exemple clair d’un point que nous ne pouvons pas autoriser.  Le blocage dans un appel à `ReadFile` sur un socket doit être évité si possible. dans l’idéal, l’API Windows doit fournir un mécanisme pour qu’une opération comme celle-ci expire.

Toute méthode qui effectue des appels dans du code natif doit de préférence utiliser un appel Win32 avec un délai d’attente raisonnable et limité.  Si l’utilisateur est autorisé à spécifier le délai d’attente, il ne doit pas être autorisé à spécifier un délai d’attente infini sans une autorisation de sécurité spécifique.  À titre indicatif, si une méthode se bloque pendant plus de 10 secondes, vous devez utiliser une version qui prend en charge des délais d’attente ou vous avez besoin d’une assistance CLR supplémentaire.

Voici quelques exemples d’API problématiques.  Les canaux (à la fois anonymes et nommés) peuvent être créés avec un délai d’attente ; toutefois, le code doit vérifier qu’il n’appelle jamais `CreateNamedPipe` ni `WaitNamedPipe` avec NMPWAIT_WAIT_FOREVER.  De plus, un blocage inattendu peut survenir même si un délai d’attente est spécifié.  L’appel à `WriteFile` sur un canal anonyme se bloque jusqu’à ce que tous les octets aient été écrits. En d’autres termes, si la mémoire tampon a des données non lues, l’appel à `WriteFile` se bloque tant que le lecteur n’a pas libéré d’espace dans la mémoire tampon du canal.  Les sockets doivent toujours utiliser une API qui applique un mécanisme de délai d’attente.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Un blocage sans délai d’attente dans du code non managé constitue une attaque par déni de service. N’exécutez pas des appels de code non managé à `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects` et `MsgWaitForMultipleObjectsEx`.  N’utilisez pas NMPWAIT_WAIT_FOREVER.

### <a name="identify-any-sta-dependent-features"></a>Identifier les fonctionnalités dépendantes du STA

Identifiez le code qui utilise les threads cloisonnés (STA) de COM.  Les threads cloisonnés sont désactivés dans le processus SQL Server.  Les fonctionnalités qui dépendent de `CoInitialize`, telles que les compteurs de performance ou le Presse-papiers, doivent être désactivées dans SQL Server.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Vérifier que les finaliseurs sont exempts de problèmes de synchronisation

Il est possible qu’il existe plusieurs threads finaliseurs dans les futures versions du .NET Framework, ce qui peut donner lieu à l’exécution simultanée de finaliseurs d’instances différentes du même type.  Ils ne doivent pas être complètement thread-safe ; le récupérateur de mémoire garantit qu’un seul thread à la fois exécute le finaliseur pour une instance d’objet donnée.  Toutefois, les finaliseurs doivent être codés pour éviter des conditions de concurrence critique et des interblocages durant leur exécution simultanée sur différentes instances d’objet.  Pendant l’utilisation d’un état externe, par exemple l’écriture dans un fichier journal, dans un finaliseur, les problèmes de threading doivent être gérés.  Ne comptez pas sur la finalisation pour garantir la cohérence de thread. N’utilisez pas le stockage local des threads, managé ou natif, pour stocker l’état sur le thread finaliseur.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Les finaliseurs ne doivent pas avoir de problèmes de synchronisation. N’utilisez pas un état mutable statique dans un finaliseur.

### <a name="avoid-unmanaged-memory-if-possible"></a>Évitez si possible la mémoire non managée

Il peut y avoir des fuites de mémoire non managée, comme pour un handle de système d’exploitation. Si possible, essayez d’utiliser la mémoire sur la pile à l’aide de [stackalloc](../../csharp/language-reference/operators/stackalloc.md) ou d’un objet managé épinglé (par exemple, avec l’[instruction fixed](../../csharp/language-reference/keywords/fixed-statement.md)) ou un <xref:System.Runtime.InteropServices.GCHandle> utilisant un tableau d’octets (byte[]). <xref:System.GC> finit par nettoyer ceux-ci. Toutefois, si vous devez allouer de la mémoire non managée, envisagez d’utiliser une classe qui dérive de <xref:System.Runtime.InteropServices.SafeHandle> pour inclure l’allocation de mémoire dans un wrapper.

Notez que <xref:System.Runtime.InteropServices.SafeHandle> ne convient pas dans un cas au moins. Pour les appels de méthode COM qui allouent ou libèrent de la mémoire, il est fréquent qu’une DLL alloue de la mémoire via `CoTaskMemAlloc`, puis qu’une autre DLL libère cette mémoire avec `CoTaskMemFree`.  Utiliser <xref:System.Runtime.InteropServices.SafeHandle> dans ces emplacements n’est pas adapté puisqu’il tente alors d’attacher la durée de vie de la mémoire non managée à la durée de vie de <xref:System.Runtime.InteropServices.SafeHandle> au lieu de laisser l’autre DLL contrôler la durée de vie de la mémoire.

### <a name="review-all-uses-of-catchexception"></a>Passer en revue toutes les utilisations de catch (exception)

Les blocs catch qui interceptent toutes les exceptions au lieu d’une exception spécifique interceptent désormais aussi les exceptions asynchrones. Examinez chaque bloc catch(Exception), en recherchant une libération de ressource peu importante ou du code réécrit qui peut être ignoré, ainsi qu’un comportement éventuellement incorrect dans le bloc catch lui-même pour gérer un <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException> ou <xref:System.OutOfMemoryException>.  Notez qu’il est possible que ce code enregistre ou suppose qu’il ne peut consulter que certaines exceptions ou encore que chaque fois qu’une exception se produit, l’échec soit lié à une raison particulière.  Il se peut que ces hypothèses doivent être mises à jour pour inclure <xref:System.Threading.ThreadAbortException>.

Envisagez de changer tous les emplacements qui interceptent toutes les exceptions pour qu’ils n’interceptent plus qu’un type spécifique d’exception dont vous prévoyez la levée, par exemple une exception <xref:System.FormatException> provenant des méthodes de mise en forme de chaînes.  Cela empêche le bloc catch de s’exécuter sur des exceptions inattendues et garantit que le code ne masque pas de bogues en interceptant des exceptions inattendues.  En règle générale, ne gérez jamais une exception dans du code de bibliothèque (du code exigeant que vous interceptiez une exception peut indiquer un défaut de conception dans le code que vous appelez).  Dans certains cas, vous pouvez souhaiter intercepter une exception et lever un type d’exception différent pour fournir plus de données.  Utilisez dans ce cas des exceptions imbriquées, en stockant la vraie cause de l’échec dans la propriété <xref:System.Exception.InnerException%2A> de la nouvelle exception.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Examinez tous les blocs catch dans le code managé qui interceptent tous les objets ou toutes les exceptions.  En C#, cela signifie marquer à la fois `catch` {} et `catch(Exception)` {} .  Envisagez de définir un type d’exception très spécifique ou effectuez une revue du code pour garantir qu’il ne se comporte pas de façon incorrecte s’il intercepte un type d’exception inattendu.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Ne partez pas du principe qu’un thread managé est un thread Win32, car il s’agit d’une fibre

L’utilisation du stockage local des threads managés fonctionne, mais vous ne pourrez peut-être pas utiliser le stockage local des threads non managés ou supposer que le code se réexécutera sur le thread du système d’exploitation actuel. Ne changez pas des paramètres tels que les paramètres régionaux du thread. N’appelez pas `InitializeCriticalSection` ou `CreateMutex` via un appel de code non managé, car ils exigent que le thread du système d’exploitation qui est verrouillé puisse aussi être déverrouillé. Comme cela n’est pas le cas pendant l’utilisation de fibres, des mutex et des sections critiques Win32 ne peuvent pas être utilisés directement dans SQL.  Notez que la classe <xref:System.Threading.Mutex> managée ne gère pas ces problèmes d’affinité de thread.

Vous pouvez utiliser sans risque la plupart des éléments d’état sur un objet <xref:System.Threading.Thread> managé, y compris le stockage local des threads managés et la culture actuelle de l’interface utilisateur du thread. Vous pouvez également utiliser <xref:System.ThreadStaticAttribute>, qui permet uniquement au thread managé actif d’accéder à la valeur d’une variable statique existante (c’est là un autre moyen de procéder à un stockage local de fibres dans le CLR). Pour des raisons liées au modèle de programmation, vous ne pouvez pas changer la culture actuelle d’un thread durant l’exécution dans SQL.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

SQL Server s’exécute en mode fibre ; n’utilisez pas le stockage local des threads. Évitez les appels de code non managé à `TlsAlloc`, `TlsFree`, `TlsGetValue` et `TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>Laissez SQL Server gérer l’emprunt d’identité

Dans la mesure où l’emprunt d’identité fonctionne au niveau du thread et où SQL peut s’exécuter en mode fibre, le code managé ne doit pas emprunter l’identité d’utilisateurs et ne doit pas appeler `RevertToSelf`.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

Laissez SQL Server gérer l’emprunt d’identité. N’utilisez pas `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx` ou `SetThreadToken`.

### <a name="do-not-call-threadsuspend"></a>Ne pas appeler Thread :: suspend

Suspendre un thread peut sembler une opération simple, mais elle peut provoquer des interblocages.  Si un thread qui maintient un verrou est suspendu par un deuxième thread et que ce deuxième thread essaie de prendre le même verrou, un interblocage se produit.  <xref:System.Threading.Thread.Suspend%2A> peut interférer avec la sécurité, le chargement de classe, la communication à distance et la réflexion.

#### <a name="code-analysis-rule"></a>Règle d’analyse du code

N’appelez pas <xref:System.Threading.Thread.Suspend%2A>. Envisagez d’utiliser à la place une vraie primitive de synchronisation, telle que <xref:System.Threading.Semaphore> ou <xref:System.Threading.ManualResetEvent>.

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Protéger les opérations critiques avec des régions d’exécution restreintes et des contrats de fiabilité

Pendant l’exécution d’une opération complexe qui met à jour un état partagé ou qui doit échouer ou réussir pleinement de façon déterministe, vérifiez si elle est protégée par une région d’exécution limitée. Cela garantit l’exécution systématique du code, même dans le cas d’un abandon brusque de thread ou d’un déchargement soudain de <xref:System.AppDomain>.

Une région d’exécution limitée est un bloc `try/finally` particulier, directement précédé par un appel à <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.

Cette action indique au compilateur juste-à-temps de préparer tout le code dans le bloc finally avant d’exécuter le bloc `try`. Cela garantit que le code du bloc finally est généré et s’exécute dans tous les cas. Il n’est pas rare d’avoir un bloc `try` vide dans une région d’exécution limitée. L’utilisation d’une région d’exécution limitée protège des abandons de threads asynchrones et des exceptions de mémoire insuffisante. Consultez <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> pour obtenir une forme de région d’exécution limitée qui gère en plus des dépassements de la capacité de la pile pour du code très profond.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.ConstrainedExecution>
- [Attributs de programmation et de protection des hôtes SQL Server](sql-server-programming-and-host-protection-attributes.md)
