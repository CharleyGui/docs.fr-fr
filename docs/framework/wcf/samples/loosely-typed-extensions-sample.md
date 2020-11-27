---
title: Loosely-Typed Extensions, exemple
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 94e01970502223febd3ff03e30be7b17d9019d93
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264884"
---
# <a name="loosely-typed-extensions-sample"></a>Loosely-Typed Extensions, exemple

Le modèle objet de syndication fournit une prise en charge complète pour l’utilisation des données d’extension : informations présentes dans la représentation XML d’un flux de syndication, mais qui ne sont pas exposées explicitement par les classes telles que <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem>. Cet exemple présente les techniques de base d’utilisation des données d’extension.  
  
 L'exemple utilise la classe <xref:System.ServiceModel.Syndication.SyndicationFeed>. Toutefois, les modèles présentés dans cet exemple peuvent être utilisés avec toutes les classes de syndication qui prennent en charge les données d’extension :  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Exemple XML  

 Pour référence, le document XML suivant est utilisé dans cet exemple.  
  
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
  
 Ce document contient les données d’extension suivantes :  
  
- Attribut `myAttribute` de l'élément `<feed>`.  
  
- Élément `<simpleString>`.  
  
- Élément `<DataContractExtension>`.  
  
- Élément `<XmlSerializerExtension>`.  
  
- Élément `<xElementExtension>`.  
  
## <a name="writing-extension-data"></a>Écriture des données d’extension  

 Les extensions d’attribut sont créées en ajoutant des entrées à la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>, comme l’illustre l’exemple de code suivant.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Les extensions d’élément sont créées en ajoutant des entrées à la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>. Ces extensions peuvent être des valeurs de base telles que des chaînes, des sérialisations XML d'objets .NET Framework ou des nœuds XML encodés manuellement.  
  
 L’exemple de code suivant crée un élément d’extension appelé `simpleString`.  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 L’espace de noms XML de cet élément est l’espace de noms vide ("") et sa valeur est un nœud de texte qui contient la chaîne "Hello, World !".  
  
 L’une des méthodes permettant de créer des extensions d’élément complexes composées de nombreux éléments imbriqués consiste à utiliser les API .NET Framework pour la sérialisation (<xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Xml.Serialization.XmlSerializer> sont tous deux pris en charge), comme illustré dans les exemples suivants.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Dans cet exemple, `DataContractExtension` et `XmlSerializerExtension` sont des types personnalisés écrits pour être utilisés avec un sérialiseur.  
  
 La classe <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> permet également de créer des extensions d'élément à partir d'une instance <xref:System.Xml.XmlReader>. Cela permet une intégration aisée avec les API de traitement XML telles que <xref:System.Xml.Linq.XElement>, comme l'illustre l'exemple de code suivant.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Lecture des données d’extension  

 Les valeurs des extensions d’attribut peuvent être obtenues en recherchant l’attribut dans la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> en fonction de son <xref:System.Xml.XmlQualifiedName>, comme l’illustre l’exemple de code suivant.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Les extensions d’élément sont accessibles à l’aide de la méthode `ReadElementExtensions<T>`.  
  
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
  
 Il est également possible d'obtenir un `XmlReader` au niveau de chaque extension d'élément en utilisant la méthode <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Voir aussi

- [Extensions fortement typées](strongly-typed-extensions-sample.md)
- [Syndication WCF](../feature-details/wcf-syndication.md)
