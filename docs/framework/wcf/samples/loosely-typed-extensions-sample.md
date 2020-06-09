---
title: Loosely-Typed Extensions, exemple
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 0a08ca19e5e6bff7223d45726617d2c2163ca3df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591863"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="80823-102">Loosely-Typed Extensions, exemple</span><span class="sxs-lookup"><span data-stu-id="80823-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="80823-103">Le modèle objet de syndication fournit une prise en charge complète pour l’utilisation des données d’extension : informations présentes dans la représentation XML d’un flux de syndication, mais qui ne sont pas exposées explicitement par les classes telles que <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="80823-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="80823-104">Cet exemple présente les techniques de base d’utilisation des données d’extension.</span><span class="sxs-lookup"><span data-stu-id="80823-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="80823-105">L'exemple utilise la classe <xref:System.ServiceModel.Syndication.SyndicationFeed>.</span><span class="sxs-lookup"><span data-stu-id="80823-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="80823-106">Toutefois, les modèles présentés dans cet exemple peuvent être utilisés avec toutes les classes de syndication qui prennent en charge les données d’extension :</span><span class="sxs-lookup"><span data-stu-id="80823-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="80823-107">Exemple XML</span><span class="sxs-lookup"><span data-stu-id="80823-107">Sample XML</span></span>  
 <span data-ttu-id="80823-108">Pour référence, le document XML suivant est utilisé dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="80823-108">For reference, the following XML document is used in this sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 <span data-ttu-id="80823-109">Ce document contient les données d’extension suivantes :</span><span class="sxs-lookup"><span data-stu-id="80823-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="80823-110">Attribut `myAttribute` de l'élément `<feed>`.</span><span class="sxs-lookup"><span data-stu-id="80823-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="80823-111">Élément `<simpleString>`.</span><span class="sxs-lookup"><span data-stu-id="80823-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="80823-112">Élément `<DataContractExtension>`.</span><span class="sxs-lookup"><span data-stu-id="80823-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="80823-113">Élément `<XmlSerializerExtension>`.</span><span class="sxs-lookup"><span data-stu-id="80823-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="80823-114">Élément `<xElementExtension>`.</span><span class="sxs-lookup"><span data-stu-id="80823-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="80823-115">Écriture des données d’extension</span><span class="sxs-lookup"><span data-stu-id="80823-115">Writing Extension Data</span></span>  
 <span data-ttu-id="80823-116">Les extensions d’attribut sont créées en ajoutant des entrées à la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>, comme l’illustre l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="80823-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="80823-117">Les extensions d’élément sont créées en ajoutant des entrées à la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="80823-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="80823-118">Ces extensions peuvent être des valeurs de base telles que des chaînes, des sérialisations XML d'objets .NET Framework ou des nœuds XML encodés manuellement.</span><span class="sxs-lookup"><span data-stu-id="80823-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="80823-119">L’exemple de code suivant crée un élément d’extension appelé `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="80823-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="80823-120">L’espace de noms XML de cet élément est l’espace de noms vide ("") et sa valeur est un nœud de texte qui contient la chaîne "Hello, World !".</span><span class="sxs-lookup"><span data-stu-id="80823-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="80823-121">L’une des méthodes permettant de créer des extensions d’élément complexes composées de nombreux éléments imbriqués consiste à utiliser les API .NET Framework pour la sérialisation (<xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Xml.Serialization.XmlSerializer> sont tous deux pris en charge), comme illustré dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="80823-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="80823-122">Dans cet exemple, `DataContractExtension` et `XmlSerializerExtension` sont des types personnalisés écrits pour être utilisés avec un sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="80823-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="80823-123">La classe <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> permet également de créer des extensions d'élément à partir d'une instance <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="80823-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="80823-124">Cela permet une intégration aisée avec les API de traitement XML telles que <xref:System.Xml.Linq.XElement>, comme l'illustre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="80823-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="80823-125">Lecture des données d’extension</span><span class="sxs-lookup"><span data-stu-id="80823-125">Reading Extension Data</span></span>  
 <span data-ttu-id="80823-126">Les valeurs des extensions d’attribut peuvent être obtenues en recherchant l’attribut dans la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> en fonction de son <xref:System.Xml.XmlQualifiedName>, comme l’illustre l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="80823-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="80823-127">Les extensions d’élément sont accessibles à l’aide de la méthode `ReadElementExtensions<T>`.</span><span class="sxs-lookup"><span data-stu-id="80823-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```csharp  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 <span data-ttu-id="80823-128">Il est également possible d'obtenir un `XmlReader` au niveau de chaque extension d'élément en utilisant la méthode <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>.</span><span class="sxs-lookup"><span data-stu-id="80823-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="80823-129">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="80823-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="80823-130">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80823-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="80823-131">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80823-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="80823-132">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="80823-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="80823-133">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="80823-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="80823-134">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="80823-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="80823-135">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="80823-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="80823-136">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="80823-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="80823-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80823-137">See also</span></span>

- [<span data-ttu-id="80823-138">Extensions fortement typées</span><span class="sxs-lookup"><span data-stu-id="80823-138">Strongly typed Extensions</span></span>](strongly-typed-extensions-sample.md)
- [<span data-ttu-id="80823-139">Syndication WCF</span><span class="sxs-lookup"><span data-stu-id="80823-139">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
