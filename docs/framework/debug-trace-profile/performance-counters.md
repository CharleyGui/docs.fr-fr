---
title: Compteurs de performance dans le .NET Framework
description: En savoir plus sur les compteurs de performance dans .NET. Il existe des compteurs de performances pour les exceptions, l’interopérabilité, les compilateurs JIT, le chargement, la mémoire, la mise en réseau, la sécurité et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
ms.openlocfilehash: 1b5ca6484f45dcee33009d8b8c12a43fa41f63de
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554447"
---
# <a name="performance-counters-in-the-net-framework"></a>Compteurs de performance dans le .NET Framework

Cette rubrique fournit une liste des compteurs de performance que vous pouvez trouver dans l' [Analyseur de performances Windows](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249(v=ws.11)).  

## <a name="exception-performance-counters"></a>Compteurs de performance des exceptions  
 La catégorie Exceptions CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur les exceptions levées par une application. Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**Nombre d’exceptions levées**|Affiche le nombre total d'exceptions qui ont été levées depuis le démarrage de l'application. Ce nombre comprend à la fois les exceptions .NET et les exceptions non managées qui sont converties en exceptions .NET. Par exemple, un HRESULT retourné par du code non managé est converti pour donner une exception en code managé.<br /><br /> Ce compteur inclut les exceptions gérées et non gérées. Il comptabilise les exceptions levées plusieurs fois.|  
|**Nombre d’exceptions levées/s**|Affiche le nombre d'exceptions levées par seconde. Ce nombre comprend à la fois les exceptions .NET et les exceptions non managées qui sont converties en exceptions .NET. Par exemple, un HRESULT retourné par du code non managé est converti pour donner une exception en code managé.<br /><br /> Ce compteur inclut les exceptions gérées et non gérées. Il ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon. Ce compteur est un indicateur de problèmes de performances potentiels si un nombre élevé d’exceptions (>100s) est levé.|  
|**Nombre de filtres/s**|Affiche le nombre de filtres d'exception .NET exécutés par seconde. Un filtre d'exception évalue si une exception doit être gérée ou non.<br /><br /> Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Nombre de Finally/s**|Affiche le nombre de blocs finally exécutés par seconde. Un bloc finally est toujours exécuté, quelle que soit la méthode de sortie du bloc try.  Seuls les blocs finally exécutés pour une exception sont comptabilisés ; ceux situés dans les chemins de code standard sont ignorés par ce compteur.<br /><br /> Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Profondeur Throw à Catch/s**|Affiche le nombre de frames de pile traversés, par seconde, entre le frame qui a levé l'exception et celui qui l'a gérée. Ce compteur est remis à zéro quand un gestionnaire d'exceptions est entré. Les exceptions imbriquées indiquent donc la profondeur de la pile entre les gestionnaires.<br /><br /> Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  

## <a name="interop-performance-counters"></a>Compteurs de performance pour l'interopérabilité  
 La catégorie Interopérabilité CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur l'interaction entre une application et les composants COM, les services COM+ et les bibliothèques de types externes. Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**Nombre CCW**|Affiche le nombre actuel de wrappers CCW (COM Callable Wrapper). Un wrapper CCW est un proxy pour un objet managé qui est référencé à partir d'un client COM non managé. Ce compteur indique le nombre d'objets managés référencés par un code COM non managé.|  
|**Nombre de marshaling**|Affiche le nombre total de fois où des arguments et des valeurs de retour ont été marshalés du code managé vers le code non managé, et vice versa, depuis le démarrage de l'application. Ce compteur n'est pas incrémenté pour les stubs inline. (Les stubs sont chargés de marshaler les arguments et les valeurs de retour.) Les stubs sont généralement inline quand la surcharge de marshaling est faible.|  
|**Nombre de stubs**|Affiche le nombre actuel de stubs créés par le common language runtime. Les stubs sont chargés de marshaler les arguments et les valeurs de retour du code managé vers le code non managé, et vice versa, pendant un appel COM Interop ou un appel de code non managé.|  
|**Nombre d’exportations TLB/s**|Réservé à un usage ultérieur.|  
|**Nombre d’importations TLB/s**|Réservé à un usage ultérieur.|  

