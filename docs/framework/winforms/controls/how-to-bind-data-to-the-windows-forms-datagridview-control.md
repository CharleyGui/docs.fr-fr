---
title: Lier les données à DataGridView Control
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182276"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Comment : lier les données au contrôle DataGridView de formulaires Windows

Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge le modèle standard de liaison de données Windows Forms, de sorte qu’il peut se lier à une variété de sources de données. Habituellement, vous vous <xref:System.Windows.Forms.BindingSource> liez à un qui gère l’interaction avec la source de données. Il <xref:System.Windows.Forms.BindingSource> peut s’agir de n’importe quelle source de données Windows Forms, ce qui vous donne une grande flexibilité lors du choix ou de la modification de l’emplacement de vos données. Pour plus d’informations <xref:System.Windows.Forms.DataGridView> sur les sources de données, le contrôle prend en charge, consultez l’aperçu du [contrôle DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio bénéficie d’un soutien étendu pour la liaison de données au contrôle DataGridView. Pour plus d’informations, voir [Comment : lier les données au contrôle Windows Forms DataGridView à l’aide du Concepteur](bind-data-to-the-datagrid-using-the-designer.md).  

Pour connecter un contrôle DataGridView aux données :

1. Implémentez une méthode pour gérer les détails de la récupération des données. L’exemple de code `GetData` suivant implémente une méthode qui initialise un <xref:System.Data.SqlClient.SqlDataAdapter>, et l’utilise pour peupler un <xref:System.Data.DataTable>. Il lie ensuite <xref:System.Data.DataTable> le <xref:System.Windows.Forms.BindingSource>.

2. Dans le gestionnaire <xref:System.Windows.Forms.Form.Load> d’événement <xref:System.Windows.Forms.DataGridView> du formulaire, lier le contrôle à la <xref:System.Windows.Forms.BindingSource>, et appeler la `GetData` méthode pour récupérer les données.  

## <a name="example"></a> Exemple

Cet exemple de code complet récupère des données d’une base de données pour remplir un contrôle DataGridView sous forme windows. Le formulaire comporte également des boutons pour recharger les données et soumettre des modifications à la base de données.  

Cet exemple nécessite :

- Accès à une base de données d’échantillons Northwind SQL Server. Pour plus d’informations sur l’installation de la base de données de l’échantillon Northwind, consultez [les données de données de l’échantillon pour ADO.NET échantillons de code.](../../data/adonet/sql/linq/downloading-sample-databases.md)

- Références aux assemblages System, System.Windows.Forms, System.Data et System.Xml.  

Pour créer et exécuter cet exemple, coller le code dans le fichier de code *Form1* dans un nouveau projet Windows Forms. Pour obtenir de l’information sur la construction à partir de la ligne de commandement C ou Visual Basic, voir [le bâtiment de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou Build à partir de la ligne de [commandement](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Remplissez `connectionString` la variable dans l’exemple avec les valeurs de votre connexion de base de données d’échantillons Northwind SQL Server. L’authentification windows, également appelée sécurité intégrée, est un moyen plus sûr de se connecter à la base de données que de stocker un mot de passe dans la chaîne de connexion. Pour plus d’informations sur la sécurité des connexions, voir [Protéger les informations de connexion](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Afficher les données dans le contrôle DataGridView des formulaires Windows](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Protéger les informations de connexion](../../data/adonet/protecting-connection-information.md)
