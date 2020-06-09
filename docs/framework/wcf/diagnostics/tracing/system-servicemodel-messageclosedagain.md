---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580435"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="f5e05-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="f5e05-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="f5e05-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="f5e05-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="f5e05-104">Description</span><span class="sxs-lookup"><span data-stu-id="f5e05-104">Description</span></span>  
 <span data-ttu-id="f5e05-105">Un message a de nouveau été fermé.</span><span class="sxs-lookup"><span data-stu-id="f5e05-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="f5e05-106">Un message ne doit être fermé qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="f5e05-106">A message should be closed only once.</span></span> <span data-ttu-id="f5e05-107">Si ce suivi est émis dans le code d’extension utilisateur, il indique que ce code ferme un message qui a déjà été fermé.</span><span class="sxs-lookup"><span data-stu-id="f5e05-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="f5e05-108">Si ce suivi est émis via le code produit, il indique que le code d’extension utilisateur peut éventuellement fermer un message trop tôt.</span><span class="sxs-lookup"><span data-stu-id="f5e05-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e05-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5e05-109">See also</span></span>

- [<span data-ttu-id="f5e05-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="f5e05-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="f5e05-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="f5e05-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f5e05-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="f5e05-112">Administration and Diagnostics</span></span>](../index.md)
