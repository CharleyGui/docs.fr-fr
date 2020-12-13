---
title: Installer des dépendances ML.NET supplémentaires
description: Découvrez comment installer les bibliothèques natives dont les packages ML.NET sont dépendants, mais qui ne sont pas installés avec les packages NuGet
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: 75d29c6bafdce5c9bb104229ddc8d7b847f57e29
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366798"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="8b687-103">Installer des dépendances ML.NET supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8b687-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="8b687-104">Dans la plupart des cas, sur tous les systèmes d’exploitation, l’installation de ML.NET est aussi simple que le fait de référencer le package NuGet approprié.</span><span class="sxs-lookup"><span data-stu-id="8b687-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="8b687-105">Dans certains cas, cependant, il existe des exigences d’installation supplémentaires, en particulier lorsque des composants natifs sont requis.</span><span class="sxs-lookup"><span data-stu-id="8b687-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="8b687-106">Ce document décrit la configuration requise pour l’installation de ces cas.</span><span class="sxs-lookup"><span data-stu-id="8b687-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="8b687-107">Les sections sont décomposées par le `Microsoft.ML.*` package NuGet spécifique qui a la dépendance supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="8b687-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="8b687-108">Microsoft. ML. TimeSeries, Microsoft. ML. AutoML</span><span class="sxs-lookup"><span data-stu-id="8b687-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="8b687-109">Ces deux packages ont une dépendance sur `Microsoft.ML.MKL.Redist` , qui a une dépendance sur `libomp` .</span><span class="sxs-lookup"><span data-stu-id="8b687-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="8b687-110">Windows</span><span class="sxs-lookup"><span data-stu-id="8b687-110">Windows</span></span>

<span data-ttu-id="8b687-111">Aucune étape d’installation supplémentaire n’est requise.</span><span class="sxs-lookup"><span data-stu-id="8b687-111">No extra installation steps required.</span></span> <span data-ttu-id="8b687-112">La bibliothèque est installée lorsque le package NuGet est ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="8b687-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="8b687-113">Linux</span><span class="sxs-lookup"><span data-stu-id="8b687-113">Linux</span></span>

1. <span data-ttu-id="8b687-114">Installer la clé GPG pour le référentiel</span><span class="sxs-lookup"><span data-stu-id="8b687-114">Install the GPG key for the repository</span></span>

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

2. <span data-ttu-id="8b687-115">Ajouter le référentiel APT pour MKL</span><span class="sxs-lookup"><span data-stu-id="8b687-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="8b687-116">Mettre à jour des packages</span><span class="sxs-lookup"><span data-stu-id="8b687-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="8b687-117">Installer MKL</span><span class="sxs-lookup"><span data-stu-id="8b687-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="8b687-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b687-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="8b687-119">Déterminer l’emplacement de `libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="8b687-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="8b687-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8b687-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="8b687-121">Ajoutez cet emplacement au chemin de la bibliothèque de chargement :</span><span class="sxs-lookup"><span data-stu-id="8b687-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="8b687-122">Mac</span><span class="sxs-lookup"><span data-stu-id="8b687-122">Mac</span></span>

1. <span data-ttu-id="8b687-123">Installer la bibliothèque avec `Homebrew`</span><span class="sxs-lookup"><span data-stu-id="8b687-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
