---
title: x:Shared, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459927"
---
# <a name="xshared-attribute"></a>x:Shared, attribut
Quand la valeur est `false`, modifie le comportement de récupération des ressources WPF afin que les demandes pour la ressource avec attributs créent une nouvelle instance pour chaque requête au lieu de partager la même instance pour toutes les demandes.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Notes  
 `x:Shared` est mappé à l’espace de noms XAML du langage XAML et est reconnu comme un élément de langage XAML valide par .NET Framework les services XAML et ses lecteurs XAML. Toutefois, les fonctionnalités spécifiées de `x:Shared` sont uniquement applicables aux applications WPF et à l’analyseur XAML WPF. Dans WPF, `x:Shared` n’est utile qu’en tant qu’attribut lorsqu’il est appliqué à un objet qui existe dans un <xref:System.Windows.ResourceDictionary>WPF. Les autres utilisations ne lèvent pas d’exception d’analyse ou d’autres erreurs, mais elles n’ont aucun effet.  
  
 La signification de `x:Shared` n’est pas spécifiée dans la spécification du langage XAML. D’autres implémentations XAML, telles que celles qui s’appuient sur des services .NET Framework XAML, ne fournissent pas nécessairement la prise en charge du partage des ressources. Ces implémentations XAML pourraient fournir un comportement similaire dans l’infrastructure de prise en charge qui utilisait également les valeurs `x:Shared`.  
  
 Dans WPF, la condition de `x:Shared` par défaut pour les ressources est `true`. Cette condition signifie que toute demande de ressource donnée retourne toujours la même instance.  
  
 La modification d’un objet retourné par une API de ressource, telle que <xref:System.Windows.FrameworkElement.FindResource%2A>, ou la modification d’un objet directement dans une <xref:System.Windows.ResourceDictionary>, modifie la ressource d’origine. Si les références à cette ressource étaient des références de ressources dynamiques, les consommateurs de cette ressource obtiennent la ressource modifiée.  
  
 Si les références à la ressource étaient des références de ressources statiques, les modifications apportées à la ressource après [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] temps de traitement ne sont pas pertinentes. Pour plus d’informations sur les références de ressources statiques et dynamiques, consultez [ressources XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 La spécification explicite de `x:Shared="true"` est rarement effectuée, car il s’agit déjà de la valeur par défaut. Il n’existe aucun équivalent direct du code pour `x:Shared` dans le modèle objet WPF ; Il peut uniquement être spécifié dans une utilisation XAML et doit être traité soit par le comportement WPF par défaut, soit dans un flux de nœud XAML intermédiaire sur le chemin de chargement s’il est traité à l’aide de .NET Framework services XAML et de ses lecteurs XAML.  
  
 Un scénario pour `x:Shared="false"` est si vous définissez une classe dérivée <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> en tant que ressource, puis que vous introduisez la ressource d’élément dans un modèle de contenu. `x:Shared="false"` permet à une ressource d’élément d’être introduite plusieurs fois dans la même collection (telle qu’une <xref:System.Windows.Controls.UIElementCollection>). Sans `x:Shared="false"` cela n’est pas valide, car la collection applique l’unicité de son contenu. Toutefois, le comportement de `x:Shared="false"` crée une autre instance de la ressource identique au lieu de retourner la même instance.  
  
 Un autre scénario pour `x:Shared="false"` est que vous utilisez une ressource <xref:System.Windows.Freezable> pour les valeurs d’animation, mais que vous souhaitez modifier la ressource pour chaque animation.  
  
 La gestion des chaînes de `false` ne respecte pas la casse.  
  
 Dans WPF, `x:Shared` n’est valide que dans les conditions suivantes :  
  
- La <xref:System.Windows.ResourceDictionary> qui contient les éléments avec `x:Shared` doit être compilée. Le <xref:System.Windows.ResourceDictionary> ne peut pas être dans du XAML libre ou utilisé pour les thèmes.  
  
- La <xref:System.Windows.ResourceDictionary> qui contient les éléments ne doit pas être imbriquée dans une autre <xref:System.Windows.ResourceDictionary>. Par exemple, vous ne pouvez pas utiliser `x:Shared` pour les éléments d’une <xref:System.Windows.ResourceDictionary> qui se trouve dans un <xref:System.Windows.Style> qui est déjà un élément <xref:System.Windows.ResourceDictionary>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Éléments de base](../wpf/advanced/base-elements.md)
