---
title: My.Response, objet
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372456"
---
# <a name="myresponse-object"></a>My.Response, objet
Obtient l' <xref:System.Web.HttpResponse> objet associé au <xref:System.Web.UI.Page> . Cet objet vous permet d’envoyer des données de réponse HTTP à un client et contient des informations relatives à cette réponse.  
  
## <a name="remarks"></a>Notes  
 L' `My.Response` objet contient l' <xref:System.Web.HttpResponse> objet actuel associé à la page.  
  
 L' `My.Response` objet est uniquement disponible pour les applications ASP.net.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant obtient la collection d’en-têtes de l' `My.Request` objet et utilise l' `My.Response` objet pour l’écrire dans la page ASP.net.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Web.HttpResponse>
- [My.Request, objet](my-request-object.md)
