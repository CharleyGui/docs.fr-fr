---
title: Noms de classes, de structures et d'interfaces
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400595"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Noms de classes, de structures et d'interfaces
Les lignes directrices de nommage qui suivent s’appliquent à la dénomination générale de type.

 ✔️ DO classes de noms et structs avec des noms ou des phrases de nom, en utilisant PascalCasing.

 Cela distingue les noms de type des méthodes, qui sont nommés avec des phrases verbe.

 ✔️ ne noms interfaces avec des phrases adjectifs, ou parfois avec des noms ou des phrases de nom.

 Les noms et les phrases de nom doivent être utilisés rarement et ils pourraient indiquer que le type doit être une classe abstraite, et non une interface.

 ❌NE PAS donner aux noms de classe un préfixe (p. ex., « C »).

 ✔️ CONSIDER terminant le nom des classes dérivées avec le nom de la classe de base.

 C’est très lisible et explique clairement la relation. Quelques exemples de cela `ArgumentOutOfRangeException`dans le code `Exception`sont: , qui est une sorte de , et `SerializableAttribute`, qui est une sorte de `Attribute`. Toutefois, il est important d’utiliser un jugement raisonnable pour appliquer cette directive; par exemple, `Button` la classe `Control` est une `Control` sorte d’événement, bien qu’il n’apparaît pas en son nom.

 ✔️ ne noms d’interface préfixe avec la lettre I, pour indiquer que le type est une interface.

 Par exemple, `IComponent` (nom descriptif), `ICustomAttributeProvider` (expression `IPersistable` de nom) et (adjectif) sont des noms d’interface appropriés. Comme avec d’autres noms de type, évitez les abréviations.

 ✔️ assurez-vous que les noms diffèrent uniquement par le préfixe " I " sur le nom de l’interface lorsque vous définissez une paire de classe-interface où la classe est une implémentation standard de l’interface.

## <a name="names-of-generic-type-parameters"></a>Noms des paramètres de type générique
 Des génériques ont été ajoutés à .NET Framework 2.0. La fonctionnalité a introduit un nouveau type d’identifiant appelé *paramètre*de type .

 ✔️ NE nomment des paramètres de type générique avec des noms descriptifs à moins qu’un nom d’une seule lettre ne soit complètement explicite et qu’un nom descriptif n’ajoute pas de valeur.

 ✔️ CONSIDER en `T` utilisant comme nom de paramètre de type pour les types avec un paramètre de type une seule lettre.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ DO prefix noms de paramètres descriptifs avec `T`.

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ CONSIDER indiquant les contraintes imposées à un paramètre de type au nom du paramètre.

 Par exemple, un paramètre contraint à `ISession` pourrait être appelé `TSession`.

## <a name="names-of-common-types"></a>Noms des types communs
 ✔️ NE suivent les lignes directrices décrites dans le tableau suivant lorsque vous nommez des types dérivés ou mettant en œuvre certains types de cadre .NET.

|Base Type|Ligne directrice de type dérivé/mise en œuvre|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ NE ajouter le suffixe "Attribut" aux noms des classes d’attributs personnalisés.|
|`System.Delegate`|✔️ NE ajouter le suffixe "EventHandler" aux noms des délégués qui sont utilisés dans les événements.<br /><br /> ✔️ NE ajouter le suffixe "Callback" aux noms des délégués autres que ceux utilisés comme gestionnaires d’événements.<br /><br /> ❌NE PAS ajouter le suffixe "Délégué" à un délégué.|
|`System.EventArgs`|✔️ NE ajouter le suffixe "EventArgs."|
|`System.Enum`|❌NE pas dériver de cette classe; utiliser le mot clé pris en charge par votre langue à la place; par exemple, dans le `enum` mot-clé C, utilisez le mot-clé.<br /><br /> ❌NE PAS ajouter le suffixe "Enum" ou "Flag".|
|`System.Exception`|✔️ NE ajouter le suffixe "Exception.".|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ NE ajouter le suffixe "Dictionnaire." Notez `IDictionary` qu’il s’agit d’un type spécifique de collection, mais cette ligne directrice prime sur la ligne directrice des collections plus générales qui suit.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ NE ajouter le suffixe "Collection".|
|`System.IO.Stream`|✔️ NE ajouter le suffixe "Stream".|
|`CodeAccessPermission IPermission`|✔️ N’ajoutez pas le suffixe "Permission".|

## <a name="naming-enumerations"></a>Nommer les énumérations
 Les noms des types d’énumération (également appelés enums) en général doivent suivre les règles standard de nommage de type (PascalCasing, etc.). Cependant, il existe d’autres lignes directrices qui s’appliquent spécifiquement aux enums.

 ✔️ NE pas utiliser un nom de type singulier pour un recensement à moins que ses valeurs sont des champs bits.

 ✔️ NE utiliser un nom de type pluriel pour un recensement avec des champs bits comme valeurs, également appelé drapeaux enum.

 ❌NE PAS utiliser un suffixe "Enum" dans les noms de type enum.

 ❌NE PAS utiliser "Flag" ou "Flags" suffixes dans les noms de type enum.

 ❌NE PAS utiliser un préfixe sur les noms de valeur de recensement (p. ex., « annonce » pour les enums ADO, « rtf » pour les enums de texte riches, etc.).

 *Parts © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
