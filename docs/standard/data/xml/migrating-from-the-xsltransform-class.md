---
title: Migration depuis la classe XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 8383d8cb3e5819c46a0716c59323e492bb9add8e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937988"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migration depuis la classe XslTransform

L’architecture XSLT a été repensée dans la version 2005 de Visual Studio. La classe <xref:System.Xml.Xsl.XslTransform> a été remplacée par la classe <xref:System.Xml.Xsl.XslCompiledTransform>.

Les sections suivantes décrivent quelques-unes des principales différences entre les classes <xref:System.Xml.Xsl.XslCompiledTransform> et <xref:System.Xml.Xsl.XslTransform>.

## <a name="performance"></a>Performances

La classe <xref:System.Xml.Xsl.XslCompiledTransform> comporte de nombreuses améliorations des performances. Le nouveau processeur XSLT compile la feuille de style XSLT en un format intermédiaire commun, à la façon dont le CLR (common language runtime) le fait pour d'autres langages de programmation. Une fois compilée, la feuille de style peut être mise en cache et réutilisée.

La classe <xref:System.Xml.Xsl.XslCompiledTransform> inclut aussi d'autres optimisations qui la rendent beaucoup plus rapide que la classe <xref:System.Xml.Xsl.XslTransform>.

> [!NOTE]
> Bien que les performances globales de la classe <xref:System.Xml.Xsl.XslCompiledTransform> soient meilleures que celles de la classe <xref:System.Xml.Xsl.XslTransform>, la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslCompiledTransform> peut s'exécuter plus lentement que la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslTransform> la première fois qu'elle est appelée pour une transformation. C'est parce que le fichier XSLT doit être compilé avant d'être chargé. Pour plus d'informations, consultez le billet de blog suivant : [XslCompiledTransform plus lent que XslTransform ?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform).

## <a name="security"></a>Sécurité

Par défaut, la classe <xref:System.Xml.Xsl.XslCompiledTransform> désactive la prise en charge de la fonction XSLT `document()` et les scripts intégrés par défaut. Ces fonctionnalités peuvent être activées en créant un objet <xref:System.Xml.Xsl.XsltSettings> où les fonctionnalités sont activées et en le passant à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>. L'exemple suivant montre comment activer les scripts et effectuer une transformation XSLT.

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

Pour plus d’informations, consultez la page [Considérations relatives à la sécurité de XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).

## <a name="new-features"></a>Nouvelles fonctionnalités

### <a name="temporary-files"></a>Fichiers temporaires

Des fichiers temporaires sont parfois générés au cours du traitement XSLT. Si une feuille de style contient des blocs de script, ou si elle est compilée avec le paramètre de débogage défini sur true, des fichiers temporaires peuvent être créés dans le dossier %TEMP%. Certains fichiers temporaires ne sont pas supprimés à cause de problèmes de synchronisation. Par exemple, si les fichiers sont utilisés par le AppDomain en cours ou par le débogueur, le finaliseur de l'objet <xref:System.CodeDom.Compiler.TempFileCollection> ne pourra pas les supprimer.

La propriété <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> peut être utilisée pour un nettoyage supplémentaire afin de s'assurer que tous les fichiers temporaires sont supprimés du client.

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Prise en charge de l'élément xsl:output et de XmlWriter

La classe <xref:System.Xml.Xsl.XslTransform> a ignoré les paramètres `xsl:output` lorsque la sortie de transformation a été envoyée à un objet <xref:System.Xml.XmlWriter>. La classe <xref:System.Xml.Xsl.XslCompiledTransform> a une propriété <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> qui retourne un objet <xref:System.Xml.XmlWriterSettings> contenant les informations de sortie dérivées de l'élément `xsl:output` de la feuille de style. L'objet <xref:System.Xml.XmlWriterSettings> est utilisé pour créer un objet <xref:System.Xml.XmlWriter> avec les paramètres corrects qui peut être passé à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Le code C# suivant illustre ce comportement :

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a>Option de débogage

La classe <xref:System.Xml.Xsl.XslCompiledTransform> peut générer des informations de débogage, ce qui vous permet de déboguer la feuille de style à l’aide du Débogueur Microsoft Visual Studio. Consultez la rubrique <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> (éventuellement en anglais) pour plus d'informations.

