---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400058"
---
# <a name="param-visual-basic"></a>\<param> (Visual Basic)
Définit un nom de paramètre et une description.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>Paramètres  
 `name`  
 Nom d’un paramètre de méthode. Mettez le nom entre guillemets doubles (" ").  
  
 `description`  
 Description du paramètre.  
  
## <a name="remarks"></a>Notes  
 La `<param>` balise doit être utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.  
  
 Le texte de la `<param>` balise apparaît aux emplacements suivants :  
  
- Informations sur les paramètres d’IntelliSense. Pour plus d’informations, consultez [Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense).  
  
- Explorateur d’objets. Pour plus d’informations, consultez [affichage de la structure du code](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `<param>` balise pour décrire le `id` paramètre.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](index.md)
