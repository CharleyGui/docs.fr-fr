---
title: 'Comment : naviguer parmi les données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 2dd900b652b0ff21ea0eb0dbc5463b22c869ec7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739403"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Comment : naviguer au sein des données dans les Windows Forms
Dans une application Windows, le moyen le plus simple de parcourir les enregistrements d’une source de données consiste à lier un composant <xref:System.Windows.Forms.BindingSource> à la source de données, puis à lier les contrôles à la <xref:System.Windows.Forms.BindingSource>. Vous pouvez ensuite utiliser la méthode de navigation intégrée sur le <xref:System.Windows.Forms.BindingSource> un tel <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> et <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. L’utilisation de ces méthodes ajuste les propriétés <xref:System.Windows.Forms.BindingSource.Position%2A> et <xref:System.Windows.Forms.BindingSource.Current%2A> de la <xref:System.Windows.Forms.BindingSource> de manière appropriée. Vous pouvez également rechercher un élément et le définir en tant qu’élément actuel en définissant la propriété <xref:System.Windows.Forms.BindingSource.Position%2A>.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Pour incrémenter la position dans une source de données  
  
1. Définissez la propriété <xref:System.Windows.Forms.BindingSource.Position%2A> du <xref:System.Windows.Forms.BindingSource> pour vos données liées à la position d’enregistrement à atteindre. L’exemple suivant illustre l’utilisation de la méthode <xref:System.Windows.Forms.BindingSource.MoveNext%2A> de la <xref:System.Windows.Forms.BindingSource> pour incrémenter la propriété <xref:System.Windows.Forms.BindingSource.Position%2A> lorsque l’utilisateur clique sur le `nextButton`. Le <xref:System.Windows.Forms.BindingSource> est associé à la table `Customers` d’un `Northwind`de DataSet.  
  
    > [!NOTE]
    > La définition de la propriété <xref:System.Windows.Forms.BindingSource.Position%2A> sur une valeur au-delà du premier ou du dernier enregistrement n’entraîne pas d’erreur, car le .NET Framework ne vous permet pas de définir la position sur une valeur en dehors des limites de la liste. Si, dans votre application, il est important de savoir si vous avez dépassé le premier ou le dernier enregistrement, incluez la logique permettant de tester si vous dépassez le nombre d’éléments de données.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Pour vérifier si vous avez dépassé la fin ou le début  
  
1. Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.BindingSource.PositionChanged>. Dans le gestionnaire, vous pouvez vérifier si la valeur de position proposée a dépassé le nombre réel d’éléments de données.  
  
     L’exemple suivant montre comment vous pouvez vérifier si vous avez atteint le dernier élément de données. Dans l’exemple, si vous êtes au dernier élément, le bouton **suivant** du formulaire est désactivé.  
  
    > [!NOTE]
    > Sachez que, si vous modifiez la liste que vous naviguez dans le code, vous devez réactiver le bouton **suivant** afin que les utilisateurs puissent parcourir la totalité de la nouvelle liste. En outre, sachez que l’événement <xref:System.Windows.Forms.BindingSource.PositionChanged> ci-dessus pour le <xref:System.Windows.Forms.BindingSource> spécifique avec lequel vous travaillez doit être associé à sa méthode de gestion d’événements. Voici un exemple de méthode de gestion de l’événement <xref:System.Windows.Forms.BindingSource.PositionChanged> :  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Pour rechercher un élément et le définir comme élément actuel  
  
1. Recherchez l’enregistrement que vous souhaitez définir en tant qu’élément actuel. Vous pouvez le faire à l’aide de la méthode <xref:System.Windows.Forms.BindingSource.Find%2A> de la <xref:System.Windows.Forms.BindingSource>, si votre source de données implémente <xref:System.ComponentModel.IBindingList>. <xref:System.ComponentModel.BindingList%601> et <xref:System.Data.DataView>sont des exemples de sources de données qui implémentent <xref:System.ComponentModel.IBindingList>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Sources de données prises en charge par les Windows Forms](data-sources-supported-by-windows-forms.md)
- [Notification de modifications dans la liaison de données Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
