---
title: 'Procédure : Obtenir l’objet de liaison d’une propriété cible liée aux données'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965435"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Procédure : Obtenir l’objet de liaison d’une propriété cible liée aux données
Cet exemple montre comment obtenir l’objet de liaison à partir d’une propriété cible liée à des données.  
  
## <a name="example"></a>Exemples  
 Vous pouvez effectuer les opérations suivantes pour récupérer <xref:System.Windows.Data.Binding> l’objet:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> Vous devez spécifier la propriété de dépendance pour la liaison de votre choix car il est possible que plusieurs propriétés de l’objet cible utilisent la liaison de données.  
  
 Vous pouvez également récupérer <xref:System.Windows.Data.BindingExpression> , puis récupérer la valeur de la <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> propriété.  
  
 Pour obtenir un exemple complet, consultez [Validation de liaison, exemple](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
> Si votre liaison est un <xref:System.Windows.Data.MultiBinding>, utilisez <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. S’il s’agit <xref:System.Windows.Data.PriorityBinding>d’un <xref:System.Windows.Data.BindingOperations>,<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>utilisez.. Si vous n’êtes pas certain que la propriété cible est liée <xref:System.Windows.Data.Binding>à l' <xref:System.Windows.Data.MultiBinding>aide d’un <xref:System.Windows.Data.PriorityBinding>, d’un ou <xref:System.Windows.Data.BindingOperations>d'<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>un, vous pouvez utiliser..  
  
## <a name="see-also"></a>Voir aussi

- [Créer une liaison dans du code](how-to-create-a-binding-in-code.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
