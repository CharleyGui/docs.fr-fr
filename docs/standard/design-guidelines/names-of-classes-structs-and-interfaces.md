---
title: Noms de classes, de structures et d'interfaces
description: Utilisez ces instructions pour nommer des classes, des structures et des interfaces dans le cadre des instructions de conception des bibliothèques qui étendent et interagissent avec les bibliothèques .NET.
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
ms.openlocfilehash: e7eee414c5bf5c69f63543ef240e50a4d2d948a3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419081"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Noms de classes, de structures et d'interfaces
Les règles d’affectation des noms qui suivent s’appliquent à la dénomination générale des types.

 ✔️ Nommez les classes et les structs avec des noms ou des expressions nominales, à l’aide de PascalCasing.

 Cela distingue les noms de types des méthodes, qui sont nommées à l’aide d’expressions de verbe.

 ✔️ Nommez les interfaces avec des expressions adjectifs, ou parfois avec des noms ou des expressions nominales.

 Les noms et les expressions nominales doivent être utilisés rarement et peuvent indiquer que le type doit être une classe abstraite, et non une interface.

 ❌N’attribuez pas de noms de classe à un préfixe (par exemple, « C »).

 ✔️ envisagez de terminer le nom des classes dérivées par le nom de la classe de base.

 Cela est très lisible et explique clairement la relation. Voici quelques exemples de ceci dans le code : `ArgumentOutOfRangeException` , qui est un genre de `Exception` , et `SerializableAttribute` , qui est un type de `Attribute` . Toutefois, il est important d’utiliser un jugement raisonnable dans le cadre de l’application de cette règle. par exemple, la `Button` classe est un type d' `Control` événement, bien que `Control` n’apparaisse pas dans son nom.

 ✔️ FAITES précéder les noms d’interface par la lettre I, pour indiquer que le type est une interface.

 Par exemple, `IComponent` (nom descriptif), `ICustomAttributeProvider` (expression nominale) et `IPersistable` (adjectif) sont des noms d’interface appropriés. Comme avec d’autres noms de types, évitez les abréviations.

 ✔️ Assurez-vous que les noms diffèrent uniquement par le préfixe « I » sur le nom de l’interface lorsque vous définissez une paire classe-interface où la classe est une implémentation standard de l’interface.

## <a name="names-of-generic-type-parameters"></a>Noms des paramètres de type générique
 Des génériques ont été ajoutés à .NET Framework 2,0. La fonctionnalité a introduit un nouveau type d’identificateur appelé *paramètre de type*.

 ✔️ Nommez les paramètres de type générique avec des noms descriptifs, sauf si un nom de lettre unique est entièrement explicite et qu’un nom descriptif n’ajoute pas de valeur.

 ✔️ envisagez `T` d’utiliser comme nom de paramètre de type pour les types avec un paramètre de type à une seule lettre.

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 ✔️ FAITES précéder les noms de paramètre de type descriptif de `T` .

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 ✔️ envisagez d’indiquer des contraintes placées sur un paramètre de type dans le nom du paramètre.

 Par exemple, un paramètre avec une limite `ISession` peut être appelé `TSession` .

## <a name="names-of-common-types"></a>Noms des types courants
 ✔️ Suivez les instructions décrites dans le tableau suivant lors de l’attribution de noms aux types dérivés de ou de l’implémentation de certains types d' .NET Framework.

|Base Type|Instruction de type Derived/Implementation|
|---------------|------------------------------------------|
|`System.Attribute`|✔️ Ajoutez le suffixe « Attribute » aux noms des classes d’attributs personnalisés.|
|`System.Delegate`|✔️ Ajoutez le suffixe « EventHandler » aux noms des délégués utilisés dans les événements.<br /><br /> ✔️ Ajoutez le suffixe « callback » aux noms des délégués autres que ceux utilisés comme gestionnaires d’événements.<br /><br /> ❌N’ajoutez pas le suffixe « Delegate » à un délégué.|
|`System.EventArgs`|✔️ Ajoutez le suffixe « EventArgs ».|
|`System.Enum`|❌NE dérivez pas de cette classe ; Utilisez le mot clé pris en charge par votre langage à la place. par exemple, en C#, utilisez le `enum` mot clé.<br /><br /> ❌N’ajoutez pas le suffixe « enum » ou « Flag ».|
|`System.Exception`|✔️ Ajoutez le suffixe « exception ».|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|✔️ Ajoutez le suffixe « dictionary ». Notez que `IDictionary` est un type spécifique de collection, mais cette règle est prioritaire sur la règle de regroupements plus généraux qui suit.|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|✔️ Ajoutez le suffixe « collection ».|
|`System.IO.Stream`|✔️ Ajoutez le suffixe « Stream ».|
|`CodeAccessPermission IPermission`|✔️ Ajoutez le suffixe « permission ».|

## <a name="naming-enumerations"></a>Énumération des noms
 En général, les noms de types énumération (également appelés énumérations) doivent respecter les règles d’attribution de noms de type standard (PascalCasing, etc.). Toutefois, des instructions supplémentaires s’appliquent spécifiquement aux enums.

 ✔️ Utilisez un nom de type singulier pour une énumération, sauf si ses valeurs sont des champs de bits.

 ✔️ Utilisez un nom de type pluriel pour une énumération avec des champs de bits comme valeurs, également appelé enum Flags.

 ❌N’utilisez pas de suffixe « enum » dans les noms de types ENUM.

 ❌N’utilisez pas les suffixes « Flag » ou « flags » dans les noms de types ENUM.

 ❌N’utilisez pas de préfixe pour les noms de valeurs d’énumération (par exemple, « AD » pour les enums ADO, « RTF » pour les énumérations de texte enrichi, etc.).

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)
- [Instructions d’affectation de noms](../../../docs/standard/design-guidelines/naming-guidelines.md)
