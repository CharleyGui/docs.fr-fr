---
title: Garbage Collection et niveau de performance
description: En savoir plus sur les problèmes liés à l’utilisation de la garbage collection et de la mémoire. Apprenez à réduire l’effet de garbage collection sur vos applications.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: dee5a4b54806bdadc18d759c5df7016da060fd75
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662847"
---
# <a name="garbage-collection-and-performance"></a>Garbage Collection et niveau de performance

Cette rubrique décrit les problèmes liés au garbage collection et à l’utilisation de la mémoire. Elle apporte des solutions aux problèmes concernant les tas managés et explique comment réduire l’effet du garbage collection sur vos applications. Chaque problème contient des liens vers des procédures à suivre pour résoudre le problème.

## <a name="performance-analysis-tools"></a>Outils d'analyse des performances

Les sections suivantes décrivent les outils disponibles pour analyser les problèmes liés à l’utilisation de la mémoire et au garbage collection. Les [procédures](#performance-check-procedures) fournies plus loin dans cette rubrique font référence à ces outils.

### <a name="memory-performance-counters"></a>Compteurs de performance mémoire

Vous pouvez utiliser les compteurs de performances pour collecter des données sur les performances. Pour obtenir des instructions, voir [Génération de profils d'exécution](../../framework/debug-trace-profile/runtime-profiling.md). La catégorie Mémoire CLR .NET des compteurs de performances, telle qu'elle est décrite dans [Compteurs de performances dans le .NET Framework](../../framework/debug-trace-profile/performance-counters.md), fournit des informations sur le garbage collector.

### <a name="debugging-with-sos"></a>Débogage avec l'extension SOS

Vous pouvez utiliser le [Débogueur Windows (WinDbg)](/windows-hardware/drivers/debugger/index) pour inspecter les objets du tas managé.

Pour installer WinDbg, installez les outils de débogage pour Windows à partir de la page [Outils de débogage pour Windows](/windows-hardware/drivers/debugger/debugger-download-tools).

### <a name="garbage-collection-etw-events"></a>Événements ETW de garbage collection

Le suivi d'événements pour Windows (ETW) est un système de suivi qui complète la prise en charge du profilage et du débogage fournie par .NET Framework. À compter de .NET Framework 4, les [événements ETW de garbage collection](../../framework/performance/garbage-collection-etw-events.md) capturent des informations utiles pour l’analyse du tas managé d’un point de vue statistique. Par exemple, l'événement `GCStart_V1`, qui est déclenché quand un garbage collection est sur le point de se produire, fournit les informations suivantes :

- La génération d'objets qui est collectée

- Ce qui a déclenché le garbage collection

- Le type de garbage collection (simultané ou non simultané)

La journalisation des événements ETW est efficace et ne masque pas les problèmes de performances liés au garbage collection. Un processus peut fournir ses propres événements conjointement aux événements ETW. Quand ils sont journalisés, les événements d'application et les événements de garbage collection peuvent être corrélés pour déterminer quand et comment les problèmes de tas se produisent. Par exemple, une application serveur peut fournir des événements au début et à la fin d'une demande client.

### <a name="the-profiling-api"></a>L'API de profilage

Les interfaces de profilage du common language runtime (CLR) fournissent des informations détaillées sur les objets qui ont été affectés pendant le garbage collection. Un profileur peut être informé quand un garbage collection commence et se termine. Il peut fournir des rapports sur les objets du tas managé, y compris une identification des objets au cours de chaque génération. Pour plus d'informations, voir [Vue d'ensemble du profilage](../../framework/unmanaged-api/profiling/profiling-overview.md).

Les profileurs peuvent fournir des informations complètes. Toutefois, les profileurs complexes peuvent potentiellement modifier le comportement d'une application.

### <a name="application-domain-resource-monitoring"></a>Analyse de ressource de domaine d'application

À compter de .NET Framework 4, l’outil ARM (Application Domain Resource Monitoring) permet aux hôtes de superviser l’utilisation du processeur et de la mémoire par domaine d’application. Pour plus d'informations, voir [Analyse de ressource de domaine d'application](app-domain-resource-monitoring.md).

## <a name="troubleshooting-performance-issues"></a>Résolution des problèmes de performances

