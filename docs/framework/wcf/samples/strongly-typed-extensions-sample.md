---
title: Exemple d’extensions fortement typées
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: e5b74188d4c9c333858c60ff95a2a90b0e2e9418
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275929"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="e75a9-102">Exemple d’extensions fortement typées</span><span class="sxs-lookup"><span data-stu-id="e75a9-102">Strongly typed extensions sample</span></span>

<span data-ttu-id="e75a9-103">L'exemple utilise la classe <xref:System.ServiceModel.Syndication.SyndicationFeed>.</span><span class="sxs-lookup"><span data-stu-id="e75a9-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="e75a9-104">Toutefois, les modèles présentés dans cet exemple peuvent être utilisés avec toutes les classes Syndication qui prennent en charge les données d'extension.</span><span class="sxs-lookup"><span data-stu-id="e75a9-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="e75a9-105">Le modèle objet Syndication (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem> et les classes connexes) prend en charge l’accès peu typé aux données d’extension en utilisant les propriétés <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> et <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="e75a9-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="e75a9-106">Cet exemple montre comment fournir un accès fortement typé aux données d’extension en implémentant des classes dérivées personnalisées de <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem> qui rendent disponibles certaines extensions spécifiques à l’application en tant que propriétés fortement typées.</span><span class="sxs-lookup"><span data-stu-id="e75a9-106">This sample shows how to provide strongly typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly typed properties.</span></span>  
  
 <span data-ttu-id="e75a9-107">En particulier, cet exemple indique comment implémenter un élément d’extension défini dans la RFC proposée, Atom Threading Extensions.</span><span class="sxs-lookup"><span data-stu-id="e75a9-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="e75a9-108">Cet exemple est fourni à titre de démonstration uniquement et n'est pas conçu comme une implémentation complète de la spécification proposée.</span><span class="sxs-lookup"><span data-stu-id="e75a9-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="e75a9-109">Exemple XML</span><span class="sxs-lookup"><span data-stu-id="e75a9-109">Sample XML</span></span>  

 <span data-ttu-id="e75a9-110">L’exemple de code XML suivant illustre une entrée Atom 1.0 avec un élément d’extension `<in-reply-to>` supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="e75a9-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"
                 p3:href="http://www.example.org/entries/1"
                 p3:type="application/xhtml+xml"
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="e75a9-111">L' `<in-reply-to>` élément spécifie trois attributs requis ( `ref` , `type` et `href` ), tout en autorisant également la présence d’attributs d’extension et d’éléments d’extension supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e75a9-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="e75a9-112">Modélisation de l'élément In-Reply-To</span><span class="sxs-lookup"><span data-stu-id="e75a9-112">Modeling the In-Reply-To element</span></span>  

 <span data-ttu-id="e75a9-113">Dans cet exemple, l'élément `<in-reply-to>` est modélisé en tant que CLR qui implémente <xref:System.Xml.Serialization.IXmlSerializable>, ce qui active son utilisation avec <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e75a9-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="e75a9-114">Il implémente également des méthodes et des propriétés pour accéder aux données de l’élément, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="e75a9-114">It also implements some methods and properties for accessing the element's data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="e75a9-115">La classe `InReplyToElement` implémente des propriétés pour l’attribut requis (`HRef`, `MediaType` et `Source`) ainsi que des collections pour stocker <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> et <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="e75a9-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="e75a9-116">La classe `InReplyToElement` implémente l'interface <xref:System.Xml.Serialization.IXmlSerializable>, qui autorise le contrôle direct de la manière dont les instances d'objet sont lues et écrites en XML.</span><span class="sxs-lookup"><span data-stu-id="e75a9-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="e75a9-117">La méthode `ReadXml` lit en premier les valeurs pour les propriétés `Ref`, `HRef`, `Source` et `MediaType` du <xref:System.Xml.XmlReader> qui lui est passé.</span><span class="sxs-lookup"><span data-stu-id="e75a9-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="e75a9-118">Les attributs inconnus sont stockés dans la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="e75a9-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="e75a9-119">Lorsque tous les attributs ont été lus, <xref:System.Xml.XmlReader.ReadStartElement> est appelé pour faire avancer le lecteur à l'élément suivant.</span><span class="sxs-lookup"><span data-stu-id="e75a9-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="e75a9-120">Vu que l'élément modélisé par cette classe ne contient aucun enfant requis, les éléments enfants sont mis en mémoire tampon dans des instances de `XElement` et stockés dans la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e75a9-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new
                                 XmlQualifiedName(reader.LocalName,
                                 reader.NamespaceURI),
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="e75a9-121">Dans `WriteXml`, la méthode `InReplyToElement` écrit d'abord les valeurs des propriétés `Ref`, `HRef`, `Source` et `MediaType` en tant qu'attributs XML (`WriteXml` n'est pas chargé d'écrire l'élément externe réel lui-même, car cela est fait par l'appelant de `WriteXml`).</span><span class="sxs-lookup"><span data-stu-id="e75a9-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="e75a9-122">Elle écrit également le contenu de <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> et de <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> dans le writer, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e75a9-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="e75a9-123">ThreadedFeed et ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="e75a9-123">ThreadedFeed and ThreadedItem</span></span>  

 <span data-ttu-id="e75a9-124">Dans l'exemple, les `SyndicationItems` avec les extensions `InReplyTo` sont modélisés par la classe `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="e75a9-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="e75a9-125">De même, la classe `ThreadedFeed` est un `SyndicationFeed` dont les éléments sont tous des instances de `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="e75a9-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="e75a9-126">La classe `ThreadedFeed` est héritée de `SyndicationFeed` et substitue la méthode `OnCreateItem` pour retourner un `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="e75a9-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="e75a9-127">Elle implémente également une méthode pour accéder à la collection `Items` en tant que `ThreadedItems`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e75a9-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="e75a9-128">La classe `ThreadedItem` hérite de `SyndicationItem` et crée `InReplyToElement` comme propriété fortement typée.</span><span class="sxs-lookup"><span data-stu-id="e75a9-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly typed property.</span></span> <span data-ttu-id="e75a9-129">Cela fournit accès par programme commode aux données d’extension `InReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="e75a9-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="e75a9-130">Elle implémente également `TryParseElement` et `WriteElementExtensions` pour lire et écrire ses données d'extension, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="e75a9-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,
                                                 string version)  
    {  
        if (this.InReplyTo != null &&
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e75a9-131">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="e75a9-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e75a9-132">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e75a9-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e75a9-133">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e75a9-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e75a9-134">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e75a9-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e75a9-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e75a9-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e75a9-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e75a9-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e75a9-137">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e75a9-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e75a9-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e75a9-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
