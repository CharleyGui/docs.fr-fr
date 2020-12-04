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
# <a name="read-values-from-an-analog-to-digital-converter"></a>Lire les valeurs d’un convertisseur analogique-numérique

Un convertisseur analogique-numérique (ADC) est un appareil qui peut lire une valeur de tension d’entrée analogique et la convertir en valeur numérique. L’ADCs est utilisé pour lire des valeurs à partir de thermistances, de potentiomètres et d’autres appareils qui modifient la résistance en fonction de certaines conditions.

Dans cette rubrique, vous allez utiliser .NET pour lire des valeurs à partir d’un connecteur ADC en modulant la tension d’entrée avec un potentiomètre.

## <a name="prerequisites"></a>Prérequis

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [MCP3008](https://www.microchip.com/wwwproducts/MCP3008) <span class="docon docon-navigate-external x-hidden-focus"></span> convertisseur analogique-numérique
- Potentiomètre à trois broches
- Platine d’expérimentation
- Câbles de liaison
- Tableau d’Raspberry pi GPIO (facultatif/recommandé)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

[!INCLUDE [prepare-pi-spi](../includes/prepare-pi-spi.md)]

## <a name="prepare-the-hardware"></a>Préparer le matériel

Utilisez les composants matériels pour créer le circuit comme illustré dans le diagramme suivant :

:::image type="content" source="../media/rpi-trimpot_spi-thumb.png" alt-text="Diagramme Fritz montrant un circuit avec un MCP3008 ADC et un potentiomètre" lightbox="../media/rpi-trimpot_spi.png":::

MCP3008 utilise l’interface de périphérique série (SPI) pour communiquer. Voici les connexions entre le MCP3008 et le Raspberry pi et potentiomètre :

- V<sub>JJ</sub> à 3.3 v (affichée en rouge)
- V<sub>ref</sub> à 3.3 v (rouge)
- AGND vers le sol (noir)
- CLK à SCLK (orange)
- D<sub>vers</sub> miso (orange)
- D<sub>dans</sub> Mosi (orange)
- CS/SHDN vers CE0 (vert)
- DGND vers le sol (noir)
- CH0 à la variable (au milieu) broche sur le potentiomètre (jaune)

Fournissez 3.3 V et sol aux broches extérieures sur le potentiomètre. L’ordre n’est pas important.

Reportez-vous aux diagrammes pinout suivants en fonction des besoins :

| MCP3008  | Raspberry pi GPIO |
|----------|-------------------|
| :::image type="content" source="../media/mcp3008-diagram-thumb.png" alt-text="Diagramme montrant le pinout du MCP3008" lightbox="../media/mcp3008-diagram.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Diagramme montrant le pinout de l’en-tête Raspberry pi GPIO. Image Raspberry pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br />[Image Raspberry pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/).
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Créer l'application

Effectuez les étapes suivantes dans votre environnement de développement préféré :

1. Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md). Nommez-le *AdcTutorial*.

    ```dotnetcli
    dotnet new console -o AdcTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Remplacez le contenu du fichier *Program.cs* par le code suivant :

    :::code language="csharp" source="~/iot-samples/tutorials/AdcTutorial/Program.cs" :::

    Dans le code précédent :

    - `hardwareSpiSettings` est défini sur une nouvelle instance de `SpiConnectionSettings` . Le constructeur affecte la valeur `busId` 0 au paramètre et la valeur `chipSelectLine` 0 au paramètre.
    - Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `SpiDevice` en appelant `SpiDevice.Create` et en passant `hardwareSpiSettings` . Cela `SpiDevice` représente le bus SPI. La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.
    - Une autre `using` déclaration crée une instance de `Mcp3008` et passe le `SpiDevice` dans le constructeur.
    - Une `while` boucle s’exécute indéfiniment. Chaque itération :
        1. Lit la valeur de CH0 sur le connecteur Active Directory en appelant `mcp.Read(0)` .
        1. Divise la valeur par 10,24. Le MCP3008 est un connecteur ADC 10 bits, ce qui signifie qu’il retourne 1024 valeurs possibles de 0-1023. La Division de la valeur par 10,24 représente la valeur sous la forme d’un pourcentage.
        1. Arrondit la valeur à l’entier le plus proche.
        1. Écrit la valeur dans la console sous forme de pourcentage.
        1. Veillez à 500 ms.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.

    ```bash
    ./AdcTutorial
    ```

    Observez la sortie lorsque vous faites pivoter la composition du potentiomètre. Cela est dû au potentiomètre qui fait varier la tension fournie à CH0 sur le connecteur Active Directory. Le connecteur Active Directory compare la tension d’entrée sur CH0 à la tension de référence fournie à V<sub>ref</sub> pour générer une valeur.

1. Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.

Félicitations ! Vous avez utilisé SPI pour lire des valeurs à partir d’un convertisseur analogique-numérique.

## <a name="get-the-source-code"></a>Obtenir le code source

La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/AdcTutorial). <span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Apprenez à utiliser usage général entrée/sortie pour faire clignoter une LED](../tutorials/blink-led.md)
