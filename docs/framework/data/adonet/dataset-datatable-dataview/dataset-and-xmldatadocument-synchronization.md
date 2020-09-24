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
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="91da5-102">Synchronisation DataSet et XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="91da5-102">DataSet and XmlDataDocument Synchronization</span></span>

<span data-ttu-id="91da5-103">L'objet <xref:System.Data.DataSet> ADO.NET vous propose une représentation relationnelle des données.</span><span class="sxs-lookup"><span data-stu-id="91da5-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="91da5-104">Pour un accès hiérarchique aux données, vous pouvez utiliser les classes XML disponibles dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91da5-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="91da5-105">Pour des raisons historiques, ces deux représentations des données ont jusqu'à présent été utilisées séparément.</span><span class="sxs-lookup"><span data-stu-id="91da5-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="91da5-106">Toutefois, le .NET Framework active l’accès synchrone et en temps réel aux représentations relationnelles et hiérarchiques des données via l’objet **DataSet** et l' <xref:System.Xml.XmlDataDocument> objet, respectivement.</span><span class="sxs-lookup"><span data-stu-id="91da5-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="91da5-107">Lorsqu’un **DataSet** est synchronisé avec un **XmlDataDocument**, les deux objets utilisent un seul jeu de données.</span><span class="sxs-lookup"><span data-stu-id="91da5-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="91da5-108">Cela signifie que si une modification est apportée au **jeu de données**, la modification est reflétée dans le **XmlDataDocument**, et vice versa.</span><span class="sxs-lookup"><span data-stu-id="91da5-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="91da5-109">La relation entre le **jeu de données** et le **XmlDataDocument** crée une grande flexibilité en autorisant une seule application, à l’aide d’un seul jeu de données, pour accéder à l’ensemble de la suite de services générés à l’aide **du jeu de données (par** exemple, les contrôles Web Forms et Windows Forms et les concepteurs Visual Studio .net), ainsi qu’à la suite de services XML, notamment XSL (extensible STYLESHEET Language), XSLT (XSL Transformations) et XPath (XML Path Language).</span><span class="sxs-lookup"><span data-stu-id="91da5-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="91da5-110">Vous n'avez pas à choisir l'ensemble de services que l'application devra utiliser, puisque les deux sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="91da5-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="91da5-111">Vous pouvez synchroniser un **DataSet** avec un **XmlDataDocument**de plusieurs manières.</span><span class="sxs-lookup"><span data-stu-id="91da5-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="91da5-112">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="91da5-112">You can:</span></span>  
  
