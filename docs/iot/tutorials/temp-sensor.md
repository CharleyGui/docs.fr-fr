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
# <a name="read-environmental-conditions-from-a-sensor"></a><span data-ttu-id="09548-103">Lire les conditions environnementales d’un capteur</span><span class="sxs-lookup"><span data-stu-id="09548-103">Read environmental conditions from a sensor</span></span>

<span data-ttu-id="09548-104">L’un des scénarios les plus courants pour les appareils IoT est la détection des conditions environnementales.</span><span class="sxs-lookup"><span data-stu-id="09548-104">One of the most common scenarios for IoT devices is detection of environmental conditions.</span></span> <span data-ttu-id="09548-105">De nombreux capteurs sont disponibles pour surveiller la température, l’humidité, la pression barométrique, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="09548-105">A variety of sensors are available to monitor temperature, humidity, barometric pressure, and more.</span></span>

<span data-ttu-id="09548-106">Dans cette rubrique, vous allez utiliser .NET pour lire des conditions environnementales à partir d’un capteur.</span><span class="sxs-lookup"><span data-stu-id="09548-106">In this topic, you will use .NET to read environmental conditions from a sensor.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09548-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="09548-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="09548-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> répartition de l’humidité/de la pression barométrique/du capteur de température</span><span class="sxs-lookup"><span data-stu-id="09548-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> humidity/barometric pressure/temperature sensor breakout</span></span>
- <span data-ttu-id="09548-109">Câbles de liaison</span><span class="sxs-lookup"><span data-stu-id="09548-109">Jumper wires</span></span>
- <span data-ttu-id="09548-110">Pains (facultatif)</span><span class="sxs-lookup"><span data-stu-id="09548-110">Breadboard (optional)</span></span>
- <span data-ttu-id="09548-111">Tableau de Raspberry pi GPIO (facultatif)</span><span class="sxs-lookup"><span data-stu-id="09548-111">Raspberry Pi GPIO breakout board (optional)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> <span data-ttu-id="09548-112">Il existe de nombreux fabricants de ateliers BME280.</span><span class="sxs-lookup"><span data-stu-id="09548-112">There are many manufacturers of BME280 breakouts.</span></span> <span data-ttu-id="09548-113">La plupart des conceptions sont similaires, et le fabricant ne doit pas faire de différence avec les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="09548-113">Most designs are similar, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="09548-114">Ce didacticiel tente de tenir compte des variations.</span><span class="sxs-lookup"><span data-stu-id="09548-114">This tutorial attempts to account for variations.</span></span> <span data-ttu-id="09548-115">Assurez-vous que votre BME280 comprend une interface I2C (Inter-Integrated circuit).</span><span class="sxs-lookup"><span data-stu-id="09548-115">Ensure your BME280 breakout includes an Inter-Integrated Circuit (I2C) interface.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="09548-116">Préparer le matériel</span><span class="sxs-lookup"><span data-stu-id="09548-116">Prepare the hardware</span></span>

<span data-ttu-id="09548-117">Utilisez les composants matériels pour créer le circuit comme illustré dans le diagramme suivant :</span><span class="sxs-lookup"><span data-stu-id="09548-117">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Diagramme Fritz montrant la connexion de Raspberry pi à BME280." lightbox="../media/rpi-bmp280_i2c.png":::

<span data-ttu-id="09548-119">Voici les connexions de Raspberry pi à la branche BME280 :</span><span class="sxs-lookup"><span data-stu-id="09548-119">The following are the connections from the Raspberry Pi to the BME280 breakout:</span></span>

- <span data-ttu-id="09548-120">3.3 v vers VIN *ou* 3v3 (en rouge)</span><span class="sxs-lookup"><span data-stu-id="09548-120">3.3V to VIN *OR* 3V3 (shown in red)</span></span>
- <span data-ttu-id="09548-121">Sol vers GND (noir)</span><span class="sxs-lookup"><span data-stu-id="09548-121">Ground to GND (black)</span></span>
- <span data-ttu-id="09548-122">SDA (GPIO 2) à SDI *ou* SDA (bleu)</span><span class="sxs-lookup"><span data-stu-id="09548-122">SDA (GPIO 2) to SDI *OR* SDA (blue)</span></span>
- <span data-ttu-id="09548-123">SCL (GPIO 3) à SCK *ou* SCL (orange)</span><span class="sxs-lookup"><span data-stu-id="09548-123">SCL (GPIO 3) to SCK *OR* SCL (orange)</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="09548-124">Créer l'application</span><span class="sxs-lookup"><span data-stu-id="09548-124">Create the app</span></span>

