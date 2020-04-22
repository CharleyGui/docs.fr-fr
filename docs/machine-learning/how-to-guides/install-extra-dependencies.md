---
title: Installer des dépendances ML.NET supplémentaires
description: Apprenez à installer toutes les bibliothèques autochtones dont ML.NET les paquets dépendent, mais ne sont pas installés avec les paquets NuGet
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c427439d0950bfea38f1d6d11af84216e0f1965f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021844"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="b3e7c-103">Installer des dépendances ML.NET supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b3e7c-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="b3e7c-104">Dans la plupart des cas, sur tous les systèmes d’exploitation, l’installation de ML.NET est aussi simple que le référencement du paquet NuGet approprié.</span><span class="sxs-lookup"><span data-stu-id="b3e7c-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```bash
dotnet add package Microsoft.ML
```

<span data-ttu-id="b3e7c-105">Dans certains cas cependant, il existe des exigences d’installation supplémentaires, en particulier lorsque des composants indigènes sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b3e7c-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="b3e7c-106">Ce document décrit les exigences d’installation de ces cas.</span><span class="sxs-lookup"><span data-stu-id="b3e7c-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="b3e7c-107">Les sections sont décomposées par le paquet NuGet spécifique `Microsoft.ML.*` qui a la dépendance supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b3e7c-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="b3e7c-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span><span class="sxs-lookup"><span data-stu-id="b3e7c-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="b3e7c-109">Ces deux paquets ont `Microsoft.ML.MKL.Redist`une dépendance à `libiomp`, qui a une dépendance sur .</span><span class="sxs-lookup"><span data-stu-id="b3e7c-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="b3e7c-110">Windows</span><span class="sxs-lookup"><span data-stu-id="b3e7c-110">Windows</span></span>

<span data-ttu-id="b3e7c-111">Aucune étape d’installation supplémentaire n’est requise.</span><span class="sxs-lookup"><span data-stu-id="b3e7c-111">No extra installation steps required.</span></span> <span data-ttu-id="b3e7c-112">La bibliothèque est installée lorsque le paquet NuGet est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="b3e7c-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="b3e7c-113">Linux</span><span class="sxs-lookup"><span data-stu-id="b3e7c-113">Linux</span></span>

1. <span data-ttu-id="b3e7c-114">Installer la clé GPG pour le dépôt</span><span class="sxs-lookup"><span data-stu-id="b3e7c-114">Install the GPG key for the repository</span></span>

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. <span data-ttu-id="b3e7c-115">Ajouter le dépôt APT pour MKL</span><span class="sxs-lookup"><span data-stu-id="b3e7c-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="b3e7c-116">Mettre à jour des packages</span><span class="sxs-lookup"><span data-stu-id="b3e7c-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="b3e7c-117">Installer MKL</span><span class="sxs-lookup"><span data-stu-id="b3e7c-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="b3e7c-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b3e7c-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="b3e7c-119">Déterminer l’emplacement de`libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="b3e7c-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="b3e7c-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b3e7c-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="b3e7c-121">Ajoutez cet emplacement au chemin de la bibliothèque de charge :</span><span class="sxs-lookup"><span data-stu-id="b3e7c-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="b3e7c-122">Mac</span><span class="sxs-lookup"><span data-stu-id="b3e7c-122">Mac</span></span>

1. <span data-ttu-id="b3e7c-123">Installer la bibliothèque avec`Homebrew`</span><span class="sxs-lookup"><span data-stu-id="b3e7c-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
