---
title: "Guide pratique : ajouter et supprimer des éléments d'un ConcurrentDictionary"
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 6e5204c5a71232ef9d1a050891e7fe6d92c375f2
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796117"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Guide pratique : ajouter et supprimer des éléments d'un ConcurrentDictionary

Cet exemple montre comment ajouter, extraire, mettre à jour et supprimer des éléments dans un <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Cette classe de collection est une implémentation thread-safe. Nous vous recommandons de l’utiliser chaque fois que plusieurs threads tentent d’accéder aux éléments de façon simultanée.

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> fournit plusieurs méthodes pratiques qui permettent au code de ne plus avoir à vérifier au préalable si une clé existe avant d’essayer d’ajouter ou de supprimer des données. Le tableau suivant répertorie ces méthodes pratiques et indique quand les utiliser.

| Méthode | À utiliser quand… |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | Vous voulez ajouter une nouvelle valeur pour une clé spécifiée et, si la clé existe déjà, vous souhaitez remplacer sa valeur. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | Vous voulez récupérer la valeur existante d’une clé spécifiée et, si la clé n’existe pas, vous voulez spécifier une paire clé/valeur. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A> | Vous voulez ajouter, obtenir, mettre à jour ou supprimer une paire clé/valeur, et, si la clé existe déjà ou si la tentative échoue pour une autre raison, vous voulez prendre une autre mesure. |

## <a name="example"></a> Exemple

L’exemple suivant utilise deux instances de<xref:System.Threading.Tasks.Task> pour ajouter des éléments à un <xref:System.Collections.Concurrent.ConcurrentDictionary%602> simultanément, puis sort tout le contenu pour montrer que les éléments ont été ajoutés avec succès. L’exemple montre également comment utiliser les <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>méthodes, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>et <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> pour ajouter, mettre à jour et récupérer des éléments de la collection.

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> est conçu pour les scénarios multithreads. Vous n’avez pas besoin d’utiliser des verrous dans votre code pour ajouter ou supprimer des éléments dans la collection. Toutefois, il est toujours possible pour un thread de récupérer une valeur et pour un autre thread de mettre à jour immédiatement la collection en donnant une nouvelle valeur à la même clé.

En outre, bien que toutes les méthodes de <xref:System.Collections.Concurrent.ConcurrentDictionary%602> soient thread-safe, toutes les méthodes sont atomiques, en particulier <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> et <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Le délégué utilisateur passé à ces méthodes est appelé en dehors du verrou interne du dictionnaire (cette opération est effectuée pour empêcher du code inconnu de bloquer tous les threads). Par conséquent, la séquence d’événements suivante peut se produire :

1. le _ThreadA_ appelle <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, ne trouve aucun élément et crée un nouvel élément à ajouter en appelant `valueFactory` le délégué.

1. _threadB_ le threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> appelle simultanément, son `valueFactory` délégué est appelé et il atteint le verrou interne avant le _ThreadA_. sa nouvelle paire clé-valeur est alors ajoutée au dictionnaire.

1. le délégué utilisateur _du ThreadA_ se termine et le thread arrive au verrou, mais il constate que l’élément existe déjà.

1. _ThreadA_ effectue une « récupération » et retourne les données précédemment ajoutées par le _threadB_.

Par conséquent, il n’est pas garanti que les données retournées par <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> sont les mêmes que celles créées par le du `valueFactory`thread. Une séquence d’événements similaire peut se produire lors de l’appel de la méthode <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Collections thread-safe](../../../../docs/standard/collections/thread-safe/index.md)
