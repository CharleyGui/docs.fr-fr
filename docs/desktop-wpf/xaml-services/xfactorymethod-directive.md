---
title: x:FactoryMethod, directive
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071534"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod, directive
Specifie une méthode autre qu’un constructeur qu’un processeur XAML devrait utiliser pour initialiser un objet après avoir résolu son type de support.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML Attribute Utilisation, no x:Arguments XAML Attribute Utilisation, no x:Arguments XAML Attribute Utilisation, no x:Arguments XAM  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML Attribute Usage, x:Arguments as Element(s)  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`methodname`|Le nom de méthode de chaîne d’une méthode que les `object`processeurs XAML appellent pour initialiser l’instance spécifiée comme . Consultez la section Notes.|  
|`oneOrMoreObjectElements`|Un ou plusieurs éléments d’objets pour les objets qui spécifient les paramètres de la méthode d’usine. L’ordre est important; il signifie l’ordre dans lequel les arguments doivent être transmis à la méthode de l’usine.|  
  
## <a name="remarks"></a>Notes  
 S’il `methodname` s’agit d’une méthode d’instance, elle ne peut pas être qualifiée.  
  
 Les méthodes statiques en tant que méthodes d’usine sont soutenues. Si `methodname` est une `methodname` méthode statique, `typeName.methodName` est `typeName` fourni comme une combinaison, où les noms de la classe qui définit la méthode d’usine statique. `typeName`peut être préfixe-qualifié si se référant à un type dans un xmlns cartographié. `typeName`peut être un `typeof(object)`type différent de .  
  
 La méthode de l’usine doit être une méthode publique déclarée du type qui soutient l’élément objet pertinent.  
  
 La méthode de l’usine doit renvoyer une instance qui est assignable à l’objet pertinent. Les méthodes d’usine ne doivent jamais revenir nulles.  
  
 `x:Arguments`fonctionne selon le principe du meilleur assortiment pour les signatures de méthodes d’usine. L’appariement évalue d’abord le nombre de paramètres. S’il y a plus d’une correspondance possible pour un nombre de paramètres, le type de paramètre est alors évalué et le meilleur match est déterminé. S’il y a encore de l’ambiguïté après cette phase d’évaluation, le comportement du processeur XAML n’est pas défini.  
  
 L’utilisation `x:FactoryMethod` de l’élément n’est pas l’utilisation de l’élément de propriété au sens typique du terme, car le balisage de la directive ne fait pas référence au type d’élément objet contenant. On s’attend à ce que l’utilisation des éléments soit moins courante que l’utilisation d’attributs. `x:Arguments`(l’utilisation d’attribut ou d’élément) peut être utilisée avec `x:FactoryMethod` l’utilisation d’éléments, mais cela n’est pas spécifiquement indiqué dans les sections d’utilisation.  
  
 `x:FactoryMethod`en tant qu’élément doit précéder `x:Arguments` tout autre élément de propriété, doit précéder tout élément également fourni comme éléments, et doit précéder tout contenu/texte intérieur/texte d’initialisation.  
  
## <a name="see-also"></a>Voir aussi

- [x:Arguments, directive](xarguments-directive.md)
