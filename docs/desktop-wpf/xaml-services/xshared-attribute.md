---
title: x:Shared, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: d5000b51d83066ec2d529db2033d8ac54f7ad329
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557786"
---
# <a name="xshared-attribute"></a>x:Shared, attribut

Lorsque la valeur est `false` , modifie le comportement de récupération des ressources WPF afin que les demandes pour la ressource avec attributs créent une nouvelle instance pour chaque requête au lieu de partager la même instance pour toutes les demandes.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Notes

`x:Shared` est mappé à l’espace de noms XAML du langage XAML et est reconnu comme un élément de langage XAML valide par les services XAML .NET et ses lecteurs XAML. Toutefois, les fonctionnalités spécifiées de `x:Shared` ne sont pertinentes que pour les applications WPF et l’analyseur XAML WPF. Dans WPF, `x:Shared` est utile uniquement en tant qu’attribut lorsqu’il est appliqué à un objet qui existe dans un WPF <xref:System.Windows.ResourceDictionary> . Les autres utilisations ne lèvent pas d’exception d’analyse ou d’autres erreurs, mais elles n’ont aucun effet.

La signification de `x:Shared` n’est pas spécifiée dans la spécification du langage XAML. D’autres implémentations XAML, telles que celles qui s’appuient sur les services XAML .NET, ne fournissent pas nécessairement la prise en charge du partage des ressources. Ces implémentations XAML pourraient fournir un comportement similaire dans l’infrastructure de prise en charge qui utilisait également des `x:Shared` valeurs.

Dans WPF, la condition par défaut `x:Shared` pour les ressources est `true` . Cette condition signifie que toute demande de ressource donnée retourne toujours la même instance.

La modification d’un objet retourné via une API de ressource, telle que <xref:System.Windows.FrameworkElement.FindResource%2A> , ou la modification d’un objet directement dans un <xref:System.Windows.ResourceDictionary> , modifie la ressource d’origine. Si les références à cette ressource étaient des références de ressources dynamiques, les consommateurs de cette ressource obtiennent la ressource modifiée.

Si les références à la ressource étaient des références de ressources statiques, les modifications apportées à la ressource après le [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] temps de traitement ne sont pas pertinentes. Pour plus d’informations sur les références de ressources statiques et dynamiques, consultez [ressources XAML](../fundamentals/xaml-resources-define.md).

La spécification explicite de `x:Shared="true"` est rarement effectuée, car il s’agit déjà de la valeur par défaut. Il n’existe aucun équivalent direct du code pour `x:Shared` dans le modèle objet WPF ; il ne peut être spécifié que dans une utilisation XAML et doit être traité soit par le comportement WPF par défaut, soit dans un flux de nœud XAML intermédiaire sur le chemin de chargement s’il est traité à l’aide des services XAML .net et de ses lecteurs XAML.

Un scénario pour `x:Shared="false"` est si vous définissez une <xref:System.Windows.FrameworkElement> classe ou une <xref:System.Windows.FrameworkContentElement> classe dérivée en tant que ressource, puis que vous introduisez la ressource d’élément dans un modèle de contenu. `x:Shared="false"` permet à une ressource d’élément d’être introduite plusieurs fois dans la même collection (telle que <xref:System.Windows.Controls.UIElementCollection> ). Sans `x:Shared="false"` cela n’est pas valide, car la collection applique l’unicité de son contenu. Toutefois, le `x:Shared="false"` comportement crée une autre instance de la ressource identique au lieu de retourner la même instance.

Un autre scénario pour `x:Shared="false"` est si vous utilisez une <xref:System.Windows.Freezable> ressource pour les valeurs d’animation, mais que vous souhaitez modifier la ressource en fonction de chaque animation.

La gestion des chaînes de `false` ne respecte pas la casse.

Dans WPF, `x:Shared` est valide uniquement dans les conditions suivantes :

- Le <xref:System.Windows.ResourceDictionary> qui contient les éléments avec `x:Shared` doit être compilé. Le <xref:System.Windows.ResourceDictionary> ne peut pas être dans du XAML libre ou utilisé pour les thèmes.

- Le <xref:System.Windows.ResourceDictionary> qui contient les éléments ne doit pas être imbriqué dans un autre <xref:System.Windows.ResourceDictionary> . Par exemple, vous ne pouvez pas utiliser `x:Shared` pour les éléments d’un <xref:System.Windows.ResourceDictionary> qui se trouve dans un <xref:System.Windows.Style> qui est déjà un <xref:System.Windows.ResourceDictionary> élément.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources XAML](../fundamentals/xaml-resources-define.md)
- [Éléments de base](/dotnet/desktop/wpf/advanced/base-elements)
