---
title: 'Comment : activer le service de partage de ports Net.TCP'
description: Découvrez comment configurer le service de partage de port Net TCP à l’aide de MMC pour activer net. TCP, qui est désactivé par défaut.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246998"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="d4817-103">Comment : activer le service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d4817-103">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="d4817-104">Windows Communication Foundation (WCF) utilise un service Windows appelé service de partage de ports net. TCP pour faciliter le partage de ports TCP entre plusieurs processus.</span><span class="sxs-lookup"><span data-stu-id="d4817-104">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="d4817-105">Ce service est installé dans le cadre de WCF, mais le service n’est pas activé par défaut pour des raisons de sécurité et doit donc être activé manuellement avant la première utilisation.</span><span class="sxs-lookup"><span data-stu-id="d4817-105">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="d4817-106">Cette rubrique décrit comment configurer le service de partage de ports Net.TCP à l'aide du composant logiciel enfichable Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="d4817-106">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="d4817-107">Après avoir activé le service de partage de port Net. TCP et l’avoir démarré manuellement, consultez [procédure : configurer un service WCF pour utiliser le partage de ports](how-to-configure-a-wcf-service-to-use-port-sharing.md) pour plus d’informations sur la façon de configurer votre service pour utiliser ce service.</span><span class="sxs-lookup"><span data-stu-id="d4817-107">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="d4817-108">Pour obtenir un exemple qui utilise le partage de ports net. TCP://, consultez l' [exemple partage de port Net. TCP](../samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d4817-108">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="d4817-109">Pour activer le service de partage de ports Net.TCP à l'aide de MMC</span><span class="sxs-lookup"><span data-stu-id="d4817-109">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="d4817-110">Dans le menu Démarrer, ouvrez la console de gestion des services en ouvrant une fenêtre d’invite de commandes et `services.msc` en tapant ou en ouvrant exécuter et `services.msc` en tapant dans la zone Ouvrir.</span><span class="sxs-lookup"><span data-stu-id="d4817-110">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="d4817-111">Dans la colonne **nom** de la liste des services, cliquez avec le bouton droit sur le **service de partage de port Net. TCP**, puis sélectionnez **Propriétés** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="d4817-111">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="d4817-112">Pour activer le démarrage manuel du service, dans la fenêtre **Propriétés** , sélectionnez l’onglet **général** , et dans la zone **type de démarrage** , sélectionnez manuel, puis cliquez sur **appliquer**.</span><span class="sxs-lookup"><span data-stu-id="d4817-112">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="d4817-113">Pour démarrer le service, dans la zone État du service, cliquez sur le bouton **Démarrer** .</span><span class="sxs-lookup"><span data-stu-id="d4817-113">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="d4817-114">L'état du service doit maintenant afficher "Démarré".</span><span class="sxs-lookup"><span data-stu-id="d4817-114">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="d4817-115">Pour revenir à la liste des services, cliquez sur **OK**, puis quittez la console MMC.</span><span class="sxs-lookup"><span data-stu-id="d4817-115">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4817-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d4817-116">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4817-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4817-117">See also</span></span>

- [<span data-ttu-id="d4817-118">Partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d4817-118">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="d4817-119">Configuration du service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="d4817-119">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
