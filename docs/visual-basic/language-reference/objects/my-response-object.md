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
# <a name="myresponse-object"></a><span data-ttu-id="2cd9e-102">My.Response, objet</span><span class="sxs-lookup"><span data-stu-id="2cd9e-102">My.Response Object</span></span>
<span data-ttu-id="2cd9e-103">Obtient l' <xref:System.Web.HttpResponse> objet associé au <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="2cd9e-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="2cd9e-104">Cet objet vous permet d’envoyer des données de réponse HTTP à un client et contient des informations relatives à cette réponse.</span><span class="sxs-lookup"><span data-stu-id="2cd9e-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cd9e-105">Notes</span><span class="sxs-lookup"><span data-stu-id="2cd9e-105">Remarks</span></span>  
 <span data-ttu-id="2cd9e-106">L' `My.Response` objet contient l' <xref:System.Web.HttpResponse> objet actuel associé à la page.</span><span class="sxs-lookup"><span data-stu-id="2cd9e-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="2cd9e-107">L' `My.Response` objet est uniquement disponible pour les applications ASP.net.</span><span class="sxs-lookup"><span data-stu-id="2cd9e-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cd9e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cd9e-108">Example</span></span>  
 <span data-ttu-id="2cd9e-109">L’exemple suivant obtient la collection d’en-têtes de l' `My.Request` objet et utilise l' `My.Response` objet pour l’écrire dans la page ASP.net.</span><span class="sxs-lookup"><span data-stu-id="2cd9e-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2cd9e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cd9e-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="2cd9e-111">My.Request, objet</span><span class="sxs-lookup"><span data-stu-id="2cd9e-111">My.Request Object</span></span>](my-request-object.md)
