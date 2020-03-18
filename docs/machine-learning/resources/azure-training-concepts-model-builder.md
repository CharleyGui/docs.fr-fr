---
title: Modèle Builder Azure Training Resources
description: Un guide des ressources pour Azure Machine Learning
ms.topic: reference
ms.date: 02/27/2020
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: a19e13955d0eaea344109eb817f3a3959c3dd883
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185820"
---
# <a name="model-builder-azure-training-resources"></a>Modèle Builder Azure Training Resources

Ce qui suit est un guide pour vous aider à en apprendre davantage sur les ressources utilisées pour former des modèles en Azure avec Model Builder.

## <a name="what-is-an-azure-machine-learning-experiment"></a>Qu’est-ce qu’une expérience Azure Machine Learning ?

Une expérience Azure Machine Learning est une ressource qui doit être créée avant d’exécuter la formation Model Builder sur Azure.

L’expérience résume la configuration et les résultats d’une ou de plusieurs courses de formation à l’apprentissage automatique. Les expériences appartiennent à un espace de travail spécifique. La première fois qu’une expérience est créée, son nom est enregistré dans l’espace de travail. Toute course ultérieure - si le même nom d’expérience est utilisé - sont enregistrées dans le cadre de la même expérience. Sinon, une nouvelle expérience est créée.

## <a name="what-is-an-azure-machine-learning-workspace"></a>Qu’est-ce qu’un espace de travail Azure Machine Learning ?

Un espace de travail est une ressource Azure Machine Learning qui fournit un lieu central pour toutes les ressources azuréennes d’apprentissage automatique et des artefacts créés dans le cadre de la course de formation.

Pour créer un espace de travail Azure Machine Learning, voici :

- Nom: Un nom pour votre espace de travail entre 3-33 caractères. Les noms ne peuvent contenir que des caractères alphanumériques et des traits d’union.
- Région : L’emplacement géographique du centre de données où votre espace de travail et vos ressources sont déployés. Il est recommandé de choisir un endroit près de l’endroit où vous ou vos clients êtes.
- Groupe de ressources : Un conteneur qui contient toutes les ressources connexes pour une solution Azure.

## <a name="what-is-an-azure-machine-learning-compute"></a>Qu’est-ce qu’un calcul Azure Machine Learning ?

Une calcul Azure Machine Learning est un Linux VM basé sur le cloud utilisé pour la formation.

Pour créer un espace de travail Azure Machine Learning, voici :

- Nom: Un nom pour votre espace de travail entre 2-16 caractères. Les noms ne peuvent contenir que des caractères alphanumériques et des traits d’union.
- Taille de calcul

    Model Builder peut utiliser l’un des types de calcul optimisés par GPU suivants :

    | Size | Processeurs virtuels | Mémoire : Gio | Stockage temporaire (SSD) en Gio | GPU | Mémoire GPU : Gio | Disques de données max. | Nombre max de cartes réseau |
    |---|---|---|---|---|---|---|---|
    | Standard_NC12   | 12 | 112 | 680  | 2 | 24 | 48 | 2 |
    | Standard_NC24   | 24 | 224 | 1440 | 4 | 48 | 64 | 4 |

    Visitez la [documentation Linux VM de la série NC](https://docs.microsoft.com/azure/virtual-machines/nc-series?toc=/azure/virtual-machines/linux/toc.json&bc=/azure/virtual-machines/linux/breadcrumb/toc.json) pour plus de détails sur les types de calcul optimisés GPU.

## <a name="training"></a>Entrainement

La formation sur Azure n’est disponible que pour le scénario de classification d’image De Model Builder. L’algorithme utilisé pour former ces modèles est un réseau neuronal profond basé sur l’architecture ResNet50. Le processus de formation prend un certain temps et le temps peut varier en fonction de la taille du calcul sélectionné ainsi que de la quantité de données. La première fois qu’un modèle est formé, vous pouvez vous attendre à un temps de formation un peu plus long parce que les ressources doivent être mises à disposition. Vous pouvez suivre l’évolution de vos courses en sélectionnant le lien "Monitor current run in Azure portal" dans Visual Studio.

## <a name="results"></a>Résultats

Une fois la formation terminée, deux projets sont ajoutés à votre solution avec les suffixes suivants :

- *ConsoleApp*: Une application de console C .NET Core qui fournit du code de démarrage pour construire le pipeline de prédiction et faire des prédictions.
- *Modèle*: Application standard C.NET qui contient les modèles de données qui définissent le schéma des données des modèles d’entrée et de production ainsi que les actifs suivants :

  - bestModel.onnx: Une version sérialisée du modèle dans le format Open Neural Network Exchange (ONNX). ONNX est un format open source pour les modèles AI qui prend en charge l’interopérabilité entre des cadres comme ML.NET, PyTorch et TensorFlow.
  - bestModelMap.json: Une liste de catégories utilisées lors de la prédiction pour cartographier la sortie du modèle à une catégorie de texte.
  - MLModel.zip: Une version sérialisée du pipeline de prédiction ML.NET qui utilise la version sérialisée du modèle `bestModelMap.json` *bestModel.onnx* pour faire des prédictions et des cartes sorties à l’aide du fichier.

## <a name="use-the-machine-learning-model"></a>Utiliser le modèle d’apprentissage automatique

Le `ModelInput` `ModelOutput` projet et les classes du projet *Modèle* définissent le schéma de l’entrée et de la sortie attendues du modèle respectivement.

Dans un scénario de `ModelInput` classification d’image, le contient deux colonnes :

- `ImageSource`: Le chemin de chaîne de l’emplacement de l’image.
- `Label`: La catégorie réelle à laquelle appartient l’image. `Label`n’est utilisé que comme entrée lors de la formation et n’a pas besoin d’être fourni lors de la prédiction.

Le `ModelOutput` contient deux colonnes:

- `Prediction`: La catégorie prévue de l’image.
- `Score`: La liste des probabilités pour toutes les `Prediction`catégories (la plus élevée appartient à la ).

## <a name="troubleshooting"></a>Dépannage

### <a name="cannot-create-compute"></a>Impossible de créer des calculs

Si une erreur se produit lors de la création de calcul d’Azure Machine Learning, la ressource de calcul peut encore exister, dans un état erroné. Si vous essayez de recréer la ressource de calcul du même nom, l’opération échoue. Pour corriger cette erreur, vous avez le choix entre plusieurs possibilités :

- Créez le nouveau calcul avec un nom différent
- Rendez-vous sur le portail Azure et supprimez la ressource de calcul d’origine