<span data-ttu-id="09548-125">Effectuez les étapes suivantes dans votre environnement de développement préféré :</span><span class="sxs-lookup"><span data-stu-id="09548-125">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="09548-126">Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="09548-126">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="09548-127">Nommez-le *SensorTutorial*.</span><span class="sxs-lookup"><span data-stu-id="09548-127">Name it *SensorTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="09548-128">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="09548-128">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    <span data-ttu-id="09548-129">Dans le code précédent :</span><span class="sxs-lookup"><span data-stu-id="09548-129">In the preceding code:</span></span>

    - <span data-ttu-id="09548-130">`i2cSettings` est défini sur une nouvelle instance de `I2cConnectionSettings` .</span><span class="sxs-lookup"><span data-stu-id="09548-130">`i2cSettings` is set to a new instance of `I2cConnectionSettings`.</span></span> <span data-ttu-id="09548-131">Le constructeur affecte au `busId` paramètre la valeur 1 et au `deviceAddress` paramètre la valeur `Bme280.DefaultI2cAddress` .</span><span class="sxs-lookup"><span data-stu-id="09548-131">The constructor sets the `busId` parameter to 1 and the `deviceAddress` parameter to `Bme280.DefaultI2cAddress`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="09548-132">Certains fabricants de BME280 utilisent la valeur d’adresse secondaire.</span><span class="sxs-lookup"><span data-stu-id="09548-132">Some BME280 breakout manufacturers use the secondary address value.</span></span> <span data-ttu-id="09548-133">Pour ces appareils, utilisez `Bme280.SecondaryI2cAddress` .</span><span class="sxs-lookup"><span data-stu-id="09548-133">For those devices, use `Bme280.SecondaryI2cAddress`.</span></span>

    - <span data-ttu-id="09548-134">Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `I2cDevice` en appelant `I2cDevice.Create` et en passant `i2cSettings` .</span><span class="sxs-lookup"><span data-stu-id="09548-134">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in `i2cSettings`.</span></span> <span data-ttu-id="09548-135">Cela `I2cDevice` représente le bus I2C.</span><span class="sxs-lookup"><span data-stu-id="09548-135">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="09548-136">La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.</span><span class="sxs-lookup"><span data-stu-id="09548-136">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="09548-137">Une autre `using` déclaration crée une instance de `Bme280` pour représenter le capteur.</span><span class="sxs-lookup"><span data-stu-id="09548-137">Another `using` declaration creates an instance of `Bme280` to represent the sensor.</span></span> <span data-ttu-id="09548-138">`I2cDevice`Est passé dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="09548-138">The `I2cDevice` is passed in the constructor.</span></span>
    - <span data-ttu-id="09548-139">Le temps nécessaire pour que la puce prenne des mesures avec les paramètres actuels (par défaut) de la puce est récupéré en appelant `GetMeasurementDuration` .</span><span class="sxs-lookup"><span data-stu-id="09548-139">The time required for the chip to take measurements with the chip's current (default) settings is retrieved by calling `GetMeasurementDuration`.</span></span>
    - <span data-ttu-id="09548-140">Une `while` boucle s’exécute indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="09548-140">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="09548-141">Chaque itération :</span><span class="sxs-lookup"><span data-stu-id="09548-141">Each iteration:</span></span>
        1. <span data-ttu-id="09548-142">Efface la console.</span><span class="sxs-lookup"><span data-stu-id="09548-142">Clears the console.</span></span>
        1. <span data-ttu-id="09548-143">Définit le mode d’alimentation sur `Bmx280PowerMode.Forced` .</span><span class="sxs-lookup"><span data-stu-id="09548-143">Sets the power mode to `Bmx280PowerMode.Forced`.</span></span> <span data-ttu-id="09548-144">Cela force la puce à effectuer une mesure, à stocker les résultats, puis à se mettre en veille.</span><span class="sxs-lookup"><span data-stu-id="09548-144">This forces the chip to perform one measurement, store the results, and then sleep.</span></span>
        1. <span data-ttu-id="09548-145">Lit les valeurs de température, de pression, d’humidité et d’altitude.</span><span class="sxs-lookup"><span data-stu-id="09548-145">Reads the values for temperature, pressure, humidity, and altitude.</span></span>

            > [!NOTE]
            > <span data-ttu-id="09548-146">L’altitude est calculée par la liaison de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="09548-146">Altitude is calculated by the device binding.</span></span> <span data-ttu-id="09548-147">Cette surcharge de `TryReadAltitude` utilise la pression moyenne au niveau de la mer pour générer une estimation.</span><span class="sxs-lookup"><span data-stu-id="09548-147">This overload of `TryReadAltitude` uses mean sea level pressure to generate an estimate.</span></span>

        1. <span data-ttu-id="09548-148">Écrit les conditions environnementales actuelles sur la console.</span><span class="sxs-lookup"><span data-stu-id="09548-148">Writes the current environmental conditions to the console.</span></span>
        1. <span data-ttu-id="09548-149">Veillez à 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="09548-149">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="09548-150">Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="09548-150">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./SensorTutorial
    ```

    <span data-ttu-id="09548-151">Observez la sortie du capteur dans la console.</span><span class="sxs-lookup"><span data-stu-id="09548-151">Observe the sensor output in the console.</span></span>

1. <span data-ttu-id="09548-152">Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="09548-152">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="09548-153">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="09548-153">Congratulations!</span></span> <span data-ttu-id="09548-154">Vous avez utilisé I2C pour lire les valeurs à partir d’un capteur de pression/humidité/température barométrique !</span><span class="sxs-lookup"><span data-stu-id="09548-154">You've used I2C to read values from a temperature/humidity/barometric pressure sensor!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="09548-155">Obtenir le code source</span><span class="sxs-lookup"><span data-stu-id="09548-155">Get the source code</span></span>

<span data-ttu-id="09548-156">La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="09548-156">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="09548-157">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="09548-157">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="09548-158">Découvrez comment afficher du texte sur un écran LCD</span><span class="sxs-lookup"><span data-stu-id="09548-158">Learn how to display text on an LCD</span></span>](../tutorials/lcd-display.md)
