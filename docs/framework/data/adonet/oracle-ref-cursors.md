---
title: REF CURSOR Oracle
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7c6b326b15a2af58da9206adf28070e57fec600c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963512"
---
# <a name="oracle-ref-cursors"></a>REF CURSOR Oracle
Le Fournisseur de données .NET Framework pour Oracle prend en charge le type de données Oracle **REF CURSOR** . Lorsque vous utilisez le fournisseur de données pour travailler avec des REF CURSOR Oracle, vous devez tenir compte des comportements suivants.  
  
> [!NOTE]
> Certains comportements diffèrent de ceux du fournisseur Microsoft OLE DB pour Oracle (MSDAORA).  
  
- Pour des raisons de performances, le Fournisseur de données pour Oracle ne lie pas automatiquement les types de données **REF CURSOR** , comme le fait MSDAORA, sauf si vous les spécifiez explicitement.  
  
- Le fournisseur de données ne prend pas en charge les séquences d'échappement ODBC, notamment l'échappement {resultset} utilisé pour spécifier les paramètres REF CURSOR.  
  
- Pour exécuter une procédure stockée qui retourne des REF CURSOR, vous devez définir les paramètres dans <xref:System.Data.OracleClient.OracleParameterCollection> le avec <xref:System.Data.OracleClient.OracleType> un **Cursor** et un <xref:System.Data.OracleClient.OracleParameter.Direction%2A> de **Output**. Le fournisseur de données prend en charge la liaison des REF CURSOR en tant que paramètres de sortie seulement. Le fournisseur ne prend pas en charge les REF CURSOR en tant que paramètres d'entrée.  
  
- L'obtention d'un <xref:System.Data.OracleClient.OracleDataReader> à partir de la valeur de paramètre n'est pas prise en charge. Les valeurs sont de type <xref:System.DBNull> après l'exécution d'une commande.  
  
- La seule valeur d’énumération **CommandBehavior** qui fonctionne avec des REF CURSOR (par exemple, <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>lors de l’appel de) est **CloseConnection**; toutes les autres sont ignorées.  
  
- L’ordre des REF CURSOR dans le **OracleDataReader** dépend de l’ordre des paramètres dans le **OracleParameterCollection**. La propriété <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> est ignorée.  
  
- Le type de données de la **table** PL/SQL n’est pas pris en charge. Toutefois, les REF CURSOR sont plus efficaces. Si vous devez utiliser un type de données de **table** , utilisez le fournisseur de données OLE DB .net avec MSDAORA.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemples REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Contient trois exemples qui illustrent l'utilisation des REF CURSOR.  
  
 [Paramètres REF CURSOR dans un OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Montre comment exécuter une procédure stockée PL/SQL qui retourne un paramètre REF CURSOR et lit la valeur comme un **OracleDataReader**.  
  
 [Récupération de données à partir de plusieurs REF CURSOR à l’aide d’un OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Montre comment exécuter une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et lit les valeurs à l’aide d’un **OracleDataReader**.  
  
 [Remplissage d’un DataSet à l’aide d’un ou de plusieurs REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Montre comment exécuter une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et remplit un <xref:System.Data.DataSet> avec les lignes qui sont retournées.  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