- <span data-ttu-id="91da5-113">Remplir un **DataSet** avec un schéma (c’est-à-dire une structure relationnelle) et des données, puis le synchroniser avec un nouveau **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="91da5-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="91da5-114">Vous obtenez ainsi une vue hiérarchique des données relationnelles existantes.</span><span class="sxs-lookup"><span data-stu-id="91da5-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="91da5-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="91da5-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="91da5-116">Remplir un **DataSet** avec un schéma uniquement (par exemple, un **DataSet**fortement typé), le synchroniser avec un **XmlDataDocument**, puis charger le **XmlDataDocument** à partir d’un document XML.</span><span class="sxs-lookup"><span data-stu-id="91da5-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="91da5-117">Vous obtenez ainsi une vue relationnelle des données hiérarchiques existantes.</span><span class="sxs-lookup"><span data-stu-id="91da5-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="91da5-118">Les noms de table et de colonne dans votre schéma de **DataSet** doivent correspondre aux noms des éléments XML avec lesquels vous voulez qu’ils soient synchronisés.</span><span class="sxs-lookup"><span data-stu-id="91da5-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="91da5-119">Cette mise en correspondance respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="91da5-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="91da5-120">Notez que le schéma du **DataSet** doit uniquement correspondre aux éléments XML que vous souhaitez exposer dans votre vue relationnelle.</span><span class="sxs-lookup"><span data-stu-id="91da5-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="91da5-121">De cette façon, vous pouvez disposer d'un document XML très volumineux et d'une toute petite « fenêtre » relationnelle sur ce document.</span><span class="sxs-lookup"><span data-stu-id="91da5-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="91da5-122">Le **XmlDataDocument** conserve l’intégralité du document XML même si le **jeu de données** n’en expose qu’une petite partie.</span><span class="sxs-lookup"><span data-stu-id="91da5-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="91da5-123">(Pour obtenir un exemple détaillé, consultez [synchronisation d’un DataSet avec un XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="91da5-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="91da5-124">L’exemple de code suivant montre les étapes à suivre pour créer un **DataSet** et remplir son schéma, puis le synchroniser avec un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="91da5-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="91da5-125">Notez que le schéma du **DataSet** ne doit correspondre qu’aux éléments du **XmlDataDocument** que vous souhaitez exposer à l’aide du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="91da5-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="91da5-126">Vous ne pouvez pas charger un **XmlDataDocument** s’il est synchronisé avec un **DataSet** qui contient des données.</span><span class="sxs-lookup"><span data-stu-id="91da5-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="91da5-127">Une exception sera levée.</span><span class="sxs-lookup"><span data-stu-id="91da5-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="91da5-128">Créez un **XmlDataDocument** et chargez-le à partir d’un document XML, puis accédez à la vue relationnelle des données à l’aide de la propriété **DataSet** du **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="91da5-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="91da5-129">Vous devez définir le schéma du **DataSet** avant de pouvoir afficher les données du **XmlDataDocument** à l’aide du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="91da5-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="91da5-130">Là encore, les noms de table et de colonne dans votre schéma de **DataSet** doivent correspondre aux noms des éléments XML avec lesquels vous voulez qu’ils soient synchronisés.</span><span class="sxs-lookup"><span data-stu-id="91da5-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="91da5-131">Cette mise en correspondance respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="91da5-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="91da5-132">L’exemple de code suivant montre comment accéder à la vue relationnelle des données dans un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="91da5-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="91da5-133">Un autre avantage de la synchronisation d’un **XmlDataDocument** avec un **DataSet** est que la fidélité d’un document XML est préservée.</span><span class="sxs-lookup"><span data-stu-id="91da5-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="91da5-134">Si le **jeu** de données est rempli à partir d’un document XML à l’aide de **ReadXml**, lorsque les données sont réécrites sous forme de document XML à l’aide de **WriteXml** , le document XML d’origine peut varier considérablement.</span><span class="sxs-lookup"><span data-stu-id="91da5-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="91da5-135">Cela est dû au fait que le **DataSet** ne conserve pas la mise en forme, telle qu’un espace blanc ou des informations hiérarchiques, telles que l’ordre des éléments, à partir du document XML.</span><span class="sxs-lookup"><span data-stu-id="91da5-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="91da5-136">Le **DataSet** ne contient pas non plus d’éléments du document XML qui ont été ignorés parce qu’ils ne correspondaient pas au schéma du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="91da5-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="91da5-137">La synchronisation d’un **XmlDataDocument** avec un **DataSet** permet de conserver la mise en forme et la structure hiérarchique des éléments du document XML d’origine dans le **XmlDataDocument**, tandis que le **DataSet** contient uniquement des données et des informations de schéma appropriées pour le **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="91da5-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="91da5-138">Lors de la synchronisation d’un **DataSet** avec un **XmlDataDocument**, les résultats peuvent différer selon que vos <xref:System.Data.DataRelation> objets sont ou non imbriqués.</span><span class="sxs-lookup"><span data-stu-id="91da5-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="91da5-139">Pour plus d’informations, consultez [imbrication de DataRelations](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="91da5-139">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91da5-140">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="91da5-140">In This Section</span></span>  

 [<span data-ttu-id="91da5-141">Synchronisation d'un DataSet et d'un XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="91da5-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="91da5-142">Illustre la synchronisation d’un **DataSet**fortement typé, avec un schéma minimal, avec un **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="91da5-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="91da5-143">Exécution d’une requête XPath sur un DataSet</span><span class="sxs-lookup"><span data-stu-id="91da5-143">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="91da5-144">Montre comment exécuter une requête XPath sur le contenu d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="91da5-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="91da5-145">Application d'une transformation XSLT à un DataSet</span><span class="sxs-lookup"><span data-stu-id="91da5-145">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="91da5-146">Illustre l’application d’une transformation XSLT au contenu d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="91da5-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="91da5-147">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="91da5-147">Related Sections</span></span>  

 [<span data-ttu-id="91da5-148">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="91da5-148">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="91da5-149">Décrit comment le **DataSet** interagit avec XML comme source de données, y compris le chargement et la persistance du contenu d’un **DataSet** en tant que données XML.</span><span class="sxs-lookup"><span data-stu-id="91da5-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="91da5-150">Imbrication de DataRelations</span><span class="sxs-lookup"><span data-stu-id="91da5-150">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="91da5-151">Explique l’importance des objets **DataRelation** imbriqués lorsqu’il s’agit de représenter le contenu d’un **DataSet** sous forme de données XML, et décrit comment créer ces relations.</span><span class="sxs-lookup"><span data-stu-id="91da5-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="91da5-152">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="91da5-152">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="91da5-153">Décrit le **jeu** de données et comment l’utiliser pour gérer les données d’application et interagir avec les sources de données, notamment les bases de données relationnelles et XML.</span><span class="sxs-lookup"><span data-stu-id="91da5-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="91da5-154">Contient des informations de référence sur la classe **XmlDataDocument** .</span><span class="sxs-lookup"><span data-stu-id="91da5-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91da5-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91da5-155">See also</span></span>

- [<span data-ttu-id="91da5-156">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="91da5-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
