---
title: Objets d'extension XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25c9c1c81db0bb6775aa9226318d7ec726a93e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924940"
---
# <a name="xslt-extension-objects"></a>Objets d'extension XSLT
Les objets d’extension permettent d’étendre les fonctionnalités des feuilles de style. Ils sont gérés par la classe <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 L’utilisation d’un objet d’extension plutôt que d’un script intégré présente les avantages suivants :  
  
- Offre une meilleure encapsulation et réutilisation des classes.  
  
- Permet aux feuilles de styles d'être plus petites et plus faciles à gérer.  
  
 Des objets d’extension XSLT sont ajoutés à l’objet <xref:System.Xml.Xsl.XsltArgumentList> à l’aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Un nom qualifié et un URI d'espace de noms sont associés à l'objet d'extension à ce stade.  
  
> [!NOTE]
> Le jeu d'autorisations FullTrust est requis pour appeler la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Pour plus d’informations, consultez les pages [Sécurité d’accès du code](../../../../docs/framework/misc/code-access-security.md) et [Jeux d’autorisations nommés](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Les types de données retournés par les objets d’extension correspondent à l’un des quatre types de données de base XPath : `number`, `string`, `Boolean` et `node set`.  
  
 Les méthodes définies avec le mot clé `params`, qui permet de transmettre un nombre non spécifié de paramètres, ne sont actuellement pas prises en charge par la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Les feuilles de style XSLT qui utilisent une méthode définie avec le mot clé `params` ne fonctionnent pas correctement. Pour plus d’informations, consultez la page [params](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Pour utiliser un objet d’extension XSLT  
  
1. Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez l'objet d'extension à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Appelez l’objet d’extension à partir de la feuille de style.  
  
3. Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Transformations XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Considérations sur la sécurité de XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)