## <a name="jit-performance-counters"></a>compteurs de performance JIT  
 La catégorie JIT CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur du code ayant été compilé juste-à-temps (JIT). Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**Nombre d’octets IL traités avec Jit**|Affiche le nombre total d'octets MSIL (Microsoft Intermediate Language) ayant été compilés par le compilateur juste-à-temps (JIT) depuis le démarrage de l'application. Ce compteur est équivalent au compteur **Nombre total d’octets IL traités avec Jit**.|  
|**Nombre de méthodes traitées avec Jit**|Affiche le nombre total de méthodes ayant été compilées juste-à-temps (JIT) depuis le démarrage de l'application. Ce compteur n'inclut pas les méthodes ayant fait l'objet d'une compilation pré-JIT.|  
|**% temps en Jit**|Affiche le pourcentage du temps écoulé passé à effectuer une compilation JIT depuis la dernière phase de compilation JIT. Ce compteur est actualisé à la fin de chaque phase de compilation JIT. Une phase de compilation JIT est une phase pendant laquelle une méthode et ses dépendances sont compilées.|  
|**Octets IL traités avec Jit/s**|Affiche le nombre d'octets MSIL ayant été compilés juste-à-temps (JIT) par seconde. Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Échecs Jit standard**|Affiche le nombre maximal de méthodes que le compilateur JIT n'a pas pu compiler depuis le démarrage de l'application. Ce type d'échec peut se produire quand le MSIL ne peut pas être vérifié ou en cas d'erreur interne au niveau du compilateur JIT.|  
|**Nombre total d’octets IL traités avec Jit**|Affiche le nombre total d'octets MSIL ayant fait l'objet d'une compilation JIT depuis le démarrage de l'application. Ce compteur est équivalent au compteur **Nombre d’octets IL traités avec Jit**.|  

## <a name="loading-performance-counters"></a>Compteurs de performance pour le chargement  
 La catégorie Chargement CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur les assemblys, les classes et les domaines d'application qui sont chargés. Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**% temps chargement**|Réservé à un usage ultérieur.|  
|**Longueur de la recherche de l’assembly**|Réservé à un usage ultérieur.|  
|**Octets dans le tas du chargeur**|Affiche la taille actuelle, en octets, de la mémoire validée par le chargeur de classes à tous les domaines d’application. La mémoire allouée représente l'espace physique réservé dans le fichier d'échange du disque.|  
|**Appdomains actuels**|Affiche le nombre actuel de domaines d'application chargés dans cette application.|  
|**Assemblys actuels**|Affiche le nombre actuel d'assemblys chargés pour l'ensemble des domaines d'application dans l'application en cours d'exécution. Si l'assembly est chargé comme étant indépendant du domaine à partir de plusieurs domaines d'application, ce compteur n'est incrémenté qu'une seule fois.|  
|**Classes chargées actuelles**|Affiche le nombre actuel de classes chargées dans tous les assemblys.|  
|**Taux des appdomains**|Affiche le nombre de domaines d'application chargés par seconde. Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Taux des appdomains déchargés**|Affiche le nombre de domaines d'application déchargés par seconde. Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Taux des assemblys**|Affiche le nombre d'assemblys chargés par seconde pour l'ensemble des domaines d'application. Si l'assembly est chargé comme étant indépendant du domaine à partir de plusieurs domaines d'application, ce compteur n'est incrémenté qu'une seule fois.<br /><br /> Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Taux des classes chargées**|Affiche le nombre de classes chargées par seconde dans tous les assemblys. Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Taux d’échecs de chargement**|Affiche le nombre de classes qui n'ont pas pu être chargées par seconde. Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.<br /><br /> Les échecs de chargement peuvent avoir de nombreuses causes telles qu'une sécurité non appropriée ou un format non valide. Pour plus d'informations, voir l'aide relative aux services de profilage.|  
|**Total des échecs de chargement**|Affiche le nombre maximal de classes qui n'ont pas pu être chargées depuis le démarrage de l'application.<br /><br /> Les échecs de chargement peuvent avoir de nombreuses causes telles qu'une sécurité non appropriée ou un format non valide. Pour plus d'informations, voir l'aide relative aux services de profilage.|  
|**Total Appdomains**|Affiche le nombre maximal de domaines d'application qui ont été chargés depuis le démarrage de l'application.|  
|**Total de appdomains déchargés**|Affiche le nombre total de domaines d'application qui ont été déchargés depuis le démarrage de l'application. Si un domaine d'application est chargé et déchargé plusieurs fois, ce compteur s'incrémente à chaque déchargement du domaine d'application.|  
|**Total d’assemblys**|Affiche le nombre total d'assemblys qui ont été chargés depuis le démarrage de l'application. Si l'assembly est chargé comme étant indépendant du domaine à partir de plusieurs domaines d'application, ce compteur n'est incrémenté qu'une seule fois.|  
|**Total de classes chargées**|Affiche le nombre total de classes qui ont été chargées dans tous les assemblys depuis le démarrage de l'application.|  

