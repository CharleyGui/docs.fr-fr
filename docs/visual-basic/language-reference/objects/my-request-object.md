---
title: My.Request, objet
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: d0459506994fb69ebfaa4186ba137044b6fe9464
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870074"
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
