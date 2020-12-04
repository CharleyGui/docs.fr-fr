---
title: Développer des applications pour les appareils IoT avec les bibliothèques .NET IoT
description: Découvrez comment .NET peut être utilisé pour créer des applications pour les appareils IoT et les scénarios.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: c3d05ec5b05780f91404c3c27e91bcd602b0faeb
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "96588582"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a>Développer des applications pour les appareils IoT avec les bibliothèques .NET IoT

.NET s’exécute sur une variété de plateformes et d’architectures. Les tableaux IoT (Internet of Things) communs, tels que Raspberry pi et Hummingboard, sont pris en charge. Les applications IoT interagissent généralement avec un matériel spécialisé, tel que des capteurs, des convertisseurs analogiques-numériques et des appareils LCD. Les bibliothèques .NET IoT activent ces scénarios.

## <a name="video-overview"></a>Présentation vidéo

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a>Bibliothèques

Les bibliothèques IoT .NET se composent de deux packages NuGet :

- [System. Device. GPIO](https://www.nuget.org/packages/System.Device.Gpio/)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [IOT. Device. Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/)<span class="docon docon-navigate-external x-hidden-focus"></span>

### <a name="systemdevicegpio"></a>System.Device.Gpio

`System.Device.Gpio` prend en charge divers protocoles pour l’interaction avec les broches matérielles de bas niveau pour contrôler les appareils. notamment :

- E/s à usage général (GPIO)
- Inter-Integrated circuit (I2C)
- Interface de périphérique série (SPI)
- Modulation d’impulsions en largeur (PWM)
- Port série

### <a name="iotdevicebindings"></a>Iot.Device.Bindings

Le `Iot.Device.Bindings` Package :

* Contient des [liaisons](https://github.com/dotnet/iot/blob/master/src/devices/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> d’appareil pour simplifier le développement d’applications en encapsulant System. Device. GPIO.
* Est pris en charge par la communauté et des liaisons supplémentaires sont continuellement ajoutées.

Les liaisons d’appareils couramment utilisées sont les suivantes :

- [CharacterLcd-affichage des caractères de l’écran LCD](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [SN74HC595-Registre de décalage 8 bits](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [Pilote de matrice del Max7219](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)<span class="docon docon-navigate-external x-hidden-focus"></span>
- [Matrice LED RGBLedMatrix-RGB](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)<span class="docon docon-navigate-external x-hidden-focus"></span>

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

`System.Device.Gpio` est pris en charge sur la plupart des versions de Linux qui prennent en charge ARM/ARM64 et Windows 10 IoT Core.

> [!TIP]
> Pour Raspberry pi, [Raspberry pi os](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> (anciennement Raspbian) est recommandé.  

## <a name="supported-hardware-platforms"></a>Plateformes matérielles prises en charge

`System.Device.Gpio` est compatible avec la plupart des plateformes à un seul tableau. Les plateformes recommandées sont Raspberry pi (2 et ultérieures) et Hummingboard. Les autres plateformes connues pour être compatibles sont BeagleBoard et ODROID.

Les plateformes PC sont prises en charge via l’utilisation d’un pont USB vers SPI/I2C.

> [!IMPORTANT]
> .NET n’est pas pris en charge sur les appareils d’architecture ARMv6, y compris les appareils Raspberry pi Zero et Raspberry pi antérieurs à Raspberry pi 2.

## <a name="resources"></a>Ressources

- [Bibliothèques .net IOT sur GitHub](https://github.com/dotnet/iot)<span class="docon docon-navigate-external x-hidden-focus"></span>
