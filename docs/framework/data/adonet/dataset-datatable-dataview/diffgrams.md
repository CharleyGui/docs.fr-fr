---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2c521ef33c98234dac5f4b819a800cd524218462
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151154"
---
# <a name="diffgrams"></a>DiffGrams
Un DiffGram est un format XML qui identifie la version actuelle et la version d'origine d'éléments de données. L'objet <xref:System.Data.DataSet> utilise le format DiffGram pour charger son contenu et le rendre persistent, ainsi que pour le sérialiser en vue de son transport via une connexion réseau. Quand <xref:System.Data.DataSet> un est écrit comme un DiffGram, il remplit le DiffGram avec toutes les informations nécessaires <xref:System.Data.DataSet>pour recréer avec précision le contenu, mais pas le schéma, de la , y compris les valeurs de colonne des versions **originales** et **actuelles** rangée, les informations d’erreur de ligne, et l’ordre de ligne.  
  
 Lors de l'envoi et de l'extraction d'un objet <xref:System.Data.DataSet> à partir d'un service Web XML, le format DiffGram est implicitement utilisé. En outre, lors du <xref:System.Data.DataSet> chargement du contenu d’un XML en <xref:System.Data.DataSet> utilisant la méthode **ReadXml,** ou lors de l’écriture du contenu d’un XML en utilisant la méthode **WriteXml,** vous pouvez spécifier que le contenu soit lu ou écrit sous la forme d’un DiffGram. Pour plus d’informations, voir [Le chargement d’un ensemble de données à partir de XML](loading-a-dataset-from-xml.md) et [l’écriture de contenus DataSet sous forme de données XML](writing-dataset-contents-as-xml-data.md).  
  
 Si le format DiffGram est principalement utilisé par le .NET Framework en tant que format de sérialisation pour le contenu d'un objet <xref:System.Data.DataSet>, vous pouvez aussi l'utiliser pour modifier des données dans les tables d'une base de données Microsoft SQL Server.  
  
 Un Diffgram est généré par l’écriture du contenu de toutes les tables à un ** \<élément>diffgram.**  
  
### <a name="to-generate-a-diffgram"></a>Pour générer un Diffgram  
  
1. Générez une liste des tables racine (autrement dit, les tables sans parent).  
  
2. Pour chaque table et ses descendants dans la liste, écrivez la version actuelle de toutes les lignes dans la première section Diffgram.  
  
3. Pour chaque table <xref:System.Data.DataSet>dans le , écrivez la version originale de toutes les lignes, le cas échéant, dans la ** \<** section avant>du Diffgram.  
  
4. Pour les lignes qui ont des erreurs, écrivez le contenu d’erreur dans les ** \<erreurs>** section du Diffgram.  
  
 Un DiffGram est traité dans l'ordre du début du fichier XML à la fin.  
  
### <a name="to-process-a-diffgram"></a>Pour traiter un Diffgram  
  
1. Traitez la première section du DiffGram qui contient la version actuelle des lignes.  
  
2. Traiter la deuxième ** \<** ou la section avant>qui contient la version de ligne originale des lignes modifiées et supprimées.  
  
    > [!NOTE]
    > Si une ligne est marquée comme supprimée, l'opération de suppression peut aussi supprimer les descendants de la ligne, en fonction de la propriété `Cascade` du <xref:System.Data.DataSet> en cours.  
  
3. Traiter ** \<** les erreurs>section. Définissez les informations d'erreur pour la ligne et la colonne spécifiées pour chaque élément dans cette section.  
  
> [!NOTE]
> Si vous affectez <xref:System.Data.XmlWriteMode> à DiffGram, le contenu du <xref:System.Data.DataSet> cible et du <xref:System.Data.DataSet> d'origine peut être différent.  
  
## <a name="diffgram-format"></a>Format DiffGram  
 Le format DiffGram est divisé en trois sections : les données actuelles, les données d'origine (ou « avant ») et une section d'erreurs, comme indiqué dans l'exemple suivant.  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 Le format DiffGram est constitué des blocs de données suivants :  
  
 **\<**  ***DataInstance (en)***  **>**  
 Le nom de cet élément, ***DataInstance***, est utilisé à des fins d’explication dans cette documentation. Un élément ***DataInstance*** représente une <xref:System.Data.DataSet> <xref:System.Data.DataTable>ou une rangée d’un . Au lieu de *DataInstance*, l’élément contiendrait le nom de la <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>. Ce bloc du format DiffGram contient les données actuelles, qu'elles aient ou non été modifiées. Un élément, ou ligne, qui a été modifié est identifié avec le **diffgr:hasChanges** annotation.  
  
 **\<diffgr:avant>**  
 Ce bloc du format DiffGram contient la version d'origine d'une ligne. Les éléments de ce bloc sont appariés aux éléments du bloc ***DataInstance*** à l’aide **de l’annotation diffgr:id.**  
  
 **\<diffgr:erreurs>**  
 Ce bloc du format DiffGram contient des informations d’erreur pour une ligne particulière dans le bloc ***DataInstance.*** Les éléments de ce bloc sont appariés aux éléments du bloc ***DataInstance*** à l’aide **de l’annotation diffgr:id.**  
  