## <a name="lock-and-thread-performance-counters"></a>Compteurs de performance pour les verrous et les threads  
 La catégorie Verrous et threads CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur les verrous et les threads managés qu'une application utilise. Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**Nombre de threads actuels logiques**|Affiche le nombre d'objets thread managés actuellement présents dans l'application. Ce compteur gère le nombre de threads en cours d'exécution et arrêtés. Il n'établit pas une moyenne temporelle ; il affiche uniquement la dernière valeur observée.|  
|**Nombre de threads actuels physiques**|Affiche le nombre de threads du système d'exploitation natifs créés et détenus par le common language runtime pour jouer le rôle de threads sous-jacents pour les objets thread managés. La valeur de ce compteur n'inclut pas les threads utilisés par le runtime dans ses opérations internes ; il s'agit d'un sous-ensemble des threads dans le processus du système d'exploitation.|  
|**Nombre de threads actuellement reconnus**|Affiche le nombre de threads actuellement reconnus par le runtime. Ces threads sont associés à un objet thread managé correspondant. Il ne s'agit pas de threads créés par le runtime, mais de threads qui ont été exécutés au moins une fois dans le runtime.<br /><br /> Seuls les threads uniques sont pris en compte. Les threads avec le même ID qui rentrent dans le runtime ou sont recréés après en être sortis sont comptabilisés une seule fois.|  
|**Nombre total de threads reconnus**|Affiche le nombre total de threads qui ont été reconnus par le runtime depuis le démarrage de l'application. Ces threads sont associés à un objet thread managé correspondant. Il ne s'agit pas de threads créés par le runtime, mais de threads qui ont été exécutés au moins une fois dans le runtime.<br /><br /> Seuls les threads uniques sont pris en compte. Les threads avec le même ID qui rentrent dans le runtime ou sont recréés après en être sortis sont comptabilisés une seule fois.|  
|**Taux de conflits/s**|Affiche le taux d'échecs des threads dans le runtime qui tentent d'acquérir un verrou managé.|  
|**Longueur de la file actuelle**|Affiche le nombre total de threads qui attendent actuellement d'acquérir un verrou managé dans l'application. Ce compteur n'établit pas une moyenne temporelle ; il affiche la dernière valeur observée.|  
|**Longueur de la file/s**|Affiche le nombre de threads par seconde qui attendent actuellement d'acquérir un verrou dans l'application. Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Longueur de la file maximale**|Affiche le nombre total de threads qui ont attendu d'acquérir un verrou managé depuis le démarrage de l'application.|  
|**Taux de threads reconnus/s**|Affiche le nombre de threads par seconde qui ont été reconnus par le runtime. Ces threads sont associés à un objet thread managé correspondant. Il ne s'agit pas de threads créés par le runtime, mais de threads qui ont été exécutés au moins une fois dans le runtime.<br /><br /> Seuls les threads uniques sont pris en compte. Les threads avec le même ID qui rentrent dans le runtime ou sont recréés après en être sortis sont comptabilisés une seule fois.<br /><br /> Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Nombre total de conflits**|Affiche le nombre total de fois où les threads du runtime ont tenté en vain d'acquérir un verrou managé.|  

## <a name="memory-performance-counters"></a>Compteurs de performance pour la mémoire  
 La catégorie Mémoire CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur le garbage collector (le récupérateur de mémoire). Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**Nombre d’octets dans tous les tas**|Affiche la somme des compteurs **Taille du tas de la génération 1**, **Taille du tas de la génération 2** et **Taille du tas des objets volumineux**. Ce compteur indique la mémoire actuellement allouée, en octets, aux tas de garbage collection.|  
