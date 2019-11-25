---
title: "Comment : obtenir l'objet de liaison d'une propriété cible liée aux données"
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: cf2ddc93a7c46ee6956d2731a786289f64086360
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976418"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Comment : obtenir l'objet de liaison d'une propriété cible liée aux données
Cet exemple montre comment obtenir l’objet de liaison à partir d’une propriété cible liée à des données.

## <a name="example"></a>Exemple
 Vous pouvez effectuer les opérations suivantes pour récupérer l’objet <xref:System.Windows.Data.Binding> :

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> Vous devez spécifier la propriété de dépendance pour la liaison de votre choix car il est possible que plusieurs propriétés de l’objet cible utilisent la liaison de données.

 Vous pouvez également récupérer le <xref:System.Windows.Data.BindingExpression>, puis récupérer la valeur de la propriété <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.

 Pour obtenir un exemple complet, consultez [Validation de liaison, exemple](https://go.microsoft.com/fwlink/?LinkID=159972).

> [!NOTE]
> Si votre liaison est un <xref:System.Windows.Data.MultiBinding>, utilisez <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>. S’il s’agit d’un <xref:System.Windows.Data.PriorityBinding>, utilisez <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>. Si vous n’êtes pas certain que la propriété cible est liée à l’aide d’un <xref:System.Windows.Data.Binding>, d’un <xref:System.Windows.Data.MultiBinding>ou d’un <xref:System.Windows.Data.PriorityBinding>, vous pouvez utiliser <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- [Créer une liaison dans du code](how-to-create-a-binding-in-code.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
