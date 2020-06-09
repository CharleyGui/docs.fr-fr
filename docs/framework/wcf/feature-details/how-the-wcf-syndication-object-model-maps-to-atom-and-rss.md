---
title: Comment le modèle objet Syndication WCF est mappé à Atom et RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: 67fbbb035a3a6683cefbf24e299f32579b674bbd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597252"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>Comment le modèle objet Syndication WCF est mappé à Atom et RSS
Lors du développement d’un service de syndication (WCF) Windows Communication Foundation, vous créez des flux et des éléments à l’aide des classes suivantes :  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed> peut être sérialisé dans n'importe quel format de syndication pour lequel un formateur est défini. WCF est fourni avec deux formateurs : <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> et <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .  
  
 Le modèle objet autour de <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem> est aligné plus étroitement avec la spécification Atom 1.0 que la spécification RSS 2.0. En effet, Atom 1.0 est une spécification plus substantielle qui définit des éléments qui sont ambigus ou omis de la spécification RSS 2.0. Pour cette raison, de nombreux éléments du modèle objet de syndication WCF n’ont pas de représentation directe dans la spécification RSS 2,0. Lors de la sérialisation <xref:System.ServiceModel.Syndication.SyndicationFeed> des <xref:System.ServiceModel.Syndication.SyndicationItem> objets et dans RSS 2,0, WCF vous permet de sérialiser des éléments de données spécifiques à Atom sous la forme d’éléments d’extension qualifiés par un espace de noms conformes à la spécification Atom. Vous pouvez contrôler cette opération avec un paramètre passé au constructeur <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.  
  
 Les exemples de code dans cette rubrique utilisent une des deux méthodes définies dans cette section pour effectuer la sérialisation à proprement dite.  
  
 `SerializeFeed` sérialise un flux de syndication.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem` sérialise un élément de syndication.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.SyndicationFeed> vers Atom 1.0 et RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationFeed> est sérialisé vers Atom 1.0.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<feed xml:lang="EN-US" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text">My Feed Title</title>  
  <subtitle type="text">My Feed Description</subtitle>  
  <id>FeedID</id>  
  <rights type="text">Copyright 2007</rights>  
  <updated>2007-08-29T13:57:17-07:00</updated>  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <logo>http://server/image.jpg</logo>  
  <generator>Sample Code</generator>  
  <link rel="alternate" href="http://myfeeduri/" />  
  <entry>  
    <id>ItemID</id>  
    <title type="text">Item Title</title>  
    <summary type="text">Item Summary</summary>  
    <published>2007-08-29T00:00:00-07:00</published>  
    <updated>2007-08-29T13:57:17-07:00</updated>  
    <author>  
      <name>Jesper Aaberg</name>  
      <uri>http://Jesper/Aaberg</uri>  
      <email>Jesper@Aaberg.com</email>  
    </author>  
    <contributor>  
      <name>Lene Aaling</name>  
      <uri>http://Lene/Aaling</uri>  
      <email>Lene@Aaling.com</email>  
    </contributor>  
    <link rel="alternate" href="http://myitemuri/" />  
    <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
    <content type="text">Item Content</content>  
    <rights type="text">Copyright 2007</rights>  
    <source>  
      <title type="text">My Feed Title</title>  
      <subtitle type="text">My Feed Description</subtitle>  
      <id>FeedID</id>  
      <rights type="text">Copyright 2007</rights>  
      <updated>2007-08-29T13:57:17-07:00</updated>  
      <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
      <logo>http://server/image.jpg</logo>  
      <generator>Sample Code</generator>  
      <link rel="alternate" href="http://myfeeduri/" />  
    </source>  
  </entry>  
</feed>  
```  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationFeed> est sérialisé vers RSS 2.0.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<rss xmlns:a10="http://www.w3.org/2005/Atom" version="2.0">  
  <channel>  
    <title>My Feed Title</title>  
    <link>http://myfeeduri/</link>  
    <description>My Feed Description</description>  
    <language>EN-US</language>  
    <copyright>Copyright 2007</copyright>  
    <lastBuildDate>Wed, 29 Aug 2007 13:57:17 -0700</lastBuildDate>  
    <category domain="categoryScheme">categoryName</category>  
    <generator>Sample Code</generator>  
    <image>  
      <url>http://server/image.jpg</url>  
      <title>My Feed Title</title>  
      <link>http://myfeeduri/</link>  
    </image>  
    <a10:id>FeedID</a10:id>  
    <item>  
      <guid isPermaLink="false">ItemID</guid>  
      <link>http://myitemuri/</link>  
      <author>Jesper@Aaberg.com</author>  
      <category domain="categoryScheme">categoryName</category>  
      <title>Item Title</title>  
      <description>Item Summary</description>  
      <source>My Feed Title</source>  
      <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
      <a10:updated>2007-08-29T13:57:17-07:00</a10:updated>  
      <a10:rights type="text">Copyright 2007</a10:rights>  
      <a10:content type="text">Item Content</a10:content>  
      <a10:contributor>  
        <a10:name>Lene Aaling</a10:name>  
        <a10:uri>http://Lene/Aaling</a10:uri>  
        <a10:email>Lene@Aaling.com</a10:email>  
      </a10:contributor>  
    </item>  
  </channel>  
