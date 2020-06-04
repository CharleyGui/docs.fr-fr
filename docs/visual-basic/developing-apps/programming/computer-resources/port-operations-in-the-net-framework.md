---
title: Opérations relatives au port dans .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 0ef0b8a7aec40603185d227d972cea655fd238c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360135"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Opérations relatives aux ports dans le .NET Framework avec Visual Basic

Vous pouvez accéder aux ports série de votre ordinateur par l’intermédiaire des classes .NET Framework dans l’espace de noms <xref:System.IO.Ports?displayProperty=nameWithType>. La classe la plus importante, <xref:System.IO.Ports.SerialPort>, fournit un framework pour les E/S synchrones et pilotées par événements, l’accès aux états d’épinglage et d’arrêt, et l’accès aux propriétés des pilotes séries. Elle peut être encapsulée dans un objet <xref:System.IO.Stream>, accessible par l’intermédiaire de la propriété <xref:System.IO.Ports.SerialPort.BaseStream>. L’encapsulage de <xref:System.IO.Ports.SerialPort> dans un objet <xref:System.IO.Stream> permet aux classes qui utilisent des flux d’accéder au port série. L’espace de noms contient des énumérations qui simplifient le contrôle des ports série.

Le moyen le plus simple de créer un objet <xref:System.IO.Ports.SerialPort> consiste à utiliser la méthode <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.

> [!NOTE]
> Vous ne pouvez pas utiliser les classes .NET Framework pour accéder directement aux autres types de ports, tels que les ports parallèles, les ports USB, etc.

## <a name="enumerations"></a>Énumérations

Ce tableau répertorie et décrit les principales énumérations utilisées pour accéder à un port série :

|Énumération|Description|
|---|---|
|<xref:System.IO.Ports.Handshake>|Spécifie le protocole de contrôle utilisé pour établir une communication de port série pour un objet <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.Parity>|Spécifie le bit de parité pour un objet <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialData>|Spécifie le type de caractère qui a été reçu sur le port série de l’objet <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialError>|Spécifie les erreurs qui se produisent sur l’objet <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.SerialPinChange>|Spécifie le type de changement qui s’est produit sur l’objet <xref:System.IO.Ports.SerialPort>.|
|<xref:System.IO.Ports.StopBits>|Spécifie le nombre de bits d’arrêt utilisés sur l’objet <xref:System.IO.Ports.SerialPort>.|

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Accès aux ports de l’ordinateur](accessing-the-computer-s-ports.md)
