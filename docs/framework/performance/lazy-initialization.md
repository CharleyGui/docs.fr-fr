---
title: Initialisation tardive
description: Explorez l’initialisation tardive dans .NET, une amélioration des performances qui signifie que la création d’un objet est différée jusqu’à ce que l’objet soit utilisé pour la première fois.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 355fa326fc19e9a50a74e21ace0a6353f5c740c5
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904232"
---
# <a name="lazy-initialization"></a>Initialisation tardive
*L’initialisation tardive* d’un objet signifie que sa création est différée jusqu’à sa première utilisation. (Pour cette rubrique, les termes *initialisation tardive* et *instanciation différée* sont synonymes.) L’initialisation tardive est principalement utilisée pour améliorer les performances, éviter le calcul du gaspillage et réduire les besoins en mémoire du programme. Voici les scénarios les plus courants :  
  
- Lorsqu’un objet est coûteux à créer, et qu’il est possible que le programme ne l’utilise pas. Par exemple, supposons que vous ayez en mémoire un objet `Customer` avec une propriété `Orders` contenant un grand tableau d’objets `Order` qui, pour être initialisé, nécessite une connexion de base de données. Si l’utilisateur ne demande jamais à afficher les commandes ou à utiliser les données dans un calcul, il est inutile d’utiliser la mémoire système ou les cycles de calcul pour les créer. En utilisant `Lazy<Orders>` pour déclarer l’objet `Orders` en vue de son initialisation tardive, vous évitez de gaspiller les ressources système lorsque l’objet n’est pas utilisé.  
  
- Si vous avez un objet qui est coûteux à créer, et si vous souhaitez différer sa création jusqu’à ce que d’autres opérations coûteuses soient terminées. Par exemple, supposons que votre programme charge plusieurs instances d’objet lorsqu’il démarre, mais que seules certaines d’entre elles soient immédiatement nécessaires. Vous pouvez améliorer les performances de démarrage du programme en différant l’initialisation des objets qui ne sont pas nécessaires tant que les objets nécessaires n’ont pas été créés.  
  
 Même si vous pouvez écrire votre propre code pour effectuer une initialisation tardive, nous vous recommandons d’utiliser <xref:System.Lazy%601>. <xref:System.Lazy%601> et ses types associés prennent également en charge la cohérence de thread et fournissent une stratégie cohérente de propagation des exceptions.  
  
 Le tableau suivant répertorie les types fournis par le .NET Framework version 4 pour permettre l’initialisation tardive dans différents scénarios.  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Classe wrapper qui fournit une sémantique d’initialisation tardive pour toute bibliothèque de classes ou type défini par l’utilisateur.|  
|<xref:System.Threading.ThreadLocal%601>|Similaire à <xref:System.Lazy%601>, sauf qu’il fournit une sémantique d’initialisation tardive en fonction du thread local. Chaque thread a accès à sa propre valeur.|  
|<xref:System.Threading.LazyInitializer>|Fournit des méthodes `static` avancées (`Shared` en Visual Basic) pour l’initialisation tardive des objets, sans la surcharge d’une classe.|  
  
