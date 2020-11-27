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
# <a name="strongly-typed-extensions-sample"></a>Exemple d’extensions fortement typées

L'exemple utilise la classe <xref:System.ServiceModel.Syndication.SyndicationFeed>. Toutefois, les modèles présentés dans cet exemple peuvent être utilisés avec toutes les classes Syndication qui prennent en charge les données d'extension.  
  
 Le modèle objet Syndication (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem> et les classes connexes) prend en charge l’accès peu typé aux données d’extension en utilisant les propriétés <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> et <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>. Cet exemple montre comment fournir un accès fortement typé aux données d’extension en implémentant des classes dérivées personnalisées de <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem> qui rendent disponibles certaines extensions spécifiques à l’application en tant que propriétés fortement typées.  
  
 En particulier, cet exemple indique comment implémenter un élément d’extension défini dans la RFC proposée, Atom Threading Extensions. Cet exemple est fourni à titre de démonstration uniquement et n'est pas conçu comme une implémentation complète de la spécification proposée.  
  
## <a name="sample-xml"></a>Exemple XML  

 L’exemple de code XML suivant illustre une entrée Atom 1.0 avec un élément d’extension `<in-reply-to>` supplémentaire.  
  
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
  
 L' `<in-reply-to>` élément spécifie trois attributs requis ( `ref` , `type` et `href` ), tout en autorisant également la présence d’attributs d’extension et d’éléments d’extension supplémentaires.  
  
## <a name="modeling-the-in-reply-to-element"></a>Modélisation de l'élément In-Reply-To  

 Dans cet exemple, l'élément `<in-reply-to>` est modélisé en tant que CLR qui implémente <xref:System.Xml.Serialization.IXmlSerializable>, ce qui active son utilisation avec <xref:System.Runtime.Serialization.DataContractSerializer>. Il implémente également des méthodes et des propriétés pour accéder aux données de l’élément, comme indiqué dans l’exemple de code suivant.  
  
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
  
 La classe `InReplyToElement` implémente des propriétés pour l’attribut requis (`HRef`, `MediaType` et `Source`) ainsi que des collections pour stocker <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> et <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 La classe `InReplyToElement` implémente l'interface <xref:System.Xml.Serialization.IXmlSerializable>, qui autorise le contrôle direct de la manière dont les instances d'objet sont lues et écrites en XML. La méthode `ReadXml` lit en premier les valeurs pour les propriétés `Ref`, `HRef`, `Source` et `MediaType` du <xref:System.Xml.XmlReader> qui lui est passé. Les attributs inconnus sont stockés dans la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>. Lorsque tous les attributs ont été lus, <xref:System.Xml.XmlReader.ReadStartElement> est appelé pour faire avancer le lecteur à l'élément suivant. Vu que l'élément modélisé par cette classe ne contient aucun enfant requis, les éléments enfants sont mis en mémoire tampon dans des instances de `XElement` et stockés dans la collection <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>, comme illustré dans le code suivant.  
  
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
  
 Dans `WriteXml`, la méthode `InReplyToElement` écrit d'abord les valeurs des propriétés `Ref`, `HRef`, `Source` et `MediaType` en tant qu'attributs XML (`WriteXml` n'est pas chargé d'écrire l'élément externe réel lui-même, car cela est fait par l'appelant de `WriteXml`). Elle écrit également le contenu de <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> et de <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> dans le writer, comme illustré dans le code suivant.  
  
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
  
## <a name="threadedfeed-and-threadeditem"></a>ThreadedFeed et ThreadedItem  

 Dans l'exemple, les `SyndicationItems` avec les extensions `InReplyTo` sont modélisés par la classe `ThreadedItem`. De même, la classe `ThreadedFeed` est un `SyndicationFeed` dont les éléments sont tous des instances de `ThreadedItem`.  
  
 La classe `ThreadedFeed` est héritée de `SyndicationFeed` et substitue la méthode `OnCreateItem` pour retourner un `ThreadedItem`. Elle implémente également une méthode pour accéder à la collection `Items` en tant que `ThreadedItems`, comme illustré dans le code suivant.  
  
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
  
 La classe `ThreadedItem` hérite de `SyndicationItem` et crée `InReplyToElement` comme propriété fortement typée. Cela fournit accès par programme commode aux données d’extension `InReplyTo`. Elle implémente également `TryParseElement` et `WriteElementExtensions` pour lire et écrire ses données d'extension, comme illustré dans le code suivant.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
