---
title: Conception des propriétés
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: 5d5cdbfdb38c7aebaca6cbcdeb63959ac12884e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709125"
---
# <a name="property-design"></a>Conception des propriétés
Bien que les propriétés soient techniquement très similaires aux méthodes, elles sont très différentes en termes de scénarios d’utilisation. Elles doivent être considérées comme des champs intelligents. Ils ont la syntaxe d’appel des champs et la flexibilité des méthodes.  
  
 **✓ DO** créer des propriétés get-only si l’appelant ne doit pas être en mesure de modifier la valeur de la propriété.  
  
 Gardez à l’esprit que si le type de la propriété est un type référence mutable, la valeur de la propriété peut être modifiée même si la propriété est en extraction seule.  
  
 **X DO NOT** fournissent des propriétés ou propriétés à définir uniquement avec la méthode setter ayant le plus large d’accessibilité de l’accesseur Get.  
  
 Par exemple, n’utilisez pas de propriétés avec un accesseur Set public et un accesseur Get protégé.  
  
 Si l’accesseur Get de la propriété ne peut pas être fourni, implémentez la fonctionnalité comme une méthode à la place. Envisagez de démarrer le nom de la méthode avec `Set` et suivez ce que vous auriez nommé la propriété. Par exemple, <xref:System.AppDomain> a une méthode appelée `SetCachePath` au lieu d’avoir une propriété définie uniquement appelée `CachePath`.  
  
 **✓ DO** fournissent des valeurs par défaut raisonnables pour toutes les propriétés, garantissant que les valeurs par défaut n’entraînent pas une faille de sécurité ou du code très inefficace.  
  
 **✓ DO** permettent d’être définie dans n’importe quel ordre, même si cela aboutit à un état temporaire non valide de l’objet.  
  
 Il est courant que deux propriétés ou plus soient associées à un point où certaines valeurs d’une propriété peuvent ne pas être valides étant donné les valeurs d’autres propriétés sur le même objet. Dans ce cas, les exceptions résultant de l’état non valide doivent être reportées jusqu’à ce que les propriétés interdépendantes soient utilisées ensemble par l’objet.  
  
 **✓ DO** conserver la valeur précédente si un accesseur Set de propriété lève une exception.  
  
 **X AVOID** lever des exceptions à partir des accesseurs Get de propriété.  
  
 Les accesseurs get de propriété doivent être des opérations simples et ne doivent pas avoir de conditions préalables. Si un accesseur Get peut lever une exception, il doit probablement être remanié pour être une méthode. Notez que cette règle ne s’applique pas aux indexeurs, où nous attendons des exceptions en raison de la validation des arguments.  
  
### <a name="indexed-property-design"></a>Conception des propriétés indexées  
 Une propriété indexée est une propriété spéciale qui peut avoir des paramètres et qui peut être appelée avec une syntaxe spéciale similaire à l’indexation de tableau.  
  
 Les propriétés indexées sont communément appelées indexeurs. Les indexeurs ne doivent être utilisés que dans les API qui permettent d’accéder aux éléments d’une collection logique. Par exemple, une chaîne est une collection de caractères, et l’indexeur sur <xref:System.String?displayProperty=nameWithType> a été ajouté pour accéder à ses caractères.  
  
 **✓ CONSIDER** des indexeurs pour fournir l’accès aux données stockées dans un tableau interne.  
  
 **✓ CONSIDER** fournir des indexeurs sur les types de collections d’éléments.  
  
 **X AVOID** à l’aide des propriétés avec plusieurs paramètres indexées.  
  
 Si la conception requiert plusieurs paramètres, reconsidérez si la propriété représente vraiment un accesseur à une collection logique. Si ce n’est pas le cas, utilisez plutôt des méthodes. Envisagez de démarrer le nom de la méthode avec `Get` ou `Set`.  
  
 **X AVOID** indexeurs avec les types de paramètres autres que <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, ou d’un enum.  
  
 Si la conception requiert d’autres types de paramètres, réévaluez fortement si l’API représente vraiment un accesseur à une collection logique. Si ce n’est pas le cas, utilisez une méthode. Envisagez de démarrer le nom de la méthode avec `Get` ou `Set`.  
  
 **✓ DO** utiliser le nom `Item` pour des propriétés indexées, sauf s’il existe un meilleur nom (par exemple, consultez la <xref:System.String.Chars%2A> propriété sur `System.String`).  
  
 Dans C#, les indexeurs sont par défaut un élément nommé. Le <xref:System.Runtime.CompilerServices.IndexerNameAttribute> peut être utilisé pour personnaliser ce nom.  
  
 **X DO NOT** fournissent à la fois un indexeur et des méthodes qui sont sémantiquement équivalents.  
  
 **X DO NOT** fournissent plusieurs familles d’indexeurs surchargés dans un type.  
  
 Cela est appliqué par le C# compilateur.  
  
 **X DO NOT** différent de l’utilisation des propriétés indexées.  
  
 Cela est appliqué par le C# compilateur.  
  
### <a name="property-change-notification-events"></a>Événements de notification de modification de propriété  
 Parfois, il est utile de fournir un événement pour notifier l’utilisateur des modifications apportées à une valeur de propriété. Par exemple, `System.Windows.Forms.Control` déclenche un événement `TextChanged` après la modification de la valeur de sa propriété `Text`.  
  
 **✓ CONSIDER** modifier les déclenchement d’événements de notification lorsque les valeurs de propriété dans les API de niveau supérieur (composants de concepteur généralement) sont modifiés.  
  
 S’il existe un bon scénario pour qu’un utilisateur sache quand une propriété d’un objet change, l’objet doit déclencher un événement de notification de modification pour la propriété.  
  
 Toutefois, il est peu probable qu’il soit nécessaire de déclencher de tels événements pour les API de bas niveau, telles que les types de base ou les collections. Par exemple, <xref:System.Collections.Generic.List%601> ne déclencherait pas de tels événements lorsqu’un nouvel élément est ajouté à la liste et que la propriété `Count` change.  
  
 **✓ CONSIDER** déclenchement modifier les événements de notification lorsque la valeur d’une propriété modifiée via la force externe.  
  
 Si une valeur de propriété change via une force externe (d’une manière autre que en appelant des méthodes sur l’objet), les événements Raise indiquent au développeur que la valeur change et a changé. Le `Text` propriété d’un contrôle zone de texte en est un bon exemple. Lorsque l’utilisateur tape du texte dans un `TextBox`, la valeur de la propriété change automatiquement.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
