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
# <a name="net-on-azure-development-environment-checklist"></a>Liste de vérification de l’environnement de développement .NET sur Azure

Cette liste de vérification est fournie pour vous aider à vérifier que votre environnement de développement est correctement configuré pour le développement .NET avec Azure.

## <a name="create-an-azure-account"></a>Création d'un compte Azure

Pour accéder aux services Azure ou exécuter des applications dans Azure, vous avez besoin d’un compte Azure.

* Si vous êtes abonné à Visual Studio, vous disposez de [crédits Azure gratuits](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) mensuels disponibles chaque mois
* [Créer un compte Azure gratuit](https://azure.microsoft.com/free/dotnet/) et recevoir $200 de crédits et sélectionner des services gratuits pendant 12 mois
* Utilisez un compte qui vous est attribué par l’administrateur Azure de votre entreprise

## <a name="configure-your-ide"></a>Configurer votre IDE

Des outils populaires tels que Visual Studio et Visual Studio Code ont des extensions disponibles pour vous permettre d’utiliser Azure directement à partir de votre IDE.

* [Configurer Visual Studio](./configure-visual-studio.md) pour le développement .net à l’aide d’Azure
* [Configurer Visual Studio code](./configure-vs-code.md) pour le développement .net à l’aide d’Azure

## <a name="install-the-azure-cli"></a>Installer l’interface de ligne de commande Microsoft Azure

En plus de l’utilisation de la Portail Azure, vous pouvez installer le Azure CLI pour créer et gérer des ressources Azure.

* [Installer le Azure CLI pour Windows](/cli/azure/install-azure-cli-windows?tabs=azure-cli))
* [Installer l’interface de ligne de commande Azure pour macOS](/cli/azure/install-azure-cli-macos)
* [Installer le Azure CLI pour Linux](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a>Installer des outils et utilitaires supplémentaires

Ces outils supplémentaires sont conçus pour vous permettre d’être plus productif quand vous travaillez avec Azure.

* [Installer Azure PowerShell](/powershell/azure/install-az-ps) si vous envisagez d’utiliser des scripts PowerShell pour créer et gérer des ressources Azure
* [Installez Explorateur stockage Azure](https://azure.microsoft.com/features/storage-explorer/) pour charger, télécharger et gérer des données dans des ressources de stockage Azure, notamment des objets BLOB, des files d’attente, des tables et des CosmosDB.
* [Installer Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio) si vous utilisez Azure SQL

## <a name="bookmark-the-following-sites"></a>Associer les sites suivants aux favoris

Vous utiliserez fréquemment ces sites lors du développement Azure.  Ajoutez-les aux signets pour référence rapide.

* Portail Azure- [https://portal.azure.com/](https://portal.azure.com/)
* Azure Cloud Shell- [https://shell.azure.com/](https://shell.azure.com/)
