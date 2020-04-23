---
title: x:Arguments, directive
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071590"
---
# <a name="xarguments-directive"></a>x:Arguments, directive

Arguments de construction de paquets pour une déclaration d’élément constructeur non-paramètre dans XAML, ou pour une déclaration d’objet de méthode d’usine.

## <a name="xaml-element-usage-nonparameterless-constructor"></a>Utilisation d’éléments XAML (constructeur non nonparameterless)

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a>Utilisation d’éléments XAML (méthode d’usine)

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`oneOrMoreObjectElements`|Un ou plusieurs éléments d’objet qui spécifient des arguments à transmettre au constructeur ou à la méthode d’usine sans paramètres.<br /><br /> L’utilisation typique consiste à utiliser le texte de initialisation dans les éléments de l’objet pour spécifier les valeurs réelles de l’argument. Voir la section Exemples.<br /><br /> L’ordre des éléments est significatif. Les types XAML afin de correspondre aux types et à l’ordre de type du constructeur de support ou de la surcharge de méthode d’usine.|
|`methodName`|Le nom de la méthode `x:Arguments` de l’usine qui doit traiter tous les arguments.|

## <a name="dependencies"></a>Les dépendances

`x:FactoryMethod`peut modifier la portée `x:Arguments` et le comportement lorsque cela s’applique.

Si `x:FactoryMethod` aucun n’est spécifié, `x:Arguments` s’applique aux signatures alternatives (non-par défaut) des constructeurs de support.

Si `x:FactoryMethod` elle `x:Arguments` est spécifiée, s’applique à une surcharge de la méthode nommée.

## <a name="remarks"></a>Notes

XAML 2006 peut prendre en charge l’initialisation par défaut par le biais du texte de initialisation. Cependant, l’application pratique d’une technique de construction de texte d’initialisation est limitée. Le texte de initialisation est traité comme une seule chaîne de texte; par conséquent, il ajoute seulement la capacité pour une initialisation de paramètres unique à moins qu’un convertisseur de type soit défini pour le comportement de construction qui peut analyser des éléments d’information personnalisés et des délimitations personnalisées de la chaîne. En outre, la chaîne de texte à la logique d’objet est potentiellement un convertisseur de type par défaut natif d’un par défaut de XAML pour manipuler des primitifs autres qu’une vraie chaîne.

L’utilisation `x:Arguments` de XAML n’est pas l’utilisation de l’élément de propriété dans le sens typique, parce que le balisage de la directive ne fait pas référence au type de l’élément objet contenant. Il s’apparente davantage à `x:Code` d’autres directives telles que l’endroit où l’élément marque une plage dans laquelle la majoration doit être interprétée comme autre que la valeur par défaut pour le contenu de l’enfant. Dans ce cas, le type XAML de chaque élément d’objet communique des informations sur les types d’argument, `x:Arguments` qui est utilisé par les analyseurs XAML pour déterminer quelle signature spécifique de méthode d’usine de constructeur une utilisation tente de référence.

`x:Arguments`pour un élément d’objet en construction doit précéder tout autre élément de propriété, contenu, texte intérieur ou chaînes d’initialisation de l’élément objet. Les éléments `x:Arguments` d’objet à l’intérieur peuvent inclure des attributs et des chaînes d’initialisation, comme le permet ce type XAML et sa méthode de construction ou d’usine. Pour l’objet ou les arguments, vous pouvez spécifier les types XAML personnalisés ou les types XAML qui sont autrement en dehors de l’espace nom XAML par défaut en faisant référence aux cartes préfixes établies.

Les processeurs XAML utilisent les lignes directrices suivantes pour déterminer comment les arguments spécifiés `x:Arguments` devraient être utilisés pour construire un objet. Si `x:FactoryMethod` elle est spécifiée, `x:FactoryMethod` l’information est `x:FactoryMethod` comparée à la spécifiée (notez que la valeur est le nom de la méthode, et la méthode nommée peut avoir des surcharges. Si `x:FactoryMethod` elle n’est pas spécifiée, l’information est comparée à l’ensemble de toutes les surcharges constructoraires publiques de l’objet. La logique de traitement XAML compare ensuite le nombre de paramètres et sélectionne la surcharge avec une aité assortie. S’il y a plus d’une correspondance, le processeur XAML doit comparer les types de paramètres en fonction des types XAML des éléments d’objets fournis. S’il y a encore plus d’un match, le comportement du processeur XAML n’est pas défini. Si `x:FactoryMethod` un a est spécifié mais que la méthode ne peut pas être résolue, un processeur XAML doit faire une exception.

Une utilisation d’attribut `<x:Arguments>string</x:Arguments>` XAML est techniquement possible. Cependant, cela ne fournit aucune capacité au-delà de ce qui pourrait être fait autrement par le biais de la initialisation texte et convertisseurs de type, et l’utilisation de cette syntaxe n’est pas l’intention de conception de la XAML 2009 caractéristiques de la méthode d’usine.

## <a name="examples"></a>Exemples

L’exemple suivant montre une signature constructeur non sans paramètres, `x:Arguments` puis l’utilisation XAML de celui accès à cette signature.

```csharp
public class Food {
  private string _name;
  private Int32 _calories;
  public Food(string name, Int32 calories) {
      _name=name;
      _calories=calories;
  }
}
```

```xaml
<my:Food>
  <x:Arguments>
      <x:String>Apple</x:String>
      <x:Int32>150</x:Int32>
  </x:Arguments>
</my:Food>
```

L’exemple suivant montre une signature de méthode d’usine cible, puis l’utilisation XAML de `x:Arguments` celui accès à cette signature.

```csharp
public Food TryLookupFood(string name)
{
switch (name) {
  case "Apple": return new Food("Apple",150);
  case "Chocolate": return new Food("Chocolate",200);
  case "Cheese": return new Food("Cheese", 450);
  default: {return new Food(name,0);
}
}
```

```xaml
<my:Food x:FactoryMethod="TryLookupFood">
  <x:Arguments>
      <x:String>Apple</x:String>
  </x:Arguments>
</my:Food>
```

## <a name="see-also"></a>Voir aussi

- [Définition de types personnalisés pour les utiliser avec les services XAML .NET](define-custom-types.md)
- [Vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md)
