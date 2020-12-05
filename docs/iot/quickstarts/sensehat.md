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
# <a name="quickstart---use-net-to-drive-a-raspberry-pi-sense-hat"></a><span data-ttu-id="6d203-103">Démarrage rapide : utilisez .NET pour piloter une Raspberry pi Sense HAT</span><span class="sxs-lookup"><span data-stu-id="6d203-103">Quickstart - Use .NET to drive a Raspberry Pi Sense HAT</span></span>

<span data-ttu-id="6d203-104">Raspberry pi [sens Hat](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> (**H** matérielle **a** ttached on **T** op) est un tableau complémentaire pour Raspberry pi.</span><span class="sxs-lookup"><span data-stu-id="6d203-104">The Raspberry Pi [Sense HAT](https://www.raspberrypi.org/products/sense-hat/) <span class="docon docon-navigate-external x-hidden-focus"></span> (**H** ardware **A** ttached on **T** op) is an add-on board for Raspberry Pi.</span></span> <span data-ttu-id="6d203-105">Le chapeau de détection est équipé d’une matrice LED de 8 × 8 RGB, d’une manette à cinq boutons et comprend les capteurs suivants :</span><span class="sxs-lookup"><span data-stu-id="6d203-105">The Sense HAT is equipped with an 8×8 RGB LED matrix, a five-button joystick, and includes the following sensors:</span></span>

- <span data-ttu-id="6d203-106">Gyroscope</span><span class="sxs-lookup"><span data-stu-id="6d203-106">Gyroscope</span></span>
- <span data-ttu-id="6d203-107">Accéléromètre</span><span class="sxs-lookup"><span data-stu-id="6d203-107">Accelerometer</span></span>
- <span data-ttu-id="6d203-108">Magnétomètre</span><span class="sxs-lookup"><span data-stu-id="6d203-108">Magnetometer</span></span>
- <span data-ttu-id="6d203-109">Température</span><span class="sxs-lookup"><span data-stu-id="6d203-109">Temperature</span></span>
- <span data-ttu-id="6d203-110">Pression barométrique</span><span class="sxs-lookup"><span data-stu-id="6d203-110">Barometric pressure</span></span>
- <span data-ttu-id="6d203-111">Humidité</span><span class="sxs-lookup"><span data-stu-id="6d203-111">Humidity</span></span>

<span data-ttu-id="6d203-112">Ce guide de démarrage rapide utilise .NET pour récupérer les valeurs de capteur à partir de l’outil de détection de la manette de jeu, répondre à l’entrée de manette et piloter la matrice LED.</span><span class="sxs-lookup"><span data-stu-id="6d203-112">This quickstart uses .NET to retrieve sensor values from the Sense HAT, respond to joystick input, and drive the LED matrix.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d203-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="6d203-113">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="6d203-114">Sens de la détection</span><span class="sxs-lookup"><span data-stu-id="6d203-114">Sense HAT</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="run-the-quickstart"></a><span data-ttu-id="6d203-115">Exécuter le démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="6d203-115">Run the quickstart</span></span>

<span data-ttu-id="6d203-116">Attachez le chapeau de sens à votre Raspberry pi.</span><span class="sxs-lookup"><span data-stu-id="6d203-116">Attach the Sense HAT to your Raspberry Pi.</span></span> <span data-ttu-id="6d203-117">À partir d’une invite bash sur le Raspberry pi (local ou distant), exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6d203-117">From a Bash prompt on the Raspberry Pi (local or remote), run the following command:</span></span>

```bash
. <(wget -q -O - https://aka.ms/dotnet-iot-sensehat-quickstart)
```

<span data-ttu-id="6d203-118">La commande télécharge et exécute un script.</span><span class="sxs-lookup"><span data-stu-id="6d203-118">The command downloads and runs a script.</span></span> <span data-ttu-id="6d203-119">Le script :</span><span class="sxs-lookup"><span data-stu-id="6d203-119">The script:</span></span>

- <span data-ttu-id="6d203-120">Installe le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="6d203-120">Installs the .NET SDK.</span></span>
- <span data-ttu-id="6d203-121">Clone un référentiel GitHub qui comprend le projet de démarrage rapide de sens HAT.</span><span class="sxs-lookup"><span data-stu-id="6d203-121">Clones a GitHub repository that includes the Sense HAT quickstart project.</span></span>
- <span data-ttu-id="6d203-122">Génère le projet.</span><span class="sxs-lookup"><span data-stu-id="6d203-122">Builds the project.</span></span>
- <span data-ttu-id="6d203-123">Exécute le projet.</span><span class="sxs-lookup"><span data-stu-id="6d203-123">Runs the project.</span></span>

<span data-ttu-id="6d203-124">Observez la sortie de la console lorsque les données de capteur sont affichées.</span><span class="sxs-lookup"><span data-stu-id="6d203-124">Observe the console output as sensor data is displayed.</span></span> <span data-ttu-id="6d203-125">La matrice LED affiche un pixel jaune sur un champ de bleu.</span><span class="sxs-lookup"><span data-stu-id="6d203-125">The LED matrix displays a yellow pixel on a field of blue.</span></span> <span data-ttu-id="6d203-126">Le maintien de la manette dans n’importe quelle direction déplace le pixel jaune dans cette direction.</span><span class="sxs-lookup"><span data-stu-id="6d203-126">Holding the joystick in any direction moves the yellow pixel in that direction.</span></span> <span data-ttu-id="6d203-127">Lorsque vous cliquez sur le bouton de la manette de jeu, l’arrière-plan passe du bleu au rouge.</span><span class="sxs-lookup"><span data-stu-id="6d203-127">Clicking the center joystick button causes the background to switch from blue to red.</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="6d203-128">Obtenir le code source</span><span class="sxs-lookup"><span data-stu-id="6d203-128">Get the source code</span></span>

<span data-ttu-id="6d203-129">La source de ce guide de démarrage rapide est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart) <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="6d203-129">The source for this quickstart is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/quickstarts/SenseHat.Quickstart) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d203-130">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6d203-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6d203-131">Apprenez à utiliser usage général entrée/sortie pour faire clignoter une LED</span><span class="sxs-lookup"><span data-stu-id="6d203-131">Learn to use General Purpose Input/Output to blink an LED</span></span>](../tutorials/blink-led.md)
