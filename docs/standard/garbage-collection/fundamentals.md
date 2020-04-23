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
ms.openlocfilehash: 1fdf7fcd61fb4bf9e8e0cbfe28842208f6eadd00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102435"
---
# <a name="fundamentals-of-garbage-collection"></a>Notions de base du garbage collection

Dans le langage courant runtime (CLR), le collecteur d’ordures (GC) sert de gestionnaire automatique de mémoire. Le collecteur d’ordures gère l’attribution et la libération de mémoire pour une application. Pour les développeurs travaillant avec le code géré, cela signifie que vous n’avez pas à écrire du code pour effectuer des tâches de gestion de la mémoire. La gestion automatique de la mémoire peut éliminer les problèmes courants, comme l’oubli de libérer un objet et provoquer une fuite de mémoire ou tenter d’accéder à la mémoire pour un objet qui a déjà été libéré.

Cet article décrit les concepts fondamentaux de la collecte des ordures.

## <a name="benefits"></a>Avantages

Le collecteur d’ordures offre les avantages suivants :

- Libère les développeurs d’avoir à libérer manuellement la mémoire.

- Il alloue efficacement les objets sur le tas managé.

- Il libère les objets qui ne sont plus utilisés, efface leur mémoire et garde la mémoire disponible pour les futures allocations. Les objets gérés obtiennent automatiquement du contenu propre pour commencer, de sorte que leurs constructeurs n’ont pas à initialiser tous les champs de données.

- Il sécurise la mémoire en s'assurant qu'un objet ne peut pas utiliser le contenu d'un autre objet.

## <a name="fundamentals-of-memory"></a>Notions de base de la mémoire

La liste suivante résume les concepts importants de la mémoire CLR.

- Chaque processus possède son propre espace d'adressage virtuel séparé. Tous les processus sur le même ordinateur partagent la même mémoire physique et le fichier de page, s’il y en a un.

- Par défaut, sur les ordinateurs 32 bits, chaque processus a un espace d'adressage virtuel en mode utilisateur de 2 Go.

- En tant que développeur d'applications, vous travaillez uniquement avec l'espace d'adressage virtuel et ne gérez jamais directement la mémoire physique. Le garbage collector alloue et libère la mémoire virtuelle pour vous sur le tas managé.

  Si vous écrivez du code natif, vous utilisez les fonctions Windows pour travailler avec l’espace d’adresse virtuel. Ces fonctions allouent et libèrent la mémoire virtuelle pour vous sur les tas natifs.

- La mémoire virtuelle peut être dans trois états :

  | State | Description |
  |---------|---------|
  | Gratuit | Il n'existe aucune référence au bloc de mémoire et celui-ci est disponible pour allocation. |
  | Réservé | Le bloc de mémoire est disponible pour votre utilisation et ne peut pas être utilisé pour une autre demande d'allocation. Toutefois, vous ne pouvez pas stocker de données dans ce bloc de mémoire tant qu'il n'est pas validé. |
  | Committed | Le bloc de mémoire est assigné au stockage physique. |

- L'espace d'adressage virtuel peut être fragmenté. Cela signifie qu'il existe des blocs libres, également appelés trous, dans l'espace d'adressage. Lorsqu'une allocation de mémoire virtuelle est demandée, le gestionnaire de mémoire virtuelle doit rechercher un bloc unique libre suffisamment grand pour satisfaire la demande d'allocation. Même si vous avez 2 Go d’espace libre, une allocation qui nécessite 2 Go sera infructueuse à moins que tout cet espace libre est dans un bloc d’adresse unique.

- Vous pouvez manquer de mémoire s’il n’y a pas assez d’espace d’adresse virtuelle pour réserver ou de l’espace physique à engager.

  Le fichier de page est utilisé même si la pression de mémoire physique (c’est-à-dire la demande de mémoire physique) est faible. La première fois que la pression de mémoire physique est élevée, le système d’exploitation doit faire de la place dans la mémoire physique pour stocker des données, et il soutient certaines des données qui sont en mémoire physique au fichier de page. Ces données ne sont pas bipées jusqu’à ce qu’elles soient nécessaires, il est donc possible de rencontrer des paging dans des situations où la pression de mémoire physique est faible.
  
