---
title: Lire les valeurs d’un convertisseur analogique-numérique
description: Découvrez comment lire les valeurs de tension variables à l’aide d’un convertisseur analogique-numérique.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: eda6d8980d256c8063f2bfe1e051b0cb90b587ad
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96588696"
---
<!--markdownlint-disable DOCSMD011 -->
# <a name="read-values-from-an-analog-to-digital-converter"></a><span data-ttu-id="3ddf9-103">Lire les valeurs d’un convertisseur analogique-numérique</span><span class="sxs-lookup"><span data-stu-id="3ddf9-103">Read values from an analog-to-digital converter</span></span>

<span data-ttu-id="3ddf9-104">Un convertisseur analogique-numérique (ADC) est un appareil qui peut lire une valeur de tension d’entrée analogique et la convertir en valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-104">An analog-to-digital converter (ADC) is a device that can read an analog input voltage value and convert it into a digital value.</span></span> <span data-ttu-id="3ddf9-105">L’ADCs est utilisé pour lire des valeurs à partir de thermistances, de potentiomètres et d’autres appareils qui modifient la résistance en fonction de certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-105">ADCs are used for reading values from thermistors, potentiometers, and other devices that change resistance based on certain conditions.</span></span>

<span data-ttu-id="3ddf9-106">Dans cette rubrique, vous allez utiliser .NET pour lire des valeurs à partir d’un connecteur ADC en modulant la tension d’entrée avec un potentiomètre.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-106">In this topic, you will use .NET to read values from an ADC as you modulate the input voltage with a potentiometer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3ddf9-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="3ddf9-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="3ddf9-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> convertisseur analogique-numérique</span><span class="sxs-lookup"><span data-stu-id="3ddf9-108">[MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> analog-to-digital converter</span></span>
- <span data-ttu-id="3ddf9-109">Potentiomètre à trois broches</span><span class="sxs-lookup"><span data-stu-id="3ddf9-109">Three-pin potentiometer</span></span>
- <span data-ttu-id="3ddf9-110">Platine d’expérimentation</span><span class="sxs-lookup"><span data-stu-id="3ddf9-110">Breadboard</span></span>
- <span data-ttu-id="3ddf9-111">Câbles de liaison</span><span class="sxs-lookup"><span data-stu-id="3ddf9-111">Jumper wires</span></span>
- <span data-ttu-id="3ddf9-112">Tableau d’Raspberry pi GPIO (facultatif/recommandé)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="3ddf9-113">Préparer le matériel</span><span class="sxs-lookup"><span data-stu-id="3ddf9-113">Prepare the hardware</span></span>

<span data-ttu-id="3ddf9-114">Utilisez les composants matériels pour créer le circuit comme illustré dans le diagramme suivant :</span><span class="sxs-lookup"><span data-stu-id="3ddf9-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="Diagramme Fritz montrant un circuit avec un MCP3008 ADC et un potentiomètre" lightbox="../media/rpi-trimpot_spi.png":::

<span data-ttu-id="3ddf9-116">MCP3008 utilise l’interface de périphérique série (SPI) pour communiquer.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-116">The MCP3008 uses Serial Peripheral Interface (SPI) to communicate.</span></span> <span data-ttu-id="3ddf9-117">Voici les connexions entre le MCP3008 et le Raspberry pi et potentiomètre :</span><span class="sxs-lookup"><span data-stu-id="3ddf9-117">The following are the connections from the MCP3008 to the Raspberry Pi and potentiometer:</span></span>

