---
title: "Comment : obtenir l'objet de liaison d'une propriété cible liée aux données"
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c528515124898c7deb6114e620ce21766123ab3c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453050"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Comment : obtenir l'objet de liaison d'une propriété cible liée aux données
Cet exemple montre comment obtenir l’objet de liaison à partir d’une propriété cible liée à des données.

## <a name="example"></a>Exemple
 Vous pouvez effectuer les opérations suivantes pour récupérer l’objet <xref:System.Windows.Data.Binding> :

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> Vous devez spécifier la propriété de dépendance pour la liaison de votre choix car il est possible que plusieurs propriétés de l’objet cible utilisent la liaison de données.

 Vous pouvez également récupérer le <xref:System.Windows.Data.BindingExpression>, puis récupérer la valeur de la propriété <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.

 Pour obtenir un exemple complet, consultez [Validation de liaison, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).

> [!NOTE]
> Si votre liaison est un <xref:System.Windows.Data.MultiBinding>, utilisez <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>. S’il s’agit d’un <xref:System.Windows.Data.PriorityBinding>, utilisez <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>. Si vous n’êtes pas certain que la propriété cible est liée à l’aide d’un <xref:System.Windows.Data.Binding>, d’un <xref:System.Windows.Data.MultiBinding>ou d’un <xref:System.Windows.Data.PriorityBinding>, vous pouvez utiliser <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- [Créer une liaison dans du code](how-to-create-a-binding-in-code.md)
- [Rubriques Comment](data-binding-how-to-topics.md)