|**Nombre de handles GC**|Affiche le nombre de handles de garbage collection (GC) actuellement utilisés. Les handles de garbage collection sont des handles vers des ressources externes au common language runtime et à l'environnement managé.|  
|**Nombre de collections de génération 0**|Affiche le nombre de fois où les objets de la génération 0 (les objets les plus récents, les derniers alloués) ont été récupérés par le garbage collector depuis le démarrage de l'application.<br /><br /> Un garbage collection de la génération 0 se produit lorsque la mémoire disponible dans la génération 0 n’est pas suffisante pour répondre à une demande d’allocation. Ce compteur s’incrémente à la fin de chaque garbage collection de la génération 0. Un garbage collection d’une génération supérieure inclut tous les garbage collection des générations inférieures. Ce compteur est explicitement incrémenté quand un garbage collection d'une génération supérieure (génération 1 ou 2) se produit.<br /><br /> Ce compteur affiche la dernière valeur observée. La valeur du compteur **_Global\_** n’est pas exacte et doit être ignorée.|  
|**Nombre de collections de génération 1**|Affiche le nombre de fois où les objets de la génération 1 ont été récupérés par le garbage collector depuis le démarrage de l'application.<br /><br /> Ce compteur s'incrémente à la fin de chaque garbage collection de la génération 1. Un garbage collection d’une génération supérieure inclut tous les garbage collection des générations inférieures. Ce compteur est explicitement incrémenté quand un garbage collection d’une génération supérieure (génération 2) se produit.<br /><br /> Ce compteur affiche la dernière valeur observée. La valeur du compteur **_Global\_** n’est pas exacte et doit être ignorée.|  
|**Nombre de collections de génération 2**|Affiche le nombre de fois où les objets de la génération 2 ont été récupérés par le garbage collector depuis le démarrage de l'application. Ce compteur s’incrémente à la fin de chaque garbage collection de la génération 2 (garbage collection complet).<br /><br /> Ce compteur affiche la dernière valeur observée. La valeur du compteur **_Global\_** n’est pas exacte et doit être ignorée.|  
|**Nombre GC induit**|Affiche le nombre maximal de fois où un garbage collection a été effectué en raison d'un appel explicite à <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Il est recommandé de laisser le récupérateur de mémoire déterminer la fréquence de ses collections.|  
|**Nombre d’objets épinglés**|Affiche le nombre d'objets épinglés rencontrés lors du dernier garbage collection. Un objet épinglé est un objet que le garbage collector ne peut pas déplacer dans la mémoire. Ce compteur effectue le suivi des objets épinglés uniquement dans les tas récupérés par le garbage collector. Par exemple, un garbage collection de la génération 0 ne comptabilise que les objets épinglés dans le tas de la génération 0.|  
|**Nombre de blocs de synchronisation utilisés**|Affiche le nombre de blocs de synchronisation actuellement utilisés. Les blocs de synchronisation sont des structures de données par objet qui sont allouées au stockage d'informations de synchronisation. Ils contiennent des références faibles aux objets managés et doivent être analysés par le garbage collector. Les blocs de synchronisation ne servent pas uniquement à stocker des informations de synchronisation ; ils peuvent aussi stocker des métadonnées COM Interop. Ce compteur indique les problèmes de performance liés à un usage intensif de primitives de synchronisation.|  
|**Nombre total d’octets dédiés**|Affiche la quantité de mémoire virtuelle, exprimée en octets, qui est actuellement allouée par le garbage collector. La mémoire allouée représente la mémoire physique pour laquelle un espace a été réservé dans le fichier d'échange du disque.|  
|**Nombre total d’octets réservés**|Affiche la quantité de mémoire virtuelle, exprimée en octets, qui est actuellement réservée par le garbage collector. La mémoire réservée représente l'espace de mémoire virtuelle réservé à l'application quand aucun disque ni page de mémoire principale n'a été utilisé.|  
|**% de temps dans GC**|Affiche le pourcentage du temps écoulé passé à effectuer un garbage collection depuis le dernier cycle de garbage collection. Ce compteur indique habituellement le travail réalisé par le garbage collector pour collecter et compacter de la mémoire de la part d'une application. Ce compteur est actualisé uniquement à la fin de chaque garbage collection. Ce compteur n'établit pas une moyenne ; il affiche la dernière valeur observée.|  
|**Octets alloués/s**|Affiche le nombre d’octets par seconde alloués au tas de garbage collection. Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation. Ce compteur ne représente pas une moyenne temporelle ; il affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Survivants de finalisation**|Affiche le nombre d’objets récupérés par le garbage collector qui survivent à un garbage collection parce qu’ils sont en attente de finalisation. Si ces objets contiennent des références à d'autres objets, ces derniers survivent également, mais ils seront ignorés par ce compteur. Le compteur **Finalisation-mémoire promues de la génération 0** représente la mémoire qui a survécu en raison de la finalisation.<br /><br /> Ce compteur n’est pas cumulatif : il est actualisé à la fin de chaque garbage collection avec le nombre de survivants à cette opération uniquement. Ce compteur indique la surcharge que l'application peut subir en raison de la finalisation.|  
|**Taille du tas de la génération 0**|Affiche la quantité maximale d'octets pouvant être alloués à la génération 0. Il n'indique pas le nombre d'octets qui sont actuellement alloués à la génération 0.<br /><br /> Un garbage collection de la génération 0 se produit quand les allocations effectuées depuis le dernier garbage collection dépassent cette taille. La taille de la génération 0 est déterminée par le garbage collector et peut changer pendant l'exécution de l'application. À la fin d'un garbage collection de la génération 0, la taille du tas de la génération 0 est de zéro (0) octet. Ce compteur affiche la taille (en octets) des allocations qui appellent le garbage collection de génération 0 suivant.<br /><br /> Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation.|  
|**Octets promus de la génération 0/s**|Affiche le nombre d'octets par seconde promus de la génération 0 à la génération 1. La mémoire est promue quand elle survit à un garbage collection. Ce compteur est un indicateur du nombre d'objets à durée de vie relativement longue qui sont créés par seconde.<br /><br /> Ce compteur affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Taille du tas de la génération 1**|Affiche le nombre d'octets actuellement alloués à la génération 1. Ce compteur n'affiche pas la taille maximale de la génération 1. Les objets ne sont pas alloués directement à cette génération : ils sont promus à partir des précédents garbage collection de la génération 0. Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation.|  
|**Octets promus de la génération 1/s**|Affiche le nombre d'octets par seconde promus de la génération 1 à la génération 2. Les objets promus uniquement parce qu'ils attendent d'être finalisés sont ignorés par ce compteur.<br /><br /> La mémoire est promue quand elle survit à un garbage collection. La génération 2 étant la plus ancienne, les promotions depuis celle-ci ne sont pas possibles. Ce compteur est un indicateur du nombre d'objets à durée de vie très longue qui sont créés par seconde.<br /><br /> Ce compteur affiche la différence entre les valeurs observées dans les deux derniers intervalles de temps, divisée par la durée de l'intervalle échantillon.|  
|**Taille du tas de la génération 2**|Affiche le nombre d'octets actuellement alloués à la génération 2. Les objets ne sont pas alloués directement à cette génération : ils sont promus à partir de la génération 1 durant les précédents garbage collection de la génération 1. Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation.|  
|**Taille du tas d’objets volumineux**|Affiche la taille actuelle, en octets, du tas d’objets volumineux. Les objets qui sont supérieurs à environ 85 000 octets sont traités comme des objets volumineux par le garbage collector et sont directement alloués dans un tas spécial. Ils ne sont pas promus via les générations. Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation.|  
|**ID de processus**|Affiche l'ID de processus de l'instance de CLR qui est surveillée.|  
|**Finalisation-mémoire promues de la génération 0**|Affiche le nombre d'octets de mémoire qui sont promus de la génération 0 à la génération 1 uniquement parce qu'ils sont en attente de finalisation. Ce compteur n’est pas cumulatif : il affiche la valeur observée à la fin du dernier garbage collection uniquement.|  
|**Mémoire promue de la génération 0**|Affiche le nombre d'octets de mémoire qui survivent au garbage collection et sont promus de la génération 0 à la génération 1. Les objets promus uniquement parce qu'ils attendent d'être finalisés sont ignorés par ce compteur. Ce compteur n’est pas cumulatif : il affiche la valeur observée à la fin du dernier garbage collection uniquement.|  
|**Mémoire promue de la génération 1**|Affiche le nombre d’octets de mémoire qui survivent au garbage collection et sont promus de la génération 1 à la génération 2. Les objets promus uniquement parce qu'ils attendent d'être finalisés sont ignorés par ce compteur. Ce compteur n’est pas cumulatif : il affiche la valeur observée à la fin du dernier garbage collection uniquement. Ce compteur est remis à 0 uniquement si le dernier garbage collection était de la génération 0.|  

