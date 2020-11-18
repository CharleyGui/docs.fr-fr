---
title: Instructions relatives aux collections
ms.date: 10/22/2008
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 2306462d933e71d0d23021a0e036e8cc23100c68
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821084"
---
# <a name="guidelines-for-collections"></a>Instructions relatives aux collections
Tout type conçu spécifiquement pour manipuler un groupe d’objets ayant des caractéristiques communes peut être considéré comme une collection. Il est presque toujours approprié pour que ces types implémentent <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> . par conséquent, dans cette section, nous prenons uniquement en compte les types qui implémentent l’une de ces interfaces, ou les deux, pour être des collections.

 ❌ N’utilisez pas de collections faiblement typées dans les API publiques.

 Le type de toutes les valeurs de retour et paramètres représentant les éléments de la collection doit être le type d’élément exact, et non l’un de ses types de base (cela s’applique uniquement aux membres publics de la collection).

 ❌ N’utilisez pas <xref:System.Collections.ArrayList> ou <xref:System.Collections.Generic.List%601> dans les API publiques.

 Ces types sont des structures de données conçues pour être utilisées dans une implémentation interne, et non dans des API publiques. `List<T>` est optimisé pour les performances et la puissance au détriment du nettoyage des API et de la flexibilité. Par exemple, si vous retournez `List<T>` , vous ne serez jamais en mesure de recevoir des notifications lorsque le code client modifie la collection. En outre, `List<T>` expose de nombreux membres, tels que <xref:System.Collections.Generic.List%601.BinarySearch%2A> , qui ne sont pas utiles ou applicables dans de nombreux scénarios. Les deux sections suivantes décrivent les types (abstractions) conçus spécifiquement pour une utilisation dans les API publiques.

 ❌ N’utilisez pas `Hashtable` ou `Dictionary<TKey,TValue>` dans les API publiques.

 Ces types sont des structures de données conçues pour être utilisées dans une implémentation interne. Les API publiques doivent utiliser <xref:System.Collections.IDictionary> , `IDictionary <TKey, TValue>` ou un type personnalisé qui implémente l’une des interfaces ou les deux.

 ❌ N’utilisez pas <xref:System.Collections.Generic.IEnumerator%601> , <xref:System.Collections.IEnumerator> ou tout autre type qui implémente l’une de ces interfaces, sauf en tant que type de retour d’une `GetEnumerator` méthode.

 Les types qui retournent des énumérateurs à partir de méthodes autres que `GetEnumerator` ne peuvent pas être utilisés avec l' `foreach` instruction.

 ❌ N’implémentez pas `IEnumerator<T>` et `IEnumerable<T>` sur le même type. Il en va de même pour les interfaces non génériques `IEnumerator` et `IEnumerable` .

## <a name="collection-parameters"></a>Paramètres de collection
 ✔️ Utilisez le type le moins spécialisé possible comme type de paramètre. La plupart des membres qui prennent des collections comme paramètres utilisent l' `IEnumerable<T>` interface.

 ❌ Évitez <xref:System.Collections.Generic.ICollection%601> d’utiliser ou <xref:System.Collections.ICollection> comme paramètre simplement pour accéder à la `Count` propriété.

 Au lieu de cela, envisagez d’utiliser `IEnumerable<T>` ou `IEnumerable` et de vérifier dynamiquement si l’objet implémente `ICollection<T>` ou `ICollection` .

