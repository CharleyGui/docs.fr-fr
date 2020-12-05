---
title: 'Démarrage rapide : utilisez .NET pour piloter une Raspberry pi Sense HAT'
description: Prise en main des bibliothèques IoT .NET en 5 minutes à l’aide d’un chapeau de sens, un tableau complémentaire pour Raspberry pi.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: quickstart
ms.prod: dotnet
ms.openlocfilehash: 2919db55304590f5557aa0cbda50cc4bd6640443
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739528"
---
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a>Démarrage rapide : utilisez .NET pour piloter une Raspberry pi Sense HAT

Raspberry pi [sens Hat](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> (**H** matérielle **a** ttached on **T** op) est un tableau complémentaire pour Raspberry pi. Le chapeau de détection est équipé d’une matrice LED de 8 × 8 RGB, d’une manette à cinq boutons et comprend les capteurs suivants :

- Gyroscope
- Accéléromètre
- Magnétomètre
- Température
- Pression barométrique
- Humidité

Ce guide de démarrage rapide utilise .NET pour récupérer les valeurs de capteur à partir de l’outil de détection de la manette de jeu, répondre à l’entrée de manette et piloter la matrice LED.

## <a name="prerequisites"></a>Prérequis

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- Sens de la détection

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a>Exécuter le démarrage rapide

Attachez le chapeau de sens à votre Raspberry pi. À partir d’une invite bash sur le Raspberry pi (local ou distant), exécutez la commande suivante :

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

La commande télécharge et exécute un script. Le script :

- Installe le kit de développement logiciel (SDK) .NET.
- Clone un référentiel GitHub qui comprend le projet de démarrage rapide de sens HAT.
- Génère le projet.
- Exécute le projet.

Observez la sortie de la console lorsque les données de capteur sont affichées. La matrice LED affiche un pixel jaune sur un champ de bleu. Le maintien de la manette dans n’importe quelle direction déplace le pixel jaune dans cette direction. Lorsque vous cliquez sur le bouton de la manette de jeu, l’arrière-plan passe du bleu au rouge.

## <a name="get-the-source-code"></a>Obtenir le code source

La source de ce guide de démarrage rapide est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart) <span class="docon docon-navigate-external x-hidden-focus"></span> .

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Apprenez à utiliser usage général entrée/sortie pour faire clignoter une LED](../tutorials/blink-led.md)
