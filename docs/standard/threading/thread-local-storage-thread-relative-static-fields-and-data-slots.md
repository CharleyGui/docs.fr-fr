---
title: 'Stockage local des threads : champs static et emplacements de données relatifs à un thread'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], local storage
- threading [.NET], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
ms.openlocfilehash: f80cc09d87116d3daff8047c1d1398c5e6104178
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188157"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Stockage local des threads : champs static et emplacements de données relatifs à un thread

Vous pouvez utiliser le stockage local des threads managés (TLS) pour stocker des données propres à un thread et à un domaine d’application. .NET offre deux façons d’utiliser TLS géré : les champs statiques relatifs à un thread et les emplacements de données.  
  
- Utilisez les champs statiques relatifs à un thread (champs `Shared` relatifs à un thread en Visual Basic) si vous pouvez anticiper vos besoins précis au moment de la compilation. Les champs statiques relatifs à un thread offrent les meilleures performances. Ils vous offrent également les avantages du contrôle de type au moment de la compilation.  
  
- Utilisez des emplacements de données lorsque vos exigences réelles peuvent être détectées uniquement au moment de l’exécution. Les emplacements de données sont plus lents et plus difficiles à utiliser que les champs statiques relatifs à un thread, et les données sont stockées en tant que type <xref:System.Object>, de sorte que vous devez les caster en tant que type correct avant de les utiliser.  
  
 Dans C++ non géré, vous utilisez `TlsAlloc` pour allouer dynamiquement des emplacements et `__declspec(thread)` pour déclarer qu’une variable doit être allouée dans un stockage relatif à un thread. Des champs statiques relatifs à un thread et des emplacements de données fournissent la version managée de ce comportement.  
  
Vous pouvez utiliser la <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> classe pour créer des objets locaux de thread qui sont initialisés tardivement lorsque l’objet est consommé pour la première fois. Pour plus d’informations, consultez [Initialisation tardive](../../framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Unicité des données dans TLS managé  
 Si vous utilisez les champs statiques relatifs à un thread ou des emplacements de données, les données dans TLS managé sont uniques à la combinaison du thread et du domaine d’application.  
  
- Au sein d’un domaine d’application, un thread ne peut pas modifier des données à partir d’un autre thread, même lorsque les deux threads utilisent le même emplacement ou champ.  
  
- Lorsqu’un thread accède au même emplacement ou champ à partir de plusieurs domaines d’application, une valeur séparée est maintenue dans chaque domaine d’application.  
  
 Par exemple, si un thread définit la valeur d’un champ statique relatif à un thread, passe à un autre domaine d’application, puis récupère la valeur du champ, la valeur récupérée dans le deuxième domaine d’application est différente de la valeur dans le premier domaine d’application. La définition d’une nouvelle valeur pour le champ dans le deuxième domaine d’application n’affecte pas la valeur du champ dans le premier domaine d’application.  
  
 De même, lorsqu’un thread obtient le même emplacement de données nommé dans deux domaines d’application différents, les données dans le premier domaine d’application restent indépendantes des données dans le deuxième domaine d’application.  
  
## <a name="thread-relative-static-fields"></a>Champs statiques relatifs à un thread  
 Si vous savez qu’un élément de données est toujours unique à un thread et à une combinaison de domaines d’application, appliquez l’attribut <xref:System.ThreadStaticAttribute> dans le champ statique. Utilisez le champ comme vous utiliseriez tout autre champ statique. Les données dans le champ sont uniques à chaque thread qui les utilise.  
  
 Les champs statiques relatifs à un thread fournissent de meilleures performances que les emplacements de données et offrent l’avantage du contrôle de type au moment de la compilation.  
  
 N’oubliez pas que tout code de constructeur de classe s’exécutera sur le premier thread dans le premier contexte qui accède au champ. Dans tous les autres threads ou contextes du même domaine d’application, les champs seront initialisés à `null` (`Nothing` en Visual Basic) s’ils sont de types référence ou à leurs valeurs par défaut s’ils sont de types valeur. Par conséquent, vous ne devriez pas vous fier à des constructeurs de classe pour initialiser des champs statiques relatifs à un thread. Au lieu de cela, évitez d’initialiser des champs statiques relatifs à un thread et supposez qu’ils sont initialisés à `null` (`Nothing`) ou à leurs valeurs par défaut.  
  
## <a name="data-slots"></a>Emplacements de données  

.NET fournit des emplacements de données dynamiques qui sont uniques à une combinaison de thread et de domaine d’application. Il existe deux types d’emplacements de données : des emplacements nommés et des emplacements sans nom. Tous deux sont implémentés à l’aide de la structure <xref:System.LocalDataStoreSlot>.  
  
- Pour créer un emplacement de données nommé, utilisez la méthode <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> ou <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>. Pour obtenir une référence à un emplacement nommé existant, passez son nom à la méthode <xref:System.Threading.Thread.GetNamedDataSlot%2A>.  
  
- Pour créer un emplacement de données non nommé, utilisez la méthode <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType>.  
  
 Pour les emplacements nommés et non nommés, utilisez les méthodes <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> pour définir et récupérer les informations contenues dans l’emplacement. Il s’agit de méthodes statiques qui agissent toujours sur les données pour le thread qui les exécute actuellement.  
  
 Les emplacements nommés peuvent être pratiques, car vous pouvez récupérer l’emplacement lorsque vous en avez besoin en passant son nom à la <xref:System.Threading.Thread.GetNamedDataSlot%2A> méthode, au lieu de conserver une référence à un emplacement sans nom. Toutefois, si un autre composant utilise le même nom pour son stockage relatifs à un thread et qu’un thread exécute du code à partir de votre composant comme de l’autre composant, chacun d’eux peut endommager les données de l’autre. (Ce scénario suppose que les deux composants s’exécutent dans le même domaine d’application, et qu’ils ne sont pas conçus pour partager les mêmes données.)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [Thread](index.md)
