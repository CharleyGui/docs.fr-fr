---
title: Comment installer la prise en charge des GPU dans le générateur de modèles
description: Découvrez comment installer la prise en charge des GPU dans le générateur de modèles
ms.date: 08/18/2020
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: ce629efa4c12a69f87196de35ebfe4331dc0800f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608567"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a>Comment installer la prise en charge des GPU dans le générateur de modèles

Découvrez comment installer les pilotes GPU pour utiliser votre GPU avec le générateur de modèles.

## <a name="prerequisites"></a>Prérequis

- Extension Visual Studio du générateur de modèles. L’extension est intégrée à Visual Studio à partir de la version 16.6.1.
- [Extension de prise en charge du GPU Visual Studio](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)pour le générateur de modèles.
- Au moins un GPU compatible CUDA. Pour obtenir la liste des GPU compatibles, consultez le [Guide NVIDIA](https://developer.nvidia.com/cuda-gpus).
- Compte de développeur NVIDIA. Si vous n’en avez pas, [créez un compte gratuit](https://developer.nvidia.com/developer-program).

## <a name="install-dependencies"></a>Installer des dépendances

1. Installez [CUDA v 10.0](https://developer.nvidia.com/cuda-10.0-download-archive). Veillez à installer CUDA v 10.0, et non une autre version plus récente. Plusieurs versions de CUDA ne peuvent pas être installées.
1. Installez [cuDNN v 7.6.4 pour CUDA 10,0](https://developer.nvidia.com/rdp/cudnn-download). Plusieurs versions de cuDNN ne peuvent pas être installées. Après avoir téléchargé le fichier zip cuDNN v 7.6.4 et l’avoir décompressé, copiez-le `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` dans `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` .

## <a name="troubleshooting"></a>Dépannage

**Comment faire savez-vous du GPU que je possède ?**

Suivez les instructions fournies :

1. Cliquer avec le bouton droit sur le Bureau
1. Si vous voyez « panneau de configuration NVIDIA » ou « affichage NVIDIA » dans la fenêtre contextuelle, vous disposez d’un GPU NVIDIA
1. Cliquez sur le « panneau de configuration NVIDIA » ou sur « Affichage NVIDIA » dans la fenêtre contextuelle.
1. Regarder « informations sur les cartes graphiques »
1. Vous verrez le nom de votre GPU NVIDIA

**Je ne vois pas le panneau de configuration NVIDIA (ou il ne parvient pas à s’ouvrir), mais je sais que j’ai un GPU NVIDIA.**

1. Ouvrez le Gestionnaire de périphériques.
1. Examiner les adaptateurs d’affichage
1. Installez le [pilote](https://www.nvidia.com/drivers) approprié pour votre GPU.
