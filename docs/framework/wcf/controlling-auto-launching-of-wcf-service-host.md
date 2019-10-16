---
title: Contrôle de l'auto-lancement de l'hôte de service WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320626"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="a901b-102">Contrôle de l'auto-lancement de l'hôte de service WCF</span><span class="sxs-lookup"><span data-stu-id="a901b-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="a901b-103">Vous pouvez contrôler la capacité de lancement automatique de Windows Communication Foundation hôte de service (WcfSvcHost. exe) pour un projet de bibliothèque de service WCF, lorsque vous déboguez un autre projet dans la même solution Visual Studio contenant plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="a901b-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="a901b-104">Pour ce faire, cliquez avec le bouton droit sur le projet de service WCF dans **Explorateur de solutions**, choisissez **Propriétés**, puis cliquez sur l’onglet **options WCF** . La case à cocher **Démarrer l’hôte de service WCF lors du débogage d’un autre projet dans la même solution** est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="a901b-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="a901b-105">Vous pouvez décocher la case pour que l’hôte de service WCF pour ce projet spécifique ne démarre pas lorsqu’un autre projet est débogué dans la même solution.</span><span class="sxs-lookup"><span data-stu-id="a901b-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="a901b-106">Ce comportement n'affecte pas le débogage F5 ni les fonctionnalités d'ajout d'une référence de service pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="a901b-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="a901b-107">Cette option est disponible dans le cadre des projets suivants :</span><span class="sxs-lookup"><span data-stu-id="a901b-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="a901b-108">Projet de bibliothèque du service WCF.</span><span class="sxs-lookup"><span data-stu-id="a901b-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="a901b-109">Projet de la bibliothèque du service du workflow séquentiel</span><span class="sxs-lookup"><span data-stu-id="a901b-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="a901b-110">Projet de la bibliothèque du service de workflow d'ordinateur d'état</span><span class="sxs-lookup"><span data-stu-id="a901b-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="a901b-111">Projet de la bibliothèque du service de syndication</span><span class="sxs-lookup"><span data-stu-id="a901b-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a901b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a901b-112">See also</span></span>

- [<span data-ttu-id="a901b-113">WCF Service Host (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="a901b-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
