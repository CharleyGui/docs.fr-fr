---
title: My.Response, objet
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 53e8012e762c46e6efbd8e9d2191aa62d58aa42b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870039"
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