## <a name="behavioral-differences"></a>Différences comportementales

### <a name="transforming-to-an-xmlreader"></a>Transformation vers un XmlReader

La classe <xref:System.Xml.Xsl.XslTransform> possède plusieurs surcharges Transform qui retournent des résultats de transformation sous forme d'objet <xref:System.Xml.XmlReader>. Ces surcharges peuvent être utilisées pour charger les résultats de transformation dans une représentation en mémoire (telle que <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>) sans subir la charge de sérialisation et de désérialisation de l'arborescence XML résultante. Le code C# suivant montre comment charger les résultats de transformation dans un objet <xref:System.Xml.XmlDocument>.

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

La classe <xref:System.Xml.Xsl.XslCompiledTransform> ne prend pas en charge la transformation vers un objet <xref:System.Xml.XmlReader>. Vous pouvez cependant effectuer une opération similaire en utilisant la méthode <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> pour charger directement l’arborescence XML résultante à partir d’un <xref:System.Xml.XmlWriter>. Le code C# suivant montre comment exécuter la même tâche à l’aide de <xref:System.Xml.Xsl.XslCompiledTransform>.

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a>Comportement discrétionnaire

La recommandation du W3C sur XSLT (XSL Transformations) Version 1.0 comprend des zones dans lesquelles le fournisseur d'implémentation peut décider de la manière de gérer une situation. Ces zones sont considérées comme discrétionnaires en termes de comportement. Il existe plusieurs domaines où le <xref:System.Xml.Xsl.XslCompiledTransform> se comporte différemment de la classe <xref:System.Xml.Xsl.XslTransform>. Pour plus d’informations, consultez la page [Erreurs XSLT récupérables](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).

### <a name="extension-objects-and-script-functions"></a>Objets d’extension et fonctions de script

<xref:System.Xml.Xsl.XslCompiledTransform> introduit deux nouvelles restrictions sur l'utilisation des fonctions de script :

- Seules les méthodes publiques peuvent être appelées à partir des expressions XPath.

- Il est possible de différencier les surcharges en fonction du nombre d’arguments. Si plusieurs surcharges ont le même nombre d'arguments, une exception est levée.

Dans <xref:System.Xml.Xsl.XslCompiledTransform>, une liaison (recherche de nom de méthode) vers des fonctions de script se produit au moment de la compilation, et les feuilles de style qui fonctionnaient avec XslTransform risquent de déclencher une exception lorsqu’elles sont chargées avec <xref:System.Xml.Xsl.XslCompiledTransform>.

<xref:System.Xml.Xsl.XslCompiledTransform> accepte la présence d'éléments enfants `msxsl:using` et `msxsl:assembly` dans l'élément `msxsl:script`. Les éléments `msxsl:using` et `msxsl:assembly` sont utilisés pour déclarer des espaces de noms et des assemblys supplémentaires pour une utilisation dans le bloc de script. Consultez la page [Blocs de script utilisant msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) pour plus d’informations.

<xref:System.Xml.Xsl.XslCompiledTransform> interdit les objets d'extension qui ont plusieurs surcharges avec le même nombre d'arguments.

### <a name="msxml-functions"></a>Fonctions MSXML

La prise en charge de fonctions MSXML supplémentaires a été ajoutée à la classe <xref:System.Xml.Xsl.XslCompiledTransform>. La liste suivante décrit les fonctionnalités nouvelles ou améliorées :

- msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> avait besoin que l'argument de la fonction [node-set Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) soit un fragment de l'arborescence de résultats. La classe <xref:System.Xml.Xsl.XslCompiledTransform> n’impose pas cette exigence.

- msxsl:version : cette fonction est prise en charge dans <xref:System.Xml.Xsl.XslCompiledTransform>.

- Fonctions d’extension XPath : les fonctions [ms:string-compare Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)) et [ms:format-time Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) sont maintenant prises en charge.

- Fonctions d’extension Xpath liées au schéma : ces fonctions ne sont pas prises en charge en natif par <xref:System.Xml.Xsl.XslCompiledTransform>. Toutefois, elles peuvent être implémentées en tant que fonctions d’extension.

## <a name="see-also"></a>Voir aussi

- [Transformations XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
