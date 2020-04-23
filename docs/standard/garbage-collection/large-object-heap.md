---
title: Grand tas d’objets (LOH) sur Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: ab9beca58b3d6118bc0f5121b6f5dec71a9f9f36
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102266"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Tas de grands objets sur les systèmes Windows

Le collecteur d’ordures .NET (GC) divise les objets en petits et grands objets. Quand un objet est grand, certains de ses attributs prennent plus d’importance que s’il est petit. Par exemple, le&mdash;compactage qui est, le copier&mdash;en mémoire ailleurs sur le tas peut être coûteux. Pour cette raison, le collecteur d’ordures place de grands objets sur le tas de gros objets (LOH). Cet article traite de ce qui qualifie un objet comme un grand objet, comment de grands objets sont collectés, et quel genre d’implications de performance de grands objets imposent.

> [!IMPORTANT]
> Cet article traite du tas de gros objets dans .NET Framework et .NET Core fonctionnant uniquement sur les systèmes Windows. Elle ne couvre pas le LOH exécuté sur des implémentations de .NET sur d’autres plateformes.

## <a name="how-an-object-ends-up-on-the-loh"></a>Comment un objet se retrouve sur le LOH

Si un objet est supérieur ou égal à 85 000 octets de taille, il est considéré comme un objet de grande taille. Ce chiffre a été déterminé par le réglage des performances. Quand une demande d’allocation d’objet est de 85 000 octets ou plus, le runtime l’alloue sur le tas de grands objets.

Pour comprendre ce que cela signifie, il est utile d’examiner certains principes fondamentaux sur le collecteur d’ordures.

Le collecteur d’ordures est un collectionneur générationnel. Il a trois générations : génération 0, génération 1 et génération 2. La raison de ces 3 générations est que la plupart des objets meurent dans la génération 0 (dans une application optimisée). Par exemple, dans une application serveur, les allocations associées à chaque demande doivent mourir une fois la demande terminée. Les demandes d’allocation en cours passent en génération 1 et y meurent. La génération 1 joue, pour ainsi dire, le rôle de tampon entre les zones d’objets jeunes et les zones d’objets qui vivent déjà depuis un certain temps.

Les petits objets sont toujours alloués dans la génération 0 et, selon leur durée de vie, peuvent être promus dans les générations 1 ou 2. Les grands objets sont toujours alloués dans la génération 2.

Les grands objets appartiennent à la génération 2 parce qu’ils sont nettoyés uniquement lors d’un nettoyage de la génération 2. Quand une génération est nettoyée, ses générations plus jeunes sont également nettoyées. Par exemple, pendant le nettoyage de la mémoire (GC, Garbage Collection) de la génération 1, les générations 1 et 0 sont toutes deux nettoyées. De la même façon, pendant le GC de la génération 2, le tas tout entier est nettoyé. Pour cette raison, un GC de la génération 2 est également appelé *GC complet*. Cet article fait référence au GC de la génération 2 et non au GC complet, mais les termes sont interchangeables.

Les générations fournissent une vue logique du tas du récupérateur de mémoire. Physiquement, les objets vivent dans des segments de tas managés. Un *segment de tas managé* est un bloc de mémoire que le récupérateur de mémoire réserve sur le système d’exploitation en appelant la [fonction VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) pour le compte du code managé. Lorsque le CLR est chargé, le GC alloue deux segments de tas initiaux : l’un pour les petits objets (le tas de petit objet, ou SOH), et l’autre pour les gros objets (le tas de gros objets).

Les demandes d’allocation sont alors traitées en plaçant des objets managés sur ces segments de tas managés. Si l’objet est inférieur à 85 000 octets, il est placé sur un segment SOH, sinon, sur un segment LOH. Les segments sont réservés (en blocs plus petits) à mesure que leur nombre d’objets alloués augmente.
Pour le SOH, les objets qui survivent à un GC sont promus à la génération suivante. Les objets qui survivent à un nettoyage de la génération 0 sont considérés comme des objets de génération 1, et ainsi de suite. Toutefois, les objets qui survivent à la plus vieille génération sont toujours considérés comme des objets de cette génération. En d’autres termes, les survivants de la génération 2 sont des objets de la génération 2 et les survivants du LOH sont des objets du LOH (qui sont nettoyés avec la génération 2).

