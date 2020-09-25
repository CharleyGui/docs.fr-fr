---
title: Interrogation de la collection DataRowView dans un DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 5757079bbc0ef8c498ea1db1a88f6b356ab0409e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172747"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Interrogation de la collection DataRowView dans un DataView

L’objet <xref:System.Data.DataView> expose une collection énumérable d’objets <xref:System.Data.DataRowView>. L'objet <xref:System.Data.DataRowView> représente une vue personnalisée d'un objet <xref:System.Data.DataRow> et affiche une version spécifique de cet objet <xref:System.Data.DataRow> dans un contrôle. Une seule version d'un objet <xref:System.Data.DataRow> peut être affichée par le biais d'un contrôle, comme un objet <xref:System.Windows.Forms.DataGridView>. Vous pouvez accéder à l'objet <xref:System.Data.DataRow> qui est exposé par le <xref:System.Data.DataRowView> par le biais de la propriété <xref:System.Data.DataRowView.Row%2A> de l'objet <xref:System.Data.DataRowView>. Lorsque vous affichez des valeurs à l'aide d'un <xref:System.Data.DataRowView>, la propriété <xref:System.Data.DataView.RowStateFilter%2A> détermine la version de ligne de l'objet <xref:System.Data.DataRow> sous-jacent qui est exposée. Pour plus d’informations sur l’accès à différentes versions de ligne à l’aide d’un <xref:System.Data.DataRow> , consultez [États de ligne et versions de ligne](./dataset-datatable-dataview/row-states-and-row-versions.md). Étant donné que la collection d' <xref:System.Data.DataRowView> objets exposée par le <xref:System.Data.DataView> est énumérable, vous pouvez utiliser LINQ to DataSet pour effectuer une interrogation.  
  
 L'exemple suivant recherche les produits de couleur rouge dans la table `Product` et crée une table à partir de cette requête. Un objet <xref:System.Data.DataView> est créé à partir de cette table et la propriété <xref:System.Data.DataView.RowStateFilter%2A> est définie pour filtrer sur les lignes supprimées et modifiées. L'objet <xref:System.Data.DataView> est ensuite utilisé comme source dans une requête LINQ, et les objets <xref:System.Data.DataRowView> qui ont été modifiés et supprimés sont liés à un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 L'exemple suivant crée une table de produits à partir d'une vue qui est liée à un contrôle <xref:System.Windows.Forms.DataGridView>. Une requête recherche les produits de couleur rouge dans l'objet <xref:System.Data.DataView> et les résultats classés sont liés à un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Voir aussi

- [Liaison de données et LINQ to DataSet](data-binding-and-linq-to-dataset.md)
