---
title: 'Procédure : Ajouter une référence de service de données (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790736"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="71d52-102">Procédure : Ajouter une référence de service de données (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="71d52-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="71d52-103">Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="71d52-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="71d52-104">De cette manière, vous pouvez accéder plus facilement à un service de données dans une application cliente que vous développez dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71d52-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="71d52-105">Lorsque vous complétez cette procédure, les classes de données sont générées selon les métadonnées obtenues auprès du service de données.</span><span class="sxs-lookup"><span data-stu-id="71d52-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="71d52-106">Pour plus d’informations, consultez [génération de la bibliothèque cliente du service de données](generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="71d52-106">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="71d52-107">Ajouter une référence de service de données</span><span class="sxs-lookup"><span data-stu-id="71d52-107">Add a data service reference</span></span>

1. <span data-ttu-id="71d52-108">(Facultatif) Si le service de données n'appartient pas à la solution et n'est pas déjà en cours d'exécution, démarrez le service de données et notez l'URI du service de données.</span><span class="sxs-lookup"><span data-stu-id="71d52-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="71d52-109">Dans Visual Studio, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet client, puis sélectionnez **Ajouter** > une**référence de service**.</span><span class="sxs-lookup"><span data-stu-id="71d52-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="71d52-110">Si le service de données fait partie de la solution actuelle, cliquez sur **découvrir**.</span><span class="sxs-lookup"><span data-stu-id="71d52-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="71d52-111">ou</span><span class="sxs-lookup"><span data-stu-id="71d52-111">-or-</span></span>

     <span data-ttu-id="71d52-112">Dans la zone de texte **adresse** , tapez l’URL de base du service de données, `http://localhost:1234/Northwind.svc`par exemple, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="71d52-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="71d52-113">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="71d52-113">Select **OK**.</span></span>

     <span data-ttu-id="71d52-114">Un nouveau fichier de code qui contient les classes de données qui peuvent accéder aux ressources du service de données et interagir avec celles-ci est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="71d52-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="71d52-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71d52-115">See also</span></span>

- [<span data-ttu-id="71d52-116">Démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="71d52-116">Quickstart</span></span>](quickstart-wcf-data-services.md)