## <a name="collection-properties-and-return-values"></a>Propriétés de collection et valeurs de retour
 ❌ NE fournissez pas de propriétés de collection définissables.

 Les utilisateurs peuvent remplacer le contenu de la collection en effaçant d’abord la collection, puis en ajoutant le nouveau contenu. Si le remplacement de l’ensemble de la collection est un scénario courant, envisagez de fournir la `AddRange` méthode sur la collection.

 ✔️ Utilisez `Collection<T>` ou une sous-classe de `Collection<T>` pour les propriétés ou les valeurs de retour représentant des collections en lecture/écriture.

 Si `Collection<T>` ne répond pas à certaines exigences (par exemple, si la collection ne doit pas implémenter <xref:System.Collections.IList> ), utilisez une collection personnalisée en implémentant `IEnumerable<T>` , `ICollection<T>` ou <xref:System.Collections.Generic.IList%601> .

 ✔️ Utilisez <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> , une sous-classe de `ReadOnlyCollection<T>` ou, dans de rares cas, `IEnumerable<T>` des propriétés ou des valeurs de retour représentant des collections en lecture seule.

 En général, préférez `ReadOnlyCollection<T>` . S’il ne répond pas à certaines exigences (par exemple, si la collection ne doit pas implémenter `IList` ), utilisez une collection personnalisée en implémentant `IEnumerable<T>` , `ICollection<T>` ou `IList<T>` . Si vous implémentez une collection en lecture seule personnalisée, implémentez `ICollection<T>.IsReadOnly` pour retourner `true` .

 Dans les cas où vous êtes certain que le seul scénario que vous souhaiterez peut-être prendre en charge est l’itération avant uniquement, vous pouvez simplement utiliser `IEnumerable<T>` .

 ✔️ envisagez d’utiliser des sous-classes de collections de base génériques au lieu d’utiliser directement les collections.

 Cela permet d’obtenir un meilleur nom et d’ajouter des membres d’assistance qui ne sont pas présents sur les types de collections de base. Cela s’applique en particulier aux API de haut niveau.

 ✔️ envisagez de retourner une sous-classe de `Collection<T>` ou `ReadOnlyCollection<T>` à partir de méthodes et de propriétés très couramment utilisées.

 Cela vous permettra d’ajouter des méthodes d’assistance ou de modifier l’implémentation de la collection à l’avenir.

 ✔️ envisagez d’utiliser une collection à clé si les éléments stockés dans la collection ont des clés uniques (noms, ID, etc.). Les collections à clé sont des collections qui peuvent être indexées à la fois par un entier et une clé et qui sont généralement implémentées à partir de `KeyedCollection<TKey,TItem>` .

 Les collections à clé sont généralement plus volumineuses et ne doivent pas être utilisées si la surcharge de mémoire compense les avantages de l’utilisation des clés.

 ❌ NE retournez pas de valeurs NULL à partir de propriétés de collection ou de méthodes qui retournent des collections. Retourne une collection vide ou un tableau vide à la place.

 La règle générale est que les collections ou tableaux null et vides (0 élément) doivent être traités de la même façon.

### <a name="snapshots-versus-live-collections"></a>Captures instantanées et collections en direct
 Les collections représentant un État à un moment donné sont appelées collections d’instantanés. Par exemple, une collection contenant des lignes retournées par une requête de base de données serait un instantané. Les collections qui représentent toujours l’état actuel sont appelées collections dynamiques. Par exemple, une collection d' `ComboBox` éléments est une collection en direct.

 ❌ NE retournez pas de collections d’instantanés à partir des propriétés. Les propriétés doivent retourner des collections dynamiques.

 Les accesseurs get de propriété doivent être des opérations très légères. Le retour d’un instantané requiert la création d’une copie d’une collection interne dans une opération O (n).

 ✔️ Utilisez soit une collection d’instantanés, soit un `IEnumerable<T>` en direct (ou son sous-type) pour représenter les collections volatiles (c’est-à-dire, qui peuvent changer sans modification explicite de la collection).

 En général, toutes les collections représentant une ressource partagée (par exemple, les fichiers dans un répertoire) sont volatiles. Ces collections sont très difficiles ou impossibles à implémenter en tant que collections dynamiques, sauf si l’implémentation est simplement un énumérateur avant uniquement.

