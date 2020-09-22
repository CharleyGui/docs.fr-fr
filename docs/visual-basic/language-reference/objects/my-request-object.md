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
# <a name="myrequest-object"></a><span data-ttu-id="f51a9-102">My.Request, objet</span><span class="sxs-lookup"><span data-stu-id="f51a9-102">My.Request Object</span></span>

<span data-ttu-id="f51a9-103">Obtient l’objet <xref:System.Web.HttpRequest> pour la page demandée.</span><span class="sxs-lookup"><span data-stu-id="f51a9-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f51a9-104">Notes</span><span class="sxs-lookup"><span data-stu-id="f51a9-104">Remarks</span></span>  

 <span data-ttu-id="f51a9-105">L’objet `My.Request` contient des informations sur la requête HTTP en cours.</span><span class="sxs-lookup"><span data-stu-id="f51a9-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="f51a9-106">L’objet `My.Request` est disponible uniquement pour les applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f51a9-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f51a9-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f51a9-107">Example</span></span>  

 <span data-ttu-id="f51a9-108">L’exemple suivant obtient la collection d’en-têtes de l' `My.Request` objet et utilise l' `My.Response` objet pour l’écrire dans la page ASP.net.</span><span class="sxs-lookup"><span data-stu-id="f51a9-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f51a9-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f51a9-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="f51a9-110">My.Response, objet</span><span class="sxs-lookup"><span data-stu-id="f51a9-110">My.Response Object</span></span>](my-response-object.md)
