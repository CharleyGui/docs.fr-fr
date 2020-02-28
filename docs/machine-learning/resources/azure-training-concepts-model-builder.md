---
title: Ressources de formation Azure sur le générateur de modèles
description: Guide des ressources pour Azure Machine Learning
ms.topic: reference
ms.date: 02/25/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a0a75283cdc7402c67b6bfb0799189fa34cd39a7
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77675204"
---
# <a name="model-builder-azure-training-resources"></a>Ressources de formation Azure sur le générateur de modèles

Vous trouverez ci-dessous un guide pour en savoir plus sur les ressources utilisées pour l’apprentissage des modèles dans Azure avec le générateur de modèles.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Qu’est-ce qu’une expérience Azure Machine Learning ?

Une expérience Azure Machine Learning est une ressource qui doit être créée avant l’exécution de la formation du générateur de modèles sur Azure.

L’expérimentation encapsule la configuration et les résultats d’une ou de plusieurs Machine Learning exécutions d’apprentissage. Les expériences appartiennent à un espace de travail spécifique. La première fois qu’une expérience est créée, son nom est enregistré dans l’espace de travail. Toutes les exécutions suivantes : si le même nom d’expérimentation est utilisé, sont enregistrés dans le cadre de la même expérience. Dans le cas contraire, une nouvelle expérience est créée.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Qu’est-ce qu’un espace de travail Azure Machine Learning ?

Un espace de travail est une ressource Azure Machine Learning qui fournit un emplacement central pour toutes les ressources Azure Machine Learning et les artefacts créés dans le cadre de l’exécution de la formation.

Pour créer un espace de travail Azure Machine Learning, les conditions suivantes sont requises :

- Nom : un nom pour votre espace de travail entre 3-33 caractères. Les noms peuvent uniquement contenir des caractères alphanumériques et des traits d’Union. 
- Région : emplacement géographique du centre de données où votre espace de travail et vos ressources sont déployés. Il est recommandé de choisir un emplacement proche de l’emplacement où se trouvent vos clients ou vous-même.
- Groupe de ressources : conteneur qui contient toutes les ressources associées d’une solution Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>Qu’est-ce qu’un calcul Azure Machine Learning ?

Une Azure Machine Learning Compute est une machine virtuelle Linux basée sur le Cloud, utilisée pour l’apprentissage.

Pour créer un espace de travail Azure Machine Learning, les conditions suivantes sont requises :

- Nom : un nom pour votre espace de travail entre 2-16 caractères. Les noms peuvent uniquement contenir des caractères alphanumériques et des traits d’Union.
- Taille de calcul

    Le générateur de modèles peut utiliser l’un des types de calcul optimisés GPU suivants :

    | Size | Processeurs virtuels | Mémoire : Gio | Stockage temporaire (SSD) en Gio | GPU | Mémoire GPU : Gio | Disques de données max. | Nombre max de cartes réseau |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Pour plus d’informations sur les types de calcul optimisés GPU, consultez la documentation sur les [machines virtuelles Linux de série NC](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) .

## <a name="training"></a>Entrainement

La formation sur Azure est disponible uniquement pour le scénario de classification d’image du générateur de modèles. L’algorithme utilisé pour l’apprentissage de ces modèles est un réseau neuronal profond basé sur l’architecture ResNet50. Pendant la formation, les ressources nécessaires pour former le modèle sont approvisionnées et le modèle est formé. Ce processus prend quelques minutes et la durée peut varier en fonction de la taille du calcul sélectionné et de la quantité de données. Vous pouvez suivre la progression de vos exécutions en sélectionnant le lien « analyser l’exécution actuelle en Portail Azure » dans Visual Studio.

## <a name="results"></a>Résultats

Une fois l’apprentissage terminé, deux projets sont ajoutés à votre solution avec les suffixes suivants :

- *ConsoleApp*: application C# console .net core qui fournit un code de démarrage pour créer le pipeline de prédiction et effectuer des prédictions.
- *Modèle*: application C# .NET standard qui contient les modèles de données qui définissent le schéma des données de modèle d’entrée et de sortie, ainsi que les ressources suivantes :

  - bestModel. Onnx : version sérialisée du modèle au format ONNX (Open neuronal Network Exchange). ONNX est un format Open source pour les modèles AI qui prend en charge l’interopérabilité entre les infrastructures telles que ML.NET, PyTorch et TensorFlow.
  - bestModelMap. JSON : liste des catégories utilisées lors de l’élaboration de prédictions pour mapper la sortie du modèle à une catégorie de texte.
  - MLModel. zip : version sérialisée du pipeline de prédiction ML.NET qui utilise la version sérialisée du modèle *bestModel. Onnx* pour effectuer des prédictions et mapper des sorties à l’aide du fichier `bestModelMap.json`.
  
## <a name="troubleshooting"></a>Dépannage

### <a name="cannot-create-compute"></a>Impossible de créer le calcul

Si une erreur se produit lors de la création de Azure Machine Learning calcul, il se peut que la ressource de calcul existe toujours, dans un état d’erreur. Si vous essayez de recréer la ressource de calcul portant le même nom, l’opération échoue. Pour corriger cette erreur, vous avez le choix entre plusieurs possibilités :

* Créer le calcul avec un nom différent
* Accéder au Portail Azure et supprimer la ressource de calcul d’origine
