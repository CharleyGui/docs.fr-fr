---
title: Afficher du texte sur un écran LCD
description: Découvrez comment afficher des caractères sur un écran à cristaux liquides avec les bibliothèques IoT .NET.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: d4c3e373207e23877903491871f4d09e11000c1a
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588689"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="display-text-on-an-lcd"></a><span data-ttu-id="9dbff-103">Afficher du texte sur un écran LCD</span><span class="sxs-lookup"><span data-stu-id="9dbff-103">Display text on an LCD</span></span>

<span data-ttu-id="9dbff-104">Les affichages de caractères LCD sont utiles pour afficher des informations sans avoir besoin d’un moniteur externe.</span><span class="sxs-lookup"><span data-stu-id="9dbff-104">LCD character displays are useful for displaying information without the need for an external monitor.</span></span> <span data-ttu-id="9dbff-105">Les affichages de caractères LCD courants peuvent être connectés directement aux broches GPIO, mais une telle approche nécessite l’utilisation d’un maximum de 10 broches GPIO.</span><span class="sxs-lookup"><span data-stu-id="9dbff-105">Common LCD character displays can be connected directly to the GPIO pins, but such an approach requires the use of up to 10 GPIO pins.</span></span> <span data-ttu-id="9dbff-106">Pour les scénarios qui nécessitent une connexion à une combinaison d’appareils, le fait de ne pas voter autant de l’en-tête GPIO pour un affichage de caractères est souvent peu pratique.</span><span class="sxs-lookup"><span data-stu-id="9dbff-106">For scenarios that require connecting to a combination of devices, devoting so much of the GPIO header to a character display is often impractical.</span></span>

<span data-ttu-id="9dbff-107">De nombreux fabricants vendent des affichages de caractères 20x4 LCD avec un Expander GPIO intégré.</span><span class="sxs-lookup"><span data-stu-id="9dbff-107">Many manufacturers sell 20x4 LCD character displays with an integrated GPIO expander.</span></span> <span data-ttu-id="9dbff-108">L’affichage des caractères se connecte directement à l’expandeur GPIO, qui se connecte ensuite au Raspberry pi via le protocole série I2C (Inter-Integrated circuit).</span><span class="sxs-lookup"><span data-stu-id="9dbff-108">The character display connects directly to the GPIO expander, which then connects to the Raspberry Pi via the Inter-Integrated Circuit (I2C) serial protocol.</span></span>

