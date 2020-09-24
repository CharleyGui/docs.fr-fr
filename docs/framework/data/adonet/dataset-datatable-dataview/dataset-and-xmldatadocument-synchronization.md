---
title: Synchronisation DataSet et XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 2790f0a9edd5bfde96683e00725dd04555379adf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153298"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Synchronisation DataSet et XmlDataDocument

L'objet <xref:System.Data.DataSet> ADO.NET vous propose une représentation relationnelle des données. Pour un accès hiérarchique aux données, vous pouvez utiliser les classes XML disponibles dans le .NET Framework. Pour des raisons historiques, ces deux représentations des données ont jusqu'à présent été utilisées séparément. Toutefois, le .NET Framework active l’accès synchrone et en temps réel aux représentations relationnelles et hiérarchiques des données via l’objet **DataSet** et l' <xref:System.Xml.XmlDataDocument> objet, respectivement.  
  
 Lorsqu’un **DataSet** est synchronisé avec un **XmlDataDocument**, les deux objets utilisent un seul jeu de données. Cela signifie que si une modification est apportée au **jeu de données**, la modification est reflétée dans le **XmlDataDocument**, et vice versa. La relation entre le **jeu de données** et le **XmlDataDocument** crée une grande flexibilité en autorisant une seule application, à l’aide d’un seul jeu de données, pour accéder à l’ensemble de la suite de services générés à l’aide **du jeu de données (par** exemple, les contrôles Web Forms et Windows Forms et les concepteurs Visual Studio .net), ainsi qu’à la suite de services XML, notamment XSL (extensible STYLESHEET Language), XSLT (XSL Transformations) et XPath (XML Path Language). Vous n'avez pas à choisir l'ensemble de services que l'application devra utiliser, puisque les deux sont disponibles.  
  
 Vous pouvez synchroniser un **DataSet** avec un **XmlDataDocument**de plusieurs manières. Vous pouvez :  
  
- Remplir un **DataSet** avec un schéma (c’est-à-dire une structure relationnelle) et des données, puis le synchroniser avec un nouveau **XmlDataDocument**. Vous obtenez ainsi une vue hiérarchique des données relationnelles existantes. Par exemple :  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- Remplir un **DataSet** avec un schéma uniquement (par exemple, un **DataSet**fortement typé), le synchroniser avec un **XmlDataDocument**, puis charger le **XmlDataDocument** à partir d’un document XML. Vous obtenez ainsi une vue relationnelle des données hiérarchiques existantes. Les noms de table et de colonne dans votre schéma de **DataSet** doivent correspondre aux noms des éléments XML avec lesquels vous voulez qu’ils soient synchronisés. Cette mise en correspondance respecte la casse.  
  
     Notez que le schéma du **DataSet** doit uniquement correspondre aux éléments XML que vous souhaitez exposer dans votre vue relationnelle. De cette façon, vous pouvez disposer d'un document XML très volumineux et d'une toute petite « fenêtre » relationnelle sur ce document. Le **XmlDataDocument** conserve l’intégralité du document XML même si le **jeu de données** n’en expose qu’une petite partie. (Pour obtenir un exemple détaillé, consultez [synchronisation d’un DataSet avec un XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     L’exemple de code suivant montre les étapes à suivre pour créer un **DataSet** et remplir son schéma, puis le synchroniser avec un **XmlDataDocument**. Notez que le schéma du **DataSet** ne doit correspondre qu’aux éléments du **XmlDataDocument** que vous souhaitez exposer à l’aide du **DataSet**.  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     Vous ne pouvez pas charger un **XmlDataDocument** s’il est synchronisé avec un **DataSet** qui contient des données. Une exception sera levée.  
  
- Créez un **XmlDataDocument** et chargez-le à partir d’un document XML, puis accédez à la vue relationnelle des données à l’aide de la propriété **DataSet** du **XmlDataDocument**. Vous devez définir le schéma du **DataSet** avant de pouvoir afficher les données du **XmlDataDocument** à l’aide du **DataSet**. Là encore, les noms de table et de colonne dans votre schéma de **DataSet** doivent correspondre aux noms des éléments XML avec lesquels vous voulez qu’ils soient synchronisés. Cette mise en correspondance respecte la casse.  
  
     L’exemple de code suivant montre comment accéder à la vue relationnelle des données dans un **XmlDataDocument**.  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 Un autre avantage de la synchronisation d’un **XmlDataDocument** avec un **DataSet** est que la fidélité d’un document XML est préservée. Si le **jeu** de données est rempli à partir d’un document XML à l’aide de **ReadXml**, lorsque les données sont réécrites sous forme de document XML à l’aide de **WriteXml** , le document XML d’origine peut varier considérablement. Cela est dû au fait que le **DataSet** ne conserve pas la mise en forme, telle qu’un espace blanc ou des informations hiérarchiques, telles que l’ordre des éléments, à partir du document XML. Le **DataSet** ne contient pas non plus d’éléments du document XML qui ont été ignorés parce qu’ils ne correspondaient pas au schéma du **DataSet**. La synchronisation d’un **XmlDataDocument** avec un **DataSet** permet de conserver la mise en forme et la structure hiérarchique des éléments du document XML d’origine dans le **XmlDataDocument**, tandis que le **DataSet** contient uniquement des données et des informations de schéma appropriées pour le **DataSet**.  
  
 Lors de la synchronisation d’un **DataSet** avec un **XmlDataDocument**, les résultats peuvent différer selon que vos <xref:System.Data.DataRelation> objets sont ou non imbriqués. Pour plus d’informations, consultez [imbrication de DataRelations](nesting-datarelations.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Synchronisation d'un DataSet et d'un XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Illustre la synchronisation d’un **DataSet**fortement typé, avec un schéma minimal, avec un **XmlDataDocument**.  
  
 [Exécution d’une requête XPath sur un DataSet](performing-an-xpath-query-on-a-dataset.md)  
 Montre comment exécuter une requête XPath sur le contenu d’un **DataSet**.  
  
 [Application d'une transformation XSLT à un DataSet](applying-an-xslt-transform-to-a-dataset.md)  
 Illustre l’application d’une transformation XSLT au contenu d’un **DataSet**.  
  
## <a name="related-sections"></a>Sections connexes  

 [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)  
 Décrit comment le **DataSet** interagit avec XML comme source de données, y compris le chargement et la persistance du contenu d’un **DataSet** en tant que données XML.  
  
 [Imbrication de DataRelations](nesting-datarelations.md)  
 Explique l’importance des objets **DataRelation** imbriqués lorsqu’il s’agit de représenter le contenu d’un **DataSet** sous forme de données XML, et décrit comment créer ces relations.  
  
 [DataSets, DataTables et DataViews](index.md)  
 Décrit le **jeu** de données et comment l’utiliser pour gérer les données d’application et interagir avec les sources de données, notamment les bases de données relationnelles et XML.  
  
 <xref:System.Xml.XmlDataDocument>  
 Contient des informations de référence sur la classe **XmlDataDocument** .  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
