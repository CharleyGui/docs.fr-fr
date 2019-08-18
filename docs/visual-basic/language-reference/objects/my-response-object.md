---
title: My. Response, objet (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567455"
---
# <a name="myresponse-object"></a>My.Response, objet
Obtient l' <xref:System.Web.HttpResponse> objet associé <xref:System.Web.UI.Page>au. Cet objet vous permet d’envoyer des données de réponse HTTP à un client et contient des informations relatives à cette réponse.  
  
## <a name="remarks"></a>Notes  
 L' `My.Response` objet contient l’objet <xref:System.Web.HttpResponse> actuel associé à la page.  
  
 L' `My.Response` objet est uniquement disponible pour les applications ASP.net.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant obtient la collection d’en- `My.Request` têtes de l’objet `My.Response` et utilise l’objet pour l’écrire dans la page ASP.net.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Web.HttpResponse>
- [My.Request (objet)](../../../visual-basic/language-reference/objects/my-request-object.md)