## <a name="networking-performance-counters"></a>Compteurs de performance pour le réseau  

La catégorie Réseau CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur les données qu'une application envoie et reçoit via le réseau. Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**Octets reçus**|Nombre total cumulatif d'octets qui ont été reçus par tous les objets <xref:System.Net.Sockets.Socket> dans l'<xref:System.AppDomain> depuis le démarrage du processus. Ce nombre inclut des données et toutes les informations de protocole non définies par le protocole TCP/IP.|  
|**Octets envoyés**|Nombre total cumulatif d'octets qui ont été envoyés par tous les objets <xref:System.Net.Sockets.Socket> dans l'<xref:System.AppDomain> depuis le démarrage du processus. Ce nombre inclut des données et toutes les informations de protocole non définies par le protocole TCP/IP.|  
|**Connexions établies**|Nombre total cumulatif d'objets <xref:System.Net.Sockets.Socket> pour les sockets de flux qui ont été connectés dans l'<xref:System.AppDomain> depuis le démarrage du processus.|  
|**Datagrammes reçus**|Nombre total cumulatif de paquets de datagrammes qui ont été reçus par tous les objets <xref:System.Net.Sockets.Socket> dans l'<xref:System.AppDomain> depuis le démarrage du processus.|  
|**Datagrammes envoyés**|Nombre total cumulatif de paquets de datagrammes qui ont été envoyés par tous les objets <xref:System.Net.Sockets.Socket> dans l'<xref:System.AppDomain> depuis le démarrage du processus.|  
|**Durée de vie moyenne des requêtes HttpWebRequest**|Durée moyenne d'achèvement pour tous les objets <xref:System.Net.HttpWebRequest> qui se sont terminés dans le dernier intervalle dans l'<xref:System.AppDomain> depuis le démarrage du processus.|  
|**Durée d’attente moyenne des requêtes HttpWebRequest**|Durée d'attente moyenne pour tous les objets <xref:System.Net.HttpWebRequest> qui ont quitté la file d'attente dans le dernier intervalle dans l'<xref:System.AppDomain> depuis le démarrage du processus.|  
|**Nombre de requêtes HttpWebRequest créées/s**|Nombre d'objets <xref:System.Net.HttpWebRequest> créés par seconde dans l'<xref:System.AppDomain>.|  
|**Nombre de requêtes HttpWebRequest mises en file d’attente/s**|Nombre d'objets <xref:System.Net.HttpWebRequest> ajoutés à la file d'attente par seconde dans l'<xref:System.AppDomain>.|  
|**Nombre de requêtes HttpWebRequest abandonnées/s**|Nombre d'objets <xref:System.Net.HttpWebRequest> par seconde pour lesquels l'application a appelé la méthode <xref:System.Net.HttpWebRequest.Abort%2A> dans l'<xref:System.AppDomain>.|  
|**Nombre de requêtes HttpWebRequest ayant échoué/s**|Nombre d'objets <xref:System.Net.HttpWebRequest> par seconde ayant reçu un code d'état d'échec du serveur dans l'<xref:System.AppDomain>.|  
  
 Plusieurs classes de compteurs de performance pour le réseau sont prises en charge :  
  