- <span data-ttu-id="3ddf9-118">V<sub>JJ</sub> à 3.3 v (affichée en rouge)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-118">V<sub>DD</sub> to 3.3V (shown in red)</span></span>
- <span data-ttu-id="3ddf9-119">V<sub>ref</sub> à 3.3 v (rouge)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-119">V<sub>REF</sub> to 3.3V (red)</span></span>
- <span data-ttu-id="3ddf9-120">AGND vers le sol (noir)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-120">AGND to ground (black)</span></span>
- <span data-ttu-id="3ddf9-121">CLK à SCLK (orange)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-121">CLK to SCLK (orange)</span></span>
- <span data-ttu-id="3ddf9-122">D<sub>vers</sub> miso (orange)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-122">D<sub>OUT</sub> to MISO (orange)</span></span>
- <span data-ttu-id="3ddf9-123">D<sub>dans</sub> Mosi (orange)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-123">D<sub>IN</sub> to MOSI (orange)</span></span>
- <span data-ttu-id="3ddf9-124">CS/SHDN vers CE0 (vert)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-124">CS/SHDN to CE0 (green)</span></span>
- <span data-ttu-id="3ddf9-125">DGND vers le sol (noir)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-125">DGND to ground (black)</span></span>
- <span data-ttu-id="3ddf9-126">CH0 à la variable (au milieu) broche sur le potentiomètre (jaune)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-126">CH0 to variable (middle) pin on potentiometer (yellow)</span></span>

<span data-ttu-id="3ddf9-127">Fournissez 3.3 V et sol aux broches extérieures sur le potentiomètre.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-127">Supply 3.3V and ground to the outer pins on the potentiometer.</span></span> <span data-ttu-id="3ddf9-128">L’ordre n’est pas important.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-128">Order is unimportant.</span></span>

<span data-ttu-id="3ddf9-129">Reportez-vous aux diagrammes pinout suivants en fonction des besoins :</span><span class="sxs-lookup"><span data-stu-id="3ddf9-129">Refer to the following pinout diagrams as needed:</span></span>

