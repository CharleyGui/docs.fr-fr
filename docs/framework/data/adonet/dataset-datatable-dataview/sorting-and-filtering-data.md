---
title: Tri et filtre de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 0907aa2a66e1bf51fefc7bed8ea2612cc0c830fa
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203216"
---
# <a name="sorting-and-filtering-data"></a>Tri et filtre de données
L'objet <xref:System.Data.DataView> offre plusieurs méthodes de tri et de filtrage de données dans un objet <xref:System.Data.DataTable> :  
  
- Vous pouvez utiliser la propriété <xref:System.Data.DataView.Sort%2A> pour spécifier un ordre de tri en fonction d'une ou de plusieurs colonnes et inclure des paramètres ASC (ordre croissant) et DESC (ordre décroissant).  
  
- Vous pouvez utiliser la propriété <xref:System.Data.DataView.ApplyDefaultSort%2A> pour créer automatiquement un ordre de tri, croissant, basé sur la ou les colonnes de clé primaire de la table. <xref:System.Data.DataView.ApplyDefaultSort%2A>s’applique uniquement lorsque la propriété **sort** est une référence null ou une chaîne vide et lorsque la table a une clé primaire définie.  
  
- Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowFilter%2A> pour spécifier des sous-ensembles de lignes basés sur les valeurs de colonne. Pour plus d’informations sur les expressions valides pour la propriété **RowFilter** , consultez les <xref:System.Data.DataColumn.Expression%2A> informations de référence <xref:System.Data.DataColumn> pour la propriété de la classe.  
  
     Si vous souhaitez retourner les résultats d’une requête particulière sur les données, au lieu de fournir une vue dynamique d’un sous-ensemble des données, utilisez les <xref:System.Data.DataView.Find%2A> méthodes <xref:System.Data.DataView.FindRows%2A> ou du **DataView** pour obtenir des performances optimales au lieu de définir la  **Propriété RowFilter** . La définition de la propriété **RowFilter** reconstruit l’index pour les données, en ajoutant une surcharge à votre application et en diminuant les performances. La propriété **RowFilter** est mieux utilisée dans une application liée aux données, où un contrôle lié affiche des résultats filtrés. Les méthodes **Find** et **FindRows** tirent parti de l’index actuel sans nécessiter la reconstruction de l’index. Pour plus d’informations sur les méthodes **Find** et **FindRows** , consultez [recherche de lignes](finding-rows.md).  
  
- Vous pouvez utiliser la propriété <xref:System.Data.DataView.RowStateFilter%2A> pour spécifier les versions de ligne à afficher. Le **DataView** gère implicitement la version de ligne à exposer en fonction du **RowState** de la ligne sous-jacente. Par exemple, si la valeur **RowStateFilter** est définie sur **DataViewRowState. Deleted**, le **DataView** expose la version de ligne d' **origine** de toutes les lignes **supprimées** , car il n’y a pas de version de ligne **actuelle** . Vous pouvez déterminer la version de ligne d’une ligne qui est exposée à l’aide de la propriété **rowversion** du **DataRowView**.  
  
     Le tableau suivant présente les options de **DataViewRowState**.  
  
    |Options DataViewRowState|Description|  
    |------------------------------|-----------------|  
    |**CurrentRows**|Version de ligne **actuelle** de toutes les lignes non **modifiées**, **ajoutées**et **modifiées** . Il s'agit de la valeur par défaut.|  
    |**Ajoute**|Version de ligne **actuelle** de toutes les lignes **ajoutées** .|  
    |**Supprimé**|Version de ligne d' **origine** de toutes les lignes **supprimées** .|  
    |**ModifiedCurrent**|Version de ligne **actuelle** de toutes les lignes **modifiées** .|  
    |**ModifiedOriginal**|Version de ligne d' **origine** de toutes les lignes **modifiées** .|  
    |**Aucun**|Aucune ligne.|  
    |**OriginalRows**|Version de ligne d' **origine** de toutes les lignes inchangées, **modifiées**et **supprimées** .|  
    |**Inchangé**|Version de ligne **actuelle** de toutes les lignes inchangées.|  
  
 Pour plus d’informations sur les États de ligne et les versions de ligne, consultez [États de ligne et versions de ligne](row-states-and-row-versions.md).  
  
 L'exemple de code suivant crée une vue faisant apparaître tous les produits pour lesquels la quantité en stock est inférieure ou égale au niveau de passage d'une nouvelle commande, triés d'abord par ID de fournisseur, puis par nom de produit.  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
