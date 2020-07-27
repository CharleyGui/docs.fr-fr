---
title: Guide pratique pour implémenter une propriété de dépendance
description: Définissez une propriété de dépendance dans Windows Presentation Foundation, en sauvegardant une propriété common language runtime avec un champ DependencyProperty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 673f653a9b02627efcccdfe08c4812ca0834217c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165096"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="7731d-103">Guide pratique pour implémenter une propriété de dépendance</span><span class="sxs-lookup"><span data-stu-id="7731d-103">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="7731d-104">Cet exemple montre comment sauvegarder une propriété common language runtime (CLR) avec un <xref:System.Windows.DependencyProperty> champ, définissant ainsi une propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="7731d-104">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="7731d-105">Quand vous définissez vos propres propriétés et que vous souhaitez qu’elles prennent en charge de nombreux aspects des fonctionnalités de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], notamment les styles, la liaison de données, l’héritage, l’animation et les valeurs par défaut, vous devez les implémenter en tant que propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="7731d-105">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7731d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="7731d-106">Example</span></span>  
 <span data-ttu-id="7731d-107">L’exemple suivant inscrit d’abord une propriété de dépendance en appelant la <xref:System.Windows.DependencyProperty.Register%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="7731d-107">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="7731d-108">Le nom du champ d’identificateur que vous utilisez pour stocker le nom et les caractéristiques de la propriété de dépendance doit être celui que <xref:System.Windows.DependencyProperty.Name%2A> vous avez choisi pour la propriété de dépendance dans le cadre de l' <xref:System.Windows.DependencyProperty.Register%2A> appel, ajouté par la chaîne littérale `Property` .</span><span class="sxs-lookup"><span data-stu-id="7731d-108">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="7731d-109">Par exemple, si vous inscrivez une propriété de dépendance avec un <xref:System.Windows.DependencyProperty.Name%2A> de `Location` , le champ d’identificateur que vous définissez pour la propriété de dépendance doit être nommé `LocationProperty` .</span><span class="sxs-lookup"><span data-stu-id="7731d-109">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="7731d-110">Dans cet exemple, le nom de la propriété de dépendance et de son accesseur CLR est `State` ; le champ d’identificateur est ; `StateProperty` le type de la propriété est <xref:System.Boolean> ; et le type qui inscrit la propriété de dépendance est `MyStateControl` .</span><span class="sxs-lookup"><span data-stu-id="7731d-110">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="7731d-111">Si vous ne respectez pas ce modèle d’affectation de noms, les concepteurs risquent de ne pas signaler correctement votre propriété et certains aspects de l’application des styles du système de propriétés risquent de ne pas se comporter comme prévu.</span><span class="sxs-lookup"><span data-stu-id="7731d-111">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="7731d-112">Vous pouvez également spécifier des métadonnées par défaut pour une propriété de dépendance.</span><span class="sxs-lookup"><span data-stu-id="7731d-112">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="7731d-113">Cet exemple inscrit `false` comme valeur par défaut de la propriété de dépendance `State`.</span><span class="sxs-lookup"><span data-stu-id="7731d-113">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="7731d-114">Pour plus d’informations sur l’implémentation d’une propriété de dépendance, par opposition à la simple sauvegarde d’une propriété CLR avec un champ privé, consultez [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7731d-114">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7731d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7731d-115">See also</span></span>

- [<span data-ttu-id="7731d-116">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="7731d-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="7731d-117">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="7731d-117">How-to Topics</span></span>](properties-how-to-topics.md)
