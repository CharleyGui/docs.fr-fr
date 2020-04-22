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
# <a name="install-extra-mlnet-dependencies"></a>Installer des dépendances ML.NET supplémentaires

Dans la plupart des cas, sur tous les systèmes d’exploitation, l’installation de ML.NET est aussi simple que le référencement du paquet NuGet approprié.

```bash
dotnet add package Microsoft.ML
```

Dans certains cas cependant, il existe des exigences d’installation supplémentaires, en particulier lorsque des composants indigènes sont nécessaires. Ce document décrit les exigences d’installation de ces cas. Les sections sont décomposées par le paquet NuGet spécifique `Microsoft.ML.*` qui a la dépendance supplémentaire.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft.ML.TimeSeries, Microsoft.ML.AutoML

Ces deux paquets ont `Microsoft.ML.MKL.Redist`une dépendance à `libiomp`, qui a une dépendance sur .

### <a name="windows"></a>Windows

Aucune étape d’installation supplémentaire n’est requise. La bibliothèque est installée lorsque le paquet NuGet est ajouté au projet.

### <a name="linux"></a>Linux

1. Installer la clé GPG pour le dépôt

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

2. Ajouter le dépôt APT pour MKL

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

5. Ajoutez cet emplacement au chemin de la bibliothèque de charge :

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Installer la bibliothèque avec`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
