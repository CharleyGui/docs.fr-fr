---
title: Noms de membres de type
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: a9cd531100057fbad4884a20e6e7db6ef94e7956
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709216"
---
# <a name="names-of-type-members"></a>Noms de membres de type
Les types se composent de membres, de méthodes, de propriétés, d’événements, de constructeurs et de champs. Les sections suivantes décrivent les règles de nommage des membres de type.  
  
## <a name="names-of-methods"></a>Noms des méthodes  
 Comme les méthodes permettent d’entreprendre des actions, les règles de conception exigent que les noms des méthodes soient des verbes ou des expressions verbales. Cette règle sert également à distinguer les noms de méthode des noms de propriété et de type, qui sont des expressions nominales ou adjectivales.  
  
 **✓ DO** Donner des noms de méthode qui sont des verbes ou des expressions verbales.  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Noms des propriétés  
 Contrairement aux autres membres, les noms des propriétés doivent être des expressions nominales ou adjectivales. C’est parce que les propriétés font référence à des données, donc leur nom doivent le refléter. La casse Pascal est toujours utilisée pour les noms de propriété.  
  
 **✓ DO** Nommer les propriétés en utilisant un substantif, une expression nominale ou un adjectif.  
  
 **X DO NOT** Avoir des propriétés qui correspondent au nom des méthodes "Get", comme dans l’exemple suivant :  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Ce modèle indique typiquement que la propriété doit vraiment être une méthode.  
  
 **✓** Nommez les propriétés de collection avec une expression pluriel décrivant les éléments de la collection au lieu d’utiliser une expression singulière suivie de « List » ou « collection ».  
  
 **✓ DO** Nommer des propriétés booléennes avec une expression affirmative (`CanSeek` au lieu de `CantSeek`). Si vous le souhaitez, vous pouvez également préfixer les propriétés booléennes avec « is », « CAN » ou « has », mais uniquement à l’endroit où elle ajoute value.  
  
 **✓ CONSIDER** Donner à une propriété le même nom que son type.  
  
 Par exemple, la propriété suivante obtient et définit correctement une valeur enum nommée `Color`, donc la propriété est nommée `Color`:  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Noms des événements  
 Les événements font toujours référence à une action, soit une action en cours, soit une action passée. Par conséquent, comme avec les méthodes, les événements sont nommés avec des verbes, le temps des verbes servant à indiquer l’heure où l’événement est déclenché.  
  
 **✓ DO** Nommer les événements avec un verbe ou une expression verbale.  
  
 Par exemple, `Clicked`, `Painting`, `DroppedDown`, etc.  
  
 **✓ DO** Donner des noms d’événement avec un concept avant/après, en utilisant les temps du présent et du passé.  
  
 Par exemple, un événement de fermeture déclenché avant la fermeture d’une fenêtre serait nommé `Closing`, tandis qu’un événement déclenché après la fermeture de la fenêtre serait nommé `Closed`.  
  
 **X DO NOT** Utiliser « Before » ou « After » comme préfixes ou suffixes pour indiquer des pré/post-événements. Utilisez les temps du présent et du passé, comme nous venons de le décrire.  
  
 **✓ DO** Nommer les gestionnaires d’événements (délégués utilisés comme types d’événements) avec le suffixe « EventHandler », comme illustré dans l’exemple suivant :  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ DO** Utiliser deux paramètres nommés `sender` et `e` dans les gestionnaires d’événements.  
  
 Le paramètre d’expéditeur représente l’objet qui a déclenché l’événement. Le paramètre d’expéditeur est généralement de type `object`, même s’il est possible d’employer un type plus spécifique.  
  
 **✓ DO** Nommer les classes d’argument d’événement avec le suffixe « EventArgs ».  
  
## <a name="names-of-fields"></a>Noms des champs  
 Les règles de nommage des champs s’appliquent à des champs publics et protégés statiques. Les champs internes et privés ne sont pas couverts par les règles, tandis que les champs d’instance publics ou protégés ne sont pas autorisés par les [règles de conception de membres](../../../docs/standard/design-guidelines/member.md).  
  
 **✓ DO** Utiliser la casse Pascal dans les noms de champ.  
  
 **✓ DO** Nommer les champs en utilisant un substantif, une expression nominale ou un adjectif.  
  
 **X DO NOT** Utiliser un préfixe pour les noms de champ.  
  
 Par exemple, n’utilisez pas « g_ » ou « s_ » pour indiquer des champs statiques.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
