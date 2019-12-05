---
title: Déploiement d'applications WCF à l'aide de ClickOnce
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: b520931751bbba00d440b46657962ad3f1e41cd3
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802234"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="b96c0-102">Déploiement d'applications WCF à l'aide de ClickOnce</span><span class="sxs-lookup"><span data-stu-id="b96c0-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="b96c0-103">Les applications clientes qui utilisent Windows Communication Foundation (WCF) peuvent être déployées à l’aide de la technologie ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="b96c0-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="b96c0-104">Cette technologie leur permet de tirer parti des protections de sécurité d'exécution fournies par la sécurité d'accès du code, sous réserve qu'elles soient signées numériquement avec un certificat approuvé.</span><span class="sxs-lookup"><span data-stu-id="b96c0-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="b96c0-105">Le certificat utilisé pour signer l'application ClickOnce doit résider dans le magasin d'éditeurs approuvés, et la stratégie de sécurité locale sur l'ordinateur client doit être configurée pour accorder des autorisations Confiance totale aux applications signées avec le certificat de l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="b96c0-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="b96c0-106">Pour plus d’informations sur la configuration des applications ClickOnce et des éditeurs approuvés, consultez [Configuration des éditeurs approuvés ClickOnce](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="b96c0-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://docs.microsoft.com/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96c0-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b96c0-107">See also</span></span>

- [<span data-ttu-id="b96c0-108">Vue d’ensemble du déploiement d’applications approuvées</span><span class="sxs-lookup"><span data-stu-id="b96c0-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="b96c0-109">[Déploiement ClickOnce pour les applications Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b96c0-109">[ClickOnce Deployment for Windows Forms Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>