## <a name="basic-lazy-initialization"></a>Initialisation tardive de base  
 Pour définir un type initialisé tardivement (par exemple, `MyType`), utilisez `Lazy<MyType>` (`Lazy(Of MyType)` en Visual Basic), comme illustré dans l’exemple suivant. Si aucun délégué n’est passé dans le constructeur <xref:System.Lazy%601>, le type encapsulé est créé à l’aide de <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> lors du premier accès à la propriété de la valeur. Si le type n’a pas de constructeur sans paramètre, une exception Runtime est levée.  
  
 Dans l’exemple suivant, supposons que `Orders` soit une classe qui contienne un tableau d’objets `Order` récupérés à partir d’une base de données. Un objet `Customer` contient une instance de `Orders`, mais en fonction des actions de l’utilisateur, les données de l’objet `Orders` peuvent ne pas être nécessaires.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Vous pouvez également passer un délégué dans le constructeur <xref:System.Lazy%601> qui appelle une surcharge de constructeur sur le type encapsulé au moment de la création, et effectuer d’autres étapes d’initialisation nécessaires, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Une fois que l’objet différé est créé, aucune instance de `Orders` n’est créée tant que la propriété <xref:System.Lazy%601.Value%2A> de la variable tardive n’a pas fait l’objet d’un accès. Lors du premier accès à la propriété, le type encapsulé est créé, retourné, puis stocké en vue d’une utilisation ultérieure.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Un objet <xref:System.Lazy%601> retourne toujours le même objet (ou la même valeur) qui a été utilisé lors de son initialisation. Par conséquent, la propriété <xref:System.Lazy%601.Value%2A> est en lecture seule. Si <xref:System.Lazy%601.Value%2A> stocke un type référence, vous ne pouvez pas lui attribuer un nouvel objet (Toutefois, vous pouvez modifier la valeur de ses propriétés et champs publics définissables.) Si <xref:System.Lazy%601.Value%2A> stocke un type valeur, vous ne pouvez pas modifier sa valeur. Toutefois, vous pouvez créer une variable en rappelant le constructeur de variable à l’aide de nouveaux arguments.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 La nouvelle instance tardive, comme la précédente, n’instancie pas `Orders` tant que sa propriété <xref:System.Lazy%601.Value%2A> n’a pas fait l’objet d’un accès.  
  
### <a name="thread-safe-initialization"></a>Initialisation thread-safe  
 Par défaut, les objets <xref:System.Lazy%601> sont thread-safe. Autrement dit, si le constructeur ne spécifie pas le type de cohérence de thread, les objets <xref:System.Lazy%601> qu’il crée sont thread-safe. Dans les scénarios multithreads, le premier thread qui accède à la propriété <xref:System.Lazy%601.Value%2A> d’un objet <xref:System.Lazy%601> thread-safe initialise celui-ci pour tous les accès suivants sur tous les threads. De plus, tous les threads partagent les mêmes données. Par conséquent, le thread qui initialise l’objet importe peu, et les conditions de concurrence sont sans conséquences.  
  