Le code d’utilisateur peut seulement allouer dans la génération 0 (petits objets) ou le LOH (grands objets). Seul le récupérateur de mémoire peut « allouer » des objets dans la génération 1 (en promouvant les survivants de la génération 0) et la génération 2 (en promouvant les survivants des générations 1 et 2).

Quand un nettoyage de la mémoire est déclenché, le récupérateur de mémoire repère les objets en vie et les compacte. Parce que le compactage coûte cher, le récupérateur de mémoire *balaye* le LOH et dresse une liste des objets morts qui peuvent être réutilisés plus tard pour répondre aux demandes d’allocation des grands objets. Les objets morts adjacents sont transformés en un seul objet libre.

Le .NET Framework (à partir de .NET Framework 4.5.1) et .NET Core intègrent la propriété <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> qui permet aux utilisateurs de spécifier que le LOH doit être compacté au prochain GC bloquant complet. Par la suite, .NET peut décider de compacter le LOH automatiquement. Donc, si vous allouez des grands objets et voulez garantir qu'ils ne bougent pas, vous devez quand même les épingler.

La figure 1 illustre un scénario dans lequel le récupérateur de mémoire forme la génération 1 après le premier GC de la génération 0 où `Obj1` et `Obj3` sont morts, et forme la génération 2 après le premier GC de la génération 1 où `Obj2` et `Obj5` sont morts. Notez que cette figure et les suivantes sont uniquement à titre d’illustration. Elles contiennent très peu d’objets pour mieux montrer ce qui se passe sur le tas. En réalité, un GC implique généralement bien plus d’objets.

![Figure 1 : GC de la génération 0 et GC de la génération 1](media/loh/loh-figure-1.jpg)\
Figure 1 : GC des générations 0 et 1.

La figure 2 montre qu’après un GC de la génération 2 qui a vu que `Obj1` et `Obj2` étaient morts, le récupérateur de mémoire forme un espace libre contigu dans la mémoire qui était auparavant occupée par `Obj1` et `Obj2`, lequel est ensuite utilisé pour répondre à une demande d’allocation concernant `Obj4`. L’espace entre le dernier objet `Obj3` et la fin du segment peut aussi être utilisé pour répondre aux demandes d’allocation.

![Figure 2 : Après un GC de la génération 2](media/loh/loh-figure-2.jpg)\
Figure 2 : Après un GC de la génération 2

Si l’espace libre est insuffisant pour répondre aux demandes d’allocation des grands objets, le récupérateur de mémoire tente d’acquérir d’autres segments du système d’exploitation. En cas d’échec, il déclenche un GC de la génération 2 pour tenter de libérer l’espace.

Pendant un GC de la génération 1 ou 2, le récupérateur de mémoire libère les segments qui n’ont pas d’objet en vie et les rend au système d’exploitation en appelant la [fonction VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree). La réservation de l’espace entre le dernier objet en vie et la fin du segment est annulée (sauf sur le segment éphémère, où vivent les générations 0 et 1, sur lequel le récupérateur de mémoire maintient la réservation pour que votre application puisse l’utiliser immédiatement). Par ailleurs, les espaces libres restent réservés bien qu’ils soient réinitialisés, ce qui signifie que le système d’exploitation n’a pas besoin d’écrire de données dans ces espaces une fois revenus sur le disque.

