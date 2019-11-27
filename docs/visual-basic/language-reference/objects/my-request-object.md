---
title: My.Request, objet
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 22329bc501c9bb75b1336dd5384ab5b23a98ac21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350676"
---
# <a name="myrequest-object"></a>My.Request, objet
Obtient l’objet <xref:System.Web.HttpRequest> pour la page demandée.  
  
## <a name="remarks"></a>Notes  
 L’objet `My.Request` contient des informations sur la requête HTTP en cours.  
  
 L’objet `My.Request` est disponible uniquement pour les applications ASP.NET.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant obtient la collection d’en-têtes de l’objet `My.Request` et utilise l’objet `My.Response` pour l’écrire dans la page ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Web.HttpRequest>
- [My.Response (objet)](../../../visual-basic/language-reference/objects/my-response-object.md)