- Compteurs d'événements qui comptabilisent le nombre d'occurrences d'un événement donné.  
  
- Compteurs de données qui mesurent la quantité de données envoyées ou reçues.  
  
- Compteurs de durée qui mesurent le temps nécessaire à l'exécution de différents processus. Les durées sont mesurées sur les objets à chaque intervalle (généralement en secondes) après leur sortie de différents états.  
  
- Compteurs par intervalle qui comptabilisent le nombre d'objets faisant une transition particulière par intervalle (généralement par seconde).  
  
Les compteurs de performance réseau pour les événements sont les suivants :  
  
- **Connexions établies**  
  
- **Datagrammes reçus**  
  
- **Datagrammes envoyés**  
  
 Ces compteurs de performance fournissent les nombres cumulés depuis le démarrage du processus. Le nombre de connexions <xref:System.Net.Sockets.Socket> établies inclut les appels de méthode <xref:System.Net.Sockets.Socket> explicites effectués par une application pour une connexion de socket de flux établie ainsi que les appels internes faits par d'autres classes (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient> et <xref:System.Net.Sockets.TcpClient>, par exemple) à la classe <xref:System.Net.Sockets.Socket>.  
  
 Les nombres **Datagrammes reçus** et **Datagrammes envoyés** incluent les paquets de datagrammes envoyés ou reçus par le biais des appels de méthode <xref:System.Net.Sockets.Socket> explicites effectués par une application ainsi que les appels internes faits par d’autres classes (<xref:System.Net.Sockets.UdpClient>, par exemple) à la classe <xref:System.Net.Sockets.Socket>. . Les compteurs **Datagrammes reçus** et **Datagrammes envoyés** peuvent aussi être utilisés pour fournir une mesure très approximative du nombre d’octets envoyés ou reçus à l’aide de datagrammes, en supposant une taille moyenne de datagramme.  
  
 Les compteurs de performance réseau pour les données sont les suivants :  
  
