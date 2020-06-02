---
title: Notions de base du garbage collection
description: Découvrez comment fonctionne le récupérateur de mémoire et comment le configurer pour optimiser ses performances.
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: 98dee04593ea26bbbc3079f5da98d8106a373168
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286065"
---
# <a name="fundamentals-of-garbage-collection"></a>Notions de base du garbage collection

Dans le common language runtime (CLR), le garbage collector (GC) sert de gestionnaire de mémoire automatique. Le garbage collector gère l’allocation et la libération de mémoire pour une application. Pour les développeurs qui utilisent du code managé, cela signifie que vous n’avez pas besoin d’écrire du code pour effectuer des tâches de gestion de la mémoire. La gestion automatique de la mémoire permet d’éliminer les problèmes courants, tels que l’oubli de libérer un objet et de provoquer une fuite de mémoire ou une tentative d’accès à la mémoire pour un objet qui a déjà été libéré.

Cet article décrit les concepts fondamentaux de garbage collection.

## <a name="benefits"></a>Avantages

Le garbage collector offre les avantages suivants :

- Évite aux développeurs d’avoir à libérer manuellement de la mémoire.

- Il alloue efficacement les objets sur le tas managé.

- Il libère les objets qui ne sont plus utilisés, efface leur mémoire et garde la mémoire disponible pour les futures allocations. Les objets managés obtiennent automatiquement un contenu propre au démarrage, de sorte que leurs constructeurs n’ont pas à initialiser chaque champ de données.

- Il sécurise la mémoire en s'assurant qu'un objet ne peut pas utiliser le contenu d'un autre objet.

## <a name="fundamentals-of-memory"></a>Notions de base de la mémoire

La liste suivante résume les concepts importants de la mémoire CLR.

- Chaque processus possède son propre espace d'adressage virtuel séparé. Tous les processus sur le même ordinateur partagent la même mémoire physique et le même fichier d’échange, le cas échéant.

- Par défaut, sur les ordinateurs 32 bits, chaque processus a un espace d'adressage virtuel en mode utilisateur de 2 Go.

- En tant que développeur d'applications, vous travaillez uniquement avec l'espace d'adressage virtuel et ne gérez jamais directement la mémoire physique. Le garbage collector alloue et libère la mémoire virtuelle pour vous sur le tas managé.

  Si vous écrivez du code natif, vous utilisez des fonctions Windows pour travailler avec l’espace d’adressage virtuel. Ces fonctions allouent et libèrent la mémoire virtuelle pour vous sur les tas natifs.

- La mémoire virtuelle peut être dans trois états :

  | État | Description |
  |---------|---------|
  | Gratuit | Il n'existe aucune référence au bloc de mémoire et celui-ci est disponible pour allocation. |
  | Réservé | Le bloc de mémoire est disponible pour votre utilisation et ne peut pas être utilisé pour une autre demande d'allocation. Toutefois, vous ne pouvez pas stocker de données dans ce bloc de mémoire tant qu'il n'est pas validé. |
  | Committed | Le bloc de mémoire est assigné au stockage physique. |

- L'espace d'adressage virtuel peut être fragmenté. Cela signifie qu'il existe des blocs libres, également appelés trous, dans l'espace d'adressage. Lorsqu'une allocation de mémoire virtuelle est demandée, le gestionnaire de mémoire virtuelle doit rechercher un bloc unique libre suffisamment grand pour satisfaire la demande d'allocation. Même si vous disposez de 2 Go d’espace libre, une allocation qui requiert 2 Go échoue, sauf si tout cet espace libre se trouve dans un bloc d’adresses unique.

- Vous pouvez manquer de mémoire s’il n’y a pas suffisamment d’espace d’adressage virtuel à réserver ou d’espace physique à valider.

  Le fichier d’échange est utilisé même si la sollicitation de la mémoire physique (c’est-à-dire, la demande de mémoire physique) est faible. La première fois que la sollicitation de la mémoire physique est élevée, le système d’exploitation doit libérer de l’espace dans la mémoire physique pour stocker les données, et il sauvegarde certaines des données qui se trouvent dans la mémoire physique dans le fichier d’échange. Ces données ne sont pas paginées tant qu’elles ne sont pas nécessaires, il est donc possible de rencontrer la pagination dans les situations où la sollicitation de la mémoire physique est faible.
  