La première étape consiste à [déterminer si le problème est effectivement lié au garbage collection](#IsGC). Si c'est le cas, cliquez sur l'un des liens suivants pour résoudre le problème.

- [Une exception de mémoire insuffisante est levée](#Issue_OOM)

- [Le processus utilise trop de mémoire](#Issue_TooMuchMemory)

- [Le garbage collector ne récupère pas les objets suffisamment rapidement](#Issue_NotFastEnough)

- [Le tas managé est trop fragmenté](#Issue_Fragmentation)

- [Les pauses du nettoyage de la mémoire sont trop longues](#Issue_LongPauses)

- [La génération 0 est trop volumineuse](#Issue_Gen0)

- [L’utilisation du processeur pendant une garbage collection est trop élevée](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problème : une exception de mémoire insuffisante est levée

Il existe deux cas légitimes pour la levée d'une <xref:System.OutOfMemoryException> managée :

- Une mémoire virtuelle insuffisante.

  Le garbage collector alloue la mémoire depuis le système en segments d'une taille prédéterminée. Si une allocation requiert un segment supplémentaire, mais qu'il n'existe aucun bloc contigu libre dans l'espace de mémoire virtuelle du processus, l'allocation du tas managé échoue.

- Ne pas avoir suffisamment de mémoire physique à allouer.

|Contrôle des performances|
|------------------------|
|[Déterminez si l’exception de mémoire insuffisante est gérée.](#OOMIsManaged)<br /><br /> [Identifiez la quantité de mémoire virtuelle pouvant être réservée.](#GetVM)<br /><br /> [Déterminez si la mémoire physique est suffisante.](#Physical)|

Si vous déterminez que l'exception n'est pas légitime, contactez le support technique Microsoft et préparez-vous à fournir les informations suivantes :

- La pile où a été levée l'exception d'insuffisance de mémoire managée.

- Le fichier complet de vidage mémoire.

- Les données qui prouvent qu'il ne s'agit pas d'une exception de mémoire insuffisante légitime, y compris les données indiquant que ni la mémoire virtuelle ni la mémoire physique ne posent un problème.

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a>Problème : le processus utilise trop de mémoire

On suppose souvent que l’utilisation de la mémoire qui s’affiche sous l’onglet **Performances** du Gestionnaire des tâches Windows peut indiquer à l’utilisateur que trop de mémoire est utilisée. Toutefois, cet affichage concerne le jeu de travail et ne fournit pas d'informations sur l'utilisation de la mémoire virtuelle.

Si vous déterminez que le problème est provoqué par le tas managé, vous devez examiner le tas managé dans le temps pour déterminer les éventuels schémas récurrents.

Si vous déterminez que le problème n'est pas provoqué par le tas managé, vous devez utiliser le débogage natif.

|Contrôle des performances|
|------------------------|
|[Identifiez la quantité de mémoire virtuelle pouvant être réservée.](#GetVM)<br /><br /> [Identifiez la quantité de mémoire validée par le tas managé.](#ManagedHeapCommit)<br /><br /> [Identifiez la quantité de mémoire réservée par le tas managé.](#ManagedHeapReserve)<br /><br /> [Identifiez les objets volumineux dans la génération 2.](#ExamineGen2)<br /><br /> [Identifiez les références aux objets.](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problème : le garbage collector ne récupère pas les objets suffisamment rapidement

Quand les objets semblent ne pas être récupérés comme prévu pour le garbage collection, vous devez déterminer s'il existe des références solides à ces objets.

Vous pouvez également rencontrer ce problème si aucun garbage collection n'a eu lieu pour la génération qui contient un objet mort, ce qui indique que le finaliseur de l'objet mort n'a pas été exécuté. Par exemple, ceci est possible quand vous exécutez une application à thread unique cloisonné (STA) et que le thread qui gère la file d'attente du finaliseur ne peut pas appeler depuis celle-ci.

|Contrôle des performances|
|------------------------|
|[Vérifiez les références aux objets.](#ObjRef)<br /><br /> [Déterminez si un finaliseur a été exécuté.](#Induce)<br /><br /> [Déterminez s’il y a des objets en attente de finalisation.](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problème : le tas managé est trop fragmenté

Le niveau de fragmentation est calculé comme le rapport entre l'espace libre et le total de la mémoire allouée pour la génération. Pour la génération 2, un niveau acceptable de fragmentation ne doit pas dépasser 20 %. Étant donné que la génération 2 peut devenir très volumineuse, le taux de fragmentation est plus important que la valeur absolue.

L'espace libre n'est pas une préoccupation pour la génération 0, car il s'agit de la génération où les nouveaux objets sont alloués.

La fragmentation se produit toujours dans le tas des objets volumineux, car il n'est pas compacté. Les objets libres qui sont adjacents sont réduits naturellement dans un même espace pour répondre aux requêtes d'allocation des objets volumineux.

La fragmentation peut devenir un problème avec la génération 1 et la génération 2. Si ces générations disposent d'une grande quantité d'espace libre après un garbage collection, l'utilisation des objets d'une application peut nécessiter des modifications et vous devrez envisager de réévaluer la durée de vie des objets à long terme.

L'épinglage excessif d'objets peut augmenter la fragmentation. Si la fragmentation est élevée, un trop grand nombre d’objets a pu être épinglé.

Si la fragmentation de la mémoire virtuelle empêche le garbage collector d'ajouter des segments, la cause peut se trouver dans la liste ci-dessous :

- Le chargement et le déchargement fréquents de nombreux petits assemblys.

- Des références trop nombreuses à des objets COM en cas d'interopérabilité avec du code non managé.

- La création d'objets transitoires volumineux, ce qui entraîne l'allocation et la libération fréquentes de segments par le tas des objets volumineux.

  Lors de l'hébergement du CLR, une application peut demander que le garbage collector conserve ses segments. Cela réduit la fréquence des allocations de segments. Pour cela, utilisez la balise STARTUP_HOARD_GC_VM dans l'[énumération STARTUP_FLAGS](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md).

|Contrôle des performances|
|------------------------|
|[Identifiez la quantité d’espace libre dans le tas managé.](#Fragmented)<br /><br /> [Identifiez le nombre d’objets épinglés.](#Pinned)|

Si vous pensez qu'il n'existe aucune cause légitime à la fragmentation, contactez le support technique Microsoft.

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problème : les pauses du garbage collection sont trop longues

Le garbage collection fonctionne en temps réel souple. Les applications doivent donc être en mesure de tolérer quelques pauses. L'un des critères du temps réel souple est que 95 % des opérations doivent se terminer à temps.

Avec le garbage collection simultané, les threads managés sont autorisés à s'exécuter pendant une collection, ce qui signifie que les pauses sont très minimes.

Les garbage collection éphémères (générations 0 et 1) ne durent que quelques millisecondes. La réduction du temps de pause n'est donc généralement pas possible. Toutefois, vous pouvez réduire les temps de pause des collections de génération 2 en modifiant le modèle des demandes d’allocation effectuées par une application.

Une autre méthode plus précise est celle qui consiste à utiliser les [événements ETW de garbage collection](../../framework/performance/garbage-collection-etw-events.md). Vous pouvez rechercher le minutage des collections en ajoutant les différences de timestamp pour une séquence d’événements. L’intégralité de la séquence de collection inclut la suspension du moteur d’exécution, le garbage collection proprement dit et la reprise du moteur d’exécution.

Vous pouvez utiliser les [notifications de garbage collection](notifications.md) pour déterminer si un serveur est sur le point de disposer d’une collection de génération 2, et si la redirection des demandes vers un autre serveur peut atténuer les problèmes liés aux pauses.

|Contrôle des performances|
|------------------------|
|[Identifiez la durée d’un nettoyage de la mémoire.](#TimeInGC)<br /><br /> [Déterminez ce qui a provoqué un nettoyage de la mémoire.](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a>Problème : la génération 0 est trop volumineuse

La génération 0 est susceptible de contenir un plus grand nombre d'objets sur un système 64 bits, notamment si vous utilisez le garbage collection pour serveur au lieu du garbage collection pour station de travail. En effet, le seuil auquel se déclenche un garbage collection de génération 0 est plus élevé dans ces environnements, et les collections de génération 0 peuvent donc être beaucoup plus volumineuses. Les performances sont améliorées quand une application alloue plus de mémoire avant qu'un garbage collection ne soit déclenché.

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problème : l'utilisation du processeur pendant un garbage collection est trop élevée

L'utilisation du processeur est élevée pendant les garbage collection. Si un temps de processus suffisant est consacré à un garbage collection, les collections seront trop fréquent ou la collection durera trop longtemps. Un taux d'allocation d'objets plus élevé sur le tas managé entraîne des garbage collection plus fréquents. La diminution du taux d'allocation réduit la fréquence des garbage collection.

Vous pouvez surveiller les taux d'allocation à l'aide du compteur de performances `Allocated Bytes/second`. Pour plus d'informations, voir [Compteurs de performance dans le .NET Framework](../../framework/debug-trace-profile/performance-counters.md).

La durée d’une collection est principalement un facteur du nombre d’objets qui survivent après l’allocation. Le garbage collector devra parcourir une grande quantité de mémoire si de nombreux objets restent à collecter. Le travail qui consiste à compacter les survivants prend beaucoup de temps. Pour déterminer le nombre d'objets traités au cours d'une collection, définissez un point d'arrêt dans le débogueur à la fin d'un garbage collection pour une génération spécifique.

|Contrôle des performances|
|------------------------|
|[Déterminez si l’utilisation élevée du processeur est provoquée par le nettoyage de la mémoire.](#HighCPU)<br /><br /> [Définissez un point d’arrêt à la fin du nettoyage de la mémoire.](#GenBreak)|

## <a name="troubleshooting-guidelines"></a>Instructions de dépannage

Cette section comporte les instructions que vous devez prendre en compte avant de commencer vos recherches.

### <a name="workstation-or-server-garbage-collection"></a>Garbage collection pour station de travail et pour serveur

Déterminez si vous utilisez le type de garbage collection qui convient. Si votre application utilise plusieurs threads et instances d'objet, utilisez le garbage collection pour serveur au lieu du garbage collection pour station de travail. Le garbage collection pour serveur traite plusieurs threads, tandis que le garbage collection pour station de travail nécessite que plusieurs instances d'une application exécutent leurs propres threads de garbage collection et soient en concurrence pour le temps processeur.

Une application qui possède une faible charge et qui n'effectue que rarement des tâches en arrière-plan, telles qu'un service, peut utiliser le garbage collection pour station de travail en désactivant le garbage collection simultané.

### <a name="when-to-measure-the-managed-heap-size"></a>Quand mesurer la taille du tas managé

Sauf si vous utilisez un profileur, vous devrez établir un modèle cohérent de mesure pour diagnostiquer efficacement les problèmes de performances. Prenez en compte les points suivants pour établir une planification :

- Si vous effectuez la mesure après un garbage collection de génération 2, le tas managé ne contiendra aucun objet mort.

- Si vous effectuez la mesure immédiatement après un garbage collection de génération 0, les objets de génération 1 et 2 n'auront pas encore été collectés.

- Si vous effectuez la mesure immédiatement avant un garbage collection, vous mesurerez autant de l'allocation que possible avant le démarrage du garbage collection.

- Effectuer une mesure pendant un garbage collection pose problème, car l'état des structures de données du garbage collector n'est pas valide pour la traversée et les résultats obtenus peuvent ne pas être complets. C'est la procédure normale.

- Quand utilisez le garbage collection pour station de travail avec le garbage collection simultané, les objets récupérés ne sont pas compactés, donc la taille du tas peut être identique voire supérieure (la fragmentation peut le faire apparaître plus volumineux).

- Le garbage collection simultané sur la génération 2 est différé quand la charge de mémoire physique est trop élevée.

La procédure suivante décrit comment définir un point d'arrêt pour mesurer le tas managé.

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Pour définir un point d'arrêt à la fin du garbage collection

- Dans le débogueur WinDbg, après avoir chargé l’extension SOS, tapez la commande suivante :

  **bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) ’kb’;’g’"**

  où **GcCondemnedGeneration** est défini sur la génération de votre choix. Cette commande requiert des symboles privés.

  Cette commande force un arrêt si **RestartEE** est exécuté après la récupération des objets de génération 2 pour le garbage collection.

  Dans le garbage collection pour serveur, un seul thread appelle **RestartEE**. Ainsi, le point d’arrêt se produit une seule fois pendant un garbage collection de génération 2.

## <a name="performance-check-procedures"></a>Procédures de contrôle des performances

Cette section décrit les procédures suivantes permettant d'isoler la cause des problèmes de performances :

- [Déterminez si le problème est causé par le nettoyage de la mémoire.](#IsGC)

- [Déterminez si l’exception de mémoire insuffisante est gérée.](#OOMIsManaged)

- [Identifiez la quantité de mémoire virtuelle pouvant être réservée.](#GetVM)

- [Déterminez si la mémoire physique est suffisante.](#Physical)

- [Identifiez la quantité de mémoire validée par le tas managé.](#ManagedHeapCommit)

- [Identifiez la quantité de mémoire réservée par le tas managé.](#ManagedHeapReserve)

- [Identifiez les objets volumineux dans la génération 2.](#ExamineGen2)

- [Identifiez les références aux objets.](#ObjRef)

- [Déterminez si un finaliseur a été exécuté.](#Induce)

- [Déterminez s’il y a des objets en attente de finalisation.](#Finalize)

- [Identifiez la quantité d’espace libre dans le tas managé.](#Fragmented)

- [Identifiez le nombre d’objets épinglés.](#Pinned)

- [Identifiez la durée d’un nettoyage de la mémoire.](#TimeInGC)

- [Déterminez ce qui a déclenché le nettoyage de la mémoire.](#Triggered)

- [Déterminez si l’utilisation élevée du processeur est causée par le nettoyage de la mémoire.](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Pour déterminer si le problème est causé par le garbage collection

- Examinez les deux compteurs de performances de mémoire suivants :

  - **% Temps dans le GC**. Affiche le pourcentage de la durée calendaire passé à effectuer un garbage collection après le dernier cycle de garbage collection. Utilisez ce compteur pour déterminer si le garbage collector passe trop de temps à libérer de l'espace dans le tas managé. Si le temps passé au garbage collection est relativement faible, cela peut indiquer un problème de ressources en dehors du tas managé. Ce compteur peut être inexact si le garbage collection simultané ou le garbage collection d’arrière-plan sont impliqués.

  - Nombre **total d’octets validés**. Affiche la quantité de mémoire virtuelle actuellement validée par le garbage collector. Utilisez ce compteur pour déterminer si la mémoire consommée par le garbage collector est trop élevée par rapport à la mémoire totale utilisée par votre application.

  La plupart des compteurs de performances de mémoire sont mis à jour à la fin de chaque garbage collection. Ils peuvent donc ne pas refléter les conditions actuelles à propos desquelles vous voulez obtenir des informations.

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Pour déterminer si l'exception de mémoire insuffisante est managée

1. Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande d’exception d’impression (**pe**) suivante :

    **! PE**

    Si l'exception est managée, <xref:System.OutOfMemoryException> s'affiche comme le type d'exception, comme illustré dans l'exemple suivant.

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. Si la sortie ne spécifie pas d'exception, vous devez déterminer de quel thread provient l'exception de mémoire insuffisante. Tapez la commande suivante dans le débogueur pour afficher tous les threads avec leurs piles d'appels :

    **~\*kbit**

    Le thread avec la pile associée aux appels d'exception est indiqué par l'argument `RaiseTheException`. Il s'agit de l'objet exception managée.

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. Vous pouvez utiliser la commande suivante pour faire un dump des exceptions imbriquées.

    **!pe -nested**

    Si vous ne trouvez pas d'exceptions, l'exception de mémoire insuffisante provient de code non managé.

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Pour déterminer la quantité de mémoire virtuelle pouvant être réservée

- Dans le débogueur WinDbg avec l’extension SOS chargée, tapez la commande suivante pour obtenir la région libre la plus grande :

  **!address -summary**

  La plus grande région libre est affichée comme dans la sortie suivante.

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  Dans cet exemple, la taille de la région libre la plus grande est d'environ 24 000 Ko (3A980 en hexadécimal). Cette région est beaucoup plus petite que ce dont le garbage collector a besoin pour un segment.

  -ou-

- Utilisez la commande **vmstat** :

  **!vmstat**

  La région libre la plus grande correspond à la plus grande valeur de la colonne MAXIMUM, comme illustré dans la sortie suivante.

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Pour déterminer si la mémoire physique est suffisante

1. Démarrez le Gestionnaire des tâches Windows.

2. Sous l’onglet **Performances**, regardez la valeur validée. (Dans Windows 7, regardez **Validation (Ko)** sous **Groupe système**.)

    Si le **Total** est proche de la **Limite**, la mémoire physique devient insuffisante.

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Pour déterminer la quantité de mémoire que le tas managé valide

- Utilisez le compteur de performances de mémoire `# Total committed bytes` pour obtenir le nombre d'octets que le tas managé valide. Le garbage collector valide des parties d'un segment au fur et à mesure des besoins, et non tous en même temps.

  > [!NOTE]
  > N'utilisez pas le compteur de performances `# Bytes in all Heaps`, car il ne représente pas l'utilisation réelle de la mémoire par le tas managé. La taille d'une génération est incluse dans cette valeur et correspond à la taille de son seuil, c'est-à-dire, à la taille qui déclenche un garbage collection si la génération est remplie d'objets. Cette valeur est donc généralement égale à zéro.

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Pour déterminer la quantité de mémoire réservée pour le tas managé

- Utilisez le compteur de performances de mémoire `# Total reserved bytes`.

  Le garbage collector réserve de la mémoire sous forme de segments, et vous pouvez déterminer où démarre un segment à l'aide de la commande **eeheap**.

  > [!IMPORTANT]
  > Même s'il est possible de déterminer la quantité de mémoire que le garbage collector alloue à chaque segment, la taille d'un segment dépend de l'implémentation et est susceptible de changer à tout moment, y compris lors des mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.

- Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :

  **!eeheap -gc**

  Le résultat est le suivant :

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  Les adresses indiquées par "segment" sont les adresses de début des segments.

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a>Pour déterminer les objets volumineux dans la génération 2

- Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :

  **!dumpheap –stat**

  Si le tas managé est volumineux, l’exécution de **dumpheap** peut prendre un certain temps.

  Vous pouvez commencer l'analyse des dernières lignes de la sortie, car elles contiennent les objets qui utilisent le plus d'espace. Par exemple :

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  Le dernier objet répertorié est une chaîne qui occupe le plus d'espace. Vous pouvez examiner votre application pour voir comment vos objets de chaîne peuvent être optimisés. Pour afficher les chaînes dont la taille est comprise entre 150 et 200 octets, tapez la commande suivante :

  **!dumpheap -type System.String -min 150 -max 200**

  Voici un exemple de résultat.

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  L'utilisation d'un entier au lieu d'une chaîne pour un ID peut être plus efficace. Si la même chaîne est répétée des milliers de fois, envisagez la centralisation des chaînes. Pour plus d'informations sur la centralisation des chaînes, voir la rubrique de référence sur la méthode <xref:System.String.Intern%2A?displayProperty=nameWithType>.

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a>Pour déterminer les références aux objets

- Dans le débogueur WinDbg avec l’extension SOS chargée, tapez la commande suivante pour obtenir la liste des références aux objets :

  **!gcroot**

  `-or-`

- Pour déterminer les références à un objet spécifique, incluez l'adresse suivante :

  **!gcroot 1c37b2ac**

  Les racines trouvées sur les piles peuvent être de faux positifs. Pour plus d'informations, utilisez la commande `!help gcroot`.

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  L'exécution de la commande **gcroot** peut prendre beaucoup de temps. Tout objet qui n’est pas récupéré par le garbage collection est un objet dynamique. Cela signifie qu’une racine maintient directement ou indirectement l’objet. **gcroot** doit donc retourner des informations de chemin d’accès à l’objet. Vous devez examiner les graphiques retournés et voir pourquoi ces objets sont encore référencés.

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Pour déterminer si un finaliseur a été exécuté

- Exécutez un programme de test contenant le code suivant :

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  Si le test résout le problème, cela signifie que le garbage collector ne récupérait pas les objets, parce que les finaliseurs de ces objets avaient été interrompus. La méthode <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> permet aux finaliseurs d'effectuer leurs tâches et résout le problème.

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Pour déterminer s'il existe des objets en attente de finalisation

1. Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :

    **!finalizequeue**

    Regardez le nombre d'objets qui sont prêts pour la finalisation. Si le nombre est élevé, vous devez examiner les raisons pour lesquelles ces finaliseurs ne peuvent pas progresser du tout ou pas assez rapidement.

2. Pour obtenir une sortie des threads, tapez la commande suivante :

    **threads -special**

    Cette commande fournit une sortie semblable à la suivante.

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    Le thread finaliseur indique quel finaliseur, est en cours d'exécution, le cas échéant. Quand un thread finaliseur n'exécute pas de finaliseur, il attend qu'un événement lui demande d'effectuer son travail. La plupart du temps, vous verrez le thread finaliseur dans cet état, car il s'exécute avec une THREAD_HIGHEST_PRIORITY et est supposé terminer l'exécution des finaliseurs, le cas échéant, très rapidement.

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Pour déterminer la quantité d'espace libre dans le tas managé

- Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :

  **!dumpheap -type Free -stat**

  Cette commande affiche la taille totale de tous les objets libres sur le tas managé, comme illustré dans l’exemple suivant.

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- Pour déterminer l'espace libre dans la génération 0, tapez la commande suivante pour obtenir des informations sur la consommation de mémoire par génération :

  **!eeheap -gc**

  Cette commande affiche une sortie similaire à la suivante : La dernière ligne indique le segment éphémère.

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- Calculez l'espace utilisé par la génération 0 :

  **? 49e05d04-0x49521f8c**

  Le résultat est le suivant : La génération 0 est d'environ 9 Mo.

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- La commande suivante fait un dump pour l'espace libre dans la plage de la génération 0 :

  **!dumpheap -type Free -stat 0x49521f8c 49e05d04**

  Le résultat est le suivant :

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  Cette sortie indique que la partie du tas consacrée à la génération 0 utilise 9 Mo d'espace pour les objets et dispose de 7 Mo d'espace libre. Cette analyse montre dans quelle mesure la génération 0 contribue à la fragmentation. Cette quantité d'utilisation du tas doit être retirée de la quantité totale, car elle est la cause de la fragmentation par les objets à long terme.

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a>Pour déterminer le nombre d'objets épinglés

- Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :

  **!gchandles**

  Les statistiques affichées incluent le nombre de handles épinglés, comme le montre l'exemple suivant.

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Pour déterminer la durée d'un garbage collection

- Regardez ce qu'affiche le compteur de performances de mémoire `% Time in GC`.

  La valeur est calculée à partir d'un échantillon d'intervalle de temps. Les compteurs sont mis à jour à la fin de chaque garbage collection. L'exemple actuel aura donc la même valeur que l'exemple précédent si aucune collection ne s'est produite pendant l'intervalle.

  La durée de la collection est obtenue en multipliant l'échantillon d'intervalle de temps par la valeur de pourcentage.

  Les données suivantes montrent quatre échantillons d'intervalles de deux secondes, pour une étude de 8 secondes. Les colonnes `Gen0`, `Gen1` et `Gen2` indiquent le nombre de garbage collection qui se sont produits pendant cet intervalle pour cette génération.

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  Ces informations n'affichent pas le moment auquel s'est produit le garbage collection, mais vous pouvez toutefois connaître le nombre de garbage collection qui se sont produits dans un intervalle de temps. Dans le pire des cas, le dixième garbage collection de génération 0 s'est terminé au début du deuxième intervalle et le onzième garbage collection de génération 0 s'est terminé à la fin du cinquième intervalle. Le délai entre la fin du dixième et la fin du onzième garbage collection est d'environ 2 secondes. Le compteur de performances indique 3 %. La durée du onzième garbage collection de génération 0 était donc de (2 secondes * 3 % = 60 ms).

  Cet exemple comprend 5 périodes.

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  Le deuxième garbage collection de génération 2 a démarré pendant le troisième intervalle et s'est terminé au cinquième intervalle. Dans le pire des cas, le dernier garbage collection était pour une collection de génération 0 qui s'est terminée au début du deuxième intervalle et le garbage collection de génération 2 s'est terminé à la fin du cinquième intervalle. Le délai entre la fin du garbage collection de génération 0 et la fin du garbage collection de génération 2 est donc de 4 secondes. Étant donné que le compteur `% Time in GC` affiche 20 %, la durée maximale du garbage collection de génération 2 est de (4 secondes * 20 % = 800 ms).

- Vous pouvez également déterminer la durée d’un garbage collection à l’aide des [événements ETW de garbage collection](../../framework/performance/garbage-collection-etw-events.md) en analysant les informations fournies.

  Par exemple, les données suivantes indiquent une séquence d’événements qui se sont produits pendant un garbage collection non simultané.

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  La suspension des threads managés a pris 26 us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).

  Le garbage collection réel a pris 4,8 ms (`GCEnd_V1` – `GCStart_V1`).

  La reprise des threads managés a pris 21 us (`GCRestartEEEnd` – `GCRestartEEBegin`).

  La sortie suivante fournit un exemple de garbage collection d'arrière-plan et inclut les champs de processus, de thread et d'événement (toutes les données ne sont pas affichées).

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  L'événement `GCStart_V1` à la ligne 42504816 indique qu'il s'agit d'un garbage collection d'arrière-plan, car le dernier champ est `1`. Cela devient le garbage collection numéro 102019.

  L'événement `GCStart` se produit, car un garbage collection éphémère doit être effectué avant de démarrer un garbage collection d'arrière-plan. Cela devient le garbage collection numéro 102020.

  À la ligne 42514170, le garbage collection numéro 102020 prend fin. Les threads managés sont redémarrés à cet endroit. L'opération se termine au thread 4372, qui a déclenché ce garbage collection d'arrière-plan.

  Au thread 4744, une suspension se produit. C'est la seule fois où le garbage collection d'arrière-plan doit suspendre les threads managés. Cette durée est d'environ 99 ms ((63784407-63685394)/1000).

  L'événement `GCEnd` pour le garbage collection d'arrière-plan se trouve à la ligne 89931423. Cela signifie que le garbage collection d'arrière-plan a duré environ 47 secondes ((89931423-42504816)/1000).

  Pendant que les threads managés sont exécutés, vous pouvez voir tous les garbage collection éphémères en cours.

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a>Pour déterminer ce qui a déclenché un garbage collection

- Dans le débogueur WinDbg ou Visual Studio avec l’extension de débogueur SOS chargée, tapez la commande suivante pour afficher tous les threads avec leurs piles d’appels :

  **~\*kbit**

  Cette commande affiche une sortie similaire à la suivante :

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  Si le garbage collection a été provoqué par une notification de mémoire insuffisante du système d'exploitation, la pile des appels sera similaire, à ceci près que le thread sera le thread finaliseur. Le thread finaliseur reçoit une notification asynchrone de mémoire insuffisante et déclenche le garbage collection.

  Si le garbage collection a été provoqué par l'allocation de mémoire, la pile se présente comme ceci :

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  Un programme d'assistance juste-à-temps (`JIT_New*`) appelle `GCHeap::GarbageCollectGeneration`. Si vous déterminez que les garbage collection de génération 2 sont dus à des allocations, vous devez déterminer quels objets sont collectés par les garbage collection de génération 2 et comment les éviter. Autrement dit, vous devez déterminer la différence entre le début et la fin d'un garbage collection de génération 2, ainsi que les objets qui ont provoqué la collection de génération 2.

  Par exemple, tapez la commande suivante dans le débogueur pour afficher le début d’une collection de génération 2 :

  **!dumpheap –stat**

  Exemple de sortie (abrégé pour montrer les objets qui utilisent le plus d'espace) :

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  Répétez la commande à la fin de la génération 2 :

  **!dumpheap –stat**

  Exemple de sortie (abrégé pour montrer les objets qui utilisent le plus d'espace) :

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  Les objets `double[]` ont disparu de la fin de la sortie, ce qui signifie qu'ils ont été collectés. Ces objets représentent environ 70 Mo. Les objets restants n'ont pas beaucoup changé. Ces objets `double[]` étaient donc à l'origine du déclenchement du garbage collection de génération 2. L'étape suivante consiste à déterminer pourquoi les objets `double[]` y sont situés et pourquoi ils sont morts. Vous pouvez demander à un développeur d'où proviennent ces objets ou vous pouvez utiliser la commande **gcroot**.

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Pour déterminer si l’utilisation élevée du processeur est causée par le garbage collection

- Mettez en corrélation la valeur du compteur de performances de mémoire `% Time in GC` avec le temps d'exécution.

  Si la valeur `% Time in GC` connaît un pic en même temps que le temps d'exécution, le garbage collection provoque une utilisation élevée du processeur. Dans le cas contraire, profilez l'application pour trouver où se produit l'utilisation élevée.

## <a name="see-also"></a>Voir aussi

- [Garbage collection](index.md)