> [!NOTE]
> Vous pouvez étendre cette cohérence aux conditions d’erreur à l’aide de la mise en cache des exceptions. Pour plus d’informations, consultez la section suivante, [Exceptions des objets différés](lazy-initialization.md#ExceptionsInLazyObjects).  
  
 L’exemple suivant montre que la même instance `Lazy<int>` a la même valeur pour trois threads différents.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Si chaque thread doit contenir des données distinctes, utilisez le type <xref:System.Threading.ThreadLocal%601>, comme décrit plus loin dans cette rubrique.  
  
 Certains constructeurs <xref:System.Lazy%601> ont un paramètre booléen nommé `isThreadSafe` qui permet de spécifier si la propriété <xref:System.Lazy%601.Value%2A> est accessible à partir de plusieurs threads. Si vous envisagez d’accéder à la propriété à partir d’un seul thread, vous pouvez passer `false` pour obtenir un gain de performances modeste. Si vous avez l’intention d’accéder à la propriété à partir de plusieurs threads, passez `true` pour indiquer à l’instance <xref:System.Lazy%601> qu’elle doit gérer correctement les conditions de concurrence dans lesquelles un thread lève une exception au moment de l’initialisation.  
  
 Certains constructeurs <xref:System.Lazy%601> ont un paramètre <xref:System.Threading.LazyThreadSafetyMode> nommé `mode`. Ces constructeurs fournissent un mode de cohérence de thread supplémentaire. Le tableau suivant montre comment la cohérence de thread d’un objet <xref:System.Lazy%601> est affectée par les paramètres du constructeur qui spécifient la cohérence de thread. Chaque constructeur comprend un tel paramètre.  
  
|Cohérence de thread de l’objet|`LazyThreadSafetyMode``mode`paramètre|Paramètre `isThreadSafe` booléen|Aucun paramètre de cohérence de thread|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Entièrement thread-safe. Seul un thread à la fois tente d’initialiser la valeur.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Oui.|  
|Non thread-safe.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Non applicable.|  
|Entièrement thread-safe. Concurrence de threads pour initialiser la valeur.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Non applicable.|Non applicable.|  
  
 Comme le montre le tableau, spécifier <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> pour le paramètre `mode` équivaut à spécifier `true` pour le paramètre `isThreadSafe`, et spécifier <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> revient à spécifier `false`.  
  
 Le fait de spécifier <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> permet à plusieurs threads de tenter d’initialiser l’instance <xref:System.Lazy%601>. Seul un thread peut gagner cette course. Tous les autres threads reçoivent la valeur qui a été initialisée par le thread gagnant. Si une exception est levée sur un thread pendant l’initialisation, ce thread ne reçoit pas la valeur définie par le thread gagnant. Les exceptions ne sont pas mises en cache. De fait, une nouvelle tentative d’accès à la propriété <xref:System.Lazy%601.Value%2A> peut aboutir à une initialisation. Ce traitement des exceptions est différent de celui des autres modes, et fait l’objet de la section suivante. Pour plus d’informations, consultez l’énumération <xref:System.Threading.LazyThreadSafetyMode>.  
  
<a name="ExceptionsInLazyObjects"></a>
## <a name="exceptions-in-lazy-objects"></a>Exceptions des objets différés  
 Comme indiqué précédemment, un objet <xref:System.Lazy%601> retourne toujours le même objet (ou la même valeur) avec lequel il a été initialisé. De fait, la propriété <xref:System.Lazy%601.Value%2A> est en lecture seule. Si vous activez la mise en cache des exceptions, cette immuabilité s’étend également au comportement des exceptions. Si la mise en cache des exceptions est activée pour un objet initialisé tardive et qu’une exception est levée à partir de sa méthode d’initialisation lors du <xref:System.Lazy%601.Value%2A> premier accès à la propriété, cette même exception est levée à chaque tentative suivante d’accès à la <xref:System.Lazy%601.Value%2A> propriété. En d’autres termes, le constructeur du type encapsulé n’est jamais rappelé, même dans les scénarios multithreads. Par conséquent, l’objet <xref:System.Lazy%601> ne peut pas lever une exception lors d’un accès et retourner une valeur lors d’un accès ultérieur.  
  
 La mise en cache des exceptions est activée lorsque vous utilisez un constructeur <xref:System.Lazy%601?displayProperty=nameWithType> qui accepte une méthode d’initialisation (un paramètre `valueFactory`). Par exemple, elle est activée lorsque vous utilisez le constructeur `Lazy(T)(Func(T))`. Si le constructeur accepte également une valeur <xref:System.Threading.LazyThreadSafetyMode> (un paramètre `mode`), spécifiez <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> ou <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. La spécification d’une méthode d’initialisation permet la mise en cache des exceptions pour ces deux modes. La méthode d’initialisation peut être très simple. Par exemple, il peut appeler le constructeur sans paramètre pour `T` : `new Lazy<Contents>(() => new Contents(), mode)` en C#, ou `New Lazy(Of Contents)(Function() New Contents())` dans Visual Basic. Si vous utilisez un constructeur <xref:System.Lazy%601?displayProperty=nameWithType> qui ne spécifie pas de méthode d’initialisation, les exceptions levées par le constructeur sans paramètre pour `T` ne sont pas mises en cache. Pour plus d’informations, consultez l’énumération <xref:System.Threading.LazyThreadSafetyMode>.  
  
> [!NOTE]
> Si vous créez un objet <xref:System.Lazy%601> avec le paramètre de constructeur `isThreadSafe` défini sur `false` ou le paramètre de constructeur `mode` défini sur <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, vous devez accéder à l’objet <xref:System.Lazy%601> à partir d’un thread unique ou fournir votre propre synchronisation. Cela s’applique à tous les aspects de l’objet, y compris la mise en cache des exceptions.  
  
 Comme indiqué dans la section précédente, les objets <xref:System.Lazy%601> créés en spécifiant <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> traitent les exceptions différemment. Avec <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, plusieurs threads peuvent rivaliser pour initialiser l’instance <xref:System.Lazy%601>. Dans ce cas, les exceptions ne sont pas mises en cache, et les tentatives d’accès à la propriété <xref:System.Lazy%601.Value%2A> peuvent continuer jusqu’à ce que l’initialisation soit effectuée.  
  
 Le tableau suivant récapitule la façon dont les constructeurs <xref:System.Lazy%601> contrôlent la mise en cache des exceptions.  
  
|Constructeur|Mode de cohérence de thread|Utilise la méthode d’initialisation|Exceptions mises en cache|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Non|Non|  
|Lazy(T)(Func(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Oui|Oui|  
|Lazy(T)(Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) ou `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Non|Non|  
|Lazy(T)(Func(T), Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) ou `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Oui|Oui|  
|Lazy(T)(LazyThreadSafetyMode)|Spécifié par l’utilisateur|Non|Non|  
|Lazy(T)(Func(T), LazyThreadSafetyMode)|Spécifié par l’utilisateur|Yes|Non, si l’utilisateur spécifie <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly> ; sinon, Oui.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Implémentation d’une propriété à initialisation tardive  
 Pour implémenter une propriété publique à l’aide de l’initialisation tardive, définissez le champ de stockage de la propriété comme un <xref:System.Lazy%601>, puis retournez la propriété <xref:System.Lazy%601.Value%2A> à partir de l’accesseur `get` de la propriété.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 La propriété <xref:System.Lazy%601.Value%2A> est en lecture seule, par conséquent, la propriété qui l’expose n’a pas d’accesseur `set`. Si vous avez besoin d’une propriété en lecture/écriture stockée par un objet <xref:System.Lazy%601>, l’accesseur `set` doit créer un nouvel objet <xref:System.Lazy%601> et l’assigner au magasin de stockage. L’accesseur `set` doit créer une expression lambda qui retourne la nouvelle valeur de propriété qui a été passée à l’accesseur `set`, et passer cette expression lambda au constructeur pour le nouvel objet <xref:System.Lazy%601>. Le prochain accès à la propriété <xref:System.Lazy%601.Value%2A> va entraîner l’initialisation du nouveau <xref:System.Lazy%601>, et sa propriété <xref:System.Lazy%601.Value%2A> va alors retourner la nouvelle valeur qui a été affectée à la propriété. L’objectif de cet arrangement complexe est de conserver les protections de multithreading intégrées à <xref:System.Lazy%601>. Sans cela, les accesseurs de propriété devraient mettre en cache la première valeur retournée par la propriété <xref:System.Lazy%601.Value%2A> et modifier uniquement la valeur mise en cache. En plus, vous auriez à écrire votre propre code thread-safe pour réaliser cela. En raison des initialisations supplémentaires exigées par une propriété en lecture/écriture stockée dans un objet <xref:System.Lazy%601>, les performances peuvent ne pas être acceptables. De plus, selon le scénario, une coordination supplémentaire peut être nécessaire pour éviter des conditions de concurrence entre les méthodes setter et getter.  
  
## <a name="thread-local-lazy-initialization"></a>Initialisation tardive de thread local  
 Dans certains scénarios multithreads, vous pouvez souhaiter que chaque thread ait ses propres données privées. Ces données sont appelées *données de thread local*. Dans le .NET Framework 3.5 et versions antérieures, vous pouvez appliquer l’attribut `ThreadStatic` à une variable statique pour qu’elle devienne une variable de thread local. Toutefois, l’utilisation de l’attribut `ThreadStatic` peut entraîner des erreurs subtiles. Par exemple, même avec des instructions d’initialisation basiques, la variable est initialisée uniquement sur le premier thread qui y accède, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Sur tous les autres threads, la variable est initialisée à l’aide de sa valeur par défaut (zéro). En guise d’alternative dans le .NET Framework version 4, vous pouvez utiliser le type <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> pour créer une variable de thread local basée sur l’instance, qui est initialisée sur tous les threads par le délégué <xref:System.Action%601> que vous fournissez. Dans l’exemple suivant, tous les threads qui accèdent à `counter` vont voir que sa valeur de départ est égale à 1.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> encapsule son objet de la même façon que <xref:System.Lazy%601>, avec toutefois ces différences essentielles :  
  
- Chaque thread initialise la variable de thread local à l’aide de ses données privées, qui ne sont pas accessibles par d’autres threads.  
  
- La propriété <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> est en lecture-écriture et peut être modifiée autant de fois que nécessaire. Cela peut affecter la propagation des exceptions. Par exemple, une opération `get` peut lever une exception, mais celle qui suit peut initialiser la valeur.  
  
- Si aucun délégué d’initialisation n’est fourni, <xref:System.Threading.ThreadLocal%601> va initialiser son type encapsulé à l’aide de la valeur par défaut du type. À cet égard, <xref:System.Threading.ThreadLocal%601> est cohérent avec l’attribut <xref:System.ThreadStaticAttribute>.  
  
 L’exemple suivant montre que chaque thread qui accède à l’instance `ThreadLocal<int>` obtient sa propre copie des données.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Variables de thread local dans Parallel.For et ForEach  
 Lorsque vous utilisez la méthode <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ou <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pour parcourir des sources de données en parallèle, vous pouvez utiliser les surcharges qui ont une prise en charge intégrée pour les données de thread local. Dans ces méthodes, pour obtenir des données de thread local, vous devez utiliser des délégués locaux pour créer ces données, y accéder et les nettoyer. Pour plus d’informations, consultez [Guide pratique pour écrire une boucle Parallel.For avec des variables locales de thread](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) et [Guide pratique pour écrire une boucle Parallel.ForEach avec des variables locales de partition](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Utilisation de l’initialisation tardive pour les scénarios de faible charge  
 Dans les scénarios où vous devez initialiser tardivement un grand nombre d’objets, vous pouvez décider que l’encapsulation de chaque objet dans un <xref:System.Lazy%601> nécessite trop de mémoire ou trop de ressources informatiques. Vous pouvez aussi avoir des exigences strictes sur la façon dont l’initialisation tardive est exposée. Dans ce cas, vous pouvez utiliser les méthodes `static` (`Shared` en Visual Basic) de la classe <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> pour initialiser tardivement chaque objet sans l’encapsuler dans une instance de <xref:System.Lazy%601>.  
  
 Dans l’exemple suivant, supposons que, au lieu d’encapsuler un objet `Orders` entier dans un objet <xref:System.Lazy%601>, vous n’avez que des objets `Order` initialisés tardivement seulement lorsqu’ils sont nécessaires.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 Dans cet exemple, notez que la procédure d’initialisation est appelée sur chaque itération de la boucle. Dans les scénarios multithreads, le premier thread à appeler la procédure d’initialisation est celui dont la valeur est visible par tous les threads. Les threads suivants appellent également la procédure d’initialisation, mais leurs résultats ne sont pas utilisés. Si ce type de condition de concurrence potentielle n’est pas acceptable, utilisez la surcharge de <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> qui accepte un argument booléen et un objet de synchronisation.  
  
## <a name="see-also"></a>Voir aussi

- [Concepts de base du threading managé](../../standard/threading/managed-threading-basics.md)
- [Threads et threads](../../standard/threading/threads-and-threading.md)
- [Bibliothèque parallèle de tâches](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Comment : effectuer une initialisation tardive d'objets](how-to-perform-lazy-initialization-of-objects.md)