### <a name="memory-allocation"></a>Allocation de mémoire

Lorsque vous initialisez un nouveau processus, le runtime réserve une région d'espace d'adressage contigu pour le processus. Cet espace d'adressage est appelé le tas managé. Le tas managé garde un pointeur vers l'adresse qui sera allouée au nouvel objet du tas. À l’origine, ce pointeur indique l’adresse de base du tas managé. Tous les types référence sont alloués sur le tas managé. Lorsqu’une application crée le premier type référence, la mémoire est allouée pour le type à l’adresse de base du tas managé. Lorsque l'application crée l'objet suivant, le « garbage collector » lui alloue de la mémoire dans l'espace d'adressage qui suit immédiatement le premier objet. Aussi longtemps que de l'espace d'adressage est disponible, le « garbage collector » continue à allouer de l'espace pour de nouveaux objets selon la même procédure.

L'allocation de mémoire à partir du tas managé est plus rapide que l'allocation de mémoire non managée. Étant donné que le runtime alloue de la mémoire pour un objet en ajoutant une valeur à un pointeur, il est presque aussi rapide que d’allouer de la mémoire à partir de la pile. En outre, étant donné que les nouveaux objets qui sont alloués consécutivement sont stockés de façon contiguë dans le tas managé, une application peut accéder rapidement aux objets.

### <a name="memory-release"></a>Mise en mémoire

Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées. Lorsque le « garbage collector » effectue une opération garbage collection, il libère la mémoire pour les objets qui ne sont plus utilisées par l'application. Il détermine les objets qui ne sont plus utilisés en examinant les *racines*de l’application. Les racines de l’application comprennent des champs statiques, des variables et des paramètres locaux sur la pile d’un thread et des Registres du processeur. Chaque racine fait référence à un objet du tas managé ou, à défaut, a la valeur Null. Le Garbage collector a accès à la liste des racines actives entretenues par le compilateur juste-à-temps (JIT) et le runtime. À l’aide de cette liste, le garbage collector crée un graphique qui contient tous les objets accessibles à partir des racines.

Les objets non compris dans le graphique ne sont pas accessibles à partir des racines de l'application. Le garbage collector considère que les objets inaccessibles sont nettoyés et libère la mémoire qui leur est allouée. Au cours d'une opération garbage collection, le « garbage collector » examine le tas managé pour y détecter les blocs de mémoire occupés par des objets inaccessibles. Chaque fois qu'il détecte un objet inaccessible, il utilise une fonction de copie de mémoire pour compacter les objets accessibles en mémoire et libérer les blocs d'espaces d'adressage alloués aux objets inaccessibles. Lorsque la mémoire allouée aux objets accessibles a été réduite, le « garbage collector » procède aux corrections de pointeurs nécessaires pour que les racines des applications pointent vers les nouveaux emplacements des objets. Il positionne aussi le pointeur du tas managé après le dernier objet accessible.

La mémoire est compactée uniquement si une collection Découvre un nombre significatif d’objets inaccessibles. Si tous les objets du tas managé survivent à une collection, il n'est pas nécessaire de procéder à un compactage de la mémoire.

Pour améliorer les performances, le runtime alloue de la mémoire pour les objets de grandes dimensions dans un tas séparé. Le « garbage collector » libère automatiquement la mémoire des objets de grande dimension. Toutefois, pour éviter de déplacer des objets volumineux en mémoire, cette mémoire n’est généralement pas compactée.

## <a name="conditions-for-a-garbage-collection"></a>Conditions pour une opération garbage collection

Le garbage collection se produit lorsque l'une des conditions suivantes est vraie :

- Le système possède peu de mémoire physique. Cela est détecté par la notification de mémoire insuffisante du système d’exploitation ou la mémoire insuffisante, comme indiqué par l’hôte.

- La mémoire utilisée par les objets alloués sur le tas managé dépasse un seuil acceptable. Ce seuil est continuellement ajusté à mesure que le processus s'exécute.

- La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée. Dans presque tous les cas, il n’est pas nécessaire d’appeler cette méthode, car le garbage collector s’exécute en continu. Cette méthode est principalement utilisée pour les situations uniques et les tests.