### <a name="memory-allocation"></a>Allocation de mémoire

Lorsque vous initialisez un nouveau processus, le runtime réserve une région d'espace d'adressage contigu pour le processus. Cet espace d'adressage est appelé le tas managé. Le tas managé garde un pointeur vers l'adresse qui sera allouée au nouvel objet du tas. À l’origine, ce pointeur indique l’adresse de base du tas managé. Tous les types référence sont alloués sur le tas managé. Lorsqu’une application crée le premier type référence, la mémoire est allouée pour le type à l’adresse de base du tas managé. Lorsque l'application crée l'objet suivant, le « garbage collector » lui alloue de la mémoire dans l'espace d'adressage qui suit immédiatement le premier objet. Aussi longtemps que de l'espace d'adressage est disponible, le « garbage collector » continue à allouer de l'espace pour de nouveaux objets selon la même procédure.

L'allocation de mémoire à partir du tas managé est plus rapide que l'allocation de mémoire non managée. Parce que le temps d’exécution alloue la mémoire pour un objet en ajoutant une valeur à un pointeur, il est presque aussi rapide que l’attribution de la mémoire de la pile. En outre, parce que les nouveaux objets qui sont attribués consécutivement sont stockés de manière contigu dans le tas géré, une application peut accéder rapidement aux objets.

### <a name="memory-release"></a>Libération de mémoire

Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées. Lorsque le « garbage collector » effectue une opération garbage collection, il libère la mémoire pour les objets qui ne sont plus utilisées par l'application. Il détermine quels objets ne sont plus utilisés en examinant les *racines*de l’application . Les racines de l’application comprennent des champs statiques, des variables et des paramètres locaux sur la pile d’un thread et des Registres du processeur. Chaque racine fait référence à un objet du tas managé ou, à défaut, a la valeur Null. Le Garbage collector a accès à la liste des racines actives entretenues par le compilateur juste-à-temps (JIT) et le runtime. À l’aide de cette liste, le collecteur d’ordures crée un graphique qui contient tous les objets qui sont accessibles à partir des racines.

Les objets non compris dans le graphique ne sont pas accessibles à partir des racines de l'application. Le éboueur considère les objets inaccessibles et libère la mémoire qui leur est allouée. Au cours d'une opération garbage collection, le « garbage collector » examine le tas managé pour y détecter les blocs de mémoire occupés par des objets inaccessibles. Chaque fois qu'il détecte un objet inaccessible, il utilise une fonction de copie de mémoire pour compacter les objets accessibles en mémoire et libérer les blocs d'espaces d'adressage alloués aux objets inaccessibles. Lorsque la mémoire allouée aux objets accessibles a été réduite, le « garbage collector » procède aux corrections de pointeurs nécessaires pour que les racines des applications pointent vers les nouveaux emplacements des objets. Il positionne aussi le pointeur du tas managé après le dernier objet accessible.

La mémoire n’est compactée que si une collection découvre un nombre important d’objets inaccessibles. Si tous les objets du tas managé survivent à une collection, il n'est pas nécessaire de procéder à un compactage de la mémoire.

Pour améliorer les performances, le runtime alloue de la mémoire pour les objets de grandes dimensions dans un tas séparé. Le « garbage collector » libère automatiquement la mémoire des objets de grande dimension. Cependant, pour éviter de déplacer de gros objets dans la mémoire, cette mémoire n’est généralement pas compactée.

## <a name="conditions-for-a-garbage-collection"></a>Conditions pour une opération garbage collection

Le garbage collection se produit lorsque l'une des conditions suivantes est vraie :

- Le système possède peu de mémoire physique. Ceci est détecté par la notification à faible mémoire de l’OS ou la mémoire basse comme indiqué par l’hôte.

- La mémoire utilisée par les objets alloués sur le tas géré dépasse un seuil acceptable. Ce seuil est continuellement ajusté à mesure que le processus s'exécute.

- La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée. Dans presque tous les cas, vous n’avez pas à appeler cette méthode, parce que le collecteur d’ordures fonctionne en permanence. Cette méthode est principalement utilisée pour les situations uniques et les tests.

