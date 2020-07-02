---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617189"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="1331c-101">L’espacement de la zone de texte multiligne ASP.NET a été modifié pour l’utilisation d’AntiXSSEncoder</span><span class="sxs-lookup"><span data-stu-id="1331c-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="1331c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="1331c-102">Details</span></span>

<span data-ttu-id="1331c-103">Dans le .NET Framework 4.0, des lignes supplémentaires étaient insérées dans la zone de texte multiligne lors de la publication (postback), quand vous utilisiez <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1331c-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="1331c-104">Dans .NET Framework 4.5, ces sauts de ligne supplémentaires ne sont pas inclus si l’application web cible .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="1331c-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1331c-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="1331c-105">Suggestion</span></span>

<span data-ttu-id="1331c-106">Notez que les applications web 4.0 reciblées vers .NET Framework 4.5 peuvent avoir des zones de texte multilignes améliorées qui ne comportent plus de sauts de ligne supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1331c-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="1331c-107">Si vous ne souhaitez pas ce changement, vous pouvez obtenir l’ancien comportement dans .NET Framework 4.5 en ciblant .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="1331c-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="1331c-108">Nom</span><span class="sxs-lookup"><span data-stu-id="1331c-108">Name</span></span>    | <span data-ttu-id="1331c-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="1331c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1331c-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="1331c-110">Scope</span></span>   | <span data-ttu-id="1331c-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="1331c-111">Minor</span></span>       |
| <span data-ttu-id="1331c-112">Version</span><span class="sxs-lookup"><span data-stu-id="1331c-112">Version</span></span> | <span data-ttu-id="1331c-113">4,5</span><span class="sxs-lookup"><span data-stu-id="1331c-113">4.5</span></span>         |
| <span data-ttu-id="1331c-114">Type</span><span class="sxs-lookup"><span data-stu-id="1331c-114">Type</span></span>    | <span data-ttu-id="1331c-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="1331c-115">Retargeting</span></span> |