## <a name="the-managed-heap"></a>Tas managé

Une fois que le garbage collector est initialisé par le CLR, il alloue un segment de mémoire pour stocker et gérer des objets. Cette mémoire est appelée tas managé, par opposition à un tas natif dans le système d'exploitation.

Il existe un tas managé pour chaque processus managé. Tous les threads du processus allouent de la mémoire pour les objets sur le même tas.

Pour réserver de la mémoire, le garbage collector appelle la fonction [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) de Windows et réserve un segment de mémoire à la fois pour les applications managées. Le garbage collector réserve également des segments, si nécessaire, et libère des segments dans le système d’exploitation (après avoir effacé leurs objets) en appelant la fonction [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) de Windows.

> [!IMPORTANT]
> La taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris les mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.

Moins il y a d'objets alloués sur le tas, moins le garbage collector a à faire. Lorsque vous allouez des objets, n’utilisez pas de valeurs arrondies qui dépassent vos besoins, par exemple l’allocation d’un tableau de 32 octets lorsque vous n’avez besoin que de 15 octets.

Lorsqu’un garbage collection est déclenché, le garbage collector récupère la mémoire occupée par les objets morts. Le processus de libération compacte les objets vivants afin qu'ils soient déplacés ensemble, et l'espace inutilisé est supprimé, ce qui entraîne la diminution du tas. Cela garantit que les objets alloués ensemble restent ensemble sur le tas managé pour conserver leur localité.

Le déroulement (fréquence et durée) des garbage collection est le résultat du volume des allocations et de la quantité de mémoire restante sur le tas managé.

Le tas peut être considéré comme l’accumulation de deux tas : le [tas de grands objets](large-object-heap.md) et le tas de petits objets. Le tas d’objets volumineux contient des objets de 85 000 octets et plus grands, qui sont généralement des tableaux. Il est rare qu’un objet d’instance soit extrêmement volumineux.

