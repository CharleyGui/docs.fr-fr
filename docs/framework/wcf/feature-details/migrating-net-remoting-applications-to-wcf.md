---
title: Migration d'applications .NET Remoting vers WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 1d7edab8ad89660f3384d0ccf556384175c4d5db
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212161"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="c5dea-102">Migration d'applications .NET Remoting vers WCF</span><span class="sxs-lookup"><span data-stu-id="c5dea-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="c5dea-103">**Cette rubrique est spécifique à une technologie héritée qui est conservée pour la compatibilité descendante avec les applications existantes et n’est pas recommandée pour un nouveau développement. Les applications distribuées doivent maintenant être développées à l’aide de WCF.**</span><span class="sxs-lookup"><span data-stu-id="c5dea-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="c5dea-104">Il existe deux façons de tirer parti de WCF avec les applications .NET Remoting existantes : intégration et migration.</span><span class="sxs-lookup"><span data-stu-id="c5dea-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="c5dea-105">L’intégration vous permet d’avoir .NET Remoting 2,0 et WCF s’exécutant côte à côte, ce qui vous permet d’exposer les mêmes objets métier sur les deux technologies simultanément, sans avoir à modifier votre code .NET Remoting .NET 2,0 Remoting existant.</span><span class="sxs-lookup"><span data-stu-id="c5dea-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="c5dea-106">Pour l’intégration, vous devez exécuter sur .NET Framework 2,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c5dea-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="c5dea-107">Si vous souhaitez tirer parti des fonctionnalités WCF et que vous n’avez pas besoin de la compatibilité des câbles avec les systèmes Remoting 2,0, vous pouvez migrer l’ensemble de votre service vers WCF.</span><span class="sxs-lookup"><span data-stu-id="c5dea-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="c5dea-108">La migration de .NET Remoting 2,0 vers WCF nécessite des modifications de l’interface de l’objet distant et de ses paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="c5dea-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="c5dea-109">Ces deux rubriques sont abordées dans [la rubrique de la communication à distance au Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).</span><span class="sxs-lookup"><span data-stu-id="c5dea-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dea-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5dea-110">See also</span></span>

- [<span data-ttu-id="c5dea-111">Vue d’ensemble conceptuelle</span><span class="sxs-lookup"><span data-stu-id="c5dea-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
