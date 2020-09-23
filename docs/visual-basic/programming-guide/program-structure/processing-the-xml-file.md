---
title: Traitement du fichier XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 9e12f6f5d86957a7f9aaea6047a79957fac8ce1e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072130"
---
# <a name="processing-the-xml-file-visual-basic"></a>Traitement du fichier XML (Visual Basic)

Le compilateur génère une chaîne d’ID pour chaque construction de votre code qui est marquée pour générer la documentation. (Pour plus d’informations sur la façon de baliser votre code, consultez [balises de commentaire XML](../../language-reference/xmldoc/index.md).) La chaîne d’ID identifie de façon unique la construction. Les programmes qui traitent le fichier XML peuvent utiliser la chaîne d’ID pour identifier l’élément de métadonnées/réflexion .NET Framework correspondant.  
  
 Le fichier XML n’est pas une représentation hiérarchique de votre code. Il s’agit d’une liste plate avec un ID généré pour chaque élément.  
  
 Le compilateur respecte les règles suivantes quand il génère les chaînes d’ID :  
  
- La chaîne ne contient aucun espace blanc.  
  
- La première partie de la chaîne d’ID identifie le type du membre, avec un caractère unique suivi de deux-points. Les types de membres suivants sont utilisés.  
  
|Caractère|Description|  
|---|---|  
|N|espace de noms<br /><br /> Vous ne pouvez pas ajouter de commentaires de documentation à un espace de noms, mais vous pouvez y faire référence à CREF, le cas échéant.|  
|T|tapez : `Class` , `Module` ,,, `Interface` `Structure` `Enum` , `Delegate`|  
|F|case `Dim`|  
|P|propriété : `Property` (y compris les propriétés par défaut)|  
|M|méthode : `Sub` , `Function` , `Declare` , `Operator`|  
|E|événement `Event`|  
|!|chaîne d’erreur<br /><br /> Le reste de la chaîne fournit des informations sur l’erreur. Le compilateur Visual Basic génère des informations d’erreur pour les liens qui ne peuvent pas être résolus.|  
  
- La deuxième partie du `String` est le nom qualifié complet de l’élément, en commençant à la racine de l’espace de noms. Le nom de l’élément, son ou ses types englobants et l’espace de noms sont séparés par des points. Si le nom de l’élément lui-même contient des points, ils sont remplacés par le signe dièse (#). Il est supposé qu’aucun élément n’a un signe dièse directement dans son nom. Par exemple, le nom qualifié complet du `String` constructeur serait `System.String.#ctor` .  
  
- Pour les propriétés et méthodes, si la méthode a des arguments, la liste d’arguments entre parenthèses suit. S’il n’y a pas d’arguments, aucune parenthèse n’est présente. Les arguments sont séparés par des virgules. L’encodage de chaque argument suit directement la manière dont il est encodé dans une signature de .NET Framework.  
  
## <a name="example"></a>Exemple  

 Le code suivant montre comment les chaînes d’ID pour une classe et ses membres sont générées.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Voir aussi

- [-doc](../../reference/command-line-compiler/doc.md)
- [Guide pratique : créer une documentation XML](how-to-create-xml-documentation.md)