> [!TIP]
> Vous pouvez [configurer la taille de seuil](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pour les objets à atteindre sur le tas d’objets volumineux.

## <a name="generations"></a>Générations

L’algorithme GC est basé sur plusieurs considérations :

- Il est plus rapide de compacter la mémoire pour une partie du tas managé que pour l’intégralité du tas managé.
- Les objets plus récents ont des durées de vie plus courtes et les objets plus anciens ont des durées de vie plus longues.
- Les objets les plus récents ont tendance à être liés les uns aux autres et à être accessibles à l’application en même temps.

Le garbage collection se produit principalement avec la récupération d’objets éphémères. Pour optimiser les performances du garbage collector, le tas managé est divisé en trois générations, 0, 1 et 2. il peut donc gérer séparément les objets à durée de vie et à courte durée de vie. Le garbage collector stocke les nouveaux objets dans la génération 0. Les objets qui sont créés à un stade précoce de la durée de vie de l'application et qui survivent aux collectes sont promus et stockés dans les générations 1 et 2. Étant donné qu’il est plus rapide de compacter une partie du tas managé que le tas entier, ce schéma permet au garbage collector de libérer la mémoire dans une génération spécifique plutôt que de libérer la mémoire pour l’intégralité du tas managé chaque fois qu’il effectue une collection.

- **Génération 0**. Il s'agit de la génération la plus jeune, qui contient des objets éphémères. Un exemple d'objet éphémère est une variable temporaire. Le garbage collection a le plus souvent lieu dans cette génération.

  Les objets alloués récemment forment une nouvelle génération d’objets et sont implicitement des collections de génération 0. Toutefois, s’il s’agit d’objets volumineux, ils sont placés sur le tas d’objets volumineux (LOH), parfois appelé *génération 3*. La génération 3 est une génération physique qui est collectée logiquement dans le cadre de la génération 2.

  La plupart des objets sont récupérés pour garbage collection dans la génération 0 et ne survivent pas à la génération suivante.
  
  Si une application tente de créer un nouvel objet lorsque la génération 0 est complète, le garbage collector effectue une collection pour tenter de libérer de l’espace d’adressage pour l’objet. Le « garbage collector » commence par examiner les objets de la génération 0 plutôt que tous les objets du tas managé. Une collection de génération 0 récupère souvent suffisamment de mémoire pour permettre à l’application de continuer à créer des objets.

- **Génération 1**. Cette génération contient des objets éphémères et sert de tampon entre objets éphémères et objets durables.

  Une fois que le « garbage collector » effectue une opération garbage collection de la génération 0, il compacte la mémoire pour les objets accessibles et les promeut à la génération 1. Étant donné que les objets qui survivent aux collectes ont tendance à avoir de plus longues durées de vie, il est logique de les promouvoir à une génération supérieure. Le garbage collector n’a pas à réexaminer les objets des générations 1 et 2 chaque fois qu’il exécute une collection de génération 0.
  
  Si une collection de génération 0 ne libère pas assez de mémoire pour que l’application puisse créer un nouvel objet, le garbage collector peut exécuter une collection de génération 1, puis de génération 2. Les objets qui survivent aux collectes sont promus et stockés dans les générations 1 et 2.

- **Génération 2**. Cette génération contient des objets durables. Un exemple d’objet de longue durée est un objet dans une application serveur qui contient des données statiques qui sont actives pendant la durée du processus.

  Les objets de génération 2 qui survivent à une collection restent dans la génération 2 jusqu’à ce qu’ils soient considérés comme inaccessibles dans une prochaine collection.
  
  Les objets sur le tas d’objets volumineux (parfois appelé *génération 3*) sont également collectés dans la génération 2.

Les opérations garbage collection se produisent sur des générations spécifiques, selon les conditions spécifiées. La collecte d'une génération signifie la collecte des objets de cette génération et de toutes ses générations plus jeunes. Une garbage collection de génération 2 est également appelée garbage collection complète, car elle libère des objets dans toutes les générations (autrement dit, tous les objets du tas managé).

### <a name="survival-and-promotions"></a>Survie et promotions

Les objets qui ne sont pas récupérés dans un garbage collection sont appelés survivants et sont promus à la génération suivante :

- Les objets qui survivent à une garbage collection de génération 0 sont promus à la génération 1.
- Les objets qui survivent à une garbage collection de génération 1 sont promus à la génération 2.
- Les objets qui survivent à une garbage collection de génération 2 restent dans la génération 2.

Lorsque le garbage collector détecte que le taux de survie est élevé dans une génération, il augmente le seuil des allocations pour cette génération. La collection suivante obtient une taille substantielle de mémoire libérée. Le CLR équilibre continuellement deux priorités : ne pas permettre à la plage de travail d’une application d’être trop volumineuse en retardant garbage collection et en empêchant l’exécution trop fréquente du garbage collection.

### <a name="ephemeral-generations-and-segments"></a>Segments et générations éphémères

Étant donné que les objets des générations 0 et 1 sont éphémères, ces générations sont appelées *générations éphémères*.

Les générations éphémères sont allouées dans le segment de mémoire appelé segment éphémère. Chaque nouveau segment acquis par le garbage collector devient le nouveau segment éphémère et contient les objets qui ont survécu à un garbage collection de génération 0. L'ancien segment éphémère devient le nouveau segment de génération 2.

La taille du segment éphémère varie selon qu’il s’agit d’un système 32 bits ou 64 bits et du type de garbage collector en cours d’exécution (station de[travail ou GC de serveur](workstation-server-gc.md)). Le tableau suivant indique les tailles par défaut du segment éphémère.

|GC station de travail/serveur|32 bits|64 bits|
|-|-------------|-------------|
|Garbage collector pour station de travail|16 Mo|256 octets|
|Garbage collector pour serveur|64 Mo|4 Go|
|Garbage collector pour serveur > 4 processeurs logiques|32 Mo|2 Go|
|Garbage collector pour serveur > 8 processeurs logiques|16 Mo|1 Go|

Le segment éphémère peut inclure des objets de la génération 2. Les objets de génération 2 peuvent utiliser plusieurs segments (autant que votre processus en requiert et que la mémoire en autorise).

La quantité de mémoire libérée à partir d'un garbage collection éphémère est limitée à la taille du segment éphémère. La quantité de mémoire libérée est proportionnelle à l'espace occupé par les objets morts.

## <a name="what-happens-during-a-garbage-collection"></a>Déroulement d’une opération garbage collection

Une opération garbage collection présente les phases suivantes :

- Une phase de marquage qui recherche et crée une liste de tous les objets actifs.

- Une phase de déplacement qui met à jour les références aux objets qui seront compactés.

- Une phase de compactage qui libère l'espace occupé par les objets morts et compacte les objets survivants. La phase de compactage déplace les objets qui ont survécu à un garbage collection vers l'extrémité la plus ancienne du segment.

  Étant donné que les collections de génération 2 peuvent occuper plusieurs segments, les objets promus dans la génération 2 peuvent être déplacés dans un segment plus ancien. Les survivants des générations 1 et 2 peuvent être déplacés vers un autre segment, car ils sont promus à la génération 2.

  En règle générale, le tas d’objets volumineux (LOH) n’est pas compacté, car la copie d’objets volumineux impose une baisse des performances. Toutefois, dans .NET Core et dans .NET Framework 4.5.1 et versions ultérieures, vous pouvez utiliser la <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriété pour compacter le tas d’objets volumineux à la demande. En outre, le LOH est automatiquement compacté lorsqu’une limite inconditionnelle est définie en spécifiant l’un ou l’autre des éléments suivants :

  - Limite de mémoire sur un conteneur.
  - Options de configuration [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) ou [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) Runtime.

Le garbage collector utilise les informations suivantes pour déterminer si les objets sont vivants :

- **Racines de pile**. Variables de pile fournies par le compilateur juste-à-temps (JIT) et l'explorateur de pile. Les optimisations JIT peuvent rallonger ou raccourcir les régions de code au sein desquelles les variables de pile sont signalées au garbage collector.

- **Handles de garbage collection**. Handles qui pointent vers les objets managés qui peuvent être alloués par le code utilisateur ou par le Common Language Runtime.

- **Données statiques**. Objets statiques des domaines d'application qui pourraient référencer d'autres objets. Chaque domaine d'application effectue le suivi de ses objets statiques.

Avant qu'une opération garbage collection ne démarre, tous les threads managés sont suspendus à l'exception du thread qui a déclenché l'opération.

L'illustration suivante montre un thread qui déclenche un garbage collection et entraîne l'interruption des autres threads.

![Lorsqu'un thread déclenche un nettoyage de la mémoire](./media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Ressources non managées

Pour la plupart des objets créés par votre application, vous pouvez vous appuyer sur garbage collection pour effectuer automatiquement les tâches de gestion de mémoire nécessaires. Cependant, les ressources non managées requièrent un nettoyage explicite. Le type le plus répandu de ressource non managée est un objet qui enveloppe une ressource de système d'exploitation telle qu'un handle de fichier ou de fenêtre ou une connexion réseau. Bien que le « garbage collector » soit en mesure de suivre la durée de vie d’un objet managé qui encapsule une ressource non managée, il n’a pas de connaissance spécifique sur le nettoyage de la ressource.

Lorsque vous créez un objet qui encapsule une ressource non managée, il est recommandé de fournir le code nécessaire pour nettoyer la ressource non managée dans une `Dispose` méthode publique. En fournissant une méthode `Dispose`, vous donnez la possibilité aux utilisateurs de votre objet d’en libérer explicitement la mémoire lorsqu’ils ont fini de s’en servir. Quand vous utilisez un objet qui encapsule une ressource non managée, veillez à appeler `Dispose` si nécessaire.

Vous devez également fournir un moyen pour que vos ressources non managées soient libérées si un consommateur de votre type oublie d’appeler `Dispose` . Vous pouvez utiliser un handle sécurisé pour encapsuler la ressource non managée ou substituer la <xref:System.Object.Finalize?displayProperty=nameWithType> méthode.

Pour plus d’informations sur le nettoyage des ressources non managées, consultez [nettoyer les ressources non managées](unmanaged.md).

## <a name="see-also"></a>Voir aussi

- [Garbage collection de station de travail et de serveur](workstation-server-gc.md)
- [garbage collection d’arrière-plan](background-gc.md)
- [Options de configuration pour GC](../../core/run-time-config/garbage-collector.md)
- [Garbage collection](index.md)
