---
title: x:Arguments, directive
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a18de9a07839f5b01620311832b85667680c12ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053832"
---
# <a name="xarguments-directive"></a>x:Arguments, directive
Les arguments de construction de packages pour une déclaration d’élément objet de constructeur sans paramètre en XAML, ou pour une déclaration d’objet de méthode de fabrique.  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>Utilisation des éléments XAML (constructeur sans paramètre)  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Utilisation des éléments XAML (méthode de fabrique)  
  
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
|`oneOrMoreObjectElements`|Un ou plusieurs éléments objet qui spécifient des arguments à passer au constructeur sans paramètre de sauvegarde ou à la méthode de fabrique.<br /><br /> L’utilisation classique consiste à utiliser le texte d’initialisation dans les éléments de l’objet pour spécifier les valeurs d’arguments réelles. Consultez la section exemples.<br /><br /> L’ordre des éléments est significatif. Les types XAML dans l’ordre doivent correspondre aux types et à l’ordre de type du constructeur de stockage ou de la surcharge de méthode de fabrique.|  
|`methodName`|Nom de la méthode de fabrique qui doit traiter tous `x:Arguments` les arguments.|  
  
## <a name="dependencies"></a>Dépendances  
 `x:FactoryMethod`peut modifier l’étendue et le comportement `x:Arguments` où s’applique.  
  
 Si aucun `x:FactoryMethod` n’est spécifié `x:Arguments` , s’applique aux signatures de remplacement (non par défaut) des constructeurs de stockage.  
  
 Si `x:FactoryMethod` est spécifié, `x:Arguments` s’applique à une surcharge de la méthode nommée.  
  
## <a name="remarks"></a>Notes  
 XAML 2006 peut prendre en charge l’initialisation non définie par défaut par le texte d’initialisation. Toutefois, l’application pratique d’une technique de construction de texte d’initialisation est limitée. Le texte d’initialisation est traité comme une chaîne de texte unique. par conséquent, il ajoute uniquement des fonctionnalités pour l’initialisation d’un seul paramètre, sauf si un convertisseur de type est défini pour le comportement de construction qui peut analyser des éléments d’information personnalisés et des délimiteurs personnalisés de la chaîne. En outre, la chaîne de texte à la logique d’objet est potentiellement un convertisseur de type natif par défaut de l’analyseur XAML donné pour gérer les primitives autres que la chaîne true.  
  
 L' `x:Arguments` utilisation de XAML n’est pas une utilisation d’élément de propriété dans le sens type, car la balise de directive ne fait pas référence au type de l’élément objet conteneur. Elle est plus similaire aux autres directives, par `x:Code` exemple lorsque l’élément délimite une plage dans laquelle la balise doit être interprétée comme autre que la valeur par défaut pour le contenu enfant. Dans ce cas, le type XAML de chaque élément Object communique des informations sur les types d’arguments, qui sont utilisés par les analyseurs XAML pour déterminer la signature de méthode `x:Arguments` de fabrique de constructeur spécifique qu’une utilisation tente de référencer.  
  
 `x:Arguments`pour un élément objet en cours de construction doit précéder tout autre élément de propriété, contenu, texte interne ou chaîne d’initialisation de l’élément objet. Les éléments objet dans `x:Arguments` peuvent inclure des attributs et des chaînes d’initialisation, comme l’autorise ce type XAML et son constructeur de stockage ou sa méthode de fabrique. Pour l’objet ou les arguments, vous pouvez spécifier des types XAML personnalisés ou des types XAML qui sont autrement en dehors de l’espace de noms XAML par défaut en référençant les mappages de préfixe établis.  
  
 Les processeurs XAML utilisent les indications suivantes pour déterminer comment les arguments `x:Arguments` spécifiés dans doivent être utilisés pour construire un objet. Si `x:FactoryMethod` est spécifié, les informations sont comparées au `x:FactoryMethod` spécifié (Notez que la valeur `x:FactoryMethod` de est le nom de la méthode, et la méthode nommée peut avoir des surcharges. Si `x:FactoryMethod` n’est pas spécifié, les informations sont comparées à l’ensemble de toutes les surcharges de constructeur public de l’objet. La logique de traitement XAML compare ensuite le nombre de paramètres et sélectionne la surcharge avec l’arité correspondante. S’il existe plusieurs correspondances, le processeur XAML doit comparer les types des paramètres en fonction des types XAML des éléments objet fournis. S’il existe encore plusieurs correspondances, le comportement du processeur XAML n’est pas défini. Si un `x:FactoryMethod` est spécifié mais que la méthode ne peut pas être résolue, un processeur XAML doit lever une exception.  
  
 Une utilisation `<x:Arguments>string</x:Arguments>` d’attribut XAML est techniquement possible. Toutefois, cela ne fournit pas de fonctionnalités au-delà de ce qui pourrait être fait autrement par le biais d’un texte d’initialisation et de convertisseurs de type, et l’utilisation de cette syntaxe n’est pas l’intention de conception des fonctionnalités de la méthode de fabrique XAML 2009.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre une signature de constructeur sans paramètre, puis l’utilisation de XAML de `x:Arguments` qui accède à cette signature.  
  
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
  
 L’exemple suivant illustre une signature de méthode de fabrique cible, puis l’utilisation `x:Arguments` de XAML de qui accède à cette signature.  
  
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

- [Définition de types personnalisés pour une utilisation avec les services XAML .NET Framework](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [Vue d’ensemble du langage XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
