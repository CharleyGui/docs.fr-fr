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
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="dcf46-102">PresentationOptions:Freeze, attribut</span><span class="sxs-lookup"><span data-stu-id="dcf46-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="dcf46-103">Affecte à <xref:System.Windows.Freezable.IsFrozen%2A> l’état `true` la valeur sur <xref:System.Windows.Freezable> l’élément conteneur.</span><span class="sxs-lookup"><span data-stu-id="dcf46-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="dcf46-104">Le comportement par défaut <xref:System.Windows.Freezable> pour un `PresentationOptions:Freeze` sans l' `false` attribut spécifié <xref:System.Windows.Freezable.IsFrozen%2A> est celui au moment du chargement, et dépend <xref:System.Windows.Freezable> du comportement général au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dcf46-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="dcf46-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="dcf46-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="dcf46-106">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="dcf46-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="dcf46-107">Préfixe d’espace de noms XML, qui peut être n’importe quelle chaîne de préfixe valide, conformément à la spécification XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="dcf46-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="dcf46-108">Le préfixe `PresentationOptions` est utilisé à des fins d’identification dans cette documentation.</span><span class="sxs-lookup"><span data-stu-id="dcf46-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="dcf46-109">Élément qui instancie toute classe dérivée de <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="dcf46-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcf46-110">Notes</span><span class="sxs-lookup"><span data-stu-id="dcf46-110">Remarks</span></span>  
 <span data-ttu-id="dcf46-111">L' `Freeze` attribut est le seul attribut ou un autre élément de programmation défini `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` dans l’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="dcf46-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="dcf46-112">L' `Freeze` attribut existe spécifiquement dans cet espace de noms spécial afin qu’il puisse être désigné comme pouvant être ignoré, à l’aide de l' [attribut MC : Ignorable](mc-ignorable-attribute.md) dans le cadre des déclarations d’élément racine.</span><span class="sxs-lookup"><span data-stu-id="dcf46-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="dcf46-113">La raison qui `Freeze` doit pouvoir être ignorée est que les implémentations de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ne sont pas toutes en mesure de <xref:System.Windows.Freezable> geler un au moment du chargement ; cette fonctionnalité ne fait [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pas partie de la spécification.</span><span class="sxs-lookup"><span data-stu-id="dcf46-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="dcf46-114">La possibilité de traiter l' `Freeze` attribut est spécifiquement intégrée [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au processeur qui traite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les applications compilées.</span><span class="sxs-lookup"><span data-stu-id="dcf46-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="dcf46-115">L’attribut n’est pris en charge par aucune classe, et la syntaxe d’attribut n’est pas extensible ni modifiable.</span><span class="sxs-lookup"><span data-stu-id="dcf46-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="dcf46-116">Si vous implémentez votre propre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur, vous pouvez choisir de mettre en parallèle le comportement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de gel du processeur `Freeze` lors du <xref:System.Windows.Freezable> traitement de l’attribut sur les éléments au moment du chargement.</span><span class="sxs-lookup"><span data-stu-id="dcf46-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="dcf46-117">Toute valeur pour l' `Freeze` attribut autre que `true` (sans respect de la casse) génère une erreur de temps de chargement.</span><span class="sxs-lookup"><span data-stu-id="dcf46-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="dcf46-118">(Si vous `Freeze` spécifiez `false` l’attribut comme n’est pas une erreur, mais qu’il s’agit déjà `false` de la valeur par défaut, affectez la valeur à ne rien faire).</span><span class="sxs-lookup"><span data-stu-id="dcf46-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf46-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcf46-119">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="dcf46-120">Vue d’ensemble des objets Freezable</span><span class="sxs-lookup"><span data-stu-id="dcf46-120">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="dcf46-121">mc:Ignorable, attribut</span><span class="sxs-lookup"><span data-stu-id="dcf46-121">mc:Ignorable Attribute</span></span>](mc-ignorable-attribute.md)
