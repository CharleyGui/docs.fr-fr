---
title: x:Shared, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: e1cd1d9db5c19decd840b433f986e0ba53557a8b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071373"
---
# <a name="xshared-attribute"></a>x:Shared, attribut

Lorsqu’il `false`est configuré, modifie le comportement de récupération des ressources WPF de sorte que les demandes pour la ressource attribuée créent une nouvelle instance pour chaque demande au lieu de partager la même instance pour toutes les demandes.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Notes

`x:Shared`est cartographié à la langue XAML XAML namespace et est reconnu comme un élément de langue XAML valide par .NET XAML Services et ses lecteurs XAML. Toutefois, les capacités `x:Shared` déclarées ne sont pertinentes que pour les applications WPF et pour le parsemètre WPF XAML. Dans WPF, `x:Shared` n’est utile comme attribut que lorsqu’il est <xref:System.Windows.ResourceDictionary>appliqué à un objet qui existe au sein d’un WPF . D’autres utilisations ne jettent pas d’exceptions d’analyse ou d’autres erreurs, mais elles n’ont aucun effet.

Le sens `x:Shared` de n’est pas spécifié dans la spécification de la langue XAML. D’autres implémentations XAML, comme celles qui s’appuient sur .NET XAML Services, ne fournissent pas nécessairement un soutien au partage des ressources. De telles implémentations XAML pourraient fournir `x:Shared` un comportement similaire dans le cadre de soutien qui a également utilisé des valeurs.

Dans WPF, `x:Shared` la condition `true`par défaut pour les ressources est . Cette condition signifie que toute demande de ressource donnée renvoie toujours le même cas.

Modifier un objet qui est retourné par une <xref:System.Windows.FrameworkElement.FindResource%2A>API de ressource, <xref:System.Windows.ResourceDictionary>telle que, ou modifier un objet directement dans un , modifie la ressource originale. Si les références à cette ressource étaient des références de ressources dynamiques, les consommateurs de cette ressource obtiennent la ressource modifiée.

Si les références à la ressource étaient des [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] références de ressources statiques, les changements apportés à la ressource après le traitement ne sont pas pertinents. Pour plus d’informations sur les références de ressources statiques par rapport à dynamique, voir [XAML Resources](../fundamentals/xaml-resources-define.md).

La spécifier explicitement `x:Shared="true"` est rarement faite, parce que c’est déjà la valeur par défaut. Il n’y a `x:Shared` pas d’équivalent code direct pour le modèle d’objet WPF; il ne peut être spécifié que dans une utilisation XAML et doit être traité soit par le comportement WPF par défaut ou dans un flux de nœudS XAML intermédiaire sur la trajectoire de charge si traité en utilisant .NET XAML Services et ses lecteurs XAML.

Un scénario `x:Shared="false"` pour est <xref:System.Windows.FrameworkElement> si <xref:System.Windows.FrameworkContentElement> vous définissez une classe ou dérivée comme une ressource, puis vous introduisez la ressource d’élément dans un modèle de contenu. `x:Shared="false"`permet d’introduire plusieurs fois une ressource d’élément <xref:System.Windows.Controls.UIElementCollection>dans la même collection (comme un ). Sans `x:Shared="false"` cela est invalide parce que la collection impose un caractère unique de son contenu. Cependant, `x:Shared="false"` le comportement crée un autre exemple identique de la ressource au lieu de retourner le même cas.

Un autre `x:Shared="false"` scénario est <xref:System.Windows.Freezable> si vous utilisez une ressource pour les valeurs d’animation, mais que vous souhaitez modifier la ressource par animation.

La manipulation `false` des cordes n’est pas sensible aux cas.

Dans WPF, `x:Shared` n’est valable que dans les conditions suivantes :

- Le <xref:System.Windows.ResourceDictionary> qui contient `x:Shared` les éléments avec doit être compilé. Le <xref:System.Windows.ResourceDictionary> ne peut pas être dans XAML lâche ou utilisé pour des thèmes.

- Le <xref:System.Windows.ResourceDictionary> qui contient les éléments ne <xref:System.Windows.ResourceDictionary>doit pas être imbriqué dans un autre . Par exemple, vous `x:Shared` ne pouvez <xref:System.Windows.ResourceDictionary> pas utiliser <xref:System.Windows.Style> pour des <xref:System.Windows.ResourceDictionary> articles dans un qui est dans un qui est déjà un élément.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources XAML](../fundamentals/xaml-resources-define.md)
- [Éléments de base](../../framework/wpf/advanced/base-elements.md)
