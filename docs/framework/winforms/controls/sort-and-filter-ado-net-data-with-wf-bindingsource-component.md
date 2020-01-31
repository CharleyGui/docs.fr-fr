---
title: Trier et filtrer les données ADO.NET avec le composant BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742976"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms
Vous pouvez exposer la fonctionnalité de tri et de filtrage de <xref:System.Windows.Forms.BindingSource> contrôle via les propriétés <xref:System.Windows.Forms.BindingSource.Sort%2A> et <xref:System.Windows.Forms.BindingSource.Filter%2A>. Vous pouvez appliquer un tri simple lorsque la source de données sous-jacente est un <xref:System.ComponentModel.IBindingList>, et vous pouvez appliquer le filtrage et le tri avancé lorsque la source de données est un <xref:System.ComponentModel.IBindingListView>. La propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> requiert une syntaxe ADO.NET standard : une chaîne représentant le nom d’une colonne de données dans la source de données, suivi de `ASC` ou `DESC` pour indiquer si la liste doit être triée par ordre croissant ou décroissant. Vous pouvez définir un tri avancé ou un tri sur plusieurs colonnes en séparant chaque colonne par un séparateur de virgule. La propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> prend une expression de chaîne.  
  
> [!NOTE]
> Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Pour filtrer des données avec le BindingSource  
  
- Affectez à la propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> la valeur expression de votre choix.  
  
     Dans l’exemple de code suivant, l’expression est un nom de colonne suivi de la valeur que vous souhaitez pour la colonne.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Pour trier des données avec le BindingSource  
  
1. Définissez la propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> sur le nom de colonne que vous souhaitez suivi de `ASC` ou `DESC` pour indiquer l’ordre croissant ou décroissant.  
  
2. Séparez plusieurs colonnes par une virgule.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant charge des données de la table Customers de l’exemple de base de données Northwind dans un contrôle <xref:System.Windows.Forms.DataGridView>, puis filtre et trie les données affichées.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour exécuter cet exemple, collez le code dans un formulaire qui contient un <xref:System.Windows.Forms.BindingSource> nommé `BindingSource1` et un <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1`. Gérez l’événement <xref:System.Windows.Forms.Form.Load> pour le formulaire et appelez `InitializeSortedFilteredBindingSource` dans la méthode de gestionnaire d’événements Load.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Guide pratique pour installer des exemples de bases de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource, composant](bindingsource-component.md)
