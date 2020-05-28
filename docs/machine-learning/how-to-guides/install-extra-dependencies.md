---
title: Installer des dépendances ML.NET supplémentaires
description: Découvrez comment installer les bibliothèques natives dont les packages ML.NET sont dépendants, mais qui ne sont pas installés avec les packages NuGet
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c744b42b4b95681de7b0cbeaef338cc890708fd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008428"
---
# <a name="install-extra-mlnet-dependencies"></a>Installer des dépendances ML.NET supplémentaires

Dans la plupart des cas, sur tous les systèmes d’exploitation, l’installation de ML.NET est aussi simple que le fait de référencer le package NuGet approprié.

```dotnetcli
dotnet add package Microsoft.ML
```

Dans certains cas, cependant, il existe des exigences d’installation supplémentaires, en particulier lorsque des composants natifs sont requis. Ce document décrit la configuration requise pour l’installation de ces cas. Les sections sont décomposées par le `Microsoft.ML.*` package NuGet spécifique qui a la dépendance supplémentaire.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft. ML. TimeSeries, Microsoft. ML. AutoML

Ces deux packages ont une dépendance sur `Microsoft.ML.MKL.Redist` , qui a une dépendance sur `libiomp` .

### <a name="windows"></a>Windows

Aucune étape d’installation supplémentaire n’est requise. La bibliothèque est installée lorsque le package NuGet est ajouté au projet.

### <a name="linux"></a>Linux

1. Installer la clé GPG pour le référentiel

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

2. Ajouter le référentiel APT pour MKL

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. Mettre à jour des packages

    ```bash
    sudo apt-get update
    ```

4. Installer MKL

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Par exemple :

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Déterminer l’emplacement de`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Par exemple :

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Ajoutez cet emplacement au chemin de la bibliothèque de chargement :

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Installer la bibliothèque avec`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