<span data-ttu-id="9dbff-109">Dans cette rubrique, vous allez utiliser .NET pour afficher du texte sur un écran LCD à l’aide d’un Expander GPIO I2C.</span><span class="sxs-lookup"><span data-stu-id="9dbff-109">In this topic, you will use .NET to display text on an LCD character display using an I2C GPIO expander.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9dbff-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="9dbff-110">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="9dbff-111">[affichage des caractères de l’écran LCD 20x4 avec l’interface I2C](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="9dbff-111">[20x4 LCD Character Display with I2C interface](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="9dbff-112">Câbles de liaison</span><span class="sxs-lookup"><span data-stu-id="9dbff-112">Jumper wires</span></span>
- <span data-ttu-id="9dbff-113">Pains (facultatif/recommandé)</span><span class="sxs-lookup"><span data-stu-id="9dbff-113">Breadboard (optional/recommended)</span></span>
- <span data-ttu-id="9dbff-114">Tableau d’Raspberry pi GPIO (facultatif/recommandé)</span><span class="sxs-lookup"><span data-stu-id="9dbff-114">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> <span data-ttu-id="9dbff-115">Il existe de nombreux fabricants d’affichages de caractères LCD.</span><span class="sxs-lookup"><span data-stu-id="9dbff-115">There are many manufacturers of LCD character displays.</span></span> <span data-ttu-id="9dbff-116">La plupart des conceptions sont identiques et le fabricant ne doit pas faire de différence avec les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9dbff-116">Most designs are identical, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="9dbff-117">Pour référence, ce didacticiel a été développé avec le [LCD2004](https://www.sunfounder.com/lcd2004-module.html) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="9dbff-117">For reference, this tutorial was developed with the [SunFounder LCD2004](https://www.sunfounder.com/lcd2004-module.html) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="9dbff-118">Préparer le matériel</span><span class="sxs-lookup"><span data-stu-id="9dbff-118">Prepare the hardware</span></span>

<span data-ttu-id="9dbff-119">Utilisez les câbles de cavalier pour connecter les quatre broches de l’expandeur GPIO I2C à Raspberry pi comme suit :</span><span class="sxs-lookup"><span data-stu-id="9dbff-119">Use jumper wires to connect the four pins on the I2C GPIO expander to the Raspberry Pi as follows:</span></span>

- <span data-ttu-id="9dbff-120">Terre jusqu’au sol</span><span class="sxs-lookup"><span data-stu-id="9dbff-120">GND to ground</span></span>
- <span data-ttu-id="9dbff-121">VCC à 5 v</span><span class="sxs-lookup"><span data-stu-id="9dbff-121">VCC to 5V</span></span>
- <span data-ttu-id="9dbff-122">SDA à SDA (GPIO 2)</span><span class="sxs-lookup"><span data-stu-id="9dbff-122">SDA to SDA (GPIO 2)</span></span>
- <span data-ttu-id="9dbff-123">SCL vers SCL (GPIO 3)</span><span class="sxs-lookup"><span data-stu-id="9dbff-123">SCL to SCL (GPIO 3)</span></span>

<span data-ttu-id="9dbff-124">Reportez-vous aux figures suivantes en fonction des besoins :</span><span class="sxs-lookup"><span data-stu-id="9dbff-124">Refer to the following figures as needed:</span></span>

| <span data-ttu-id="9dbff-125">Interface I2C (arrière de l’affichage)</span><span class="sxs-lookup"><span data-stu-id="9dbff-125">I2C interface (back of display)</span></span> | <span data-ttu-id="9dbff-126">Raspberry pi GPIO</span><span class="sxs-lookup"><span data-stu-id="9dbff-126">Raspberry Pi GPIO</span></span> |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="Image de l’arrière de l’affichage de caractères affichant l’expandeur GPIO I2C." lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Diagramme montrant le pinout de l’en-tête Raspberry pi GPIO. Image Raspberry pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="9dbff-129">[Image Raspberry pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="9dbff-129">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="9dbff-130">Créer l'application</span><span class="sxs-lookup"><span data-stu-id="9dbff-130">Create the app</span></span>

<span data-ttu-id="9dbff-131">Effectuez les étapes suivantes dans votre environnement de développement préféré :</span><span class="sxs-lookup"><span data-stu-id="9dbff-131">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="9dbff-132">Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9dbff-132">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="9dbff-133">Nommez-le *LcdTutorial*.</span><span class="sxs-lookup"><span data-stu-id="9dbff-133">Name it *LcdTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="9dbff-134">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="9dbff-134">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    <span data-ttu-id="9dbff-135">Dans le code précédent :</span><span class="sxs-lookup"><span data-stu-id="9dbff-135">In the preceding code:</span></span>

    - <span data-ttu-id="9dbff-136">Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `I2cDevice` en appelant `I2cDevice.Create` et en passant un nouveau `I2cConnectionSettings` avec les `busId` `deviceAddress` paramètres et.</span><span class="sxs-lookup"><span data-stu-id="9dbff-136">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in a new `I2cConnectionSettings` with the `busId` and `deviceAddress` parameters.</span></span> <span data-ttu-id="9dbff-137">Cela `I2cDevice` représente le bus I2C.</span><span class="sxs-lookup"><span data-stu-id="9dbff-137">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="9dbff-138">La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.</span><span class="sxs-lookup"><span data-stu-id="9dbff-138">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>

        > [!WARNING]
        > <span data-ttu-id="9dbff-139">L’adresse de l’appareil pour l’expandeur GPIO dépend de la puce utilisée par le fabricant.</span><span class="sxs-lookup"><span data-stu-id="9dbff-139">The device address for the GPIO expander depends on the chip used by the manufacturer.</span></span> <span data-ttu-id="9dbff-140">Les expandeurs GPIO équipés d’un PCF8574 utilisent l’adresse `0x27` , tandis que ceux utilisant des processeurs PCF8574A utilisent `0x3F` .</span><span class="sxs-lookup"><span data-stu-id="9dbff-140">GPIO expanders equipped with a PCF8574 use the address `0x27`, while those using PCF8574A chips use `0x3F`.</span></span> <span data-ttu-id="9dbff-141">Consultez la documentation de votre LCD.</span><span class="sxs-lookup"><span data-stu-id="9dbff-141">Consult your LCD's documentation.</span></span>

    - <span data-ttu-id="9dbff-142">Une autre `using` déclaration crée une instance de `Pcf8574` et passe le `I2cDevice` dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="9dbff-142">Another `using` declaration creates an instance of `Pcf8574` and passes the `I2cDevice` into the constructor.</span></span> <span data-ttu-id="9dbff-143">Cette instance représente l’Expander GPIO.</span><span class="sxs-lookup"><span data-stu-id="9dbff-143">This instance represents the GPIO expander.</span></span>
    - <span data-ttu-id="9dbff-144">Une autre `using` déclaration crée une instance de `Lcd2004` pour représenter l’affichage.</span><span class="sxs-lookup"><span data-stu-id="9dbff-144">Another `using` declaration creates an instance of `Lcd2004` to represent the display.</span></span> <span data-ttu-id="9dbff-145">Plusieurs paramètres sont passés au constructeur décrivant les paramètres à utiliser pour communiquer avec l’Expander GPIO.</span><span class="sxs-lookup"><span data-stu-id="9dbff-145">Several parameters are passed to the constructor describing the settings to use to communicate with the GPIO expander.</span></span> <span data-ttu-id="9dbff-146">L’Expander GPIO est passé en tant que `controller` paramètre.</span><span class="sxs-lookup"><span data-stu-id="9dbff-146">The GPIO expander is passed as the `controller` parameter.</span></span>
    - <span data-ttu-id="9dbff-147">Une `while` boucle s’exécute indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="9dbff-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="9dbff-148">Chaque itération :</span><span class="sxs-lookup"><span data-stu-id="9dbff-148">Each iteration:</span></span>
        1. <span data-ttu-id="9dbff-149">Efface l’affichage.</span><span class="sxs-lookup"><span data-stu-id="9dbff-149">Clears the display.</span></span>
        1. <span data-ttu-id="9dbff-150">Définit la position du curseur à la première position sur la ligne active.</span><span class="sxs-lookup"><span data-stu-id="9dbff-150">Sets the cursor position to the first position on the current line.</span></span>
        1. <span data-ttu-id="9dbff-151">Écrit l’heure actuelle dans l’affichage à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="9dbff-151">Writes the current time to the display at the current cursor position.</span></span>
        1. <span data-ttu-id="9dbff-152">Itère le compteur de ligne actuel.</span><span class="sxs-lookup"><span data-stu-id="9dbff-152">Iterates the current line counter.</span></span>
        1. <span data-ttu-id="9dbff-153">Veillez à 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="9dbff-153">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="9dbff-154">Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="9dbff-154">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./LcdTutorial
    ```

    <span data-ttu-id="9dbff-155">Observez l’affichage des caractères de l’écran LCD lorsque l’heure actuelle s’affiche sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="9dbff-155">Observe the LCD character display as the current time displays on each line.</span></span>

    > [!TIP]
    > <span data-ttu-id="9dbff-156">Si l’affichage est allumé mais que vous ne voyez pas de texte, essayez de régler le contraste à l’arrière de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="9dbff-156">If the display is lit but you don't see any text, try adjusting the contrast dial on the back of the display.</span></span>

1. <span data-ttu-id="9dbff-157">Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9dbff-157">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="9dbff-158">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="9dbff-158">Congratulations!</span></span> <span data-ttu-id="9dbff-159">Vous avez affiché du texte sur un écran LCD à l’aide d’un I2C et d’un Expander GPIO !</span><span class="sxs-lookup"><span data-stu-id="9dbff-159">You've displayed text on an LCD using a I2C and a GPIO expander!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="9dbff-160">Obtenir le code source</span><span class="sxs-lookup"><span data-stu-id="9dbff-160">Get the source code</span></span>

<span data-ttu-id="9dbff-161">La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="9dbff-161">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9dbff-162">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9dbff-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9dbff-163">Apprenez à utiliser usage général entrée/sortie pour faire clignoter une LED</span><span class="sxs-lookup"><span data-stu-id="9dbff-163">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
