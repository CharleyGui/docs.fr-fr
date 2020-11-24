---
title: XSLT et la sécurité
ms.date: 03/30/2017
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: a8d077cf35da56795cc0b0c22e9bab26ce99f3a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685199"
---
# <a name="xslt-security-considerations"></a>XSLT et la sécurité

Le langage XSLT possède une panoplie de fonctionnalités offrant puissance et flexibilité. Il comprend de nombreuses fonctionnalités qui, tout en étant utiles, pourraient aussi être exploitées par des sources extérieures. Pour utiliser XSLT en toute sécurité, vous devez comprendre les types de risques pour la sécurité que pose l'utilisation de XSLT et les stratégies de base que vous pouvez employer pour minimiser ces risques.  
  
## <a name="xslt-extensions"></a>Extensions XSLT  

 Deux extensions XSLT populaires sont les scripts de feuille de style et les objets d'extension. Ces extensions permettent au processeur XSLT d'exécuter du code.  
  
- Les objets d'extension ajoutent des capacités de programmation aux transformations XSL.  
  
- Des scripts peuvent être intégrés dans la feuille de style à l'aide de l'élément d'extension `msxsl:script`.  
  
### <a name="extension-objects"></a>Objets d’extension  

 Les objets d’extension sont ajoutés avec la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Le jeu d’autorisations FullTrust est requis pour la prise en charge des objets d’extension. Cela garantit qu’il n’y a pas d’élévation d’autorisations lors de l’exécution du code de l’objet d’extension. Une tentative d'appel de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> sans autorisation FullTrust produit une exception de sécurité.  
  
### <a name="style-sheet-scripts"></a>Scripts de feuille de style  

 Des scripts peuvent être intégrés dans une feuille de style à l’aide de l’élément d’extension `msxsl:script`. La prise en charge des scripts est une fonction facultative de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Elle est désactivée par défaut. Les scripts peuvent être activés en définissant la propriété <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> sur `true` et en transmettant l'objet <xref:System.Xml.Xsl.XsltSettings> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
#### <a name="guidelines"></a>Consignes  

 N'activez les scripts que lorsque la source de la feuille de style est fiable. Si vous ne pouvez pas vérifier la source de la feuille de style ou si celle-ci ne provient pas d'une source fiable, transmettez l'argument `null` dans les réglages XSLT.  
  
## <a name="external-resources"></a>Ressources externes  

 Le langage XSLT possède des fonctions telles que `xsl:import`, `xsl:include` ou `document()` où le processeur doit résoudre des références URI. La classe <xref:System.Xml.XmlResolver> permet de résoudre des ressources externes. La résolution de ressources externes peut être requise dans les deux cas suivants :  
  
- Lors de la compilation d'une feuille de style, l'objet <xref:System.Xml.XmlResolver> est utilisé pour résoudre `xsl:import` et `xsl:include`.  
  
- Lorsque la transformation est effectuée, l'objet <xref:System.Xml.XmlResolver> est utilisé pour résoudre la fonction `document()`.  
  
    > [!NOTE]
    > La fonction `document()` est désactivée par défaut dans la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Cette fonctionnalité peut être activée en définissant la propriété <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> sur `true` et en transmettant l’objet <xref:System.Xml.Xsl.XsltSettings> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
 Les méthodes <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> et <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> comprennent des surcharges qui prennent un objet <xref:System.Xml.XmlResolver> comme l’un de leurs arguments. Si aucun <xref:System.Xml.XmlResolver> n'est spécifié, un <xref:System.Xml.XmlUrlResolver> par défaut sans informations d'identification est utilisé.  
  
#### <a name="guidelines"></a>Consignes  

 N'activez la fonction `document()` que lorsque la source de la feuille de style est fiable.  
  
 La liste suivante décrit les cas dans lesquels vous pouvez préférer spécifier un objet <xref:System.Xml.XmlResolver> :  
  
- Si le traitement XSLT doit accéder à une ressource réseau qui nécessite une authentification, vous pouvez utiliser un objet <xref:System.Xml.XmlResolver> avec les informations d'identification nécessaires.  
  
- Si vous souhaitez limiter les ressources auxquelles le traitement XSLT peut accéder, vous pouvez utiliser un objet <xref:System.Xml.XmlSecureResolver> avec toutes les autorisations correctes. La classe <xref:System.Xml.XmlSecureResolver> doit être utilisée si vous devez ouvrir une ressource non contrôlée ou non fiable.  
  
- Pour personnaliser le comportement, vous pouvez implémenter votre propre classe <xref:System.Xml.XmlResolver> et l'utiliser pour résoudre les ressources.  
  
- Pour vous assurer qu’aucune ressource externe n’est accessible, vous pouvez spécifier `null` pour l’argument <xref:System.Xml.XmlResolver>.  
  
## <a name="see-also"></a>Voir aussi

- [Transformations XSLT](xslt-transformations.md)
- [Résolution de ressources externes lors du traitement XSLT](resolving-external-resources-during-xslt-processing.md)
- [Sécurité d’accès du code](../../../framework/misc/code-access-security.md)
