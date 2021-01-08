---
title: Liste de vérification de la configuration du développement .NET sur Azure
description: Fournit un récapitulatif rapide de tous les outils que vous devez installer pour effectuer le développement .net avec Azure
ms.date: 1/1/2021
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: a2ff9bbf1e6a8790ddc161a1a1c8d14e8fab6e41
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98027267"
---
# <a name="net-on-azure-development-environment-checklist"></a><span data-ttu-id="247a7-103">Liste de vérification de l’environnement de développement .NET sur Azure</span><span class="sxs-lookup"><span data-stu-id="247a7-103">.NET on Azure development environment checklist</span></span>

<span data-ttu-id="247a7-104">Cette liste de vérification est fournie pour vous aider à vérifier que votre environnement de développement est correctement configuré pour le développement .NET avec Azure.</span><span class="sxs-lookup"><span data-stu-id="247a7-104">This checklist is provided to help you make sure you have your development environment correctly configured for .NET development with Azure</span></span>

## <a name="create-an-azure-account"></a><span data-ttu-id="247a7-105">Création d'un compte Azure</span><span class="sxs-lookup"><span data-stu-id="247a7-105">Create an Azure account</span></span>

<span data-ttu-id="247a7-106">Pour accéder aux services Azure ou exécuter des applications dans Azure, vous avez besoin d’un compte Azure.</span><span class="sxs-lookup"><span data-stu-id="247a7-106">To access Azure services or run applications in Azure, you need an Azure account.</span></span>

* <span data-ttu-id="247a7-107">Si vous êtes abonné à Visual Studio, vous disposez de [crédits Azure gratuits](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) mensuels disponibles chaque mois</span><span class="sxs-lookup"><span data-stu-id="247a7-107">If you are a Visual Studio subscriber, you have monthly [free Azure credits](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) available to you every month</span></span>
* <span data-ttu-id="247a7-108">[Créer un compte Azure gratuit](https://azure.microsoft.com/free/dotnet/) et recevoir $200 de crédits et sélectionner des services gratuits pendant 12 mois</span><span class="sxs-lookup"><span data-stu-id="247a7-108">[Create a free Azure account](https://azure.microsoft.com/free/dotnet/) and receive $200 in credits and select services free for 12 months</span></span>
* <span data-ttu-id="247a7-109">Utilisez un compte qui vous est attribué par l’administrateur Azure de votre entreprise</span><span class="sxs-lookup"><span data-stu-id="247a7-109">Use an account assigned to you by your company's Azure administrator</span></span>

## <a name="configure-your-ide"></a><span data-ttu-id="247a7-110">Configurer votre IDE</span><span class="sxs-lookup"><span data-stu-id="247a7-110">Configure your IDE</span></span>

<span data-ttu-id="247a7-111">Des outils populaires tels que Visual Studio et Visual Studio Code ont des extensions disponibles pour vous permettre d’utiliser Azure directement à partir de votre IDE.</span><span class="sxs-lookup"><span data-stu-id="247a7-111">Popular tools like Visual Studio and Visual Studio Code have extensions available to let you work with Azure right from your IDE.</span></span>

* <span data-ttu-id="247a7-112">[Configurer Visual Studio](./configure-visual-studio.md) pour le développement .net à l’aide d’Azure</span><span class="sxs-lookup"><span data-stu-id="247a7-112">[Configure Visual Studio](./configure-visual-studio.md) for .NET development using Azure</span></span>
* <span data-ttu-id="247a7-113">[Configurer Visual Studio code](./configure-vs-code.md) pour le développement .net à l’aide d’Azure</span><span class="sxs-lookup"><span data-stu-id="247a7-113">[Configure Visual Studio Code](./configure-vs-code.md) for .NET Development using Azure</span></span>

## <a name="install-the-azure-cli"></a><span data-ttu-id="247a7-114">Installer l’interface de ligne de commande Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="247a7-114">Install the Azure CLI</span></span>

<span data-ttu-id="247a7-115">En plus de l’utilisation de la Portail Azure, vous pouvez installer le Azure CLI pour créer et gérer des ressources Azure.</span><span class="sxs-lookup"><span data-stu-id="247a7-115">In addition to using the Azure portal, you will want to install the Azure CLI to create and manage Azure resources.</span></span>

* <span data-ttu-id="247a7-116">[Installer le Azure CLI pour Windows](/cli/azure/install-azure-cli-windows?tabs=azure-cli))</span><span class="sxs-lookup"><span data-stu-id="247a7-116">[Install the Azure CLI for Windows](/cli/azure/install-azure-cli-windows?tabs=azure-cli))</span></span>
* [<span data-ttu-id="247a7-117">Installer l’interface de ligne de commande Azure pour macOS</span><span class="sxs-lookup"><span data-stu-id="247a7-117">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)
* [<span data-ttu-id="247a7-118">Installer le Azure CLI pour Linux</span><span class="sxs-lookup"><span data-stu-id="247a7-118">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a><span data-ttu-id="247a7-119">Installer des outils et utilitaires supplémentaires</span><span class="sxs-lookup"><span data-stu-id="247a7-119">Install additional tools and utilities</span></span>

<span data-ttu-id="247a7-120">Ces outils supplémentaires sont conçus pour vous permettre d’être plus productif quand vous travaillez avec Azure.</span><span class="sxs-lookup"><span data-stu-id="247a7-120">These additional tools are designed to make you more productive when working with Azure.</span></span>

* <span data-ttu-id="247a7-121">[Installer Azure PowerShell](/powershell/azure/install-az-ps) si vous envisagez d’utiliser des scripts PowerShell pour créer et gérer des ressources Azure</span><span class="sxs-lookup"><span data-stu-id="247a7-121">[Install Azure PowerShell](/powershell/azure/install-az-ps) if you plan on using PowerShell scripts to create and manage Azure resources</span></span>
* <span data-ttu-id="247a7-122">[Installez Explorateur stockage Azure](https://azure.microsoft.com/features/storage-explorer/) pour charger, télécharger et gérer des données dans des ressources de stockage Azure, notamment des objets BLOB, des files d’attente, des tables et des CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="247a7-122">[Install Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) to upload, download, and manage data in Azure storage resources including blobs, queues, tables, and CosmosDB.</span></span>
* <span data-ttu-id="247a7-123">[Installer Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio) si vous utilisez Azure SQL</span><span class="sxs-lookup"><span data-stu-id="247a7-123">[Install Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio) if you are working with Azure SQL</span></span>

## <a name="bookmark-the-following-sites"></a><span data-ttu-id="247a7-124">Associer les sites suivants aux favoris</span><span class="sxs-lookup"><span data-stu-id="247a7-124">Bookmark the following sites</span></span>

<span data-ttu-id="247a7-125">Vous utiliserez fréquemment ces sites lors du développement Azure.</span><span class="sxs-lookup"><span data-stu-id="247a7-125">You will use these sites frequently when doing Azure development.</span></span>  <span data-ttu-id="247a7-126">Ajoutez-les aux signets pour référence rapide.</span><span class="sxs-lookup"><span data-stu-id="247a7-126">Bookmark them for quick reference.</span></span>

* <span data-ttu-id="247a7-127">Portail Azure- [https://portal.azure.com/](https://portal.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="247a7-127">Azure Portal - [https://portal.azure.com/](https://portal.azure.com/)</span></span>
* <span data-ttu-id="247a7-128">Azure Cloud Shell- [https://shell.azure.com/](https://shell.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="247a7-128">Azure Cloud Shell - [https://shell.azure.com/](https://shell.azure.com/)</span></span>
