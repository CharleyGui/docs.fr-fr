---
title: Lire les conditions environnementales d’un capteur
description: Découvrez comment lire les termperature, la pression barométrique et l’humidité avec les bibliothèques .NET IoT.
author: camsoper
ms.author: casoper
ms.date: 11/14/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 1270e7629e9afc12b1d76d260d4b8b51428f1040
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588707"
---
# <a name="read-environmental-conditions-from-a-sensor"></a>Lire les conditions environnementales d’un capteur

L’un des scénarios les plus courants pour les appareils IoT est la détection des conditions environnementales. De nombreux capteurs sont disponibles pour surveiller la température, l’humidité, la pression barométrique, et bien plus encore.

Dans cette rubrique, vous allez utiliser .NET pour lire des conditions environnementales à partir d’un capteur.

## <a name="prerequisites"></a>Prérequis

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> répartition de l’humidité/de la pression barométrique/du capteur de température
- Câbles de liaison
- Pains (facultatif)
- Tableau de Raspberry pi GPIO (facultatif)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> Il existe de nombreux fabricants de ateliers BME280. La plupart des conceptions sont similaires, et le fabricant ne doit pas faire de différence avec les fonctionnalités. Ce didacticiel tente de tenir compte des variations. Assurez-vous que votre BME280 comprend une interface I2C (Inter-Integrated circuit).

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>Préparer le matériel

Utilisez les composants matériels pour créer le circuit comme illustré dans le diagramme suivant :

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Diagramme Fritz montrant la connexion de Raspberry pi à BME280." lightbox="../media/rpi-bmp280_i2c.png":::

Voici les connexions de Raspberry pi à la branche BME280 :

- 3.3 v vers VIN *ou* 3v3 (en rouge)
- Sol vers GND (noir)
- SDA (GPIO 2) à SDI *ou* SDA (bleu)
- SCL (GPIO 3) à SCK *ou* SCL (orange)

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Créer l'application

Effectuez les étapes suivantes dans votre environnement de développement préféré :

1. Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md). Nommez-le *SensorTutorial*.

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Remplacez le contenu du fichier *Program.cs* par le code suivant :

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    Dans le code précédent :

    - `i2cSettings` est défini sur une nouvelle instance de `I2cConnectionSettings` . Le constructeur affecte au `busId` paramètre la valeur 1 et au `deviceAddress` paramètre la valeur `Bme280.DefaultI2cAddress` .

        > [!IMPORTANT]
        > Certains fabricants de BME280 utilisent la valeur d’adresse secondaire. Pour ces appareils, utilisez `Bme280.SecondaryI2cAddress` .

    - Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `I2cDevice` en appelant `I2cDevice.Create` et en passant `i2cSettings` . Cela `I2cDevice` représente le bus I2C. La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.
    - Une autre `using` déclaration crée une instance de `Bme280` pour représenter le capteur. `I2cDevice`Est passé dans le constructeur.
    - Le temps nécessaire pour que la puce prenne des mesures avec les paramètres actuels (par défaut) de la puce est récupéré en appelant `GetMeasurementDuration` .
    - Une `while` boucle s’exécute indéfiniment. Chaque itération :
        1. Efface la console.
        1. Définit le mode d’alimentation sur `Bmx280PowerMode.Forced` . Cela force la puce à effectuer une mesure, à stocker les résultats, puis à se mettre en veille.
        1. Lit les valeurs de température, de pression, d’humidité et d’altitude.

            > [!NOTE]
            > L’altitude est calculée par la liaison de l’appareil. Cette surcharge de `TryReadAltitude` utilise la pression moyenne au niveau de la mer pour générer une estimation.

        1. Écrit les conditions environnementales actuelles sur la console.
        1. Veillez à 1000 ms.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.

    ```bash
    ./SensorTutorial
    ```

    Observez la sortie du capteur dans la console.

1. Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.

Félicitations ! Vous avez utilisé I2C pour lire les valeurs à partir d’un capteur de pression/humidité/température barométrique !

## <a name="get-the-source-code"></a>Obtenir le code source

La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Découvrez comment afficher du texte sur un écran LCD](../tutorials/lcd-display.md)