Comme que le LOH est collecté uniquement pendant le GC de la génération 2, le segment LOH peut seulement être libéré pendant ce GC. La figure 3 illustre un scénario où le récupérateur de mémoire rend un segment (segment 2) au système d’exploitation et annule la réservation d’espace supplémentaire sur les segments restants. S’il doit utiliser l’espace libéré à la fin du segment pour répondre aux demandes d’allocation de grands objets, il réserve de nouveau la mémoire. (Pour obtenir une explication de la réservation/libération, consultez la documentation de [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).

![Figure 3 : LOH après un GC de la génération 2](media/loh/loh-figure-3.jpg)\
Figure 3 : LOH après un GC de la génération 2

## <a name="when-is-a-large-object-collected"></a>Quand un grand objet est-il collecté ?

En général, un GC se produit sous l’une des trois conditions suivantes :

- L’allocation dépasse le seuil des grands objets ou de la génération 0.

  Le seuil est une propriété des générations. Le seuil d’une génération est défini quand le récupérateur de mémoire lui alloue des objets. Quand le seuil est dépassé, un GC est déclenché sur cette génération. Quand vous allouez des petits ou des grands objets, vous consommez les seuils de la génération 0 et du LOH, respectivement. Quand le récupérateur de mémoire alloue des objets dans les générations 1 et 2, il consomme leurs seuils. Ces seuils sont réglés dynamiquement pendant l’exécution du programme.

  C’est le cas par défaut. La plupart des GC se produisent suite à des allocations sur le tas managé.

- La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée.

  Si la méthode <xref:System.GC.Collect?displayProperty=nameWithType> sans paramètre est appelée ou qu’une autre surcharge reçoit <xref:System.GC.MaxGeneration?displayProperty=nameWithType> comme argument, le LOH est nettoyé avec le reste du tas managé.

- Le système est en situation d’insuffisance de mémoire.

  Cela se produit quand le récupérateur de mémoire reçoit une notification de mémoire haute du système d’exploitation. Si le récupérateur de mémoire pense qu’un GC de la génération 2 peut être productif, il le déclenche.

## <a name="loh-performance-implications"></a>Incidences sur le rendement de LOH

Les allocations sur le tas de grands objets impacte les performances des façons suivantes.

- Coût d’allocation.

  Le CLR garantit que la mémoire allouée pour chaque nouvel objet est libérée. Cela signifie que le coût d’allocation d’un grand objet est complètement dominé par la libération de la mémoire (sauf s’il déclenche un GC). S’il faut 2 cycles pour libérer un octet, il faut 170 000 cycles pour libérer le plus petit des grands objets. Pour libérer la mémoire d’un objet de 16 Mo sur une machine de 2 GHz, il faut environ 16 ms. C’est un coût plutôt élevé.

- Coût de nettoyage.

  Comme le LOH et la génération 2 sont nettoyés ensemble, si le seuil de l’un des deux est dépassé, un nettoyage de la génération 2 est déclenché. Si le nettoyage de la génération 2 est déclenché à cause du LOH, la génération 2 n’est pas forcément plus petite après le GC. Si la génération 2 n’a pas beaucoup de données, l’impact est minime. En revanche, si la génération 2 est grande, le nettoyage peut entraîner des problèmes de performances s’il faut déclencher plusieurs GC sur la génération 2. Si de nombreux grands objets sont alloués de façon très temporaire et que vous avez un grand SOH, vous risquez de passer trop de temps sur les GC. Par ailleurs, le coût d’allocation vient s’ajouter si vous continuez d’allouer et de libérer de très grands objets.

- Éléments de tableau avec des types référence.

  Les très grands objets sur le LOH sont généralement des tableaux (il est très rare d’avoir un objet d’instance très grand). Si les éléments d’un tableau ont beaucoup de références, le coût est plus élevé. Si l’élément n’a aucune référence, le récupérateur de mémoire n’a pas besoin de traiter le tableau. Par exemple, si vous utilisez un tableau pour stocker des nœuds dans une arborescence binaire, vous pouvez l’implémenter en référençant les nœuds droit et gauche d’un nœud comme étant les nœuds eux-mêmes :

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Si `num_nodes` est grand, le récupérateur de mémoire doit traiter au moins deux références par élément. Une autre méthode est de stocker l’index des nœuds droit et gauche :

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Au lieu de référencer les données du nœud gauche comme `left.d`, vous les référencez comme `binary_tr[left_index].d`. Ainsi, le récupérateur de mémoire n’a pas besoin d’examiner les références des nœuds gauche et droit.

Des trois facteurs, les deux premiers ont généralement plus d’impact que le troisième. Pour cette raison, nous vous recommandons d’allouer un pool de grands objets que vous réutilisez au lieu d’allouer des objets temporaires.

## <a name="collect-performance-data-for-the-loh"></a>Recueillir des données sur le rendement pour le LOH

Avant de collecter des données de performances pour une zone spécifique, vous devez déjà avoir effectué les étapes suivantes :

1. Rechercher les raisons d’examiner cette zone.

2. Examiner toutes les autres zones connues sans trouver ce qui pourrait expliquer le problème de performances rencontré.

Consultez le blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) (Comprendre le problème avant d’essayer de chercher une solution) pour plus d’informations sur les principes fondamentaux de la mémoire et du processeur.

