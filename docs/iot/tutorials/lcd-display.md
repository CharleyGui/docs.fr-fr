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
# <a name="display-text-on-an-lcd"></a>Afficher du texte sur un écran LCD

Les affichages de caractères LCD sont utiles pour afficher des informations sans avoir besoin d’un moniteur externe. Les affichages de caractères LCD courants peuvent être connectés directement aux broches GPIO, mais une telle approche nécessite l’utilisation d’un maximum de 10 broches GPIO. Pour les scénarios qui nécessitent une connexion à une combinaison d’appareils, le fait de ne pas voter autant de l’en-tête GPIO pour un affichage de caractères est souvent peu pratique.

De nombreux fabricants vendent des affichages de caractères 20x4 LCD avec un Expander GPIO intégré. L’affichage des caractères se connecte directement à l’expandeur GPIO, qui se connecte ensuite au Raspberry pi via le protocole série I2C (Inter-Integrated circuit).

Dans cette rubrique, vous allez utiliser .NET pour afficher du texte sur un écran LCD à l’aide d’un Expander GPIO I2C.

## <a name="prerequisites"></a>Prérequis

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- [affichage des caractères de l’écran LCD 20x4 avec l’interface I2C](https://www.bing.com/images/search?q=20x4+lcd+display+with+i2c)<span class="docon docon-navigate-external x-hidden-focus"></span>
- Câbles de liaison
- Pains (facultatif/recommandé)
- Tableau d’Raspberry pi GPIO (facultatif/recommandé)
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!NOTE]
> Il existe de nombreux fabricants d’affichages de caractères LCD. La plupart des conceptions sont identiques et le fabricant ne doit pas faire de différence avec les fonctionnalités. Pour référence, ce didacticiel a été développé avec le [LCD2004](https://www.sunfounder.com/lcd2004-module.html) <span class="docon docon-navigate-external x-hidden-focus"></span> .

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a>Préparer le matériel

Utilisez les câbles de cavalier pour connecter les quatre broches de l’expandeur GPIO I2C à Raspberry pi comme suit :

- Terre jusqu’au sol
- VCC à 5 v
- SDA à SDA (GPIO 2)
- SCL vers SCL (GPIO 3)

Reportez-vous aux figures suivantes en fonction des besoins :

| Interface I2C (arrière de l’affichage) | Raspberry pi GPIO |
|---------------------------------|-------------------|
| :::image type="content" source="../media/character-display-i2c-thumb.png" alt-text="Image de l’arrière de l’affichage de caractères affichant l’expandeur GPIO I2C." lightbox="../media/character-display-i2c.png"::: | :::image type="content" source="../media/gpio-pinout-diagram-thumb.png" alt-text="Diagramme montrant le pinout de l’en-tête Raspberry pi GPIO. Image Raspberry pi Foundation." lightbox="../media/gpio-pinout-diagram.png":::<br />[Image Raspberry pi Foundation](https://www.raspberrypi.org/documentation/usage/gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span> .
 |

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a>Créer l'application

Effectuez les étapes suivantes dans votre environnement de développement préféré :

1. Créez une application de console .NET à l’aide de l' [interface de commande .net](../../core/tools/dotnet-new.md) ou de [Visual Studio](../../core/tutorials/with-visual-studio.md). Nommez-le *LcdTutorial*.

    ```dotnetcli
    dotnet new console -o LcdTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. Remplacez le contenu du fichier *Program.cs* par le code suivant :

    :::code language="csharp" source="~/iot-samples/tutorials/LcdTutorial/Program.cs" :::

    Dans le code précédent :

    - Une [déclaration using](../../csharp/whats-new/csharp-8.md#using-declarations) crée une instance de `I2cDevice` en appelant `I2cDevice.Create` et en passant un nouveau `I2cConnectionSettings` avec les `busId` `deviceAddress` paramètres et. Cela `I2cDevice` représente le bus I2C. La `using` déclaration garantit que l’objet est supprimé et que les ressources matérielles sont libérées correctement.

        > [!WARNING]
        > L’adresse de l’appareil pour l’expandeur GPIO dépend de la puce utilisée par le fabricant. Les expandeurs GPIO équipés d’un PCF8574 utilisent l’adresse `0x27` , tandis que ceux utilisant des processeurs PCF8574A utilisent `0x3F` . Consultez la documentation de votre LCD.

    - Une autre `using` déclaration crée une instance de `Pcf8574` et passe le `I2cDevice` dans le constructeur. Cette instance représente l’Expander GPIO.
    - Une autre `using` déclaration crée une instance de `Lcd2004` pour représenter l’affichage. Plusieurs paramètres sont passés au constructeur décrivant les paramètres à utiliser pour communiquer avec l’Expander GPIO. L’Expander GPIO est passé en tant que `controller` paramètre.
    - Une `while` boucle s’exécute indéfiniment. Chaque itération :
        1. Efface l’affichage.
        1. Définit la position du curseur à la première position sur la ligne active.
        1. Écrit l’heure actuelle dans l’affichage à la position actuelle du curseur.
        1. Itère le compteur de ligne actuel.
        1. Veillez à 1000 ms.

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. Exécutez l’application sur le Raspberry pi en basculant vers le répertoire de déploiement et en exécutant l’exécutable.

    ```bash
    ./LcdTutorial
    ```

    Observez l’affichage des caractères de l’écran LCD lorsque l’heure actuelle s’affiche sur chaque ligne.

    > [!TIP]
    > Si l’affichage est allumé mais que vous ne voyez pas de texte, essayez de régler le contraste à l’arrière de l’affichage.

1. Arrêtez le programme en appuyant sur <kbd>Ctrl + C</kbd>.

Félicitations ! Vous avez affiché du texte sur un écran LCD à l’aide d’un I2C et d’un Expander GPIO !

## <a name="get-the-source-code"></a>Obtenir le code source

La source de ce didacticiel est [disponible sur GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/LcdTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> .

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Apprenez à utiliser usage général entrée/sortie pour faire clignoter une LED](../tutorials/blink-led.md)