## <a name="choosing-between-arrays-and-collections"></a>Choix entre les tableaux et les collections
 ✔️ préférez les collections sur les tableaux.

 Les collections permettent de mieux contrôler le contenu, peuvent évoluer au fil du temps et sont plus utilisables. En outre, il est déconseillé d’utiliser des tableaux pour les scénarios en lecture seule, car le coût du clonage du tableau est prohibitif. Les études de convivialité ont montré que certains développeurs se sentent plus à l’aise avec les API basées sur les collections.

 Toutefois, si vous développez des API de bas niveau, il peut être préférable d’utiliser des tableaux pour les scénarios de lecture-écriture. Les tableaux ont un faible encombrement mémoire, ce qui permet de réduire la plage de travail, et l’accès aux éléments d’un tableau est plus rapide, car il est optimisé par le Runtime.

 ✔️ envisagez d’utiliser des tableaux dans les API de bas niveau pour réduire la consommation de mémoire et optimiser les performances.

 ✔️ Utilisez des tableaux d’octets au lieu de collections d’octets.

 ❌ N’utilisez pas de tableaux pour les propriétés si la propriété doit retourner un nouveau tableau (par exemple, une copie d’un tableau interne) chaque fois que l’accesseur Get de propriété est appelé.

## <a name="implementing-custom-collections"></a>Implémentation de regroupements personnalisés
 ✔️ ENVISAGER d’hériter de `Collection<T>` , `ReadOnlyCollection<T>` ou lors de la `KeyedCollection<TKey,TItem>` conception de nouvelles collections.

 ✔️ implémenter `IEnumerable<T>` lors de la conception de nouvelles collections. Envisagez d’implémenter `ICollection<T>` ou même `IList<T>` là où cela est pertinent.

 Lors de l’implémentation de cette collection personnalisée, suivez le modèle d’API établi par et le plus `Collection<T>` `ReadOnlyCollection<T>` fidèlement possible. Autrement dit, implémentez les mêmes membres explicitement, nommez-les comme ces deux collections, et ainsi de suite.

 ✔️ envisagez d’implémenter des interfaces de collection non génériques ( `IList` et `ICollection` ) si la collection est souvent passée à des API acceptant ces interfaces comme entrée.

 ❌ Évitez d’implémenter des interfaces de collection sur des types avec des API complexes sans rapport avec le concept d’une collection.

 ❌ N’héritez pas de collections de base non génériques telles que `CollectionBase` . Utilisez `Collection<T>` , `ReadOnlyCollection<T>` et à la `KeyedCollection<TKey,TItem>` place.

### <a name="naming-custom-collections"></a>Nommer des collections personnalisées
 Les collections (types qui implémentent `IEnumerable` ) sont créées principalement pour deux raisons : (1) pour créer une nouvelle structure de données avec des opérations spécifiques à la structure et souvent différentes caractéristiques de performances que les structures de données existantes (par exemple,,,  <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.LinkedList%601> <xref:System.Collections.Generic.Stack%601> ) et (2) pour créer une collection spécialisée pour conserver un ensemble spécifique d’éléments (par exemple,  <xref:System.Collections.Specialized.StringCollection> ). Les structures de données sont le plus souvent utilisées dans l’implémentation interne des applications et des bibliothèques. Les collections spécialisées sont principalement exposées dans les API (en tant que types de propriété et de paramètre).

 ✔️ Utilisez le suffixe « dictionary » dans les noms d’abstractions implémentant `IDictionary` ou `IDictionary<TKey,TValue>` .

 ✔️ Utilisez le suffixe « collection » dans les noms des types `IEnumerable` qui implémentent (ou l’un de ses descendants) et qui représentent une liste d’éléments.

 ✔️ Utilisez le nom de structure de données approprié pour les structures de données personnalisées.

 ❌ Évitez d’utiliser des suffixes qui impliquent une implémentation particulière, telle que « LinkedList » ou « Hashtable », dans les noms des abstractions de collection.

 ✔️ envisagez de préfixer les noms de collections avec le nom du type d’élément. Par exemple, une collection qui stocke des éléments de type `Address` (implémentation `IEnumerable<Address>` ) doit être nommée `AddressCollection` . Si le type d’élément est une interface, le préfixe « I » du type d’élément peut être omis. Par conséquent, une collection d' <xref:System.IDisposable> éléments peut être appelée `DisposableCollection` .

 ✔️ envisagez d’utiliser le préfixe « ReadOnly » dans les noms de collections en lecture seule si une collection accessible en écriture correspondante peut être ajoutée ou existe déjà dans le Framework.

 Par exemple, une collection de chaînes en lecture seule doit être appelée `ReadOnlyStringCollection` .

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions d’utilisation](usage-guidelines.md)