Vous pouvez utiliser les outils suivants pour collecter des données sur les performances du LOH :

- [Compteurs de performance pour la mémoire CRL .NET](#net-clr-memory-performance-counters)

- [Événements ETW](#etw-events)

- [Débogueur](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Compteurs de performances pour la mémoire CRL .NET

Ces compteurs de performances sont une bonne première étape pour rechercher les problèmes de performances (même si nous vous recommandons d’utiliser les [événements ETW](#etw-events)). Vous configurez le moniteur de performances en ajoutant les compteurs souhaités, comme le montre la Figure 4. Ceux qui sont pertinents pour le LOH sont les suivants :

- **Gen 2 Collections**

   Affiche le nombre d’occurrences de GC de la génération 2 depuis le démarrage du processus. Ce compteur est incrémenté à la fin de chaque nettoyage de la génération 2 (aussi appelé nettoyage complet de la mémoire). Ce compteur affiche la dernière valeur observée.

- **Taille du tas d’objets volumineux**

   Affiche la taille actuelle du LOH en octets (y compris l’espace libre). Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation.

En général, vous surveillez les compteurs de performances par le biais du moniteur de performances (PerfMon.exe). Utilisez « Ajouter des compteurs » pour ajouter le compteur de votre choix pour les processus qui vous intéressent. Vous pouvez enregistrer les données des compteurs de performances dans un fichier journal, comme illustré dans la figure 4 :

![Capture d’écran qui montre l’ajout de compteurs de performance.](media/large-object-heap/add-performance-counter.png)
Figure 4 : LOH après un GC de la génération 2

Les compteurs de performances peuvent également être interrogés par programmation. Beaucoup d’utilisateurs les collectent de cette façon dans le cadre de leur processus de test normal. S’ils repèrent des compteurs avec des valeurs anormales, ils utilisent d’autres moyens d’obtenir des données plus détaillées pour les aider dans leurs recherches.

> [!NOTE]
> Nous vous recommandons d’utiliser les événements ETW au lieu des compteurs de performances, car ETW fournit des informations plus détaillées.

### <a name="etw-events"></a>Événements ETW

Le récupérateur de mémoire fournit un riche ensemble d’événements ETW pour vous aider à comprendre ce que fait le tas et pourquoi. Les billets de blog suivants décrivent comment collecter et comprendre les événements GC avec ETW :

- [Événements GC ETW - 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [Événements ETW de GC - 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [Événements ETW de GC - 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [Événements ETW de GC - 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Pour identifier le nombre excessif de GC de la génération 2 dus à des allocations de LOH temporaires, observez la colonne Raison du déclencheur pour les GC. Pour un test simple qui alloue uniquement des grands objets temporaires, vous pouvez collecter des informations sur les événements ETW avec la ligne de commande [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) suivante :

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Le résultat ressemble à ceci :

![Capture d’écran montrant les événements ETW dans PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)
Figure 5 : Événements ETW affichés à l’aide de PerfView

Comme vous pouvez le voir, tous les GC sont effectués sur la génération 2 et ils sont déclenchés par AllocLarge, ce qui signifie que c’est l’allocation d’un grand objet qui a déclenché ce GC. Nous savons que ces allocations sont temporaires parce que la colonne **% de taux de survie LOH** indique 1 %.

Vous pouvez collecter d’autres événements ETW qui vous indiquent qui a alloué ces grands objets. La ligne de commande suivante :

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

collecte un événement AllocationTick qui est déclenché toutes les 100 000 allocations environ. En d’autres termes, un événement est déclenché chaque fois qu’un grand objet est alloué. Vous pouvez alors examiner une des vues d’allocation de tas du récupérateur de mémoire qui indique les pile d’appels qui ont alloué des grands objets :

![Capture d’écran montrant une vue du tas garbage collector.](media/large-object-heap/garbage-collector-heap.png)
Figure 6 : Une vue d’allocation de tas du récupérateur de mémoire

Comme vous pouvez le voir, il s’agit d’un test très simple qui alloue simplement de grands objets à partir de sa méthode `Main`.

### <a name="a-debugger"></a>Débogueur

Si tout ce que vous avez est un vidage de mémoire et que vous devez examiner les objets qui se trouvent sur le LOH, vous pouvez utiliser [l’extension de débogueur SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) fournie par .NET.

> [!NOTE]
> Les commandes de débogage indiquées dans cette section sont applicables aux [débogueurs Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Le code suivant illustre un exemple de sortie de l’analyse du LOH :

```console
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

La taille du tas LOH est (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 octets. Entre les adresses 023e1000 et 033db630, 8 008 736 octets sont occupés par un tableau d’objets <xref:System.Object?displayProperty=nameWithType>, 6 663 696 octets sont occupés par un tableau d’objets <xref:System.Byte?displayProperty=nameWithType> et 2 081 792 octets sont occupés par de l’espace libre.

Parfois, le débogueur montre que la taille totale du LOH est inférieure à 85 000 octets. C’est parce que le runtime lui-même utilise le LOH pour allouer des objets dont la taille est inférieure à celle d’un grand objet.

Comme le LOH n’est pas compacté, il est parfois perçu comme la source de la fragmentation. Une fragmentation peut désigner :

- La fragmentation du tas managé, indiquée par la quantité d’espace libre entre les objets managés. Dans SoS, la commande `!dumpheap –type Free` affiche la quantité d’espace libre entre les objets managés.

- La fragmentation de l’espace d’adressage de mémoire virtuelle, qui est la mémoire marquée comme `MEM_FREE`. Vous pouvez l’obtenir à l’aide de diverses commandes de débogueur dans windbg.

   L’exemple suivant montre une fragmentation dans l’espace de mémoire virtuelle :

   ```console
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

Souvent, la fragmentation de mémoire virtuelle est causée par des grands objets temporaires qui obligent le récupérateur de mémoire à fréquemment acquérir de nouveaux segments de tas managé du système d’exploitation et lui en rendre des vides.

Pour vérifier si le LOH provoque une fragmentation de mémoire virtuelle, vous pouvez définir un point d’arrêt sur [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) et [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) et voir qui les appelle. Par exemple, pour voir qui a essayé d’allouer des blocs de mémoire virtuelle de système d’exploitation supérieurs à 8 Mo, vous pouvez définir un point d’arrêt de la façon suivante :

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

Cette commande entre dans le débbugger et montre la pile d’appel que si [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) est appelé avec une taille d’allocation supérieure à 8 Mo (0x800000).

CLR 2.0 a ajouté une fonctionnalité appelée *VM Hoarding* (Réserve de mémoire virtuelle) qui peut être utile dans les scénarios où des segments (y compris ceux des tas de petits et grands objets) sont fréquemment acquis et libérés. Pour utiliser la fonctionnalité VM Hoarding, vous spécifiez un indicateur de démarrage appelé `STARTUP_HOARD_GC_VM` via l’API d’hébergement. Au lieu de renvoyer des segments vides au système d’exploitation, le CLR annule la réservation de mémoire sur ces segments et les met sur liste d’attente. (Notez que le CLR ne le fait pas pour les segments qui sont trop grands.) Le CLR utilise plus tard ces segments pour satisfaire les nouvelles demandes de segment. La prochaine fois que votre application a besoin d’un nouveau segment, le CLR en utilise un de cette liste d’attente, s’il est assez grand.

La thésaurisation VM est également utile pour les applications qui veulent conserver les segments qu’ils ont déjà acquis, tels que certaines applications serveur qui sont les applications dominantes en cours d’exécution sur le système, pour éviter les exceptions hors mémoire.

Nous vous recommandons vivement de tester soigneusement votre application quand vous utilisez cette fonctionnalité, pour vérifier qu’elle utilise la mémoire de façon suffisamment stable.
