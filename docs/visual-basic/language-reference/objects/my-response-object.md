---
title: My.Response, objet
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 522814ad48fb7548032b8a37779bb3ff6ca62413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350657"
---
# <a name="myresponse-object"></a>My.Response, objet
Obtient l’objet <xref:System.Web.HttpResponse> associé au <xref:System.Web.UI.Page>. Cet objet vous permet d’envoyer des données de réponse HTTP à un client et contient des informations relatives à cette réponse.  
  
## <a name="remarks"></a>Notes  
 L’objet `My.Response` contient l’objet <xref:System.Web.HttpResponse> actuel associé à la page.  
  
 L’objet `My.Response` est uniquement disponible pour les applications ASP.NET.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant obtient la collection d’en-têtes de l’objet `My.Request` et utilise l’objet `My.Response` pour l’écrire dans la page ASP.NET.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Web.HttpResponse>
- [My.Request (objet)](../../../visual-basic/language-reference/objects/my-request-object.md)