| <span data-ttu-id="3ddf9-130">MCP3008</span><span class="sxs-lookup"><span data-stu-id="3ddf9-130">MCP3008</span></span>  | <span data-ttu-id="3ddf9-131">Raspberry pi GPIO</span><span class="sxs-lookup"><span data-stu-id="3ddf9-131">Raspberry Pi GPIO</span></span> |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="Diagramme montrant le pinout du MCP3008" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Diagramme montrant le pinout de l’en-tête Raspberry pi GPIO. Image Raspberry pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br /><span data-ttu-id="3ddf9-134">[Image Raspberry pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span><span class="sxs-lookup"><span data-stu-id="3ddf9-134">[Image courtesy Raspberry Pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).</span></span>
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="3ddf9-135">Créer l'application</span><span class="sxs-lookup"><span data-stu-id="3ddf9-135">Create the app</span></span>

<span data-ttu-id="3ddf9-136">Effectuez les étapes suivantes dans votre environnement de développement préféré :</span><span class="sxs-lookup"><span data-stu-id="3ddf9-136">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="3ddf9-137">Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3ddf9-137">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="3ddf9-138">Nommez-le *AdcTutorial*.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-138">Name it *AdcTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="3ddf9-139">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3ddf9-139">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    <span data-ttu-id="3ddf9-140">Dans le code précédent :</span><span class="sxs-lookup"><span data-stu-id="3ddf9-140">In the preceding code:</span></span>

    - <span data-ttu-id="3ddf9-141">`hardwareSpiSettings` est défini sur une nouvelle instance de `SpiConnectionSettings` .</span><span class="sxs-lookup"><span data-stu-id="3ddf9-141">`hardwareSpiSettings` is set to a new instance of `SpiConnectionSettings`.</span></span> <span data-ttu-id="3ddf9-142">Le constructeur affecte la valeur `busId` 0 au paramètre et la valeur `chipSelectLine` 0 au paramètre.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-142">The constructor sets the `busId` parameter to 0 and the `chipSelectLine` parameter to 0.</span></span>
    - <span data-ttu-id="3ddf9-143">Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `SpiDevice` en appelant `SpiDevice.Create` et en passant `hardwareSpiSettings` .</span><span class="sxs-lookup"><span data-stu-id="3ddf9-143">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `SpiDevice` by calling `SpiDevice.Create` and passing in `hardwareSpiSettings`.</span></span> <span data-ttu-id="3ddf9-144">Cela `SpiDevice` représente le bus SPI.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-144">This `SpiDevice` represents the SPI bus.</span></span> <span data-ttu-id="3ddf9-145">La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-145">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="3ddf9-146">Une autre `using` déclaration crée une instance de `Mcp3008` et passe le `SpiDevice` dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-146">Another `using` declaration creates an instance of `Mcp3008` and passes the `SpiDevice` into the constructor.</span></span>
    - <span data-ttu-id="3ddf9-147">Une `while` boucle s’exécute indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-147">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="3ddf9-148">Chaque itération :</span><span class="sxs-lookup"><span data-stu-id="3ddf9-148">Each iteration:</span></span>
        1. <span data-ttu-id="3ddf9-149">Lit la valeur de CH0 sur le connecteur Active Directory en appelant `mcp.Read(0)` .</span><span class="sxs-lookup"><span data-stu-id="3ddf9-149">Reads the value of CH0 on the ADC by calling `mcp.Read(0)`.</span></span>
        1. <span data-ttu-id="3ddf9-150">Divise la valeur par 10,24.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-150">Divides the value by 10.24.</span></span> <span data-ttu-id="3ddf9-151">Le MCP3008 est un connecteur ADC 10 bits, ce qui signifie qu’il retourne 1024 valeurs possibles de 0-1023.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-151">The MCP3008 is a 10-bit ADC, which means it returns 1024 possible values ranging 0-1023.</span></span> <span data-ttu-id="3ddf9-152">La Division de la valeur par 10,24 représente la valeur sous la forme d’un pourcentage.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-152">Dividing the value by 10.24 represents the value as a percentage.</span></span>
        1. <span data-ttu-id="3ddf9-153">Arrondit la valeur à l’entier le plus proche.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-153">Rounds the value to the nearest integer.</span></span>
        1. <span data-ttu-id="3ddf9-154">Écrit la valeur dans la console sous forme de pourcentage.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-154">Writes the value to the console formatted as a percentage.</span></span>
        1. <span data-ttu-id="3ddf9-155">Veillez à 500 ms.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-155">Sleeps 500 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="3ddf9-156">Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-156">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./AdcTutorial
    ```

    <span data-ttu-id="3ddf9-157">Observez la sortie lorsque vous faites pivoter la composition du potentiomètre.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-157">Observe the output as you rotate the potentiometer dial.</span></span> <span data-ttu-id="3ddf9-158">Cela est dû au potentiomètre qui fait varier la tension fournie à CH0 sur le connecteur Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-158">This is due to the potentiometer varying the voltage supplied to CH0 on the ADC.</span></span> <span data-ttu-id="3ddf9-159">Le connecteur Active Directory compare la tension d’entrée sur CH0 à la tension de référence fournie à V<sub>ref</sub> pour générer une valeur.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-159">The ADC compares the input voltage on CH0 to the reference voltage supplied to V<sub>REF</sub> to generate a value.</span></span>

1. <span data-ttu-id="3ddf9-160">Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-160">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="3ddf9-161">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="3ddf9-161">Congratulations!</span></span> <span data-ttu-id="3ddf9-162">Vous avez utilisé SPI pour lire des valeurs à partir d’un convertisseur analogique-numérique.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-162">You've used SPI to read values from an analog-to-digital converter.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="3ddf9-163">Obtenir le code source</span><span class="sxs-lookup"><span data-stu-id="3ddf9-163">Get the source code</span></span>

<span data-ttu-id="3ddf9-164">La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span><span class="sxs-lookup"><span data-stu-id="3ddf9-164">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial).</span></span> <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a><span data-ttu-id="3ddf9-165">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3ddf9-165">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ddf9-166">Apprenez à utiliser usage général entrée/sortie pour faire clignoter une LED</span><span class="sxs-lookup"><span data-stu-id="3ddf9-166">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