</rss>  
```  
  
## <a name="syndicationitem"></a>SyndicationItem  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.SyndicationItem> vers Atom 1.0 et RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationItem> est sérialisé vers Atom 1.0.  
  
```xml  
<entry xmlns="http://www.w3.org/2005/Atom">  
  <id>ItemID</id>  
  <title type="text">Item Title</title>  
  <summary type="text">Item Summary</summary>  
  <published>2007-08-29T00:00:00-07:00</published>  
  <updated>2007-08-29T14:07:09-07:00</updated>  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
  <author>  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor>  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
  <link rel="alternate" href="http://myitemuri/" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <content type="text">Item Content</content>  
  <rights type="text">Copyright 2007</rights>  
  <source>  
    <title type="text">My Feed Title</title>  
    <subtitle type="text">My Feed Description</subtitle>  
    <link rel="alternate" href="http://myfeeduri/" />  
  </source>  
</entry>  
```  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationItem> est sérialisé vers RSS 2.0.  
  
```xml  
<item>  
  <guid isPermaLink="false">ItemID</guid>  
  <link>http://myitemuri/</link>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Jesper Aaberg</name>  
    <uri>http://Jesper/Aaberg</uri>  
    <email>Jesper@Aaberg.com</email>  
  </author>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <category domain="categoryScheme">categoryName</category>  
  <category domain="categoryScheme">categoryName</category>  
  <title>Item Title</title>  
  <description>Item Summary</description>  
  <source>My Feed Title</source>  
  <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
  <updated xmlns="http://www.w3.org/2005/Atom">2007-08-29T14:07:09-07:00</updated>  
  <rights type="text" xmlns="http://www.w3.org/2005/Atom">Copyright 2007</rights>  
  <content type="text" xmlns="http://www.w3.org/2005/Atom">Item Content</content>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
</item>  
```  
  
## <a name="syndicationperson"></a>SyndicationPerson  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.SyndicationPerson> vers Atom 1.0 et RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationPerson> est sérialisé vers Atom 1.0.  
  
```xml  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
<contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
```  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.SyndicationPerson> est sérialisée vers RSS 2.0 si une seule <xref:System.ServiceModel.Syndication.SyndicationPerson> existe dans les collections `Authors` ou `Contributors`, respectivement.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.SyndicationPerson> est sérialisée vers RSS 2.0 si plusieurs <xref:System.ServiceModel.Syndication.SyndicationPerson> existent dans les collections `Authors` ou `Contributors`, respectivement.  
  
```xml  
<a10:author>  
    <a10:name>Jesper Aaberg</a10:name>  
    <a10:uri>http://Contoso/Aaberg</a10:uri>  
    <a10:email>Jesper.Aaberg@contoso.com</a10:email>  
</a10:author>  
<a10:author>  
    <a10:name>Syed Abbas</a10:name>  
    <a10:uri>http://Contoso/Abbas</a10:uri>  
    <a10:email>Syed.Abbas@contoso.com</a10:email>  
</a10:author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
<a10:contributor>  
    <a10:name>Kim Abercrombie</a10:name>  
    <a10:uri>http://Contoso/Abercrombie</a10:uri>  
    <a10:email>Kim.Abercrombie@contoso.com</a10:email>  
</a10:contributor>  
```  
  
## <a name="syndicationlink"></a>SyndicationLink  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.SyndicationLink> vers Atom 1.0 et RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationLink> est sérialisé vers Atom 1.0.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationLink> est sérialisé vers RSS 2.0.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.SyndicationCategory> vers Atom 1.0 et RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationCategory> est sérialisé vers Atom 1.0.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Le code XML suivant montre comment <xref:System.ServiceModel.Syndication.SyndicationCategory> est sérialisé vers RSS 2.0.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> vers Atom 1.0 et RSS 2.0 lorsque <xref:System.ServiceModel.Syndication.TextSyndicationContent> est créée avec un contenu HTML.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> avec un contenu HTML est sérialisée vers Atom 1.0.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> avec un contenu HTML est sérialisée vers RSS 2.0.  
  
 `<description><html> some html </html></description>`  
  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> vers Atom 1.0 et RSS 2.0 lorsque <xref:System.ServiceModel.Syndication.TextSyndicationContent> est créée avec un contenu en texte brut.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> avec un contenu de texte brut est sérialisée vers Atom 1.0.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> avec un contenu de texte brut est sérialisée vers RSS 2.0.  
  
 `<description>Some Plain Text</description>`  
  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> vers Atom 1.0 et RSS 2.0 lorsque <xref:System.ServiceModel.Syndication.TextSyndicationContent> est créée avec un contenu XHTML.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> avec un contenu XHTML est sérialisée vers Atom 1.0.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.TextSyndicationContent> avec un contenu XHTML est sérialisée vers RSS 2.0.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.UrlSyndicationContent> vers Atom 1.0 et RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.UrlSyndicationContent> est sérialisée vers Atom 1.0.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.UrlSyndicationContent> avec un contenu XHTML est sérialisée vers RSS 2.0.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 L'exemple de code suivant montre comment sérialiser la classe <xref:System.ServiceModel.Syndication.XmlSyndicationContent> vers Atom 1.0 et RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.XmlSyndicationContent> est sérialisée vers Atom 1.0.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Le code XML suivant montre comment la classe <xref:System.ServiceModel.Syndication.XmlSyndicationContent> avec un contenu XHTML est sérialisée vers RSS 2.0.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la syndication WCF](wcf-syndication-overview.md)
- [Architecture de syndication](architecture-of-syndication.md)
- [Comment : créer un flux RSS de base](how-to-create-a-basic-rss-feed.md)
- [Comment : créer un flux Atom de base](how-to-create-a-basic-atom-feed.md)
- [Procédure : exposer un flux en tant que flux Atom et flux RSS](how-to-expose-a-feed-as-both-atom-and-rss.md)
