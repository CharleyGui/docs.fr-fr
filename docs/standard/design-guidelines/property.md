---
title: Conception des propriétés
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: ed287b98c012622caa5f8f1cc90fced90dda3e62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730966"
---
# <a name="property-design"></a>Conception des propriétés

Bien que les propriétés soient techniquement très similaires aux méthodes, elles sont très différentes en termes de scénarios d’utilisation. Elles doivent être considérées comme des champs intelligents. Ils ont la syntaxe d’appel des champs et la flexibilité des méthodes.

 ✔️ créer des propriétés d’extraction uniquement si l’appelant ne doit pas être en mesure de modifier la valeur de la propriété.

 Gardez à l’esprit que si le type de la propriété est un type référence mutable, la valeur de la propriété peut être modifiée même si la propriété est en extraction seule.

 ❌ NE fournissez pas de propriétés ou de propriétés définies uniquement avec la méthode setter dont l’accessibilité est plus étendue que l’accesseur Get.

 Par exemple, n’utilisez pas de propriétés avec un accesseur Set public et un accesseur Get protégé.

 Si l’accesseur Get de la propriété ne peut pas être fourni, implémentez la fonctionnalité comme une méthode à la place. Envisagez de démarrer le nom de la méthode avec `Set` et de suivre le nom de la propriété. Par exemple, <xref:System.AppDomain> a une méthode appelée `SetCachePath` au lieu d’avoir une propriété définie uniquement appelée `CachePath` .

 ✔️ fournissez des valeurs par défaut sensibles pour toutes les propriétés, en veillant à ce que les valeurs par défaut n’entraînent pas de brèche de sécurité ou de code peu efficace.

 ✔️ autorisez les propriétés à être définies dans n’importe quel ordre, même si cela se traduit par un État non valide temporaire de l’objet.

 Il est courant que deux propriétés ou plus soient associées à un point où certaines valeurs d’une propriété peuvent ne pas être valides étant donné les valeurs d’autres propriétés sur le même objet. Dans ce cas, les exceptions résultant de l’état non valide doivent être reportées jusqu’à ce que les propriétés interdépendantes soient utilisées ensemble par l’objet.

 ✔️ conserver la valeur précédente si un accesseur Set de propriété lève une exception.

 ❌ Évitez de lever des exceptions à partir des accesseurs get de propriété.

 Les accesseurs get de propriété doivent être des opérations simples et ne doivent pas avoir de conditions préalables. Si un accesseur Get peut lever une exception, il doit probablement être remanié pour être une méthode. Notez que cette règle ne s’applique pas aux indexeurs, où nous attendons des exceptions en raison de la validation des arguments.

### <a name="indexed-property-design"></a>Conception des propriétés indexées

 Une propriété indexée est une propriété spéciale qui peut avoir des paramètres et qui peut être appelée avec une syntaxe spéciale similaire à l’indexation de tableau.

 Les propriétés indexées sont communément appelées indexeurs. Les indexeurs ne doivent être utilisés que dans les API qui permettent d’accéder aux éléments d’une collection logique. Par exemple, une chaîne est une collection de caractères, et l’indexeur sur <xref:System.String?displayProperty=nameWithType> a été ajouté pour accéder à ses caractères.

 ✔️ envisagez d’utiliser des indexeurs pour fournir l’accès aux données stockées dans un tableau interne.

 ✔️ envisagez de fournir des indexeurs sur des types représentant des collections d’éléments.

 ❌ Évitez d’utiliser des propriétés indexées avec plusieurs paramètres.

 Si la conception requiert plusieurs paramètres, reconsidérez si la propriété représente vraiment un accesseur à une collection logique. Si ce n’est pas le cas, utilisez plutôt des méthodes. Envisagez de démarrer le nom de la méthode avec `Get` ou `Set` .

 ❌ Évitez les indexeurs avec des types de paramètres autres que <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Int64?displayProperty=nameWithType> ,, <xref:System.String?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> ou une énumération.

 Si la conception requiert d’autres types de paramètres, réévaluez fortement si l’API représente vraiment un accesseur à une collection logique. Si ce n’est pas le cas, utilisez une méthode. Envisagez de démarrer le nom de la méthode avec `Get` ou `Set` .

 ✔️ Utilisez le nom `Item` pour les propriétés indexées, sauf si un nom est évidemment mieux adapté (par exemple, consultez la <xref:System.String.Chars%2A> propriété sur `System.String` ).

 En C#, les indexeurs sont par défaut un élément nommé. Le <xref:System.Runtime.CompilerServices.IndexerNameAttribute> peut être utilisé pour personnaliser ce nom.

 ❌ NE fournissez pas à la fois un indexeur et des méthodes sémantiquement équivalentes.

 ❌ NE fournissez pas plusieurs familles d’indexeurs surchargés dans un même type.

 Cela est appliqué par le compilateur C#.

 ❌ N’utilisez pas de propriétés indexées qui ne sont pas des valeurs par défaut.

 Cela est appliqué par le compilateur C#.

### <a name="property-change-notification-events"></a>Événements de notification de modification de propriété

 Parfois, il est utile de fournir un événement pour notifier l’utilisateur des modifications apportées à une valeur de propriété. Par exemple, `System.Windows.Forms.Control` déclenche un `TextChanged` événement après la modification de la valeur de sa `Text` propriété.

 ✔️ envisagez de déclencher des événements de notification de modification lorsque des valeurs de propriété dans des API de haut niveau (généralement des composants de concepteur) sont modifiées.

 S’il existe un bon scénario pour qu’un utilisateur sache quand une propriété d’un objet change, l’objet doit déclencher un événement de notification de modification pour la propriété.

 Toutefois, il est peu probable qu’il soit nécessaire de déclencher de tels événements pour les API de bas niveau, telles que les types de base ou les collections. Par exemple, <xref:System.Collections.Generic.List%601> ne déclencherait pas ces événements lorsqu’un nouvel élément est ajouté à la liste et que la `Count` propriété est modifiée.

 ✔️ envisagez de déclencher des événements de notification de modification lorsque la valeur d’une propriété change via des forces externes.

 Si une valeur de propriété change via une force externe (d’une manière autre que en appelant des méthodes sur l’objet), les événements Raise indiquent au développeur que la valeur change et a changé. La `Text` propriété d’un contrôle Text Box en est un bon exemple. Lorsque l’utilisateur tape du texte dans un `TextBox` , la valeur de la propriété change automatiquement.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)
