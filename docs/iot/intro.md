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
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="4f84c-103">Développer des applications pour les appareils IoT avec les bibliothèques .NET IoT</span><span class="sxs-lookup"><span data-stu-id="4f84c-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="4f84c-104">.NET s’exécute sur une variété de plateformes et d’architectures.</span><span class="sxs-lookup"><span data-stu-id="4f84c-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="4f84c-105">Les tableaux IoT (Internet of Things) communs, tels que Raspberry pi et Hummingboard, sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4f84c-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="4f84c-106">Les applications IoT interagissent généralement avec un matériel spécialisé, tel que des capteurs, des convertisseurs analogiques-numériques et des appareils LCD.</span><span class="sxs-lookup"><span data-stu-id="4f84c-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="4f84c-107">Les bibliothèques .NET IoT activent ces scénarios.</span><span class="sxs-lookup"><span data-stu-id="4f84c-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="4f84c-108">Présentation vidéo</span><span class="sxs-lookup"><span data-stu-id="4f84c-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="4f84c-109">Bibliothèques</span><span class="sxs-lookup"><span data-stu-id="4f84c-109">Libraries</span></span>

<span data-ttu-id="4f84c-110">Les bibliothèques IoT .NET se composent de deux packages NuGet :</span><span class="sxs-lookup"><span data-stu-id="4f84c-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- <span data-ttu-id="4f84c-111">[System. Device. GPIO](https://www.nuget.org/packages/System.Device.Gpio/)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-111">[System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="4f84c-112">[IOT. Device. Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-112">[Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

### <a name="systemdevicegpio"></a><span data-ttu-id="4f84c-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="4f84c-113">System.Device.Gpio</span></span>

<span data-ttu-id="4f84c-114">`System.Device.Gpio` prend en charge divers protocoles pour l’interaction avec les broches matérielles de bas niveau pour contrôler les appareils.</span><span class="sxs-lookup"><span data-stu-id="4f84c-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="4f84c-115">notamment :</span><span class="sxs-lookup"><span data-stu-id="4f84c-115">These include:</span></span>

- <span data-ttu-id="4f84c-116">E/s à usage général (GPIO)</span><span class="sxs-lookup"><span data-stu-id="4f84c-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="4f84c-117">Inter-Integrated circuit (I2C)</span><span class="sxs-lookup"><span data-stu-id="4f84c-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="4f84c-118">Interface de périphérique série (SPI)</span><span class="sxs-lookup"><span data-stu-id="4f84c-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="4f84c-119">Modulation d’impulsions en largeur (PWM)</span><span class="sxs-lookup"><span data-stu-id="4f84c-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="4f84c-120">Port série</span><span class="sxs-lookup"><span data-stu-id="4f84c-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="4f84c-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="4f84c-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="4f84c-122">Le `Iot.Device.Bindings` Package :</span><span class="sxs-lookup"><span data-stu-id="4f84c-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="4f84c-123">Contient des [liaisons](https://github.com/dotnet/iot/blob/master/src/devices/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> d’appareil pour simplifier le développement d’applications en encapsulant System. Device. GPIO.</span><span class="sxs-lookup"><span data-stu-id="4f84c-123">Contains [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="4f84c-124">Est pris en charge par la communauté et des liaisons supplémentaires sont continuellement ajoutées.</span><span class="sxs-lookup"><span data-stu-id="4f84c-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="4f84c-125">Les liaisons d’appareils couramment utilisées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f84c-125">Commonly used device bindings include:</span></span>

- <span data-ttu-id="4f84c-126">[CharacterLcd-affichage des caractères de l’écran LCD](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-126">[CharacterLcd - LCD character display](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="4f84c-127">[SN74HC595-Registre de décalage 8 bits](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-127">[SN74HC595 - 8-bit shift register](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="4f84c-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="4f84c-129">[Pilote de matrice del Max7219](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-129">[Max7219 - LED Matrix driver](https://github.com/dotnet/iot/tree/master/src/devices/Max7219) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="4f84c-130">[Matrice LED RGBLedMatrix-RGB](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-130">[RGBLedMatrix - RGB LED Matrix](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="4f84c-131">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="4f84c-131">Supported operating systems</span></span>

<span data-ttu-id="4f84c-132">`System.Device.Gpio` est pris en charge sur la plupart des versions de Linux qui prennent en charge ARM/ARM64 et Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="4f84c-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="4f84c-133">Pour Raspberry pi, [Raspberry pi os](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> (anciennement Raspbian) est recommandé.  </span><span class="sxs-lookup"><span data-stu-id="4f84c-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  <span class="docon docon-navigate-external x-hidden-focus"></span> (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="4f84c-134">Plateformes matérielles prises en charge</span><span class="sxs-lookup"><span data-stu-id="4f84c-134">Supported hardware platforms</span></span>

<span data-ttu-id="4f84c-135">`System.Device.Gpio` est compatible avec la plupart des plateformes à un seul tableau.</span><span class="sxs-lookup"><span data-stu-id="4f84c-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="4f84c-136">Les plateformes recommandées sont Raspberry pi (2 et ultérieures) et Hummingboard.</span><span class="sxs-lookup"><span data-stu-id="4f84c-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="4f84c-137">Les autres plateformes connues pour être compatibles sont BeagleBoard et ODROID.</span><span class="sxs-lookup"><span data-stu-id="4f84c-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="4f84c-138">Les plateformes PC sont prises en charge via l’utilisation d’un pont USB vers SPI/I2C.</span><span class="sxs-lookup"><span data-stu-id="4f84c-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f84c-139">.NET n’est pas pris en charge sur les appareils d’architecture ARMv6, y compris les appareils Raspberry pi Zero et Raspberry pi antérieurs à Raspberry pi 2.</span><span class="sxs-lookup"><span data-stu-id="4f84c-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="4f84c-140">Ressources</span><span class="sxs-lookup"><span data-stu-id="4f84c-140">Resources</span></span>

- <span data-ttu-id="4f84c-141">[Bibliothèques .net IOT sur GitHub](https://github.com/dotnet/iot)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="4f84c-141">[.NET IoT Libraries on Github](https://github.com/dotnet/iot) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