## <a name="diffgram-annotations"></a>Annotations DiffGram  
 Les DiffGrams utilisent plusieurs annotations pour relier les éléments des différents blocs DiffGram qui représentent différentes versions d'une ligne ou des informations d'erreur dans le <xref:System.Data.DataSet>.  
  
 Le tableau suivant décrit les annotations DiffGram qui sont définies dans l’urne DiffGram **namespace:schemas-microsoft-com:xml-diffgram-v1**.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**id**|Utilisé pour jumeler les éléments dans le **\<** **>** ** \<diffgr: avant>** et ** \<diffgr:erreurs>** blocs à des éléments dans le bloc ***DataInstance.*** Valeurs avec le **diffgr:id** annotation sont sous la forme *[TableName][RowIdentifier]*. Par exemple : `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Identifie l’élément **\<** du bloc ***DataInstance*** **>** est l’élément parent de l’élément actuel. Valeurs avec le **diffgr:parentId** annotation sont sous la forme *[TableName][RowIdentifier]*. Par exemple : `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifie une ligne **\<** dans le bloc ***DataInstance*** **>** modifiée. L’annotation **hasChanges** peut avoir l’une des deux valeurs suivantes :<br /><br /> **Inséré**<br /> Identifie une ligne **ajoutée.**<br /><br /> **Modifié**<br /> Identifie une ligne **modifiée** qui contient une version **de** ligne originale dans le ** \<diffgr: avant>** bloc. Notez que les lignes **supprimées** auront une version de ligne **originale** dans le **>** **\<** ** \<diffgr: avant>** bloc, mais il n’y aura pas d’élément annoté dans le bloc ***DataInstance.***|  
|**hasErrors**|Identifie une rangée **\<** dans le bloc ***DataInstance*** **>** avec un **RowError**. L’élément d’erreur est placé dans le ** \<diffgr:erreurs>** bloc.|  
|**Erreur**|Contient le texte du **RowError** pour un élément particulier dans le ** \<diffgr:erreurs>** bloc.|  
  
 Le <xref:System.Data.DataSet> inclut annotations supplémentaires lors de la lecture ou de l'écriture de son contenu en tant que DiffGram. Le tableau suivant décrit ces annotations supplémentaires, qui sont définies dans **l’urne namespace:schemas-microsoft-com:xml-msdata**.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**RowOrder**|Conserve l'ordre des lignes des données d'origine et identifie l'index d'une ligne dans un <xref:System.Data.DataTable> donné.|  
|**Cachés**|Identifie une colonne comme ayant une propriété **ColumnMapping** réglé à **MappingType.Hidden**. L’attribut est écrit dans le format **msdata:hidden** *[ColumnName]**valeur*". Par exemple : `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Notez que les colonnes masquées ne sont écrites sous la forme d'un attribut DiffGram que si elles contiennent des données. Autrement, elles sont ignorées.|  
  
## <a name="sample-diffgram"></a>Exemple de DiffGram  
 Un exemple du format DiffGram vous est proposé ci-après. Cet exemple illustre le résultat d’une mise à jour effectuée sur une ligne d’une table avant validation des modifications. La ligne dont le CustomerID est « ALFKI » a été modifiée, mais pas mise à jour. En conséquence, il ya une ligne **actuelle** avec un **diffgr:id** de **\<** "Customers1" dans le bloc ***DataInstance,*** **>** et une ligne **originale** avec un **diffgr:id** de "Customers1" dans le ** \<diffgr:avant>** bloc. La ligne avec un CustomerID de "ANATR" comprend un **RowError**, il est donc annoté avec `diffgr:hasErrors="true"` et il ya un élément connexe dans le ** \<diffgr:erreurs>** bloc.  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Écriture du contenu d'un DataSet comme données XML](writing-dataset-contents-as-xml-data.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
