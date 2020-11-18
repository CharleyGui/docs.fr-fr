---
title: Fonctions et variables définies par l'utilisateur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
ms.openlocfilehash: d4936ec32d54a465803d493048cba2b70ed50db6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818503"
---
# <a name="user-defined-functions-and-variables"></a>Fonctions et variables définies par l'utilisateur
La classe <xref:System.Xml.XPath.XPathNavigator> fournit un ensemble de méthodes utilisées pour interagir avec les données <xref:System.Xml.XPath.XPathDocument>. Vous pouvez compléter les fonctions XPath standard en implémentant des fonctions et variables d’extension qui seront utilisées par les expressions de requête XPath. La méthode <xref:System.Xml.XPath.XPathExpression.SetContext%2A> peut accepter un contexte défini par l'utilisateur dérivé de <xref:System.Xml.Xsl.XsltContext>. Les fonctions définies par l'utilisateur sont résolues par le contexte personnalisé.  
  
 Les fonctions et variables d’extension peuvent s’avérer utiles en prévention des attaques par injection de code XML. Dans ces scénarios, l’entrée utilisateur est affectée aux variables personnalisées et traitées par les fonctions d’extension, et non pas comme entrée brute concaténée avec les instructions de traitement. Les fonctions et variables d'extension contiennent l'entrée utilisateur afin qu'elle agisse uniquement sur les données XML comme prévu par le concepteur.  
  
 Pour utiliser les extensions, implémentez une classe <xref:System.Xml.Xsl.XsltContext> personnalisée avec les interfaces <xref:System.Xml.Xsl.IXsltContextFunction> et <xref:System.Xml.Xsl.IXsltContextVariable> qui prennent en charge les fonctions et variables d’extension. <xref:System.Xml.XPath.XPathExpression> ajoute une entrée utilisateur avec sa <xref:System.Xml.Xsl.XsltArgumentList> au <xref:System.Xml.Xsl.XsltContext> personnalisé.  
  
 <xref:System.Xml.XPath.XPathExpression> représente une requête compilée utilisée par <xref:System.Xml.XPath.XPathNavigator> pour rechercher et traiter les nœuds identifiés par l'expression.  
  
 L'exemple suivant montre l'implémentation d'une classe de contexte personnalisé dérivée de <xref:System.Xml.Xsl.XsltContext> : Les commentaires figurant dans le code décrivent les membres de la classe et leur utilisation dans des fonctions personnalisées. Des implémentations de fonctions et de variables ainsi qu'un exemple d'application utilisant ces implémentations suivent ce segment de code.  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 Le code suivant implémente <xref:System.Xml.Xsl.IXsltContextFunction>. La classe qui implémente <xref:System.Xml.Xsl.IXsltContextFunction> résout et exécute les fonctions définies par l'utilisateur. Cet exemple utilise la fonction identifiée par la déclaration : `private int CountChar(string title, char charTocount)`.  
  
 Les commentaires de code décrivent les membres de la classe.  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 Le code suivant implémente <xref:System.Xml.Xsl.IXsltContextVariable>. Cette classe résout les références aux variables définies par l’utilisateur dans les expressions de requête XPath au moment de l’exécution. Une instance de cette classe est créée et retournée par la méthode <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> substituée de la classe <xref:System.Xml.Xsl.XsltContext> personnalisée.  
  
 Les commentaires de code décrivent les membres de la classe.  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 Avec les définitions de classe précédentes dans l'étendue, le code suivant utilise la fonction personnalisée pour compter les caractères dans les éléments du document `Tasks.xml`. Les commentaires figurant dans le code décrivent le code qui compile la fonction personnalisée et l'exécute sur le document `Tasks.xml`.  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 Cet exemple utilise les données XML suivantes :  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
