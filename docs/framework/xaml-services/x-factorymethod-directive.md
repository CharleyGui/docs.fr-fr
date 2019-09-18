---
title: x:FactoryMethod, directive
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053774"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod, directive
Spécifie une méthode autre qu’un constructeur qu’un processeur XAML doit utiliser pour initialiser un objet après la résolution de son type de stockage.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Utilisation d’attributs XAML, no x :Arguments  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Utilisation d’attribut XAML, x :Arguments en tant qu’élément (s)  
  
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
|`methodname`|Nom de méthode de chaîne d’une méthode que les processeurs XAML appellent pour initialiser l' `object`instance spécifiée comme. Consultez la section Notes.|  
|`oneOrMoreObjectElements`|Un ou plusieurs éléments objet pour les objets qui spécifient des paramètres de méthode de fabrique. L’ordre est important. Il indique l’ordre dans lequel les arguments doivent être passés à la méthode de fabrique.|  
  
## <a name="remarks"></a>Notes  
 Si `methodname` est une méthode d’instance, elle ne peut pas être qualifiée.  
  
 Les méthodes statiques en tant que méthodes de fabrique sont prises en charge. Si `methodname` est une méthode statique, `methodname` est fourni en tant que *TypeName*. *combinaison methodName* , où *TypeName* nomme la classe qui définit la méthode de fabrique statique. *TypeName* peut être qualifié par un préfixe s’il fait référence à un type dans un xmlns mappé. *TypeName* peut être un type différent de `typeof(object)`.  
  
 La méthode de fabrique doit être une méthode publique déclarée du type qui stocke l’élément objet approprié.  
  
 La méthode de fabrique doit retourner une instance qui peut être assignée à l’objet approprié. Les méthodes de fabrique ne doivent jamais retourner la valeur null.  
  
 `x:Arguments`opère sur un principe de meilleure correspondance pour les signatures de méthodes de fabrique. La correspondance évalue le nombre de paramètres en premier. S’il existe plusieurs correspondances possibles pour un nombre de paramètres, le type de paramètre est évalué et la meilleure correspondance est déterminée. S’il y a toujours une ambiguïté après cette phase d’évaluation, le comportement du processeur XAML n’est pas défini.  
  
 L' `x:FactoryMethod` utilisation de l’élément n’est pas une utilisation d’élément de propriété dans le sens normal, car le balisage de directive ne fait pas référence au type de l’élément objet conteneur. Il est prévu que l’utilisation des éléments soit moins courante que l’utilisation des attributs. `x:Arguments`(utilisation de l’attribut ou de l’élément) peut être `x:FactoryMethod` utilisé avec l’utilisation de l’élément, mais cela n’est pas spécifiquement indiqué dans les sections utilisation.  
  
 `x:FactoryMethod`comme un élément doit précéder tous les autres éléments de propriété, `x:Arguments` doit précéder tout également fourni comme éléments, et doit précéder tout contenu/texte interne/texte d’initialisation.  
  
## <a name="see-also"></a>Voir aussi

- [x:Arguments (directive)](x-arguments-directive.md)
