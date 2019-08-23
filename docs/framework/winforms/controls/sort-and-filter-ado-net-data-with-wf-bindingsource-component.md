---
title: 'Procédure : trier et filtrer des données ADO.NET avec le composant BindingSource de Windows Forms'
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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960432"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Procédure : trier et filtrer des données ADO.NET avec le composant BindingSource de Windows Forms
Vous pouvez exposer la fonctionnalité de tri et de <xref:System.Windows.Forms.BindingSource> filtrage du contrôle <xref:System.Windows.Forms.BindingSource.Sort%2A> via <xref:System.Windows.Forms.BindingSource.Filter%2A> les propriétés et. Vous pouvez appliquer un tri simple lorsque la source de données sous <xref:System.ComponentModel.IBindingList>-jacente est un et vous pouvez appliquer le filtrage et le tri avancé lorsque <xref:System.ComponentModel.IBindingListView>la source de données est un. La <xref:System.Windows.Forms.BindingSource.Sort%2A> propriété requiert une syntaxe ADO.NET standard: chaîne représentant le nom d’une colonne de données dans la source de données `ASC` suivie de `DESC` ou pour indiquer si la liste doit être triée par ordre croissant ou décroissant. Vous pouvez définir un tri avancé ou un tri sur plusieurs colonnes en séparant chaque colonne par un séparateur de virgule. La <xref:System.Windows.Forms.BindingSource.Filter%2A> propriété prend une expression de chaîne.  
  
> [!NOTE]
> Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>Pour filtrer des données avec le BindingSource  
  
- Affectez <xref:System.Windows.Forms.BindingSource.Filter%2A> à la propriété l’expression de votre choix.  
  
     Dans l’exemple de code suivant, l’expression est un nom de colonne suivi de la valeur que vous souhaitez pour la colonne.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>Pour trier des données avec le BindingSource  
  
1. Affectez <xref:System.Windows.Forms.BindingSource.Sort%2A> à la propriété le nom de colonne que vous souhaitez `ASC` suivi `DESC` ou pour indiquer l’ordre croissant ou décroissant.  
  
2. Séparez plusieurs colonnes par une virgule.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant charge des données de la table Customers de l’exemple de <xref:System.Windows.Forms.DataGridView> base de données Northwind dans un contrôle, puis filtre et trie les données affichées.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour exécuter cet exemple, collez le code dans un formulaire qui contient <xref:System.Windows.Forms.BindingSource> un `BindingSource1` nommé et <xref:System.Windows.Forms.DataGridView> un `dataGridView1`nommé. Gérez l' <xref:System.Windows.Forms.Form.Load> événement pour le formulaire et appelez `InitializeSortedFilteredBindingSource` dans la méthode de gestionnaire d’événements Load.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Guide pratique pour Installer des exemples de bases de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource, composant](bindingsource-component.md)
