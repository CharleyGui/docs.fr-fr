---
title: L'expression de type '<type>' ne peut pas être interrogée
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: e61b4dac109f714b5cf25226d1029237ca77032d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409476"
---
# <a name="expression-of-type-type-is-not-queryable"></a>L'expression de type '\<type>' ne peut pas être interrogée
L’expression de type ne \<type> peut pas être interrogée. Assurez-vous qu’il ne manque pas de référence d’assembly et/ou d’importation d’espace de noms pour le fournisseur LINQ.  
  
 Les types interrogeables sont définis dans <xref:System.Linq> les <xref:System.Data.Linq> espaces de <xref:System.Xml.Linq> noms, et. Vous devez importer un ou plusieurs de ces espaces de noms pour effectuer des requêtes LINQ.  
  
 L' <xref:System.Linq> espace de noms vous permet d’interroger des objets tels que des collections et des tableaux à l’aide de Linq.  
  
 L' <xref:System.Data.Linq> espace de noms vous permet d’interroger des jeux de données ADO.net et d’SQL Server des bases de données à l’aide de Linq.  
  
 L' <xref:System.Xml.Linq> espace de noms vous permet d’interroger du code XML à l’aide de LINQ et d’utiliser des fonctionnalités XML dans Visual Basic.  
  
 **ID d’erreur :** BC36593  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Ajoutez une `Import` instruction pour l' <xref:System.Linq> <xref:System.Data.Linq> espace de noms, ou <xref:System.Xml.Linq> à votre fichier de code. Vous pouvez également importer des espaces de noms pour votre projet à l’aide de la page **références** du concepteur de projets (**My Project**).  
  
2. Assurez-vous que le type que vous avez identifié comme source de votre requête est un type pouvant être interrogé. Autrement dit, un type qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601> .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Introduction à LINQ en Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../programming-guide/language-features/linq/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
- [Références et instruction Imports](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports, instruction (espace de noms et type .NET)](../statements/imports-statement-net-namespace-and-type.md)
- [Page Références, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
