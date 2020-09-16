---
title: Gestion d'espaces de noms dans un document XML
description: Découvrez comment gérer les espaces de noms dans un document XML. Les espaces de noms XML associent les noms d'éléments et d'attributs dans un document XML à des URI prédéfinis et personnalisés.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 500c477eaa98b2858573e1012c62db4bc6c68137
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548089"
---
# <a name="managing-namespaces-in-an-xml-document"></a>Gestion d'espaces de noms dans un document XML
Les espaces de noms XML associent les noms d'éléments et d'attributs dans un document XML à des URI prédéfinis et personnalisés. Pour créer ces associations, définissez des préfixes pour des URI d'espace de noms et utilisez ces préfixes pour qualifier des noms d'élément et d'attribut dans des données XML. Les espaces de noms empêchent les conflits entre les noms d'élément et d'attribut et permettent aux éléments et attributs de même nom d'être gérés différemment et validés différemment.  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a>Déclaration d'espaces de noms  
 Pour déclarer un espace de noms sur un élément, utilisez l'attribut `xmlns:` :  
  
 `xmlns:<name>=<"uri">`  
  
 où `<name>` est le préfixe de l'espace de noms et `<"uri">` fait référence à l'URI qui identifie l'espace de noms. Une fois que vous avez déclaré le préfixe, vous pouvez l'utiliser pour qualifier des éléments et des attributs dans un document XML et les associer à un URI d'espace de noms. Le préfixe de l'espace de noms étant utilisé dans la totalité d'un document, il doit être court de préférence.  
  
 Cet exemple définit deux éléments `BOOK`. Le premier élément est qualifié par le préfixe `mybook`, tandis que le deuxième élément est qualifié par le préfixe `bb`. Chaque préfixe est associé à un URI d'espace de noms différent :  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 Pour indiquer qu'un élément fait partie d'un espace de noms particulier, ajoutez-lui le préfixe de l'espace de noms. Par exemple, si un élément `Author` appartient à l'espace de noms `mybook`, il est déclaré comme suit : `<mybook:Author>`.  
  
<a name="scope"></a>
## <a name="declaration-scope"></a>Portée de la déclaration  
 Un espace de noms est effectif à partir de son point de déclaration jusqu'à la fin de l'élément dans lequel il a été déclaré. Dans cet exemple, l'espace de noms défini dans l'élément `BOOK` ne s'applique pas aux éléments situés en dehors de l'élément `BOOK`, tels que l'élément `Publisher` :  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 Un espace de noms doit être déclaré avant de pouvoir être utilisé, mais cela ne signifie pas qu'il doit apparaître tout en haut du document XML.  
  
 Lorsque vous utilisez plusieurs espaces de noms dans un document XML, vous pouvez définir un espace de noms comme l'espace de noms par défaut afin de créer un document plus clair. L'espace de noms par défaut est déclaré dans l'élément racine et s'applique à tous les éléments non qualifiés dans le document. Les espaces de noms par défaut s'appliquent uniquement aux éléments, pas aux attributs.  
  
 Pour utiliser l'espace de noms par défaut, omettez le préfixe et le signe deux-points de la déclaration sur l'élément :  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a>Gestion des espaces de noms  
 La classe <xref:System.Xml.XmlNamespaceManager> stocke une collection d’URI d’espace de noms et leurs préfixes, et vous permet de rechercher, d’ajouter et de supprimer des espaces de noms dans cette collection. Dans certains contextes, cette classe est indispensable pour améliorer les performances de traitement XML. Par exemple, la classe <xref:System.Xml.Xsl.XsltContext> utilise <xref:System.Xml.XmlNamespaceManager> pour la prise en charge de XPath.  
  
 Le gestionnaire d'espaces de noms n'effectue aucune validation sur les espaces de noms, mais part du principe que les préfixes et les espaces de noms ont déjà été vérifiés et qu’ils sont conformes à la spécification du [W3C sur les espaces de noms](https://www.w3.org/TR/REC-xml-names/).  
  
> [!NOTE]
> LINQ to XML en [C#](../../linq/linq-xml-overview.md) et [Visual Basic](../../linq/linq-xml-overview.md) n’utilisent pas <xref:System.Xml.XmlNamespaceManager> pour gérer les espaces de noms. Pour des informations sur la gestion des espaces de noms en cas d’utilisation de LINQ to XML, consultez [Utilisation des espaces de noms XML (C#)](../../linq/namespaces-overview.md) et [Utilisation des espaces de noms XML (Visual Basic)](../../linq/namespaces-overview.md) dans la documentation LINQ.  
  
 Voici quelques tâches de recherche et de gestion que vous pouvez effectuer avec la classe <xref:System.Xml.XmlNamespaceManager>. Pour obtenir plus d'informations et des exemples, suivez les liens à la page de référence de chaque méthode ou propriété.  
  
|À|Utiliser|  
|--------|---------|  
|Ajouter un espace de noms|Méthode <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A>|  
|Supprimer un espace de noms|Méthode <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A>|  
|Rechercher l'URI de l'espace de noms par défaut|Propriété<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>|  
|Rechercher l'URI du préfixe d'un espace de noms|Méthode <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A>|  
|Rechercher le préfixe de l'URI d'un espace de noms|Méthode <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A>|  
|Obtenir une liste des espaces de noms dans le nœud actuel|Méthode <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A>|  
|Définir la portée d'un espace de noms|Méthodes <xref:System.Xml.XmlNamespaceManager.PushScope%2A> et <xref:System.Xml.XmlNamespaceManager.PopScope%2A>|  
|Vérifier si un préfixe est défini dans la portée actuelle|Méthode <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A>|  
|Obtenir la table de noms utilisée pour rechercher les préfixes et les URI|Propriété<xref:System.Xml.XmlNamespaceManager.NameTable%2A>|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlNamespaceManager>
- [Documents et données XML](index.md)
