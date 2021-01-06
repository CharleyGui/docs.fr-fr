---
title: Installation d’Azure CLI
description: Les développeurs Azure ont besoin de la Azure CLI installée, cet article explique pourquoi vous avez besoin de l’interface CLI et de l’emplacement où la télécharger et l’installer à partir de.
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 43737aaf5dfd02b8c4ffa6c213d7221cfe38162f
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701141"
---
# <a name="install-the-azure-cli"></a><span data-ttu-id="095ad-103">Installer l’interface de ligne de commande Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="095ad-103">Install the Azure CLI</span></span>

<span data-ttu-id="095ad-104">Outre le portail Azure, Azure offre également la [Azure CLI](/cli/azure/) en tant qu’outil en ligne de commande pour créer et gérer des ressources Azure.</span><span class="sxs-lookup"><span data-stu-id="095ad-104">In addition to the Azure Portal, Azure also offers the [Azure CLI](/cli/azure/) as a command-line tool to create and manage Azure resources.</span></span> <span data-ttu-id="095ad-105">Le Azure CLI offre les avantages de l’efficacité, de la répétabilité et de la possibilité de générer des scripts pour les tâches récurrentes.</span><span class="sxs-lookup"><span data-stu-id="095ad-105">The Azure CLI offers the benefits of efficiency, repeatability, and the ability to script recurring tasks.</span></span>  

<span data-ttu-id="095ad-106">Dans la pratique, la plupart des développeurs utilisent à la fois le portail Azure et le Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="095ad-106">In practice, most developers use both the Azure Portal and the Azure CLI.</span></span> <span data-ttu-id="095ad-107">Lorsque le portail Azure est utile lors de l’exploration de nouveaux services et de l’obtention d’une vue d’ensemble de toutes les ressources de votre compte Azure, la plupart des développeurs recherchent les Azure CLI plus rapides et plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="095ad-107">Where as the Azure Portal is useful when exploring new services and getting an overview of all of the resources in your Azure account, most developers find the Azure CLI to be faster and more efficient.</span></span>  <span data-ttu-id="095ad-108">Le Azure CLI peut souvent accomplir dans une seule commande qui prend plusieurs étapes dans le portail Azure.</span><span class="sxs-lookup"><span data-stu-id="095ad-108">The Azure CLI can often accomplish in a single command what takes multiple steps in the Azure Portal.</span></span>  <span data-ttu-id="095ad-109">En outre, étant donné que les commandes Azure CLI peuvent être enregistrées dans un fichier, les développeurs peuvent s’assurer que les tâches restantes sont exécutées de la même façon à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="095ad-109">In addition, since Azure CLI commands can be saved to a file, developers can assure that recurrent tasks are run the same way each time.</span></span>

<span data-ttu-id="095ad-110">Le Azure CLI est disponible pour Windows, macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="095ad-110">The Azure CLI is available for Windows, macOS, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="095ad-111">Installer l’interface de ligne de commande Azure pour Windows</span><span class="sxs-lookup"><span data-stu-id="095ad-111">Install the Azure CLI for Windows</span></span>](/cli/azure/install-azure-cli-windows?tabs=azure-cli)

> [!div class="nextstepaction"]
> [<span data-ttu-id="095ad-112">Installer l’interface de ligne de commande Azure pour macOS</span><span class="sxs-lookup"><span data-stu-id="095ad-112">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)

> [!div class="nextstepaction"]
> [<span data-ttu-id="095ad-113">Installer le Azure CLI pour Linux</span><span class="sxs-lookup"><span data-stu-id="095ad-113">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

### <a name="azure-cloud-shell"></a><span data-ttu-id="095ad-114">Azure Cloud Shell</span><span class="sxs-lookup"><span data-stu-id="095ad-114">Azure Cloud Shell</span></span>

<span data-ttu-id="095ad-115">Vous pouvez également utiliser le Azure CLI dans le Azure Cloud Shell à l’adresse [https://shell.azure.com](https://shell.azure.com) .</span><span class="sxs-lookup"><span data-stu-id="095ad-115">You can also use the Azure CLI in the Azure Cloud Shell at [https://shell.azure.com](https://shell.azure.com).</span></span>  <span data-ttu-id="095ad-116">Le Azure Cloud Shell est un interpréteur de commandes entièrement fonctionnel et basé sur un navigateur pour la gestion des ressources Azure.</span><span class="sxs-lookup"><span data-stu-id="095ad-116">The Azure Cloud Shell is a fully functional, browser-based shell for managing Azure resources.</span></span>  <span data-ttu-id="095ad-117">Le Azure Cloud Shell est utile lorsque vous avez besoin d’un environnement de ligne de commande, mais que vous travaillez sur un appareil sur lequel vous ne parvenez pas à installer le Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="095ad-117">The Azure Cloud Shell is useful when you need a command line environment but are working on a device where you are unable to install the Azure CLI.</span></span>

![Capture d’écran de l’Azure Cloud Shell s’exécutant dans un navigateur](media/azure-cloud-shell.png)
