---
title: Faire clignoter une LED
description: Découvrez comment faire clignoter une LED avec les bibliothèques .NET IoT.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 07a050c0655f9cae3d7f2b924c0dd07ac1c6c0b9
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588702"
---
# <a name="blink-an-led"></a>Faire clignoter une LED

Les codes confidentiels d’e/s à usage général (GPIO) peuvent être contrôlés individuellement. Cela est utile pour contrôler les LED, les relais et d’autres appareils avec état. Dans cette rubrique, vous allez utiliser .NET et les broches GPIO de Raspberry pi pour alimenter une LED et la faire clignoter à plusieurs reprises.

## <a name="prerequisites"></a>Prérequis

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- LED 5 mm
- résistance 330 Ω
- Platine d’expérimentation
- Câbles de liaison
- Tableau d’Raspberry pi GPIO (facultatif/recommandé)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a>Préparer le matériel

Utilisez les composants matériels pour créer le circuit comme illustré dans le diagramme suivant :

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="Diagramme Fritz montrant un circuit avec une LED et une résistance" lightbox="../media/rpi-led_bb.png":::

L’image ci-dessus décrit les connexions suivantes :

- GPIO 18 vers LED anode (plus long, Lead positif)
- Cathode à LED (plus petit, négatif) à la résistance 330 Ω (fin)
- résistance de 330 Ω (autre extrémité) au sol

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Créer l'application

Effectuez les étapes suivantes dans votre environnement de développement préféré :

1. Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md). Nommez-le *BlinkTutorial*.

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Remplacez le contenu du fichier *Program.cs* par le code suivant :

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    Dans le code précédent :

    - Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `GpioController` . La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.
    - Le pin GPIO 18 est ouvert pour la sortie
    - Une `while` boucle s’exécute indéfiniment. Chaque itération :
        1. Écrit une valeur dans le code confidentiel GPIO 18. Si `ledOn` a la valeur true, elle écrit `PinValue.High` (sur). Dans le cas contraire, il écrit `PinValue.Low` .
        1. Veillez à 1000 ms.
        1. Active ou désactive la valeur de `ledOn` .

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.

    ```bash
    ./BlinkTutorial
    ```

    La LED clignote et est activée chaque seconde.

1. Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.

Félicitations ! Vous avez utilisé GPIO pour faire clignoter une LED.

## <a name="get-the-source-code"></a>Obtenir le code source

La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [En savoir plus sur la lecture des conditions environnementales d’un capteur](../tutorials/temp-sensor.md)