- **Octets reçus**  
  
- **Octets envoyés**  
  
 Les compteurs ci-dessus indiquent le nombre d'octets qui ont été reçus et envoyés depuis le démarrage du processus.  
  
 Les deux compteurs de durée suivants mesurent le temps nécessaire aux objets <xref:System.Net.HttpWebRequest> pour achever la totalité ou une partie de leur cycle de vie :  
  
- **Durée de vie moyenne des requêtes HttpWebRequest**  
  
- **Durée d’attente moyenne des requêtes HttpWebRequest**  
  
 Le compteur **Durée de vie moyenne des requêtes HttpWebRequest** considère que la durée de vie de la plupart des objets <xref:System.Net.HttpWebRequest> s’étend toujours de la création de l’objet à la fermeture du flux de réponse par l’application. Il existe deux cas rares :  
  
- Si l'application n'appelle jamais la méthode <xref:System.Net.HttpWebRequest.GetResponse%2A> ou <xref:System.Net.HttpWebRequest.BeginGetResponse%2A>, la durée de vie de l'objet <xref:System.Net.HttpWebRequest> est ignorée.  
  
- Si l'objet <xref:System.Net.HttpWebRequest> lève une exception <xref:System.Net.WebException> quand la méthode <xref:System.Net.HttpWebRequest.GetResponse%2A> ou <xref:System.Net.HttpWebRequest.EndGetResponse%2A> est appelée, la durée de vie se termine au moment où l'exception est levée. D'un point de vue technique, le flux de réponse sous-jacent est également fermé à ce stade (le flux de réponse retourné à l'utilisateur est réellement un flux de mémoire qui contient une copie du flux de réponse).  
  
 Quatre compteurs permettent de surveiller par intervalle certains problèmes liés à l'objet <xref:System.Net.HttpWebRequest>. Ces compteurs de performance seront utiles aux développeurs d'applications, aux administrateurs et aux équipes de support technique pour mieux comprendre le fonctionnement des objets <xref:System.Net.HttpWebRequest>. Les compteurs sont les suivants :  
  
- **Nombre de requêtes HttpWebRequest créées/s**  
  
- **Nombre de requêtes HttpWebRequest mises en file d’attente/s**  
  
- **Nombre de requêtes HttpWebRequest abandonnées/s**  
  
