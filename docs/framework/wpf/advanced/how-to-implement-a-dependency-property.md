---
title: 'Procédure : Implémenter une propriété de dépendance'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400358"
---
# <a name="how-to-implement-a-dependency-property"></a>Procédure : Implémenter une propriété de dépendance
Cet exemple montre comment sauvegarder une propriété Common Language Runtime (CLR) avec un <xref:System.Windows.DependencyProperty> champ, définissant ainsi une propriété de dépendance. Quand vous définissez vos propres propriétés et que vous souhaitez qu’elles prennent en charge de nombreux aspects des fonctionnalités de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], notamment les styles, la liaison de données, l’héritage, l’animation et les valeurs par défaut, vous devez les implémenter en tant que propriétés de dépendance.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant inscrit d’abord une propriété de dépendance en appelant <xref:System.Windows.DependencyProperty.Register%2A> la méthode. Le nom du champ d’identificateur que vous utilisez pour stocker le nom et les caractéristiques de la propriété de dépendance doit être <xref:System.Windows.DependencyProperty.Name%2A> celui que vous avez choisi pour la propriété de dépendance <xref:System.Windows.DependencyProperty.Register%2A> dans le cadre de l’appel, ajouté `Property`par la chaîne littérale. Par exemple, si vous inscrivez une propriété de dépendance avec <xref:System.Windows.DependencyProperty.Name%2A> un `Location`de, le champ d’identificateur que vous définissez pour la propriété de dépendance doit être `LocationProperty`nommé.  
  
 Dans cet exemple, le nom de la propriété de dépendance et de son `State`accesseur CLR est; le champ d’identificateur est `StateProperty`; le type de <xref:System.Boolean>la propriété est; et le type qui inscrit la propriété `MyStateControl`de dépendance est.  
  
 Si vous ne respectez pas ce modèle d’affectation de noms, les concepteurs risquent de ne pas signaler correctement votre propriété et certains aspects de l’application des styles du système de propriétés risquent de ne pas se comporter comme prévu.  
  
 Vous pouvez également spécifier des métadonnées par défaut pour une propriété de dépendance. Cet exemple inscrit `false` comme valeur par défaut de la propriété de dépendance `State`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Pour plus d’informations sur l’implémentation d’une propriété de dépendance, par opposition à la simple sauvegarde d’une propriété CLR avec un champ privé, consultez [vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
- [Rubriques de guide pratique](properties-how-to-topics.md)