## <a name="the-managed-heap"></a>Tas managé

Une fois que le garbage collector est initialisé par le CLR, il alloue un segment de mémoire pour stocker et gérer des objets. Cette mémoire est appelée tas managé, par opposition à un tas natif dans le système d'exploitation.

Il existe un tas managé pour chaque processus managé. Tous les threads du processus allouent de la mémoire pour les objets sur le même tas.

Pour réserver la mémoire, le collecteur d’ordures appelle la fonction [Windows VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) et réserve un segment de mémoire à la fois pour les applications gérées. Le collecteur d’ordures réserve également des segments, au besoin, et libère des segments de nouveau au système d’exploitation (après les avoir effacés de tous les objets) en appelant la fonction [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) Windows.

> [!IMPORTANT]
> La taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris les mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.

Moins il y a d'objets alloués sur le tas, moins le garbage collector a à faire. Lorsque vous allouez des objets, n’utilisez pas de valeurs arrondies qui dépassent vos besoins, comme l’attribution d’un tableau de 32 octets lorsque vous n’avez besoin que de 15 octets.

Lorsqu’une collecte d’ordures est déclenchée, le éboueur récupère la mémoire occupée par des objets morts. Le processus de libération compacte les objets vivants afin qu'ils soient déplacés ensemble, et l'espace inutilisé est supprimé, ce qui entraîne la diminution du tas. Cela garantit que les objets qui sont alloués ensemble restent ensemble sur le tas géré pour préserver leur localité.

Le déroulement (fréquence et durée) des garbage collection est le résultat du volume des allocations et de la quantité de mémoire restante sur le tas managé.

Le tas peut être considéré comme l’accumulation de deux tas : le [tas de grands objets](large-object-heap.md) et le tas de petits objets. Le grand tas d’objets contient des objets qui sont 85.000 octets et plus grands, qui sont généralement des tableaux. Il est rare, par exemple, d’être extrêmement grand.

