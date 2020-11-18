---
title: Résolution de feuilles de style XSLT externes et de documents
ms.date: 03/30/2017
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
ms.openlocfilehash: 370d1df296666e5b5c162db34bd7fb35ae8a2e0e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823587"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Résolution de feuilles de style XSLT externes et de documents
Lors d'une transformation, il peut s'avérer nécessaire de résoudre des ressources externes à plusieurs moments.  
  
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 Lors d'une transformation, il peut s'avérer nécessaire de résoudre des ressources externes à plusieurs moments :  
  
- pendant la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> pour localiser une feuille de style externe ;  
  
- pendant la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> pour résoudre tout élément `<xsl:include>` ou `<xsl:import>` trouvé dans la feuille de style ;  
  
- pendant la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour résoudre toute fonction `document()`.  
  
## <a name="using-the-xmlresolver-class"></a>Utilisation de la classe XmlResolver  
 Si l'authentification est nécessaire pour accéder à une ressource réseau, utilisez les méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> qui ont un paramètre <xref:System.Xml.XmlResolver> à passer à l'objet <xref:System.Xml.XmlResolver> qui possède le jeu de propriétés d'informations d'identification nécessaire.  
  
 Si vous souhaitez utiliser un objet <xref:System.Xml.XmlResolver> personnalisé ou si vous devez spécifier des informations d’identification différentes, le tableau suivant répertorie la tâche requise en fonction du moment où la ressource externe doit être résolue.  
  
|Processus devant être résolu|Tâche requise|  
|--------------------------------------|-------------------|  
|Pendant la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> pour localiser la feuille de style.|Spécifiez la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> surchargée qui prend comme paramètre un objet <xref:System.Xml.XmlResolver> si la feuille de style est sur une ressource qui nécessite des informations d'identification.|  
|Pendant la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> pour résoudre `<xsl:include>` ou `<xsl:import>`.|Spécifiez la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> surchargée qui prend comme paramètre <xref:System.Xml.XmlResolver>. L'objet <xref:System.Xml.XmlResolver> est utilisé pour charger les feuilles de style référencées par les instructions `import` ou `include`. Si vous passez `null`, les ressources externes ne sont pas résolues.|  
|Lors d'une transformation pour résoudre toute fonction `document()`.|Spécifiez l’objet <xref:System.Xml.XmlResolver> durant la transformation en utilisant la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> qui prend un argument <xref:System.Xml.XmlResolver>.|  
  
 La fonction `document()` extrait d'autres ressources XML d'une feuille de style, en plus des données XML initiales fournies par le flux d'entrée. Comme cette fonction permet l'inclusion de données XML qui peuvent se localiser ailleurs, un objet <xref:System.Xml.XmlResolver> avec une valeur `null` fournie à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> empêche la fonction `document()` de s'exécuter. Si vous voulez utiliser la fonction `document()`, utilisez la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> qui prend un <xref:System.Xml.XmlResolver> comme paramètre, en plus d'avoir le jeu d'autorisations approprié.  
  
 Pour plus d'informations sur la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> et son utilisation de l'objet <xref:System.Xml.XmlResolver>, consultez <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Lorsque la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est appelée, les autorisations sont calculées par rapport aux preuves fournies au moment du chargement, et ce jeu d'autorisations est attribué à l'ensemble du processus de transformation. Si la fonction `document()` tente d'initier une action qui nécessite des autorisations qui ne se trouvent pas dans le jeu, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi

- [Transformations XSLT avec la classe XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Sorties à partir de XslTransform](outputs-from-an-xsltransform.md)
- [Transformations XSLT sur différents magasins](xslt-transformations-over-different-stores.md)
- [XsltArgumentList pour les paramètres de feuille de style et les objets d'extension](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Écriture de scripts de feuille de style XSLT à l’aide de \<msxsl:script>](xslt-stylesheet-scripting-using-msxsl-script.md)
- [Prise en charge de la fonction msxsl:node-set()](support-for-the-msxsl-node-set-function.md)
- [XPathNavigator dans les transformations](xpathnavigator-in-transformations.md)
- [XPathNodeIterator dans les transformations](xpathnodeiterator-in-transformations.md)
- [Entrée XPathDocument dans XslTransform](xpathdocument-input-to-xsltransform.md)
- [Entrée XmlDataDocument dans XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Entrée XmlDocument dans XslTransform](xmldocument-input-to-xsltransform.md)
