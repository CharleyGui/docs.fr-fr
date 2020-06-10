---
title: "Comment : déployer une application d'intégration COM+"
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: b4ae7f730296d54debc1cf2971b61e5700503430
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595425"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="e5d0c-102">Comment : déployer une application d'intégration COM+</span><span class="sxs-lookup"><span data-stu-id="e5d0c-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="e5d0c-103">Après avoir écrit une application d'intégration COM+, vous pouvez la déployer sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="e5d0c-104">Cette rubrique décrit comment déplacer une application d'intégration COM+ d'un ordinateur vers un autre.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="e5d0c-105">Déplacement d'une application d'intégration hébergée COM+</span><span class="sxs-lookup"><span data-stu-id="e5d0c-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="e5d0c-106">Assurez-vous que WCF est installé sur les deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="e5d0c-107">Exportez l'application de l'ordinateur A.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="e5d0c-108">Importez l'application sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="e5d0c-109">Définissez le répertoire racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-109">Set the Application Root Directory.</span></span> <span data-ttu-id="e5d0c-110">Par convention, il s'agit de %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="e5d0c-111">Copiez les fichiers Application.config et Application.manifest du répertoire racine de l'application sur l'ordinateur A vers le répertoire racine de l'application sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="e5d0c-112">Modifiez les adresses de point de terminaison de service dans le fichier Application.config sur l'ordinateur B pour identifier l'ordinateur approprié.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="e5d0c-113">Par exemple, remplacez `http://machineA/MyService` par `http://machineB/MyService`.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="e5d0c-114">Déplacement d'une application d'intégration hébergée sur le Web</span><span class="sxs-lookup"><span data-stu-id="e5d0c-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="e5d0c-115">Assurez-vous que WCF est installé sur les deux ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="e5d0c-116">Exportez l'application de l'ordinateur A.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="e5d0c-117">Importez l'application sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="e5d0c-118">Créez une racine virtuelle IIS sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="e5d0c-119">Copiez le fichier .svc (componentName.svc) et le fichier Web.config de la racine virtuelle sur l'ordinateur A vers la racine virtuelle que vous venez de créer sur l'ordinateur B.</span><span class="sxs-lookup"><span data-stu-id="e5d0c-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d0c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5d0c-120">See also</span></span>

- [<span data-ttu-id="e5d0c-121">Vue d’ensemble de l’intégration aux applications COM+</span><span class="sxs-lookup"><span data-stu-id="e5d0c-121">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="e5d0c-122">Comment : configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="e5d0c-122">How to: Configure COM+ Service Settings</span></span>](how-to-configure-com-service-settings.md)
- [<span data-ttu-id="e5d0c-123">Guide pratique pour utiliser l’outil de configuration de modèle de service COM+</span><span class="sxs-lookup"><span data-stu-id="e5d0c-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](how-to-use-the-com-service-model-configuration-tool.md)
