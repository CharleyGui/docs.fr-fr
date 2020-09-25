---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: aff9c2347fab51d853e19bd9dc16666c4ed549b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172799"
---
# <a name="diffgrams"></a>DiffGrams

Un DiffGram est un format XML qui identifie la version actuelle et la version d'origine d'éléments de données. L'objet <xref:System.Data.DataSet> utilise le format DiffGram pour charger son contenu et le rendre persistent, ainsi que pour le sérialiser en vue de son transport via une connexion réseau. Lorsqu’un <xref:System.Data.DataSet> est écrit sous la forme d’un DiffGram, il remplit le DiffGram avec toutes les informations nécessaires pour recréer avec précision le contenu, mais pas le schéma, du <xref:System.Data.DataSet> , y compris les valeurs de colonne des versions de ligne **d’origine** et **actuelle** , les informations d’erreur de ligne et l’ordre des lignes.  
  
 Lors de l'envoi et de l'extraction d'un objet <xref:System.Data.DataSet> à partir d'un service Web XML, le format DiffGram est implicitement utilisé. En outre, lors du chargement du contenu d’un <xref:System.Data.DataSet> à partir d’un fichier XML à l’aide de la méthode **ReadXml** , ou lors de l’écriture du contenu d’un <xref:System.Data.DataSet> fichier dans XML à l’aide de la méthode **WriteXml** , vous pouvez spécifier que le contenu doit être lu ou écrit en tant que DiffGram. Pour plus d’informations, consultez [chargement d’un DataSet à partir de XML et écriture du contenu d’un](loading-a-dataset-from-xml.md) [DataSet en tant que données XML](writing-dataset-contents-as-xml-data.md).  
  
 Si le format DiffGram est principalement utilisé par le .NET Framework en tant que format de sérialisation pour le contenu d'un objet <xref:System.Data.DataSet>, vous pouvez aussi l'utiliser pour modifier des données dans les tables d'une base de données Microsoft SQL Server.  
  
 Un DiffGram est généré en écrivant le contenu de toutes les tables dans un **\<diffgram>** élément.  
  
### <a name="to-generate-a-diffgram"></a>Pour générer un Diffgram  
  
1. Générez une liste des tables racine (autrement dit, les tables sans parent).  
  
2. Pour chaque table et ses descendants dans la liste, écrivez la version actuelle de toutes les lignes dans la première section Diffgram.  
  
3. Pour chaque table dans <xref:System.Data.DataSet> , écrivez la version d’origine de toutes les lignes, le cas échéant, dans la **\<before>** section du DiffGram.  
  
4. Pour les lignes qui contiennent des erreurs, écrivez le contenu de l’erreur dans la **\<errors>** section du DiffGram.  
  
 Un DiffGram est traité dans l'ordre du début du fichier XML à la fin.  
  
### <a name="to-process-a-diffgram"></a>Pour traiter un Diffgram  
  
1. Traitez la première section du DiffGram qui contient la version actuelle des lignes.  
  
2. Traitez la deuxième ou la **\<before>** section qui contient la version de ligne d’origine des lignes modifiées et supprimées.  
  
    > [!NOTE]
    > Si une ligne est marquée comme supprimée, l'opération de suppression peut aussi supprimer les descendants de la ligne, en fonction de la propriété `Cascade` du <xref:System.Data.DataSet> en cours.  
  
3. Traitez la **\<errors>** section. Définissez les informations d'erreur pour la ligne et la colonne spécifiées pour chaque élément dans cette section.  
  
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
  
 **\<**  ***DataInstance***  **>**  
 Le nom de cet élément, ***DataInstance***, est utilisé à des fins d’explication dans cette documentation. Un élément ***DataInstance*** représente une <xref:System.Data.DataSet> ligne ou d’un <xref:System.Data.DataTable> . Au lieu de *DataInstance*, l’élément contient le nom de <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> . Ce bloc du format DiffGram contient les données actuelles, qu'elles aient ou non été modifiées. Un élément ou une ligne qui a été modifié est identifié avec l’annotation **diffgr : hasChanges** .  
  
 **\<diffgr:before>**  
 Ce bloc du format DiffGram contient la version d'origine d'une ligne. Les éléments de ce bloc sont mis en correspondance avec les éléments du bloc ***DataInstance*** à l’aide de l’annotation **diffgr : ID** .  
  
 **\<diffgr:errors>**  
 Ce bloc du format DiffGram contient des informations d’erreur pour une ligne particulière dans le bloc ***DataInstance*** . Les éléments de ce bloc sont mis en correspondance avec les éléments du bloc ***DataInstance*** à l’aide de l’annotation **diffgr : ID** .  
  