- **Nombre de requêtes HttpWebRequest ayant échoué/s**  
  
 Le compteur **Nombre de requêtes HttpWebRequest abandonnées/s** comptabilise aussi les appels internes à <xref:System.Net.HttpWebRequest.Abort%2A>. Ces appels internes sont généralement provoqués par les délais d'attente qu'une application veut mesurer.  
  
 Le compteur **Nombre de requêtes HttpWebRequest ayant échoué/s** comptabilise le nombre d’objets <xref:System.Net.HttpWebRequest> par seconde ayant reçu un code d’état d’échec du serveur. Cela signifie que le code d'état reçu du serveur HTTP à la fin de la demande n'était pas compris entre 200 et 299. Les codes d'état qui sont gérés et aboutissent à une nouvelle demande (comme la plupart des codes d'état 401 Non autorisé, par exemple) échoueront ou pas en fonction du résultat de la nouvelle tentative. Si l'application enregistre une erreur suite à la nouvelle tentative, ce compteur est incrémenté.  
  
 Les compteurs de performance réseau sont accessibles et gérables à l'aide de la classe <xref:System.Diagnostics.PerformanceCounter> et des classes connexes dans l'espace de noms <xref:System.Diagnostics>. Les compteurs de performance réseau peuvent également être affichés dans la console Analyseur de performances Windows.  
  
 Les compteurs de performance réseau doivent être activés dans le fichier de configuration pour pouvoir être utilisés. L'ensemble des compteurs de performance réseau sont activés ou désactivés avec un paramètre unique dans le fichier de configuration. Il n'est pas possible d'activer ou de désactiver ces compteurs de manière individuelle. Pour plus d’informations, consultez [ \<performanceCounter> élément (paramètres réseau)](../configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Si les compteurs de performance réseau sont activés, il est possible de créer et d'actualiser des compteurs de performance par AppDomain et globaux. S'ils sont désactivés, l'application ne fournit pas de données de compteur de performance réseau.  
  
 Les compteurs de performance sont regroupés en catégories. Une application peut répertorier toutes les catégories avec le code suivant :  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Les compteurs de performance réseau se classent dans deux catégories :  
  
- « Réseau CLR .NET » : regroupe les compteurs de performance initialement proposés dans .NET Framework 2 et pris en charge par cette version et les versions ultérieures.  
  
- « Réseau CLR .NET 4.0.0.0 » : regroupe tous les compteurs de socket ci-dessus ainsi que les nouveaux compteurs de performance pris en charge par .NET Framework 4 et les versions ultérieures. Ces nouveaux compteurs fournissent des informations sur les performances des objets <xref:System.Net.HttpWebRequest>.  
  
 Pour plus d’informations sur l’accès aux compteurs de performance et la gestion de ces derniers dans une application, consultez [Compteurs de performance](performance-counters.md).  

## <a name="security-performance-counters"></a>Compteurs de performance pour la sécurité  
 La catégorie Sécurité CLR .NET de la Console de performances comprend des compteurs qui fournissent des informations sur les vérifications de sécurité effectuées par le common language runtime pour une application. Le tableau suivant décrit ces compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|**Nombre de vérifications durant l’édition de liens**|Affiche le nombre total de vérifications de sécurité d'accès du code durant l'édition de liens qui ont été effectuées depuis le démarrage de l'application. Les vérifications de sécurité d'accès du code durant l'édition de liens sont effectuées quand un appelant demande une autorisation particulière au moment de la compilation juste-à-temps (JIT). Une vérification durant l'édition de liens est effectuée une seule fois par appelant. Ce compteur n'indique pas de graves problèmes de performance ; il renseigne simplement sur l'activité du système de sécurité.|  
|**% temps pour les vérifications RT**|Affiche le pourcentage du la durée calendaire passé à effectuer des vérifications de sécurité d’accès du code à l’exécution depuis le dernier intervalle échantillon. Ce compteur est actualisé à la fin de chaque vérification de sécurité de .NET Framework. Il n'établit pas une moyenne ; il affiche la dernière valeur observée.|  
|**% temps authentification de la signature**|Réservé à un usage ultérieur.|  
|**Épaisseur de la pile**|Affiche l'épaisseur de la pile pendant la dernière vérification de la sécurité d'accès du code à l'exécution. Les vérifications de sécurité d'accès du code à l'exécution sont effectuées en parcourant la pile. Ce compteur n'établit pas une moyenne ; il affiche uniquement la dernière valeur observée.|  
|**Total de vérifications à l’exécution**|Affiche le nombre total de vérifications de sécurité d'accès du code à l'exécution effectuées depuis le démarrage de l'application. Les vérifications de sécurité d'accès du code à l'exécution sont effectuées quand un appelant demande une autorisation particulière. La vérification à l'exécution se produit à chaque appel par l'appelant, en examinant la pile de threads actuelle de l'appelant. Utilisé avec le compteur **Épaisseur de la pile**, ce compteur indique la diminution de performances due aux vérifications de sécurité.|  
  
## <a name="see-also"></a>Voir aussi

- [Compteurs de performance](performance-counters.md)
- [Profilage d’exécution](runtime-profiling.md)