> [!TIP]
> Vous pouvez [configurer la taille du seuil](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pour que les objets aillent sur le tas de gros objets.

## <a name="generations"></a>Générations

L’algorithme GC est basé sur plusieurs considérations :

- Il est plus rapide de compacter la mémoire pour une partie du tas géré que pour l’ensemble du tas géré.
- Les objets plus récents ont une durée de vie plus courte et les objets plus anciens ont une durée de vie plus longue.
- Les objets plus récents ont tendance à être liés les uns aux autres et accessibles par l’application à peu près au même moment.

La collecte des ordures se produit principalement avec la remise en état d’objets de courte durée. Pour optimiser la performance du collecteur d’ordures, le tas géré est divisé en trois générations, 0, 1 et 2, de sorte qu’il peut gérer des objets de longue durée et de courte durée séparément. Le collecteur d’ordures stocke de nouveaux objets de la génération 0. Les objets qui sont créés à un stade précoce de la durée de vie de l'application et qui survivent aux collectes sont promus et stockés dans les générations 1 et 2. Parce qu’il est plus rapide de compacter une partie du tas géré que l’ensemble du tas, ce régime permet au collecteur d’ordures de libérer la mémoire dans une génération spécifique plutôt que de libérer la mémoire pour l’ensemble du tas géré chaque fois qu’il effectue une collection.

- **Génération 0**. Il s'agit de la génération la plus jeune, qui contient des objets éphémères. Un exemple d'objet éphémère est une variable temporaire. Le garbage collection a le plus souvent lieu dans cette génération.

  Les objets nouvellement attribués forment une nouvelle génération d’objets et sont implicitement des collections de génération 0. Cependant, s’il s’agit de gros objets, ils vont sur le tas de gros objets dans une collection de génération 2.

  La plupart des objets sont récupérés pour la collecte des ordures en génération 0 et ne survivent pas à la prochaine génération.
  
  Si une application tente de créer un nouvel objet lorsque la génération 0 est pleine, le collecteur d’ordures effectue une collection dans une tentative de libérer l’espace d’adresse pour l’objet. Le « garbage collector » commence par examiner les objets de la génération 0 plutôt que tous les objets du tas managé. Une collection de génération 0 à elle seule récupère souvent assez de mémoire pour permettre à l’application de continuer à créer de nouveaux objets.

- **Génération 1**. Cette génération contient des objets éphémères et sert de tampon entre objets éphémères et objets durables.

  Après que le collecteur d’ordures effectue une collection de génération 0, il compacte la mémoire pour les objets accessibles et les promeut à la génération 1. Étant donné que les objets qui survivent aux collectes ont tendance à avoir de plus longues durées de vie, il est logique de les promouvoir à une génération supérieure. Le collecteur d’ordures n’a pas à réexaminer les objets dans les générations 1 et 2 chaque fois qu’il effectue une collection de génération 0.
  
  Si une collection de génération 0 ne récupère pas suffisamment de mémoire pour que l’application crée un nouvel objet, le collecteur d’ordures peut effectuer une collection de génération 1, puis de génération 2. Les objets qui survivent aux collectes sont promus et stockés dans les générations 1 et 2.

- **Génération 2**. Cette génération contient des objets durables. Un exemple d’objet à longue durée de vie est un objet dans une application serveur qui contient des données statiques qui sont en direct pendant toute la durée du processus.

  Les objets de la génération 2 qui survivent à une collection restent dans la génération 2 jusqu’à ce qu’ils soient jugés inaccessibles dans une future collection.

Les opérations garbage collection se produisent sur des générations spécifiques, selon les conditions spécifiées. La collecte d'une génération signifie la collecte des objets de cette génération et de toutes ses générations plus jeunes. Une collecte des ordures de génération 2 est également connue comme une collecte complète des ordures, car elle récupère des objets dans toutes les générations (c’est-à-dire tous les objets dans le tas géré).

### <a name="survival-and-promotions"></a>Survie et promotions

Les objets qui ne sont pas récupérés dans une collecte des ordures sont connus sous le nom de survivants et sont promus à la prochaine génération :

- Les objets qui survivent à une collecte des ordures de génération 0 sont promus à la génération 1.
- Les objets qui survivent à une collecte des ordures de génération 1 sont promus à la génération 2.
- Les objets qui survivent à une collecte des ordures de génération 2 restent de la génération 2.

Lorsque le éboueur détecte que le taux de survie est élevé en une génération, il augmente le seuil d’allocation pour cette génération. La collection suivante reçoit une taille substantielle de mémoire récupérée. Le CLR équilibre continuellement deux priorités : ne pas laisser l’ensemble de travail d’une application devenir trop grand en retardant la collecte des ordures et en ne laissant pas la collecte des ordures fonctionner trop fréquemment.

### <a name="ephemeral-generations-and-segments"></a>Segments et générations éphémères

Parce que les objets des générations 0 et 1 sont de courte durée, ces générations sont connues comme les *générations éphémères.*

Des générations éphémères sont attribuées dans le segment de la mémoire connu sous le nom de segment éphémère. Chaque nouveau segment acquis par le garbage collector devient le nouveau segment éphémère et contient les objets qui ont survécu à un garbage collection de génération 0. L'ancien segment éphémère devient le nouveau segment de génération 2.

La taille du segment éphémère varie selon qu’un système est 32 bits ou 64 bits et sur le type de collecteur d’ordures qu’il est en cours d’exécution[(poste de travail ou serveur GC](workstation-server-gc.md)). Le tableau suivant montre les tailles par défaut du segment éphémère.

|Poste de travail/serveur GC|32 bits|64 bits|
|-|-------------|-------------|
|Garbage collector pour station de travail|16 Mo|256 octets|
|Garbage collector pour serveur|64 Mo|4 Go|
|Garbage collector pour serveur > 4 processeurs logiques|32 Mo|2 Go|
|Garbage collector pour serveur > 8 processeurs logiques|16 Mo|1 Go|

Le segment éphémère peut inclure des objets de la génération 2. Les objets de génération 2 peuvent utiliser plusieurs segments (autant que votre processus en requiert et que la mémoire en autorise).

La quantité de mémoire libérée à partir d'un garbage collection éphémère est limitée à la taille du segment éphémère. La quantité de mémoire libérée est proportionnelle à l'espace occupé par les objets morts.

## <a name="what-happens-during-a-garbage-collection"></a>Déroulement d’une opération garbage collection

Une opération garbage collection présente les phases suivantes :

- Une phase de marquage qui recherche et crée une liste de tous les objets actifs.

- Une phase de déplacement qui met à jour les références aux objets qui seront compactés.

- Une phase de compactage qui libère l'espace occupé par les objets morts et compacte les objets survivants. La phase de compactage déplace les objets qui ont survécu à un garbage collection vers l'extrémité la plus ancienne du segment.

  Étant donné que les collections de génération 2 peuvent occuper plusieurs segments, les objets promus dans la génération 2 peuvent être déplacés dans un segment plus ancien. Les survivants des générations 1 et 2 peuvent être déplacés vers un autre segment, car ils sont promus à la génération 2.

  Normalement, le grand tas d’objets (LOH) n’est pas compacté, car la copie de gros objets impose une pénalité de performance. Cependant, dans .NET Core et en .NET Framework 4.5.1 et plus tard, vous pouvez utiliser la <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriété pour compacter le tas de gros objets sur demande. En outre, le LOH est automatiquement compacté lorsqu’une limite dure est définie en spécifiant soit :

  - Limite de mémoire sur un récipient.
  - Les options de configuration [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) ou [GCHeapHardLimitPercent.](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

Le garbage collector utilise les informations suivantes pour déterminer si les objets sont vivants :

- **Empiler les racines**. Variables de pile fournies par le compilateur juste-à-temps (JIT) et l'explorateur de pile. Les optimisations JIT peuvent allonger ou raccourcir les régions de code dans lesquelles les variables de pile sont signalées au collecteur d’ordures.

- **Poignées de collecte des ordures**. Handles qui pointent vers les objets managés qui peuvent être alloués par le code utilisateur ou par le Common Language Runtime.

- **Données statiques**. Objets statiques des domaines d'application qui pourraient référencer d'autres objets. Chaque domaine d'application effectue le suivi de ses objets statiques.

Avant qu'une opération garbage collection ne démarre, tous les threads managés sont suspendus à l'exception du thread qui a déclenché l'opération.

L'illustration suivante montre un thread qui déclenche un garbage collection et entraîne l'interruption des autres threads.

![Lorsqu'un thread déclenche un nettoyage de la mémoire](./media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Ressources non gestions

Pour la plupart des objets créés par votre application, vous pouvez compter sur la collecte des ordures pour effectuer automatiquement les tâches de gestion de la mémoire nécessaires. Cependant, les ressources non managées requièrent un nettoyage explicite. Le type le plus répandu de ressource non managée est un objet qui enveloppe une ressource de système d'exploitation telle qu'un handle de fichier ou de fenêtre ou une connexion réseau. Bien que le collecteur d’ordures soit en mesure de suivre la durée de vie d’un objet géré qui encapsule une ressource non gérée, il n’a pas de connaissances spécifiques sur la façon de nettoyer la ressource.

Lorsque vous créez un objet qui encapsule une ressource non gestion, il est recommandé de fournir le code `Dispose` nécessaire pour nettoyer la ressource non gestion dans une méthode publique. En fournissant une méthode `Dispose`, vous donnez la possibilité aux utilisateurs de votre objet d’en libérer explicitement la mémoire lorsqu’ils ont fini de s’en servir. Lorsque vous utilisez un objet qui encapsule une ressource non `Dispose` gémanie, assurez-vous d’appeler au besoin.

Vous devez également fournir un moyen pour vos ressources non gestion d’être libérés au cas où un consommateur de votre type oublie d’appeler `Dispose`. Vous pouvez soit utiliser une poignée sûre pour envelopper la <xref:System.Object.Finalize?displayProperty=nameWithType> ressource non gérée, ou remplacer la méthode.

Pour plus d’informations sur le nettoyage des ressources non gestion, voir [Nettoyer les ressources non gestions](unmanaged.md).

## <a name="see-also"></a>Voir aussi

- [Garbage collection de station de travail et de serveur](workstation-server-gc.md)
- [Collecte des ordures de fond](background-gc.md)
- [Options de configuration pour GC](../../core/run-time-config/garbage-collector.md)
- [Nettoyage de la mémoire](index.md)
