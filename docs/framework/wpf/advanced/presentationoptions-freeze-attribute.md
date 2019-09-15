---
title: PresentationOptions:Freeze, attribut
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991425"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze, attribut
Affecte à <xref:System.Windows.Freezable.IsFrozen%2A> l’état `true` la valeur sur <xref:System.Windows.Freezable> l’élément conteneur. Le comportement par défaut <xref:System.Windows.Freezable> pour un `PresentationOptions:Freeze` sans l' `false` attribut spécifié <xref:System.Windows.Freezable.IsFrozen%2A> est celui au moment du chargement, et dépend <xref:System.Windows.Freezable> du comportement général au moment de l’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`PresentationOptions`|Préfixe d’espace de noms XML, qui peut être n’importe quelle chaîne de préfixe valide, conformément à la spécification XML 1,0. Le préfixe `PresentationOptions` est utilisé à des fins d’identification dans cette documentation.|  
|`freezableElement`|Élément qui instancie toute classe dérivée de <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Notes  
 L' `Freeze` attribut est le seul attribut ou un autre élément de programmation défini `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` dans l’espace de noms XML. L' `Freeze` attribut existe spécifiquement dans cet espace de noms spécial afin qu’il puisse être désigné comme pouvant être ignoré, à l’aide de l' [attribut MC : Ignorable](mc-ignorable-attribute.md) dans le cadre des déclarations d’élément racine. La raison qui `Freeze` doit pouvoir être ignorée est que les implémentations de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ne sont pas toutes en mesure de <xref:System.Windows.Freezable> geler un au moment du chargement ; cette fonctionnalité ne fait [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pas partie de la spécification.  
  
 La possibilité de traiter l' `Freeze` attribut est spécifiquement intégrée [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au processeur qui traite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les applications compilées. L’attribut n’est pris en charge par aucune classe, et la syntaxe d’attribut n’est pas extensible ni modifiable. Si vous implémentez votre propre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur, vous pouvez choisir de mettre en parallèle le comportement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de gel du processeur `Freeze` lors du <xref:System.Windows.Freezable> traitement de l’attribut sur les éléments au moment du chargement.  
  
 Toute valeur pour l' `Freeze` attribut autre que `true` (sans respect de la casse) génère une erreur de temps de chargement. (Si vous `Freeze` spécifiez `false` l’attribut comme n’est pas une erreur, mais qu’il s’agit déjà `false` de la valeur par défaut, affectez la valeur à ne rien faire).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Freezable>
- [Vue d’ensemble des objets Freezable](freezable-objects-overview.md)
- [mc:Ignorable, attribut](mc-ignorable-attribute.md)