## <a name="diffgram-annotations"></a>Annotations DiffGram  

 Les DiffGrams utilisent plusieurs annotations pour relier les éléments des différents blocs DiffGram qui représentent différentes versions d'une ligne ou des informations d'erreur dans le <xref:System.Data.DataSet>.  
  
 Le tableau suivant décrit les annotations DiffGram définies dans l’espace de noms DiffGram **urn : schemas-microsoft-com : XML-DiffGram-v1**.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**id**|Utilisé pour coupler les éléments dans **\<diffgr:before>** les **\<diffgr:errors>** blocs et aux éléments du **\<** ***DataInstance*** **>** bloc. Les valeurs avec l’annotation **diffgr : ID** se présentent sous la forme *[TableName] [RowIdentifier]*. Par exemple : `<Customers diffgr:id="Customers1">`.|  
|**ID**|Identifie l’élément du **\<** ***DataInstance*** **>** bloc qui est l’élément parent de l’élément actuel. Les valeurs avec l’annotation **diffgr : ParentId** se présentent sous la forme *[TableName] [RowIdentifier]*. Par exemple : `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifie une ligne dans le **\<** ***DataInstance*** **>** bloc comme ayant été modifiée. L’annotation **HasChanges** peut avoir l’une des deux valeurs suivantes :<br /><br /> **Insérer**<br /> Identifie une ligne **ajoutée** .<br /><br /> **a modifié**<br /> Identifie une ligne **modifiée** qui contient une version de ligne **d’origine** dans le **\<diffgr:before>** bloc. Notez que les lignes **supprimées** auront une version de ligne **d’origine** dans le **\<diffgr:before>** bloc, mais qu’il n’y aura pas d’élément annoté dans le **\<** ***DataInstance*** **>** bloc.|  
|**hasErrors**|Identifie une ligne dans le **\<** ***DataInstance*** **>** bloc avec un **RowError**. L’élément error est placé dans le **\<diffgr:errors>** bloc.|  
|**Error**|Contient le texte du **RowError** pour un élément particulier dans le **\<diffgr:errors>** bloc.|  
  
 Le <xref:System.Data.DataSet> inclut annotations supplémentaires lors de la lecture ou de l'écriture de son contenu en tant que DiffGram. Le tableau suivant décrit ces annotations supplémentaires, qui sont définies dans l’espace de noms **urn : schemas-microsoft-com : xml-msdata**.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**RowOrder**|Conserve l'ordre des lignes des données d'origine et identifie l'index d'une ligne dans un <xref:System.Data.DataTable> donné.|  
|**Hidden**|Identifie une colonne comme ayant une propriété **ColumnMapping** définie sur **MappingType. Hidden**. L’attribut est écrit au format **msdata : Hidden** *[ColumnName]*= "*value*". Par exemple : `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Notez que les colonnes masquées ne sont écrites sous la forme d'un attribut DiffGram que si elles contiennent des données. Autrement, elles sont ignorées.|  
  
## <a name="sample-diffgram"></a>Exemple de DiffGram  

 Un exemple du format DiffGram vous est proposé ci-après. Cet exemple illustre le résultat d’une mise à jour effectuée sur une ligne d’une table avant validation des modifications. La ligne dont le CustomerID est « ALFKI » a été modifiée, mais pas mise à jour. Par conséquent, il existe une ligne **actuelle** avec un attribut **diffgr : ID** « Customers1 » dans le **\<** ***DataInstance*** **>** bloc, et une ligne **d’origine** avec un attribut **diffgr : ID** « Customers1 » dans le **\<diffgr:before>** bloc. La ligne avec un CustomerID de « ANATR » inclut un **RowError**, donc elle est annotée avec `diffgr:hasErrors="true"` et il y a un élément associé dans le **\<diffgr:errors>** bloc.  
  
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
