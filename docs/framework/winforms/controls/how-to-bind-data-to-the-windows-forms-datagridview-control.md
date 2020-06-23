---
title: Lier des données au contrôle DataGridView
ms.date: 02/08/2019
description: Découvrez comment le contrôle DataGridView prend en charge le modèle de liaison de données standard Windows Forms afin qu’il puisse être lié à une variété de sources de données.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904414"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Comment : lier des données au contrôle DataGridView Windows Forms

Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge le modèle de liaison de données standard Windows Forms, afin qu’il puisse être lié à une variété de sources de données. En général, vous liez à un <xref:System.Windows.Forms.BindingSource> qui gère l’interaction avec la source de données. <xref:System.Windows.Forms.BindingSource>Peut être n’importe quelle Windows Forms source de données, ce qui vous offre une grande souplesse lors du choix ou de la modification de l’emplacement de vos données. Pour plus d’informations sur les sources de données <xref:System.Windows.Forms.DataGridView> prises en charge par le contrôle, consultez [vue d’ensemble du contrôle DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio prend en charge la liaison de données au contrôle DataGridView. Pour plus d’informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms à l’aide du concepteur](bind-data-to-the-datagrid-using-the-designer.md).  

Pour connecter un contrôle DataGridView à des données :

1. Implémentez une méthode pour gérer les détails de la récupération des données. L’exemple de code suivant implémente une `GetData` méthode qui initialise un <xref:System.Data.SqlClient.SqlDataAdapter> et l’utilise pour remplir un <xref:System.Data.DataTable> . Il lie ensuite le <xref:System.Data.DataTable> à <xref:System.Windows.Forms.BindingSource> .

2. Dans le gestionnaire d' <xref:System.Windows.Forms.Form.Load> événements du formulaire, liez le <xref:System.Windows.Forms.DataGridView> contrôle à <xref:System.Windows.Forms.BindingSource> et appelez la `GetData` méthode pour récupérer les données.  

## <a name="example"></a>Exemple

Cet exemple de code complet récupère les données d’une base de données pour remplir un contrôle DataGridView dans un Windows Form. Le formulaire contient également des boutons permettant de recharger les données et de soumettre les modifications à la base de données.  

Cet exemple nécessite :

- Accès à un exemple de base de données Northwind SQL Server. Pour plus d’informations sur l’installation de l’exemple de base de données Northwind, consultez [obtenir les exemples de bases de données pour les exemples de code ADO.net](../../data/adonet/sql/linq/downloading-sample-databases.md).

- Références aux assemblys System, System. Windows. Forms, System. Data et System.Xml.  

Pour générer et exécuter cet exemple, collez le code dans le fichier de code *Form1* dans un nouveau projet de Windows Forms. Pour plus d’informations sur la génération à partir de la ligne de commande C# ou Visual Basic, consultez génération à partir de la [ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Renseignez la `connectionString` variable dans l’exemple avec les valeurs de votre connexion Northwind SQL Server exemple de connexion à la base de données. L’authentification Windows, également appelée sécurité intégrée, est un moyen plus sûr de se connecter à la base de données que de stocker un mot de passe dans la chaîne de connexion. Pour plus d’informations sur la sécurité des connexions, consultez [protéger les informations de connexion](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Afficher des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Protéger les informations de connexion](../../data/adonet/protecting-connection-information.md)
