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
# <a name="blink-an-led"></a><span data-ttu-id="4b9bd-103">Faire clignoter une LED</span><span class="sxs-lookup"><span data-stu-id="4b9bd-103">Blink an LED</span></span>

<span data-ttu-id="4b9bd-104">Les codes confidentiels d’e/s à usage général (GPIO) peuvent être contrôlés individuellement.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-104">General-purpose I/O (GPIO) pins can be controlled individually.</span></span> <span data-ttu-id="4b9bd-105">Cela est utile pour contrôler les LED, les relais et d’autres appareils avec état.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-105">This is useful for controlling LEDs, relays, and other stateful devices.</span></span> <span data-ttu-id="4b9bd-106">Dans cette rubrique, vous allez utiliser .NET et les broches GPIO de Raspberry pi pour alimenter une LED et la faire clignoter à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-106">In this topic, you will use .NET and your Raspberry Pi's GPIO pins to power an LED and blink it repeatedly.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b9bd-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="4b9bd-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="4b9bd-108">LED 5 mm</span><span class="sxs-lookup"><span data-stu-id="4b9bd-108">5 mm LED</span></span>
- <span data-ttu-id="4b9bd-109">résistance 330 Ω</span><span class="sxs-lookup"><span data-stu-id="4b9bd-109">330 Ω resistor</span></span>
- <span data-ttu-id="4b9bd-110">Platine d’expérimentation</span><span class="sxs-lookup"><span data-stu-id="4b9bd-110">Breadboard</span></span>
- <span data-ttu-id="4b9bd-111">Câbles de liaison</span><span class="sxs-lookup"><span data-stu-id="4b9bd-111">Jumper wires</span></span>
- <span data-ttu-id="4b9bd-112">Tableau d’Raspberry pi GPIO (facultatif/recommandé)</span><span class="sxs-lookup"><span data-stu-id="4b9bd-112">Raspberry Pi GPIO breakout board (optional/recommended)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [ensure-ssh](../includes/ensure-ssh.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="4b9bd-113">Préparer le matériel</span><span class="sxs-lookup"><span data-stu-id="4b9bd-113">Prepare the hardware</span></span>

<span data-ttu-id="4b9bd-114">Utilisez les composants matériels pour créer le circuit comme illustré dans le diagramme suivant :</span><span class="sxs-lookup"><span data-stu-id="4b9bd-114">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-led_bb-thumb.png" alt-text="Diagramme Fritz montrant un circuit avec une LED et une résistance" lightbox="../media/rpi-led_bb.png":::

<span data-ttu-id="4b9bd-116">L’image ci-dessus décrit les connexions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b9bd-116">The image above depicts the following connections:</span></span>

- <span data-ttu-id="4b9bd-117">GPIO 18 vers LED anode (plus long, Lead positif)</span><span class="sxs-lookup"><span data-stu-id="4b9bd-117">GPIO 18 to LED anode (longer, positive lead)</span></span>
- <span data-ttu-id="4b9bd-118">Cathode à LED (plus petit, négatif) à la résistance 330 Ω (fin)</span><span class="sxs-lookup"><span data-stu-id="4b9bd-118">LED cathode (shorter, negative lead) to 330 Ω resistor (either end)</span></span>
- <span data-ttu-id="4b9bd-119">résistance de 330 Ω (autre extrémité) au sol</span><span class="sxs-lookup"><span data-stu-id="4b9bd-119">330 Ω resistor (other end) to ground</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="4b9bd-120">Créer l'application</span><span class="sxs-lookup"><span data-stu-id="4b9bd-120">Create the app</span></span>

<span data-ttu-id="4b9bd-121">Effectuez les étapes suivantes dans votre environnement de développement préféré :</span><span class="sxs-lookup"><span data-stu-id="4b9bd-121">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="4b9bd-122">Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4b9bd-122">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="4b9bd-123">Nommez-le *BlinkTutorial*.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-123">Name it *BlinkTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o BlinkTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="4b9bd-124">Remplacez le contenu du fichier *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4b9bd-124">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/BlinkTutorial/Program.cs" :::

    <span data-ttu-id="4b9bd-125">Dans le code précédent :</span><span class="sxs-lookup"><span data-stu-id="4b9bd-125">In the preceding code:</span></span>

    - <span data-ttu-id="4b9bd-126">Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `GpioController` .</span><span class="sxs-lookup"><span data-stu-id="4b9bd-126">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `GpioController`.</span></span> <span data-ttu-id="4b9bd-127">La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-127">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="4b9bd-128">Le pin GPIO 18 est ouvert pour la sortie</span><span class="sxs-lookup"><span data-stu-id="4b9bd-128">GPIO pin 18 is opened for output</span></span>
    - <span data-ttu-id="4b9bd-129">Une `while` boucle s’exécute indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-129">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="4b9bd-130">Chaque itération :</span><span class="sxs-lookup"><span data-stu-id="4b9bd-130">Each iteration:</span></span>
        1. <span data-ttu-id="4b9bd-131">Écrit une valeur dans le code confidentiel GPIO 18.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-131">Writes a value to GPIO pin 18.</span></span> <span data-ttu-id="4b9bd-132">Si `ledOn` a la valeur true, elle écrit `PinValue.High` (sur).</span><span class="sxs-lookup"><span data-stu-id="4b9bd-132">If `ledOn` is true, it writes `PinValue.High` (on).</span></span> <span data-ttu-id="4b9bd-133">Dans le cas contraire, il écrit `PinValue.Low` .</span><span class="sxs-lookup"><span data-stu-id="4b9bd-133">Otherwise, it writes `PinValue.Low`.</span></span>
        1. <span data-ttu-id="4b9bd-134">Veillez à 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-134">Sleeps 1000 ms.</span></span>
        1. <span data-ttu-id="4b9bd-135">Active ou désactive la valeur de `ledOn` .</span><span class="sxs-lookup"><span data-stu-id="4b9bd-135">Toggles the value of `ledOn`.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="4b9bd-136">Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-136">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./BlinkTutorial
    ```

    <span data-ttu-id="4b9bd-137">La LED clignote et est activée chaque seconde.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-137">The LED blinks off and on every second.</span></span>

1. <span data-ttu-id="4b9bd-138">Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-138">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="4b9bd-139">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="4b9bd-139">Congratulations!</span></span> <span data-ttu-id="4b9bd-140">Vous avez utilisé GPIO pour faire clignoter une LED.</span><span class="sxs-lookup"><span data-stu-id="4b9bd-140">You've used GPIO to blink an LED.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="4b9bd-141">Obtenir le code source</span><span class="sxs-lookup"><span data-stu-id="4b9bd-141">Get the source code</span></span>

<span data-ttu-id="4b9bd-142">La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="4b9bd-142">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/BlinkTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4b9bd-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4b9bd-143">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b9bd-144">En savoir plus sur la lecture des conditions environnementales d’un capteur</span><span class="sxs-lookup"><span data-stu-id="4b9bd-144">Learn how to read environmental conditions from a sensor</span></span>](../tutorials/temp-sensor.md)
