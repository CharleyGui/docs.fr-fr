---
title: My.Request, objet
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 38f510e2a3958761b902f37760069aa8d595ea8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372425"
---
# <a name="myrequest-object"></a>My.Request, objet
Obtient l’objet <xref:System.Web.HttpRequest> pour la page demandée.  
  
## <a name="remarks"></a>Notes  
 L’objet `My.Request` contient des informations sur la requête HTTP en cours.  
  
 L’objet `My.Request` est disponible uniquement pour les applications ASP.NET.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant obtient la collection d’en-têtes de l' `My.Request` objet et utilise l' `My.Response` objet pour l’écrire dans la page ASP.net.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Web.HttpRequest>
- [My.Response, objet](my-response-object.md)
