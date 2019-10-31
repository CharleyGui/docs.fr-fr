---
title: 'Comment : lier des données au contrôle DataGridView Windows Forms'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: bdba8af04cd9473b17d1a28f07ead7cd5bf43698
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139091"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Comment : lier des données au contrôle DataGridView Windows Forms

Le contrôle de <xref:System.Windows.Forms.DataGridView> prend en charge le modèle de liaison de données standard Windows Forms, de sorte qu’il peut être lié à une variété de sources de données. En général, vous établissez une liaison à une <xref:System.Windows.Forms.BindingSource> qui gère l’interaction avec la source de données. La <xref:System.Windows.Forms.BindingSource> peut être n’importe quelle source de données Windows Forms, ce qui vous offre une grande souplesse lors du choix ou de la modification de l’emplacement de vos données. Pour plus d’informations sur les sources de données prises en charge par le contrôle <xref:System.Windows.Forms.DataGridView>, consultez [vue d’ensemble du contrôle DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio prend en charge la liaison de données au contrôle DataGridView. Pour plus d’informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms à l’aide du concepteur](bind-data-to-the-datagrid-using-the-designer.md).  

Pour connecter un contrôle DataGridView à des données :

1. Implémentez une méthode pour gérer les détails de la récupération des données. L’exemple de code suivant implémente une méthode `GetData` qui initialise une <xref:System.Data.SqlClient.SqlDataAdapter>et l’utilise pour remplir un <xref:System.Data.DataTable>. Il lie ensuite le <xref:System.Data.DataTable> au <xref:System.Windows.Forms.BindingSource>. 

2. Dans le gestionnaire d’événements <xref:System.Windows.Forms.Form.Load> du formulaire, liez le contrôle <xref:System.Windows.Forms.DataGridView> au <xref:System.Windows.Forms.BindingSource>et appelez la méthode `GetData` pour récupérer les données.  

## <a name="example"></a>Exemple

Cet exemple de code complet récupère les données d’une base de données pour remplir un contrôle DataGridView dans un Windows Form. Le formulaire contient également des boutons permettant de recharger les données et de soumettre les modifications à la base de données.  

Cet exemple nécessite : 

- Accès à un exemple de base de données Northwind SQL Server. Pour plus d’informations sur l’installation de l’exemple de base de données Northwind, consultez [obtenir les exemples de bases de données pour les exemples de code ADO.net](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Références aux assemblys System, System. Windows. Forms, System. Data et System. Xml.  

Pour générer et exécuter cet exemple, collez le code dans le fichier de code *Form1* dans un nouveau projet de Windows Forms. Pour plus d’informations sur la C# génération à partir de la ligne de commande ou Visual Basic, consultez génération à partir de la [ligne de commande avec CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Renseignez la variable `connectionString` dans l’exemple avec les valeurs de votre connexion Northwind SQL Server exemple de connexion à la base de données. L’authentification Windows, également appelée sécurité intégrée, est un moyen plus sûr de se connecter à la base de données que de stocker un mot de passe dans la chaîne de connexion. Pour plus d’informations sur la sécurité des connexions, consultez [protéger les informations de connexion](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Afficher des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Protéger les informations de connexion](../../data/adonet/protecting-connection-information.md)
