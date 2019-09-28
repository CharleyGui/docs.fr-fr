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
author: KrzysztofCwalina
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353705"
---
# <a name="names-of-classes-structs-and-interfaces"></a>Noms de classes, de structures et d'interfaces
Les règles d’affectation des noms qui suivent s’appliquent à la dénomination générale des types.  
  
 **✓ DO** un nom de classes et structs avec des noms ou des expressions nominales, à l’aide de la casse Pascal.  
  
 Cela distingue les noms de types des méthodes, qui sont nommées à l’aide d’expressions de verbe.  
  
 **✓ DO** nom interfaces phrases adjectivales ou parfois avec des noms ou des expressions nominales.  
  
 Les noms et les expressions nominales doivent être utilisés rarement et peuvent indiquer que le type doit être une classe abstraite, et non une interface.  
  
 **X DO NOT** donner des noms de classe un préfixe (par exemple, « C »).  
  
 **✓ CONSIDER** se terminant par le nom de classes dérivées portant le nom de la classe de base.  
  
 Cela est très lisible et explique clairement la relation. Voici quelques exemples de ceci dans le code : `ArgumentOutOfRangeException`, qui est un type de `Exception` et `SerializableAttribute`, qui est un type de `Attribute`. Toutefois, il est important d’utiliser un jugement raisonnable dans le cadre de l’application de cette règle. par exemple, la classe `Button` est un type d’événement `Control`, bien que `Control` n’apparaisse pas dans son nom.  
  
 **✓ DO** préfixe les noms d’interface avec la lettre I, pour indiquer que le type est une interface.  
  
 Par exemple, `IComponent` (nom descriptif), `ICustomAttributeProvider` (expression nominale) et `IPersistable` (adjectif) sont des noms d’interface appropriés. Comme avec d’autres noms de types, évitez les abréviations.  
  
 **✓ DO** vous assurer que les noms diffèrent uniquement par « I » du préfixe du nom de l’interface lorsque vous définissez une paire : interface de classe dans laquelle la classe est une implémentation standard de l’interface.  
  
## <a name="names-of-generic-type-parameters"></a>Noms des paramètres de type générique  
 Des génériques ont été ajoutés à .NET Framework 2,0. La fonctionnalité a introduit un nouveau type d’identificateur appelé *paramètre de type*.  
  
 **✓ DO** nom des paramètres de type générique avec des noms descriptifs, sauf si un nom de lettre unique est complètement explicite et un nom descriptif ajouterait pas de valeur.  
  
 **✓ CONSIDER** à l’aide de `T` comme nom de paramètre de type pour les types avec un paramètre de type de lettre unique.  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ DO** préfixe des noms de paramètre de type descriptifs avec `T`.  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 **✓ CONSIDER** indiquer les contraintes placées sur un paramètre de type dans le nom du paramètre.  
  
 Par exemple, un paramètre restreint à `ISession` peut être appelé `TSession`.  
  
## <a name="names-of-common-types"></a>Noms des types courants  
 **✓ DO** suivez les instructions décrites dans le tableau suivant lorsque vous nommez des types dérivés ou implémenter certains types .NET Framework.  
  
|Base Type|Instruction de type Derived/Implementation|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ DO** ajouter le suffixe « Attribute » aux noms des classes d’attributs personnalisés.|  
|`System.Delegate`|**✓ DO** ajouter le suffixe « EventHandler » aux noms de délégués qui sont utilisés dans les événements.<br /><br /> **✓ DO** ajouter le suffixe « Rappel » aux noms de délégués autres que ceux utilisés en tant que gestionnaires d’événements.<br /><br /> **X DO NOT** ajouter le suffixe « Délégué » à un délégué.|  
|`System.EventArgs`|**✓ DO** ajouter le suffixe « EventArgs ».|  
|`System.Enum`|**X DO NOT** dériver de cette classe ; utilisez le mot clé pris en charge par votre langage à la place ; par exemple, en c#, utilisez le `enum` (mot clé).<br /><br /> **X DO NOT** ajouter le suffixe « Enum » ou « Indicateur ».|  
|`System.Exception`|**✓ DO** ajouter le suffixe « Exception ».|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ DO** ajouter le suffixe « Dictionnaire ». Notez que `IDictionary` est un type spécifique de collection, mais cette règle est prioritaire sur la règle de regroupements plus généraux qui suit.|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ DO** ajouter le suffixe « Collection ».|  
|`System.IO.Stream`|**✓ DO** ajouter le suffixe « Stream ».|  
|`CodeAccessPermission IPermission`|**✓ DO** ajouter le suffixe « Autorisation ».|  
  
## <a name="naming-enumerations"></a>Énumération des noms  
 En général, les noms de types énumération (également appelés énumérations) doivent respecter les règles d’attribution de noms de type standard (PascalCasing, etc.). Toutefois, des instructions supplémentaires s’appliquent spécifiquement aux enums.  
  
 **✓ DO** utiliser un nom de type au singulier pour une énumération, sauf si ses valeurs sont les champs de bits.  
  
 **✓ DO** utiliser un nom de type au pluriel pour une énumération avec les champs de bits sous forme de valeurs, également appelés enum d’indicateurs.  
  
 **X DO NOT** utiliser le suffixe « Enum » dans les noms de type enum.  
  
 **X DO NOT** utiliser « Indicateur » ou tapez les noms des suffixes « Indicateurs » dans l’enum.  
  
 **X DO NOT** utiliser un préfixe sur les noms de valeur d’énumération (par exemple, « ad » pour les énumérations ADO.), « rtf » pour les énumérations de texte enrichi, etc.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Reprinted par l’autorisation de Pearson Education, Inc. des instructions de conception @no__t 1Framework : Conventions, idiomes et modèles pour les bibliothèques .NET réutilisables, 2e édition @ no__t-0 par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 de Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
